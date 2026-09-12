---
layout: page
title: OSWorkerBench
description: 100 long-horizon office workflows for computer-use agents, released with Tencent's UI-Mate
img: assets/img/6.jpg
importance: 3
category: research
related_publications: true
---

GUI agents are usually measured on short, self-contained tasks. Real office work is neither. **OSWorkerBench** is a benchmark of **100 long-horizon office workflows** spanning **41 applications** and **10 job families**, released alongside **UI-Mate**, the foundation GUI agent from Tencent's Hy Team {% cite uimate2026 %}.

Built during my research internship in Tencent's **Qingyun Program**, where I was a core contributor to the technical report and **owned task construction** for the benchmark.

## My contributions

**A capability-grounded generation pipeline.** Rather than writing tasks by hand and hoping for coverage, I designed a pipeline that generates tasks from an explicit map of application capabilities — so the benchmark's spread across applications and job families is a property of the construction, not an accident.

**Every task automatically scoreable.** Each task is scored by **weighted checkpoints on final application state**, so grading needs no human in the loop and gives partial credit for partial progress on long workflows. Getting this right took iterative **human-in-the-loop verification**: pilot-agent rollouts to find tasks that were ambiguous or unreachable, and synthetic test cases to confirm each checkpoint fired when — and only when — it should.

**Multimodal demonstrations as one-shot guidance.** I recorded human demonstrations for the hard tasks. This makes OSWorkerBench the **first computer-use benchmark to supply multimodal demonstrations as one-shot guidance**, and the first to test **procedural transfer**: can an agent given a demonstration of a _related but non-identical_ task carry the procedure across?

<!-- TODO(visuals): needed — (1) coverage matrix: 41 applications × 10 job families, (2) task-construction pipeline diagram, (3) checkpoint-scoring illustration on one workflow, (4) instruction-only vs. self-demo vs. variant-demo results. -->

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="placeholder" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder — to be replaced with the application × job-family coverage matrix.
</div>

## Links

[Project page](https://ui-mate.github.io/) · [Code](https://github.com/Tencent/UI-Mate) · [Technical report](https://arxiv.org/abs/2608.15930)
