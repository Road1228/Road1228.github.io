---
title: 学术研究笔记示例
author: Road
date: 2026-05-11 15:00:00 +0800
categories: [研究笔记, 深度学习]
tags: [深度学习, 神经网络, 论文笔记]
math: true
---

## 论文阅读笔记模板

本篇文章展示如何使用本站记录学术论文阅读笔记。

---

### 论文信息

- **标题**: Attention Is All You Need
- **作者**: Vaswani et al.
- **发表**: NeurIPS 2017
- **链接**: [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)

---

### 核心思想

Transformer 架构完全基于注意力机制（Attention Mechanism），摒弃了传统的循环和卷积结构。

#### Self-Attention 公式

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V
$$

其中：
- $Q$ (Query)、$K$ (Key)、$V$ (Value) 分别是查询、键、值矩阵
- $d_k$ 是键向量的维度，用于缩放防止梯度消失

#### Multi-Head Attention

$$
\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, ..., \text{head}_h)W^O
$$

其中每个头：

$$
\text{head}_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)
$$

---

### 关键贡献

1. 提出了纯注意力机制的序列转换模型
2. 引入多头注意力机制
3. 位置编码（Positional Encoding）方案
4. 在机器翻译任务上达到 SOTA

### 个人思考

> 这篇论文的革命性在于证明了注意力机制可以完全替代 RNN 和 CNN 来处理序列数据，为后来的 BERT、GPT 系列奠定了基础。
{: .prompt-tip }

---

### 实验复现

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

> 这只是一个论文笔记模板，您可以按照类似格式记录自己的学术阅读笔记。
