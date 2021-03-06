## Compositional Attention Networks for Machine Reasoning

### Indexing:
- [Introduction](#Introduction)
- [The MAC Network](#The-MAC-Network)
- [Experiments](#Experiments)
- [References](#References)
---
### Introduction
**Overview**
- Proposed MAC network, a fully differentiable neural network architecture, designed to facilitate **explicit and expressive reasoning**.
- Proposed model approaches problems by decomposing them into a series of **attention-based reasoning steps**.
- Each step performed by Memory Attention Composition (MAC) cell that maintains **control and memory**

**Problems of former Symbolic methods**
- Rely on **externally provided structured representations and functional programs**, brittle handcrafted parsers or expert demonstrations.
- Require relatively **complex** multi-stage reinforcement learning **training schemes**.

**Merits**
- State-of-the-art accuracy on CLEVR
- Computationally-efficient
- Data-efficient
- Can be adapted to novel situations and diverse language.
- The universal design of the MAC cell serves as a **structural prior** that encourages the network to solve problems by **decomposing them intoa sequence of attention-based reasoning operations** that are directly inferred from the data.
---
### The MAC Network
**Components**
- An input unit
- The core recurrent network with $p$ MAC cells
- An output unit

**Task definition**
- Given a knowledge base $K$ (for VQA, an image)
- Given a task description $q$ (for VQA, a question)
- Model infers a decomposition into a series of $p$ reasonng operations that 
- Interact with the knowledge base
- Iteratively aggregating and manipulating information to perform the task.

#### The Input Unit
- Transform the raw inputs into distributed vector representations.
- Question: word embedding; d-dimensional biLSTM
- Image: ResNet101; 

#### The MAC Cell
- A recurrent cell to capture the **atomic and universal** reasoning operation.
- $i^{th}$ cell maintains hidden states: control $c_i$ and memory $m_i$
- Control $c_i$ represents the reasoning operation, accomplished by a soft attention-based weighted average of question
- Memory $m_i$ computed recurrently by integrating the preceding hidden state with new information

#### The Control Unit
- Identifies a series of operations

#### The Read Unit
- Extracts relevant information from a given knowledge base

#### The Write Unit
- Integrates the information into memory 

#### The Output Unit
- Predicts the final answer to the question based on the question representation and final memory.

---
### Experiments
**Results on CLEVR Dataset**
- State-of-the-art results on overall accuracy especially for the **numerical questions**

**CLEVR Humans and Error Analysis**
- State-of-the-art results on CLEVR Humans

**Ablations**
- Question Attention: using attention over the question words is highly effective
- Control and Memory: Worse performance while shared weighting.

---
### Rerences
- [Compositional Attention Networks for Machine Reasoning](https://arxiv.org/pdf/1803.03067.pdf)

---
