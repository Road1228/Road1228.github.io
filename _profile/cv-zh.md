---
title: 简历
author: Road
tags: [cv, resume]
description: >-
  卢敬敬的个人简历：等离子体控制、数据驱动建模与 AI for Science（EAST 托卡马克）。
---

<div class="cv cv-zh" lang="zh-CN" markdown="1">

<div class="cv-head">
  <p class="cv-name">卢敬敬 <span class="cv-name-alt" lang="en">Jingjing Lu</span></p>
  <p class="cv-tagline">等离子体控制 · 数据驱动建模 · AI for Science</p>
  <p class="cv-links">
    <a href="mailto:jingjing.lu@ipp.ac.cn">jingjing.lu@ipp.ac.cn</a>
    <span class="cv-sep">|</span> 安徽合肥
    <span class="cv-sep">|</span> <a href="https://orcid.org/0009-0009-2629-5744">ORCID</a>
    <span class="cv-sep">|</span> <a href="https://github.com/Road1228">GitHub</a>
  </p>
  <p class="cv-actions">
    <a class="cv-btn" href="{{ '/assets/pdf/Jingjing_Lu_CV_ZH.pdf' | relative_url }}">下载 PDF</a>
    <a class="cv-btn cv-btn-ghost" href="{{ '/posts/internal/profile/cv/' | relative_url }}" lang="en">English</a>
  </p>
</div>

## 研究概况 {#profile}

中国科学技术大学博士研究生，在中国科学院等离子体物理研究所开展研究。围绕 EAST 托卡马克的等离子体平衡重建、前馈线圈电流轨迹设计，以及诊断数据重建与预测不确定性开展机器学习研究。具有第一作者论文、合作论文及国内外学术报告经历。

## 教育经历 {#education}

<div class="cv-entry">
  <div class="cv-row"><span class="cv-org">中国科学技术大学／中国科学院等离子体物理研究所</span><span class="cv-date">2023 – 至今</span></div>
  <div class="cv-row"><span>能源动力，博士研究生</span><span class="cv-note">预计毕业：2027年6月</span></div>
</div>
<div class="cv-entry">
  <div class="cv-row"><span class="cv-org">中国科学技术大学／中国科学院等离子体物理研究所</span><span class="cv-date">2020 – 2023</span></div>
  <div class="cv-row"><span>能源动力，硕士</span></div>
</div>
<div class="cv-entry">
  <div class="cv-row"><span class="cv-org">阜阳师范大学</span><span class="cv-date">2015 – 2019</span></div>
  <div class="cv-row"><span>物理学，学士</span></div>
</div>

## 研究经历 {#research}

### EAST 等离子体快速平衡重建 {#research-equilibrium}

<p class="cv-meta"><span class="cv-tag">已发表</span> <em>AIP Advances</em>（2023），第一作者</p>

- 以磁测量信号为输入、离线 EFIT 重建的二维极向磁通为监督目标，开展深度神经网络平衡重建研究。
- 采用自动超参数优化，比较预测磁面、最外闭合磁面及归一化内感的演化与 EFIT 结果。

### 物理信息模仿学习与前馈线圈电流轨迹设计 {#research-feedforward}

<p class="cv-meta"><span class="cv-tag">论文投稿中</span> <em>Communications Physics</em>，第一作者</p>

- 面向 EAST 前馈电流设计，开展物理信息模仿学习与 Seq2Seq Transformer 方法研究，关注时序轨迹建模与物理约束。
- 在 AAPPS-DPP 2026 作邀请报告，并在 IAEA 技术会议作口头报告。

### 诊断数据重建与预测不确定性研究 {#research-diagnostics}

<p class="cv-meta"><span class="cv-tag">合作研究</span> <em>Nuclear Fusion</em>（2025）</p>

- 参与利用时间序列外生回归重建缺失电子温度的研究，合作成果发表于 *Nuclear Fusion*（2025），第三作者。
- 参与利用贝叶斯神经网络预测能量约束时间及量化不确定性的研究，合作成果发表于 *Nuclear Fusion*（2025），第五作者。

## 技术能力 {#skills}

<div class="cv-skills">
  <div class="cv-skill"><span class="cv-skill-label">编程与建模</span><span>Python、PyTorch；深度神经网络、时序建模、Seq2Seq Transformer。</span></div>
  <div class="cv-skill"><span class="cv-skill-label">领域工具</span><span>EFIT；EAST 磁平衡与诊断数据分析、前馈电流波形设计。</span></div>
  <div class="cv-skill"><span class="cv-skill-label">语言</span><span>英语 CET-6；普通话二级甲等。</span></div>
</div>

## 代表论文 {#publications}

