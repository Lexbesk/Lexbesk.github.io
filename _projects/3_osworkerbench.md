---
layout: page
title: OSWorkerBench
description: 100 long-horizon office workflows for computer-use agents, released with Tencent's UI-Mate
img: assets/img/projects/osworkerbench-logo.svg
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

## What the benchmark looks like

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/osworkerbench-statistics.png" title="OSWorkerBench composition" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    OSWorkerBench composition. <b>(a)</b> The 100 tasks across 10 job families, each task assigned to one family by its main business objective. <b>(b)</b> Distinct applications required per task — <b>99% of tasks span two or more applications</b>, mean 3.26. <b>(c)</b> The most frequent of the 41 applications. <b>(d)</b> Evaluator checkpoints per task (mean 4.86, median 5) — the weighted final-state checkpoints that make every task automatically scoreable.
</div>

Panel (d) is the part I care about most. Grading a long office workflow is where
benchmarks usually give up and fall back on a human reading transcripts. Scoring
against weighted checkpoints on final application state keeps it automatic, and
gives partial credit for partial progress instead of collapsing a twelve-step
workflow into one pass/fail bit.

<!-- TODO(visuals): still wanted — (1) task-construction pipeline diagram, (2) worked checkpoint-scoring example on a single workflow, (3) instruction-only vs. self-demo vs. variant-demo results. -->

## Links

[Project page](https://ui-mate.github.io/) · [Code](https://github.com/Tencent/UI-Mate) · [Technical report](https://arxiv.org/abs/2608.15930)

<div class="caption" style="text-align: left; margin-top: 1.5rem;">
Figures from the <a href="https://github.com/Tencent/UI-Mate">Tencent/UI-Mate</a> repository, released by Tencent under the Apache-2.0 licence.
</div>
