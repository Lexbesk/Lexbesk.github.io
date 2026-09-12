---
layout: page
title: D2ART
description: Dual-modal prompting for vision–language models at test time
img: assets/img/4.jpg
importance: 5
category: research
---

**D2ART** adapts CLIP at test time by updating prompts in **both modalities** rather than text alone. Two pieces do the work: **entropy-guided prompt updates**, which use the model's own confidence as the adaptation signal in the absence of labels, and **EMA feature stabilization**, which keeps that unsupervised signal from drifting as adaptation accumulates over a test stream.

On **ImageNet-A** — the natural-adversarial split where CLIP struggles most — this improved **top-1 accuracy by 2.3%** over prior test-time adaptation methods.

Done at the [OV³ Lab](https://zhoujiahuan1991.github.io/research.html), Wangxuan Institute of Computer Technology, Peking University, with Prof. [Jiahuan Zhou](https://zhoujiahuan1991.github.io/).

<!-- TODO(visuals): needed — (1) dual-modal prompt architecture diagram, (2) with/without EMA stabilization drift plot over a test stream, (3) ImageNet-A accuracy comparison bar chart. -->

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/4.jpg" title="placeholder" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder — to be replaced with the dual-modal prompting diagram.
</div>
