# AI Mathematical Olympiad – Progress Prize 3

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)
![GPU](https://img.shields.io/badge/GPU-NVIDIA%20H100-green.svg)
![Model](https://img.shields.io/badge/Model-GPT--OSS--120B-red.svg)

A competition solution for the **AI Mathematical Olympiad – Progress Prize 3** on Kaggle, focused on solving olympiad-level mathematical problems using **large language models, symbolic reasoning, multi-attempt inference, and Python-assisted verification**.

This project uses a **GPT-OSS-120B reasoning pipeline** served with **vLLM**, combined with persistent Jupyter kernels and tool-assisted mathematical verification to improve answer reliability and final prediction quality. The notebook runs on **NVIDIA H100 GPU**, loads approximately **65.28 GB model weights**, and uses multiple reasoning attempts before selecting the final answer. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

---

## Project Overview

The goal of this competition is to solve difficult mathematical olympiad problems where the final output must be:

- a **non-negative integer**
- between **0 and 99999**
- formatted as a final boxed answer

The model follows a structured reasoning framework:

1. Understand the problem
2. Explore multiple strategies
3. Plan the best solution path
4. Execute rigorous reasoning
5. Verify using alternative checks and Python tools

This improves consistency and reduces hallucination compared to direct-answer generation. :contentReference[oaicite:2]{index=2}

---

## Repository Structure

```bash
AI-Mathematical-Olympiad/
│
├── ai-mathematical-olympiad.ipynb
├── outputs/
│   └── submission.csv
├── models/
│   └── gpt-oss-120b/
├── LICENSE
└── README.md
```

---

## Workflow

```text
Load GPT-OSS-120B model
        ↓
Initialize vLLM inference server
        ↓
Create persistent Jupyter kernels
        ↓
Receive math problem
        ↓
Multi-attempt reasoning generation
        ↓
Python / SymPy verification
        ↓
Entropy-based answer selection
        ↓
Final answer prediction
        ↓
Kaggle submission generation
```

---

## Model Summary

The solution is based on a custom reasoning engine called **AIMO3Solver**, which uses:

- GPT-OSS-120B
- vLLM inference serving
- OpenAI-compatible local API
- Harmony encoding
- persistent Jupyter kernel sandboxes
- symbolic verification with `sympy`
- numerical checking with `numpy`
- multi-attempt voting system

### Key Configuration

- attempts: **8**
- workers: **16**
- max turns: **128**
- context tokens: **65,536**
- early stop: **4**
- batch size: **256**
- timeout-aware execution
- entropy scoring for final answer selection :contentReference[oaicite:3]{index=3}

---

## Example Usage

```python
def predict(id_, question, answer=None):
    id_value = id_.item(0)
    question_text = question.item(0)

    final_answer = solver.solve_problem(question_text)

    return {"id": id_value, "answer": final_answer}
```

### Example Problem

```text
What is 0 × 10?
```

### Example Output

```text
Final Answer: 0
```

The notebook shows successful local gateway testing using Kaggle’s official inference server. :contentReference[oaicite:4]{index=4}

---

## Reasoning Strategy

The system prompt explicitly instructs the model to:

- reason step-by-step
- verify arithmetic and algebra
- test edge cases
- use symbolic computation when possible
- use Python only when necessary
- prioritize correctness over speed

The final answer must be written inside:

```text
\boxed{answer}
```

This improves formal answer extraction and leaderboard stability. :contentReference[oaicite:5]{index=5}

---

## Tool Usage

Available tools include:

### Symbolic Computation (`sympy`)
- equation solving
- modular arithmetic
- polynomial factorization
- number theory operations

### Numerical Computation (`numpy`)
- matrix operations
- brute-force validation
- statistical checking

### Standard Math (`math`)
- trigonometry
- logarithms
- constants
- arithmetic support

The notebook strongly encourages symbolic derivation first, followed by numerical verification. :contentReference[oaicite:6]{index=6}

---

## Compute Requirements

### Hardware

- GPU: NVIDIA H100
- CUDA enabled
- high-memory inference environment

### Runtime Details

- model size loaded: **65.28 GB**
- files processed: **26**
- server startup: ~119 sec
- weight preload: ~128 sec
- 16 persistent Jupyter kernels initialized :contentReference[oaicite:7]{index=7}

### Software

- Python 3.12
- vLLM
- OpenAI SDK
- transformers
- pandas
- polars
- sympy
- numpy
- jupyter_client

---

## Evaluation Strategy

The system performs:

- multiple independent attempts
- entropy-based confidence scoring
- answer voting
- fallback to safe default output (`0`) if no valid answer is found

Example evaluation output:

```text
Answer : 0
Votes  : 4
Score  : 5.7
```

This improves robustness against unstable generations. :contentReference[oaicite:8]{index=8}

---

## Key Insights

Important findings from this approach:

- multi-attempt reasoning outperforms single-pass inference
- symbolic verification reduces arithmetic failure
- entropy scoring improves answer confidence
- persistent kernels reduce inference overhead
- structured prompts significantly improve mathematical consistency

This makes the project highly valuable for:

- LLM reasoning research
- mathematical AI systems
- competition-grade inference optimization
- tool-augmented reasoning pipelines

---

## Tech Stack

- Python
- vLLM
- GPT-OSS-120B
- OpenAI SDK
- Harmony Encoding
- pandas
- polars
- numpy
- sympy
- Jupyter kernels
- Kaggle Inference Server

---

## Competition Reference

Kaggle Competition:

**AI Mathematical Olympiad – Progress Prize 3**

https://www.kaggle.com/competitions/ai-mathematical-olympiad-progress-prize-3

---

## License

This project is licensed under the **MIT License**.

You are free to use, modify, distribute, and adapt this work with proper attribution.

---

## Author

**Dimas Pasha Akrilian**

This repository is part of my **LLM reasoning and competition portfolio**, focusing on:

- mathematical reasoning systems
- tool-augmented LLM inference
- symbolic verification pipelines
- competition-grade AI problem solving
- advanced Kaggle optimization workflows
