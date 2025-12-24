# LLM_Eval

This repository provides a structured and extensible framework for **evaluating Large Language Models
(LLMs)** across **different task types**,
focusing on **what evaluation criteria and metrics are appropriate for which tasks**.

Rather than proposing a single benchmark, this project aims to **systematize evaluation choices** by mapping:
- task types → evaluation goals → suitable metrics and methods.

The repository is designed to grow incrementally as new tasks, metrics, and evaluation practices are added.

---

## Motivation

LLMs are used for a wide range of tasks (e.g., text generation, summarization, classification, code generation), but **evaluation is often task-dependent** and inconsistently applied.

Common issues include:
- using lexical metrics where semantic correctness matters,
- relying on a single metric for multi-facet tasks,
- unclear justification of evaluation choices.

This repository aims to:
- clarify **which metrics make sense for which tasks**,
- distinguish between **lexical, semantic, and functional evaluation**,
- provide reusable evaluation templates for different task categories.

---

## Task Categories and Evaluation Dimensions

We organize evaluation along two axes:
1. **Task type**
2. **Evaluation dimension**

### 1. Task Types (initial list)
- Text generation
- Summarization
- Question answering
- Classification
- Information extraction
- Code generation
- Program repair / transformation
- Reasoning tasks
- Dialogue / conversational tasks

(New task types can be added incrementally.)

---

### 2. Evaluation Dimensions

#### Lexical Similarity
Measures surface-level overlap between model output and reference.

Typical metrics:
- ROUGE (ROUGE-1, ROUGE-2, ROUGE-L)
- BLEU
- METEOR

Appropriate when:
- exact wording matters,
- reference texts are stable and well-defined.

Limitations:
- insensitive to paraphrasing,
- may penalize semantically correct outputs.

---

#### Semantic Similarity
Measures meaning preservation independent of wording.

Typical approaches:
- Embedding-based cosine similarity
- BERTScore
- Sentence-level semantic similarity models

Appropriate when:
- paraphrasing is acceptable,
- meaning matters more than exact phrasing.

Limitations:
- may reward fluent but incorrect outputs,
- depends on embedding model quality.

---

#### Functional Correctness
Measures whether the output **behaves correctly** when executed or applied.

Typical approaches:
- unit tests
- oracle-based checking
- program execution and output comparison

Appropriate when:
- evaluating code generation,
- transformations, patches, or executable artifacts.

Limitations:
- requires reliable test oracles,
- task-specific setup effort.

---

#### Task-Specific Metrics
Some tasks require **custom or domain-specific evaluation**.

Examples:
- Exact Match / F1 for QA
- Accuracy, Precision, Recall for classification
- Pass@k for code generation
- Coverage-based or mutation-based metrics for program analysis tasks

---

## Repository Structure (Current / Planned)

