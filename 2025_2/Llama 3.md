# 0.
This paper presents:
1. Llama 3, a "new"(in 2024) set of foundation models, whose component models natively support multilinguality, coding, reasoning, and tool usage.
2. An extensive empirical evaluation of Llama 3.
3. The results of experiments in which they integrate image, video, and speech capabilities into Llama 3 via a compositional approach.
# 1. Intro
The **development** of modern foundation models(FM) comprises:
1. **a pre-training stage**. The model is trained at massive scale using simple tasks(like next-word prediction);
2. **a post-training stage**. Tune the model to follow instructions align with human preferences, and improve specific capabilities(e.g. coding).
---
3 key levers in the development of high-quality FM:
1. **Data**: size$\uparrow$, performance$\uparrow$
2. **Scale**: same
3. **Managing complexity**: standard, simpler, more stable.(Adopted a post-training procedure based on SFT, RS and DPO)

results.
# 2. General Overview
More intro on the development mentioned in [Chapter 1](#(%20)1.);
The approach they perform experiments of adding image, video, and speech capabilities comprises 3 additional stages:
- Multi-modal encoder pre-training
- Vision adapter training
- Speech adapter training

# 3. Pre-Training
## 3.1 Pre-Training Data
### 3.1.1 Web Data Curation
- PII and safety filtering
- Text extraction and cleaning
- De-duplication
- Heuristic filtering
- Model-based quality filtering
- Code and reasoning data
- Multilingual data
### 3.1.2 Determining the Data Mix
- Knowledge classification
- Scaling laws for data mix
- Data mix summary: general(50%), math/reasoning(25%), code(17%), multilingual(8%)
### 3.1.3 Annealing Data
## 3.2 Model Architecture
Few small modifications compared to Llama 2:
- GQA with 8 key-value heads
- attention mask(important on very long sequences)
- a vocabulary with 128K tokens
- RoPE base frequency 500,000
model size.
### 3.2.1 Scaling Laws
considering: compute budget and forecasting model's performance
**methodology** to develop **scaling laws** that accurately predict downstream(DS) benchmark performance and select **pre-training data mix**:
1. establish a correlation between compute-optimal(CO)'s negative log-likelihood on DS tasks('A') and training FLOPs.
2. correlate 'A' with task accuracy utilizing scaling law models and older models(high FLOPs).
--- 
Determine size:
1. Run scaling law experiments to identify a series of compute-optimal models, and use them to predict the optimal number of training tokens for a specific compute budget, thus getting a scaling law.
2. adopt it to the budget.
3. observed relatively robustness to small changes in trade-offs(model size and training tokens).
## 3.3 Infrastructure, Scaling, and Efficiency
hardware and infrastructure
### 3.3.1 Training Infrastructure
- compute
- storage
- network
### 3.3.2 Parallelism for Model Scaling
4D parallelism: efficiently distributes computation and ensures each GPU's computational results fit in its HBM.
**Parallelisms**:
- tensor P splits individual weight tensors into multiple chunks on different devices.
- pipeline P partitions the model vertically into stages by layers, so that different devices can process in parallel different stages of the full model pipeline.
- context P divides the input context into segments, reducing memory bottleneck for very long sequence length inputs.
- data P processes data in parallel on multiple GPUs and synchronizes after each training step. (FSDP here, fully sharded DP, shards the model, optimizer, and gradients while implementing data parallelism).
---
**GPU utilization**
**PP challenges**:
1. Batch size constraint
2. Memory imbalance
3. Computation imbalance
**Features**:
- modified PP:
    1. allows setting N(the number of contiguous micro-batches for the same stage’s forward or backward) flexibly   // *Figure 6, didn't understand how*
    2. reduce one Transformer layer each from the first and the last stages, respectively, to balance the pipeline
	3. use an interleaved schedule with V pipeline stages on one pipeline rank to reduce pipeline bubbles
	4. adopt asynchronous point-to-point communication, which speeds up  training
	5. deallocate tensors that won't be used later to reduce memory cost
- CP:
	- 1. adopt an all-gather based method, introduced communication latency. But it is easier and more flexible to support different types of attention masks, and the latency is small
**Network-aware parallelism configuration**
**Numerical stability**
### 3.3.3 Collective Communication
### 3.3.4 Reliability and Operational Challenges
## 3.4 Training Recipe
3 stages
### 3.4.1 Initial Pre-Training
- use a lower batch size early in training to improve training stability, and increase it subsequently to improve efficiency
- Adjusting the data mix
### 3.4.2 Long Context Pre-Training
- increase the supported context length in increments, pre-training until the model has successfully adapted to the increased context length
- judge by:
	1. short-context evaluations
	2. “needle in a haystack” tasks
### 3.4.3 Annealing
- linearly annealed the learning rate to 0, maintaining a context length of 128K tokens
- also adjusted the data mix to upsample data sources of very high quality
- finally compute the average of **model checkpoints** during annealing to produce the final pre-trained model
## 4 Post-Training
rounds of post-training/human feedback -> aligned model
post-training involves SFT followed by DPO
## 4.1 Modeling
	backbone = reward_model + language_model
### 4.1.1 Chat Dialog Format
	define a chat dialog protocol
	design a multi-message chat protocol with sp header and termination tokens
### 4.1.2 Reward Modeling
### 4.1.3 Supervised Finetuning
### 4.1.4 DPO
### 4.1.5 Model Averaging
### 4.1.6 Iterative Rounds
## 4.2 Post-training Data
The post-training data composition plays a critical role in the usefulness and behavior of language models.
### 4.2.1 Preference Data
### 4.2.2 SFT Data
### 4.2.3 Data Processing and Quality Control

