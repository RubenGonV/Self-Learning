---
tags:
  - Self-learning
First Created: 2026-01-12T11:08:00
Sources:
  - https://www.ibm.com/think/topics/retrieval-augmented-generation
  - https://www.databricks.com/sites/default/files/2024-05/2024-05-EB-A_Compact_GuideTo_RAG.pdf
---
---
# INTRODUCTION

Retrieval augmented generation, or RAG, is an architecture for optimizing the performance of an artificial intelligence (AI) model by connecting it with external knowledge bases. RAG helps large language models (LLMs) deliver more relevant responses at a higher quality.


## Benefits

> [!check] 
> - Cost-efficient AI implementation and AI scaling
> - Access to current domain-specific data
> - Lower risk of AI hallucinations
> - Increased user trust
> - Expanded use cases
> - Enhanced developer control and model maintenance
> - Greater data security

### Cost-efficient AI implementation and AI scaling
When implementing AI, most organizations **first select a foundation model**: the deep-learning models that serve as the basis for the development of more advanced versions. 
Foundation models typically have generalized knowledge bases populated with publicly available training data, such as internet content available at the time of training.

Retraining a foundation model or fine-tuning it—where a foundation model is further trained on new data in a smaller, domain-specific dataset—is computationally expensive and resource-intensive. The model adjusts some or all of its parameters to adjust its performance to the new specialized data.

With RAG, enterprises can use internal, authoritative data sources and gain similar model performance increases without retraining. Enterprises can scale their implementation of AI applications as needed while mitigating cost and resource requirement increases.

### Access to current and domain-specific data
Generative AI models have a _knowledge cutoff,_ the point at which their training data was last updated. As a model ages further past its knowledge cutoff, it loses relevance over time. RAG systems connect models with supplemental external data in real-time and incorporate up-to-date information into generated responses.

RAG models can also connect to the internet with application programming interfaces (APIs) and gain access to real-time social media feeds and consumer reviews for a better understanding of market sentiment. Meanwhile, access to breaking news and search engines can lead to more accurate responses as models incorporate the retrieved information into the text-generation process.

### Lower risk of AI hallucinations
Generative AI models such as OpenAI’s GPT work by detecting patterns in their data, then using those patterns to predict the most likely outcomes to user inputs. Sometimes models detect patterns that don’t exist. A hallucination or confabulation happens when models present incorrect or made-up information as though it is factual.

RAG anchors LLMs in specific knowledge backed by factual, authoritative and current data. Compared to a generative model operating only on its training data, RAG models tend to provide more accurate answers within the contexts of their external data. While RAG can reduce the risk of hallucinations, it cannot make a model error-proof.

### Increased user trust
Chatbots, a common generative AI implementation, answer questions posed by human users. For a chatbot such as ChatGPT to be successful, users need to view its output as trustworthy. RAG models can include citations to the knowledge sources in their external data as part of their responses.

### Expanded use cases
Access to more data means that one model can handle a wider range of prompts. Enterprises can optimize models and gain more value from them by broadening their knowledge bases, in turn expanding the contexts in which those models generate reliable results.

By combining generative AI with retrieval systems, RAG models can retrieve and integrate information from multiple data sources in response to complex queries.


### Enhanced developer control and model maintenance
Modern organizations constantly process massive quantities of data, from order inputs to market projections to employee turnover and more. Effective data pipeline construction and data storage is paramount for strong RAG implementation.

At the same time, developers and data scientists can tweak the data sources to which models have access at any time. Repositioning a model from one task to another becomes a task of adjusting its external knowledge sources as opposed to fine-tuning or retraining. If fine-tuning is needed, developers can prioritize that work instead of managing the model’s data sources.


### Greater data security
Because RAG connects a model to external knowledge sources rather than incorporating that knowledge into the model’s training data, it maintains a divide between the model and that external knowledge. Enterprises can use RAG to preserve first-party data while simultaneously granting models access to it—access that can be revoked at any time.

However, enterprises must be vigilant to maintain the security of the external databases themselves. RAG uses vector databases, which use embeddings to convert data points to numerical representations. If these databases are breached, **==attackers can reverse the vector embedding process and access the original data, especially if the vector database is unencrypted.==**

---
## Use cases

- Specialized chatbots and virtual assistants  
- Research  
- Content generation  
- Market analysis and product development  
- Knowledge engines  
- Recommendation services

---

## How does RAG work?

RAG works by combining information retrieval models with generative AI models to produce more authoritative content. RAG systems query a knowledge base and add more context to a user prompt before generating a response.

Standard LLMs source information from their training datasets. RAG adds an information retrieval component to the AI workflow, gathering relevant information and feeding that to the generative AI model to enhance response quality and utility.

RAG systems follow a five-stage process:
![[Pasted image 20260112123052.png]]
1. The user submits a prompt.  
2. The information **retrieval** model queries the knowledge base for relevant data.  
3. Relevant information is returned from the knowledge base to the integration layer.  
4. The RAG system engineers an **augmented** prompt to the LLM with enhanced context from the retrieved data.  
5. The LLM **generates** an output and returns an output to the user.

## Components of a RAG system

RAG systems contain four primary components:

- The **knowledge base**: The external data repository for the system.
- The **retriever**: An AI model that searches the knowledge base for relevant data.
- The **integration layer**: The portion of the RAG architecture that coordinates its overall functioning.
- The **generator**: A generative AI model that creates an output based on the user query and retrieved data.

Other components might include a _ranker_, which ranks retrieved data based on relevance, and an _output handler_, which formats the generated response for the user.

### The knowledge base

The first stage in constructing a RAG system is creating a queryable knowledge base.

RAG systems use a process called embedding to transform data into numerical representations called vectors.

Knowledge bases must be continually updated to maintain the RAG system’s quality and relevance.

LLM inputs are limited to the context window of the model: the amount of data it can process without losing context. _Chunking_ a document into smaller sizes helps ensure that the resulting embeddings will not overwhelm the context window of the LLM in the RAG system.

Chunk size is an important hyperparameter for the RAG system. When chunks are too large, the data points can become too general and fail to correspond directly to potential user queries. But if chunks are too small, the data points can lose semantic coherency.

### The retriever

Vectorizing the data prepares the knowledge base for semantic vector search, a technique that identifies points in the database that are similar to the user’s query. Semantic search machine learning algorithms can query massive databases and quickly identify relevant information, reducing latency as compared to traditional keyword searches.

The information retrieval model transforms the user’s query into an embedding and then searches the knowledge base for similar embeddings. Then, its findings are returned from the knowledge base.

### The integration layer

The integration layer is the center of the RAG architecture, coordinating the processes and passing data around the network. With the added data from the knowledge base, the RAG system creates a new prompt for the LLM component. This prompt consists of the original user query plus the enhanced context returned by the retrieval model.

RAG systems employ various prompt engineering techniques to automate effective prompt creation and help the LLM return the best possible response. Meanwhile, LLM orchestration frameworks such as the open source LangChain and LlamaIndex or IBM® watsonx Orchestrate™ govern the overall functioning of an AI system.

### The generator

The generator creates an output based on the augmented prompt fed to it by the integration layer. The prompt synthesizes the user input with the retrieved data and instructs the generator to consider this data in its response. Generators are typically pretrained language models, such as GPT, Claude or Llama.

---
