# NLP组

### 说明

- **Task3 以及 Task4 为附加的可选题，不要求完成**，学有余力的同学可以尝试。
- 你需要为每个完成的任务提交一份说明文档及相关代码，模型文件以及数据集无需提交。
- 在学习过程中，请做好相关笔记或者记录。
- 我们不对准确率和模型结果作出硬性要求，请不要过于纠结调参，重点在于你在实现过程中获得的知识和收获。
- **使用AI**或者他人的代码框架辅助实现都是可以的，但你**需要确保理解了代码每个部分的内容**。
- 如果计算资源有限，可以在[google Colab](https://colab.research.google.com/)（单 session 限制12小时，显存 12-16GB）, [Kaggle](https://www.kaggle.com/)（每周30h免费）或者[autodl](https://www.autodl.com/)等平台租用服务器。遇到任何问题都可以联系出题人。
- 面试的时候需做相应的展示以及讲解。

## Task 1 NLP基本任务

### 前置知识

在这个任务中，我们希望你可以学会和复习NLP的一些基础核心知识。

1. **序列建模与循环神经网络 :**
  - **RNN核心思想:** 理解RNN如何通过循环结构处理序列数据，并认识到其存在的问题。
  - **LSTM / GRU:** 理解LSTM（长短期记忆网络）和GRU（门控循环单元）。
2. **常见的评估指标:**
  - 理解除了准确率（Accuracy）之外，精确率（Precision）、召回率（Recall）和 F1-Score 等指标的含义。

### 数据集说明

- 来源：ModelScope [数据集](https://www.modelscope.cn/datasets/chqingMS/game_chat)`chqingMS/game_chat`，包含游戏场景中的用户聊天文本及标签。结构：数据集分为训练集和验证集，每条数据包含`sentence`（聊天文本）和`label`（类别标签）。
- 任务：根据聊天文本预测其对应的类别标签（多分类任务）。

### 实践任务

使用 PyTorch框架构建 LSTM模型，对`chqingMS/game_chat`数据集的游戏聊天文本进行分类，根据聊天内容预测其所属类别。通过完整的文本处理、模型训练与多维度评估，掌握序列分类的核心流程，并基于评估结果分析模型性能瓶颈。



## Task 2 预训练模型

### 前置知识

1. **预训练-微调范式 :**

	- **预训练 (Pre-training):** 理解其本质是在海量无标签文本上进行自监督学习。

	- **微调 (Fine-tuning):** 掌握如何在一个预训练好的模型基础上，利用少量有标签的下游任务数据来调整模型参数，使其适配特定任务。

2. **主流预训练模型架构:**
	- 熟悉预训练模型的三种常见架构：Encoder-Only，Decoder-Only 以及 Encoder-decoder。了解他们的特点，常见的应用场景以及经典模型。

### 实践任务

1. 基于与**Task1 相同**的数据集，使用 PyTorch 及开源预训练库，使用预训练的**BERT模型**完成文本分类微调，掌握预训练模型的调用与微调核心流程。
2. 比较部分冻结层和全量微调的区别。



## Task 3 提示词工程与RAG （选做）

### 前置知识

1. **大语言模型与提示词工程:**
	- 理解提示词工程如何引导LLM完成特定任务、生成特定格式输出的技术。
	
	- 了解零样本（Zero-shot）、少样本（Few-shot）和思维链（Chain-of-Thought）等主流提示词策略。
	
	- 熟悉如何通过API接口与大语言模型进行交互。
	
2. **检索增强生成 (Retrieval-Augmented Generation - RAG):**

	- 理解RAG如何帮助大模型解决问题。

	- 掌握基础RAG实现的流程（文档加载、文本分割、构建向量数据库、向量数据库检索、结合检索结果生成回答）。

### 数据集

使用学校的研究生手册作为[数据集](https://gs.hust.edu.cn/info/1137/6338.htm)，完成任务。

### 实践任务

1. 提示词构建问答数据集
	- 基于提示词从特定文档中自动构建问答（QA）数据集。
	- 设计提示词以明确大模型的任务边界以及输出格式的约束；
	- 理解长文本分割的必要性及策略，以适配大模型的上下文长度限制；
	- 工具支持：可使用阿里云提供的免费 API 调用大模型或者私戳出题人提供。
	
2. RAG知识问答
	- 理解检索增强生成（RAG）技术在知识问答中的应用原理与核心环节相关知识。
	
	- 使用API以及研究生手册文档或自主构建的QA数据集实现RAG 的基本流程，使其可以对研究生手册或QA数据集进行知识问答。
	
		

## Task 4 微调技术（选做）

### 前置知识

1. **监督微调 (SFT):**
	- 明确SFT的目标，并熟悉其典型的数据格式。

2. **LoRA 技术原理 :**

	- 掌握LoRA通过低秩适配来模拟权重更新的核心思想。

	- 理解其关键超参数的作用及其对模型训练的影响。

3. **训练优化技术:**
	- 了解在计算资源有限时进行模型训练的常用技术，如梯度累积、混合精度训练或模型量化的工作原理。

### 实践任务

利用 LoRA 技术对 `Qwen/Qwen2.5-0.5B-Instruct` 模型进行监督微调，使其能够准确回答关于《华中科技大学学生手册》的内容。

**数据集:** `alleyf/HUST-Student-Handbook` ([数据集](https://www.modelscope.cn/datasets/alleyf/HUST-Student-Handbook/files))，也可以用Task 3自己构建的数据集

- 在实际微调中，常会遇到因资源不足导致无法训练的问题。除了选择更小的基础模型外，请至少列举并说明**两种**可以在代码层面实现的、用于缓解显存压力的训练技巧，并简述它们的基本工作原理。

- 思考应该如何全面、客观地衡量其微调后的效果？尝试设计一个评估方案。



## 课程资料与论文阅读

[吴恩达深度学习课程第五课](https://www.bilibili.com/video/BV1F4411y7BA)：包含RNN及其变体，word embedding以及seq2seq等知识

**BERT原始论文**：BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

**GPT-3**：Language Models are Few-Shot Learners

**T5**: Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer

**RAG首次提出**: Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks

**LoRA**: Low-Rank Adaptation of Large Language Models

**其他博客：**https://github.com/graykode/nlp-tutorial/tree/master
