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
