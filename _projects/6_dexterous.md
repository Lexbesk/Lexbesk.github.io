---
layout: page
title: Multi-Skill Dexterous Manipulation
description: From RL to flow-matching — a three-stage pipeline for dexterous grasping
img: assets/img/10.jpg
importance: 1
category: engineering
---

Dexterous grasping fails in a characteristic way: a policy discovers one grasp that works and collapses onto it, losing the variety that makes a hand worth having. This project builds a **three-stage pipeline** designed around that failure.

Advised by Dr. He Wang, Jan 2026 – May 2026.

## The pipeline

**1 — Flow-matching pose proposer.** A flow-matching model conditioned on the object point cloud proposes grasp poses. Because it models the full distribution rather than a point estimate, it keeps multiple valid strategies alive for the same object.

**2 — RL pick-up policy.** An RL policy learns to execute a pick-up, **rewarded against the proposed grasps**. Grounding the reward in the proposer's distribution is what prevents mode collapse — the policy is paid for realizing the variety the proposer offers, not for finding one grasp that always works.

**3 — Distilled visuomotor student.** A visuomotor policy is distilled from the RL teacher's demonstrations, so the final policy runs from vision alone.

## Fixing behavioral cloning's blind spot

A distilled student only ever sees states the teacher visits, so the first small deviation puts it somewhere it has no training signal for. I **injected noise during demonstration collection** to push the teacher off-distribution and record how it recovers, giving the student the corrective behaviors that clean demonstrations never contain.

The pipeline reached **85%+ success across Dexonomy**, retaining diverse grasp strategies rather than converging on one.

<!-- TODO(visuals): needed — (1) three-stage pipeline diagram, (2) grid of diverse grasps sampled from the proposer for one object, (3) success-rate chart across Dexonomy categories, (4) noise-injection recovery illustration, (5) short rollout GIFs. -->

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/10.jpg" title="placeholder" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder — to be replaced with the pipeline diagram and grasp gallery.
</div>
