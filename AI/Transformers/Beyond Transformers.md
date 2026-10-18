We've learned about [[Transformers]]. Now what?


Decoder-Only models are usually pre-trained on a vast corpus of language data, often encompassing a substantial portion of text available on the internet. The primary task during this pre-training phase is to predict the next word in each sequence of text. This extensive training enables the model to understand and generate human-like text. After pre-training, these models can be fine-tuned for specific tasks. This fine-tuning, done through ==methods like Instruction Tuning or Reinforcement Learning from Human Feedback (RHLF),== tailors the model for applications such as question-answering systems, virtual assistants, or dialogue-based systems.
> Source: https://medium.com/@prashunjaveri/gpt-architecture-0415e7a5796d

# Brief State-of-the-Art

**Tokenization**
- Byte-Pair Encoding (BPE), WordPiece, SentencePiece, Unigram
**Token and Position embeddings**
- Fixed and Learnable Positional Embeddings, Rotary Position Embedding (RoPE)
**Decoder Blocks (masked multiheaded attention)**
- Multi-head Latent Attention (MLA)
**Classification head**
- Usually by means of a linear layer followed by softmax
**Model training (Predicting the next token)**
- Teacher Forcing, [multi-token prediction](https://www.unite.ai/es/supercharging-large-language-models-with-multi-token-prediction/?utm_source=chatgpt.com)
**Model Evaluation**
- Perplexity, Accuracy, F1 Score, benchmarks (GLUE, SuperGLUE, ...)
**Model Inference**
- Temperature based sampling, Top K sampling, Top P sampling)
**Applications, Emerging Challenges & Future Directions**
- https://arxiv.org/pdf/2305.10435



## Interesting Related Reads

Democratizing Financial Knowledge with ChatGPT by OpenAI: Unleashing the Power of Technology [[SSRN-id4346152.pdf]]