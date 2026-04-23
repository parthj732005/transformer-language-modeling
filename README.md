# 🧠 GPT-style Language Model (From Scratch)

A decoder-only Transformer language model (~51M parameters) trained from scratch on large-scale text corpora (WikiText-103 + BookCorpus) to study cross-domain learning and training dynamics.

---

## 📌 Overview

This project implements and trains a **GPT-style autoregressive language model** using a structured multi-phase training pipeline.

The goal was to:
- Understand how transformers learn from different text domains
- Build a **robust training pipeline**
- Analyze performance across datasets

---

## ⚙️ Model Architecture

- **Model Type:** Decoder-only Transformer
- **Parameters:** ~51M
- **Layers:** 8
- **Heads:** 8
- **Embedding Size:** 512
- **Feedforward Dim:** 2048 (GELU activation)
- **Context Length:** 256 tokens

> Standard architecture with causal self-attention and pre-layer normalization.

---

## 📚 Dataset

### Phase 1:
- WikiText-103 (~103M tokens)
- Cleaned + tokenized using GPT-2 BPE

### Phase 2 & 3:
- Combined Dataset (~356M tokens)
  - WikiText-103
  - BookCorpus (streamed + filtered)

> BookCorpus added narrative structure, improving learning patterns.

---

## 🔄 Training Pipeline

Training was performed in **3 phases**:

### 🟢 Phase 1: WikiText
- Focused on factual/encyclopedic data
- Baseline learning established

### 🟡 Phase 2: Combined (v1)
- Training interrupted at 22k steps
- Successfully resumed from checkpoint

### 🔵 Phase 3: Combined (Final)
- Final run with tuned hyperparameters

---

## 📊 Results

- WikiText only: ~3.60 validation loss  
- Combined dataset: ~3.26 – 3.36 validation loss  

➡️ Adding BookCorpus improved performance due to:
- More repetitive patterns
- Better sequence learning

---

## 🧠 Key Insights

- Domain diversity improves generalization
- Narrative data helps stabilize learning
- Checkpoint recovery is critical for long training

> The resume strategy (from earlier checkpoint) helped avoid instability.

---

## 🧪 Sample Prompts

Examples evaluated:
- Narrative completion
- Factual generation
- Dialogue generation

Outputs are available in inference scripts.

---

## 🛠️ Tech Stack

- PyTorch
- Custom Transformer implementation
- GPT-2 BPE tokenizer
- Large-scale dataset streaming
