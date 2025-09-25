# LLM

精读 [Llama 3 技术报告](https://arxiv.org/pdf/2407.21783)，回答以下几个问题。除此之外，也建议你写一些阅读过程中的感悟、疑问和思考。这会是一个加分项，但不强制要求。最终提交一个 Markdown 文件。

除了阅读论文本身之外，你也可能需要查阅其参考文献。你可以使用 AI 辅助阅读论文，但请不要让 AI 代替你思考。面试时可能会问到两轮笔试题中涉及的内容，因此不要投机取巧。

**最终提交的结果中不允许包含直接由 AI 生成的内容。请在充分理解相关知识后自行作答。**

1. 在 3.2 节中：
*We use grouped query attention (GQA) with 8 key-value heads to improve inference speed and to reduce the size of key-value caches during decoding.*
GQA 和通常的多头注意力有什么区别？“reduce the size of key-value caches” 的主要意义是什么？
2. 基于 3.2.1 节，用自己的话讲述 Llama 3 是如何确定其旗舰模型尺寸的。
3. 简要概括 3.3.2 节中提到的四种 parallelism 的主要特点。
4. 根据 3.4 节，Llama 3 的预训练分成几个阶段？你认为这种做法相比只设一个阶段有什么好处？
5. 为什么后训练的 LLM 需要 [chat template](https://www.llama.com/docs/model-cards-and-prompt-formats/llama3_1/#prompt-template)？
6. 根据 4.1 和 4.2 节，reward model 在整个后训练过程中起到什么作用？

有余力者可额外阅读 [DeepSeek-v3 技术报告](https://arxiv.org/pdf/2412.19437)。


# Answer(Detailed Ver.)
## 1.
- **MHA**(multi-head attention): every query head has its own key head and value head.
- **GQA**(grouped query attention): query heads are divided into groups, with each group sharing a key head and a value head.
Also,
- **MQA**(multi-query attention): multiple query heads share 1 key head and 1 value head.
So GQA is in some sense the compromising mixture of MHA and MQA, combining the gain in inference speed and stability.

"reduce the size of key-value caches" is mainly significant because: 
This shrinks the **KV cache** size, which leads to:
- **faster inference**: less data is transferred at each step of decoding
- **longer context**: smaller cache size will consume VRAM slower

>Joshua Ainslie, James Lee-Thorp, Michiel de Jong, Yury Zemlyanskiy, Federico Lebrón, and Sumit Sanghai. Gqa: Training generalized multi-query transformer models from multi-head checkpoints. arXiv preprint arXiv:2305.13245, 2023.
## 2.
1. They have a fixed pre-training compute budget($3.8*10^{25}$ FLOPs).
2. Run scaling laws experiments to identify a series of compute-optimal models, and use them to predict the optimal number of training tokens for a specific compute budget. They assume a relation between them: $$N^*(C)=AC^\alpha$$And fit A and α, getting (α, A) = (0.53, 0.29). Adopting this scaling law to $3.8*10^{25}$ FLOPs suggests training a 402B parameter model on 16.55T tokens.
3. (Not necessarily) observed relatively robustness to small changes in trade-offs(model size and training tokens), which helped they decide.
## 3.
**Parallelisms**:
- tensor P splits individual weight tensors into multiple chunks on different devices.
- pipeline P partitions the model vertically into stages by layers, so that different devices can process in parallel different stages of the full model pipeline.
- context P divides the input context into segments, reducing memory bottleneck for very long sequence length inputs.
- data P processes data in parallel on multiple GPUs and synchronizes after each training step. (FSDP here, fully sharded DP, shards the model, optimizer, and gradients while implementing data parallelism).
**Features**:
- modified PP:
    1. allows setting N(the number of contiguous micro-batches for the same stage’s forward or backward) flexibly
    2. reduce one Transformer layer each from the first and the last stages, respectively, to balance the pipeline
	3. use an interleaved schedule with V pipeline stages on one pipeline rank to reduce pipeline bubbles
	4. adopt asynchronous point-to-point communication, which speeds up  training
	5. deallocate tensors that won't be used later to reduce memory cost
- CP:
	- 1. adopt an all-gather based method, easier and more flexible to support different types of attention masks with the small latency
- Ordered config: \[TP, CP, PP, DP], is optimized for network communication
- Some numerical issues of parallelisms are fixed(like using FP32 gradient accumulation during backward computation over multiple micro-batches)
## 4.
**3 stages**:
1. Initial Pre-Training
2. Long Context Pre-Training
3. Annealing

**benefits**:
1. more stable. In stage 1, they start with a lower batch size and increase it subsequently, which proves to be very stable
2. able to adjust training data in different stages and gaps, which allows better performance on particular fields with less cost
3. separate the expensive compute in self-attention layers to a single stage, stage 2
4. the annealing stage (probably) tunes the parameters finer
## 5.
后训练的 LLM 需要 chat template，是因为模型需要一个标准化的对话协议来区分 system / user / assistant 的角色，保证多轮交互（尤其是包含工具调用等复杂场景）能被模型稳定理解和执行。

## 6.
### **Reward Model 的作用**

1. **作为后训练的核心骨干之一**
    
    - 整个对齐流程由 **预训练模型 + reward model** 共同构成。
        
    - reward model 是建立在预训练 checkpoint 之上的，使用人工偏好数据（preference data）进行训练。
        
2. **学习人类偏好**
    
    - 每个样本包含若干个模型回答：被选中的（chosen）、被拒绝的（rejected），有时还有人工编辑后的更优回答（edited）。
        
    - reward model 通过这些排序信息（edited > chosen > rejected）学会为不同回答打分，从而量化“人类更喜欢哪个”。
        
3. **为后续步骤提供信号**
    
    - **监督微调（SFT）**：reward model 用于对人类标注数据进行 _rejection sampling_，筛掉质量差的回答，只保留高分回答来训练语言模型。
        
    - **DPO（Direct Preference Optimization）**：reward model 的打分机制相当于隐含在优化目标中，帮助模型在对比正负回答时调整生成概率。
        
    - **数据质量控制**：reward model 还被用来清理带有错误推理步骤的训练样本，保证 finetuning 的数据有效性。
        
4. **贯穿多个训练循环**
    
    - 后训练不是一次性完成，而是分成多轮迭代（iterative rounds）。在每一轮里，都会重新收集新的 preference data，再训练或更新 reward model，用它来指导当轮的 SFT / DPO。
        

---

✅ **一句话总结**：  
Reward model 在 Llama 3 的后训练中起到“人类偏好打分器”的作用，它把人工偏好转化为数值信号，贯穿数据筛选、SFT、DPO 和多轮迭代，确保最终语言模型的回答更符合人类预期。
