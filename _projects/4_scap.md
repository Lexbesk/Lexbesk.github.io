---
layout: page
title: SCAP
description: Transductive test-time adaptation via supportive clique-based attribute prompting — CVPR 2025
img: assets/img/publication_preview/SCAP.png
importance: 4
category: research
related_publications: true
---

A vision-language model deployed in the wild meets data that does not look like its training set, and accuracy quietly degrades. The usual remedies — labels, retraining — are exactly what you do not have at deployment time. **SCAP** keeps CLIP-style models accurate under distribution shift with **no labels and no retraining** {% cite zhang2025scap %}.

Done at the [OV³ Lab](https://zhoujiahuan1991.github.io/research.html), Wangxuan Institute of Computer Technology, Peking University, with Prof. [Jiahuan Zhou](https://zhoujiahuan1991.github.io/). Published at **CVPR 2025**.

## The idea

Test samples arrive together, and that is information most test-time adaptation methods throw away by treating each sample in isolation. SCAP is **transductive**: it finds **cliques of visually similar test samples** and adapts attribute prompts against the clique rather than the individual. Samples that look alike constrain each other, and the adaptation signal gets correspondingly stronger.

The useful consequence: performance **improves as the test batch grows**, where per-sample methods flatten out.

<!-- TODO(visuals): needed — (1) clique-formation diagram in embedding space, (2) accuracy-vs-batch-size curve against per-sample TTA baselines, (3) qualitative examples of a clique correcting a mistake. -->

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/SCAP.png" title="SCAP" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Supportive cliques of visually similar test samples drive attribute prompting.
</div>
