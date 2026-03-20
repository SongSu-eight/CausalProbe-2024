# Revisiting Causal Reasoning in Large Language Models under Resource-Constrained Inference

This repository reproduces and extends the experiments from:

> Chi et al., 2024  
> *Unveiling Causal Reasoning in Large Language Models: Reality or Mirage?*  
> NeurIPS 2024

We evaluate causal reasoning performance of large language models on the **CausalProbe-2024 benchmark** under a **resource-constrained inference setting**, using API-based LLM access instead of GPU-based local inference.

Our experiments compare four inference strategies:

- Vanilla prompting
- Chain-of-Thought (CoT)
- Retrieval-Augmented Generation (RAG)
- G²-Reasoner

Unlike the original implementation, our setup:

- runs without CUDA GPU
- uses Ollama API with DeepSeek-v3.1
- uses CPU-based retrieval
- includes automatic rerun pipeline for API failures
- reproduces results on CausalProbe-E and CausalProbe-H

---

# Overview

This project replicates the causal reasoning evaluation pipeline using:

| Component | Our setting |
|----------|------------|
| LLM | deepseek-v3.1 (Ollama cloud API) |
| Retrieval model | facebook/contriever-msmarco |
| Index | FAISS (CPU) |
| Knowledge base | General Knowledge QA dataset |
| Benchmark | CausalProbe-2024 |
| Inference | CPU + API |
| Error handling | rerun pipeline |

---

# Project Structure

```text
CausalProbe-2024/
│
├── benchmarks/
│   └── CausalProbe2024/
│       ├── CausalProbe-E.json
│       └── CausalProbe-H.json
│
├── main_ollama.py
├── passage_retrieval.py
├── generate_embeddings.py
├── prompts.py
├── utils.py
├── rerun_no_choice_by_id.py
│
├── README.md
└── requirements.txt
