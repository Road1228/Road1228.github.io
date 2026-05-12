---
title: Academic Research Notes Example
author: Road
date: 2026-05-11 15:00:00 +0800
categories: [Research Notes, Deep Learning]
tags: [deep learning, neural networks, paper notes]
math: true
---

## Paper Reading Notes Template

This post demonstrates how to use this site for recording academic paper reading notes.

---

### Paper Information

- **Title**: Attention Is All You Need
- **Authors**: Vaswani et al.
- **Published**: NeurIPS 2017
- **Link**: [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)

---

### Core Idea

The Transformer architecture is entirely based on the attention mechanism, discarding traditional recurrent and convolutional structures.

#### Self-Attention Formula

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V
$$

Where:
- $Q$ (Query), $K$ (Key), $V$ (Value) are the query, key, and value matrices
- $d_k$ is the dimension of the key vectors, used for scaling to prevent gradient vanishing

#### Multi-Head Attention

$$
\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, ..., \text{head}_h)W^O
$$

Where each head:

$$
\text{head}_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)
$$

---

### Key Contributions

1. Proposed a pure attention-based sequence-to-sequence model
2. Introduced the multi-head attention mechanism
3. Positional encoding scheme
4. Achieved SOTA on machine translation tasks

### Personal Thoughts

> The revolutionary aspect of this paper is that it proved attention mechanisms can completely replace RNNs and CNNs for processing sequential data, laying the foundation for the later BERT and GPT series.
{: .prompt-tip }

---

### Experiment Reproduction

```python
import torch
import torch.nn as nn
import torch.nn.functional as F

class SelfAttention(nn.Module):
    def __init__(self, d_model, n_heads):
        super().__init__()
        self.d_k = d_model // n_heads
        self.n_heads = n_heads
        self.W_q = nn.Linear(d_model, d_model)
        self.W_k = nn.Linear(d_model, d_model)
        self.W_v = nn.Linear(d_model, d_model)
        self.W_o = nn.Linear(d_model, d_model)
    
    def forward(self, x):
        B, T, C = x.shape
        q = self.W_q(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        k = self.W_k(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        v = self.W_v(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        
        attn = F.softmax(q @ k.transpose(-2, -1) / (self.d_k ** 0.5), dim=-1)
        out = (attn @ v).transpose(1, 2).contiguous().view(B, T, C)
        return self.W_o(out)
```

---

> This is just a paper notes template. You can follow a similar format to record your own academic reading notes.