<p class="cv-group">第一作者论文（含在投稿件）</p>
<ol class="cv-pubs">
  <li>
    <span class="cv-pub-title" lang="en">Fast equilibrium reconstruction by deep learning on EAST tokamak</span>
    <span class="cv-pub-authors" lang="en"><strong>J. Lu</strong>, Y. Hu, N. Xiang, Y. Sun</span>
    <span class="cv-pub-venue"><em>AIP Advances</em> 13, 075007 (2023) <a class="cv-pub-link" href="https://doi.org/10.1063/5.0152318">[doi:10.1063/5.0152318]</a></span>
  </li>
  <li>
    <span class="cv-pub-title" lang="en">Physics-informed imitation learning for feedforward coil-current trajectory design on EAST</span>
    <span class="cv-pub-authors" lang="en"><strong>J. Lu</strong> et al.</span>
    <span class="cv-pub-venue"><em>Communications Physics</em>，投稿中</span>
  </li>
</ol>

<p class="cv-group">合作论文</p>
<ol class="cv-pubs">
  <li>
    <span class="cv-pub-title" lang="en">Time series extrinsic regression for reconstructing missing electron temperature in tokamak</span>
    <span class="cv-pub-authors" lang="en">M. Wang, C. Wan, <strong>J. Lu</strong> et al.</span>
    <span class="cv-pub-venue"><em>Nuclear Fusion</em> 65, 076008 (2025) <a class="cv-pub-link" href="https://doi.org/10.1088/1741-4326/addb5f">[doi:10.1088/1741-4326/addb5f]</a></span>
  </li>
  <li>
    <span class="cv-pub-title" lang="en">Bayesian neural networks for predicting tokamak energy confinement time with uncertainty quantification</span>
    <span class="cv-pub-authors" lang="en">E. Gao, C. Wan, Y. Hu, M. Wang, <strong>J. Lu</strong> et al.</span>
    <span class="cv-pub-venue"><em>Nuclear Fusion</em> 65, 084001 (2025) <a class="cv-pub-link" href="https://doi.org/10.1088/1741-4326/ade8fd">[doi:10.1088/1741-4326/ade8fd]</a></span>
  </li>
  <li>
    <span class="cv-pub-title" lang="en">T-DDFM: an advanced denoising diffusion fusion model for high-precision neutron imaging</span>
    <span class="cv-pub-authors" lang="en">Y.-Y. Liu, D.-K. Yang, K. Zhu, <strong>J.-J. Lu</strong> et al.</span>
    <span class="cv-pub-venue"><em>Nuclear Science and Techniques</em> 37, 231 (2026) <a class="cv-pub-link" href="https://doi.org/10.1007/s41365-026-02054-6">[doi:10.1007/s41365-026-02054-6]</a></span>
  </li>
</ol>

## 专利 {#patent}

<div class="cv-entry">
  <div class="cv-row"><span class="cv-org">一种托卡马克极向场线圈前馈电流设计方法及系统</span><span class="cv-date">授权公告日：2026年10月30日</span></div>
  <div class="cv-line">孙有文、<strong>卢敬敬</strong>等（第2发明人）</div>
  <div class="cv-sub">中国发明专利，已授权。专利号：ZL202611178059.9；授权公告号：CN122735600B。</div>
</div>

## 学术报告 {#presentations}

<div class="cv-entry">
  <div class="cv-row"><span class="cv-org">邀请报告</span><span class="cv-date">2026年10月11日</span></div>
  <div class="cv-line" lang="en">Feedforward poloidal field coil current design on EAST via behavioral cloning.</div>
  <div class="cv-sub">10th Asia-Pacific Conference on Plasma Physics (AAPPS-DPP 2026)，韩国釜山</div>
</div>
<div class="cv-entry">
  <div class="cv-row"><span class="cv-org">口头报告</span><span class="cv-date">2025年9月9日</span></div>
  <div class="cv-line" lang="en">Data processing for imitation learning in EAST feedforward current design.</div>
  <div class="cv-sub">6th IAEA Technical Meeting on Fusion Data Processing, Validation and Analysis，中国上海</div>
</div>
<div class="cv-entry">
  <div class="cv-row"><span class="cv-org">口头报告</span><span class="cv-date">2023年10月27日</span></div>
  <div class="cv-line">基于深度学习的 EAST 托卡马克快速平衡重建。</div>
  <div class="cv-sub">第十一届磁约束聚变理论与模拟会议，中国成都</div>
</div>

## 奖励 {#honors}

中国科学技术大学学业奖学金：一等奖2次、二等奖1次。

<p class="cv-updated">最近更新：2026年11月</p>

</div>
