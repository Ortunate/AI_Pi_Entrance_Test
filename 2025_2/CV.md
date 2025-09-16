# CV第二轮题目  
计算机视觉领域的发展离不开强大的特征提取骨干网络（Backbone）。从以ResNet为代表的卷积神经网络（CNN）到以Vision Transformer（ViT）为代表的注意力模型，这些基础模型的演进深刻地影响了下游任务的性能。近年来，将视觉与语言等其他模态相结合的多模态学习，特别是视觉-语言预训练（Vision-Language Pre-training），已成为人工智能领域最热门的方向之一，其核心思想也是将强大的视觉骨干网络与语言模型进行有效对齐和融合。

**任务要求：**

1. **阅读至少4篇核心论文**，论文选择需满足：
   - **至少1篇** 视觉基础骨干网络论文
   - **至少2篇** 关键的视觉-语言多模态论文。
   - 第4篇及以后可**自由选择**，可以是**我列出的论文**，也可以是相关领域的**综述**、或者**对前述论文进行改进的模型**。**如果你对CV其他的领域感兴趣，也可以将第四篇文章换为其他的（例如你对3d重建很感兴趣，你也可以看类似nerf或是3dgs等工作；或者如果你对目标检测感兴趣，那么你可以阅读yolo等相关的论文）**
2. 对每一篇您选择的论文，关注并回答以下问题，撰写一份报告：
   1. 文章关注了什么**问题**，以及为什么这个问题重要；
   2. **前人**都是怎么做的，以及他们做的有哪些问题；
   3. 这篇文章做了什么，他具体是**怎么做**的；
   4. 作者怎么通过**实验**证明自己方法的有效性的；
   5. 你对这篇文章的点评，**点评**好的地方和不足的地方。
3. 读完所有文章后，**对于你感兴趣的方向，根据自己所学的知识，提出自己的思考**，包括但不限于1）前人做的工作什么地方好，什么地方不好；2）前人做的不好的地方，我们能在前人的基础上改进什么；3）前人做的好的地方，我们能借鉴过来做什么？4)如果让你来做一个新工作，你打算怎么做。（**可选**，这是一个加分项，也是对自己阅读过的内容的一个总结，但是如果对您来说**时间较为紧张**，那么可以不做这个）
4. 请注意，撰写报告的过程也是您深度理解和吸收知识的过程。**论文可以借助AI辅助阅读和理解，但所有分析和点评必须由您独立思考和撰写**。
5. 最终请将你所有的内容汇集到一个.md文档中并上交。如果你在.md文档中配图，那么你可以将其导出为pdf提交

### **核心论文推荐列表**

以下列表推荐了在这些领域具有里程碑意义的论文。**如果您对这些核心论文已经非常熟悉，可以选择其他您感兴趣且相关的经典或前沿工作进行研读分析。**

#### **方向一：视觉基础骨干网络 (至少选择一篇，推荐至少选择ViT)**

1. **ResNet**: *Deep Residual Learning for Image Recognition*
2. **Vision Transformer (ViT)**: *An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale*

#### **方向二：视觉-语言多模态模型 (至少选择两篇)**

1. **CLIP**: *Learning Transferable Visual Models From Natural Language Supervision*（该文章可能会比较长，但是其思想相对简单，如果读起来过于耗时费力，可以选择相关的讲解视频观看或者是讲解文章，**只要能弄懂所有的内容即可**）
2. **BLIP**: *BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation* （这是CLIP的升级版）
3. **BLIP-2:** *Bootstrapping Language-Image Pre-training with Frozen Image Encoders and Large Language Models* （这是将BLIP模型与LLM相结合的先例）
4. **LLaVA**: *Visual Instruction Tuning*（这是一个简洁高效的baseline，并首次在MLLM领域提出instruction tuning）
5. **Qwen2.5-VL** Technical Report（这是现在比较先进的开源MLLM的技术报告，推荐在阅读过前面的BLIP-2或是LLaVA进行阅读）

### 阅读工具

为了更高效的阅读论文，你可能需要以下工具：

#### **Zotero**

- **简介**：一个免费、开源的文献管理阅读软件，可以帮助您轻松收集、组织、引用和分享您的研究资源。
- **核心功能**：通过浏览器插件一键抓取网页和PDF、多设备同步、标签化管理等。

#### **Translate for Zotero**

- 搭配上面的zotero使用的翻译插件，可以直接翻译，更加便利
- https://zotero-chinese.com/user-guide/plugins/translate/

#### **Awesome GPT for Zotero**

- Awesome GPT for Zotero使得用户能够通过命令标签使用 Meet API，进一步增强 Zotero 与 GPT 模型的集成。

- https://zotero-chinese.com/user-guide/plugins/zotero-gpt

