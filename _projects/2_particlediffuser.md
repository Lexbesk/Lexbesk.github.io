---
layout: page
title: ParticleDiffuser
description: Generative 3D object-particle dynamics for planning
img: assets/img/8.jpg
importance: 2
category: research
---

A controller can only be as good as its model of what happens next. **ParticleDiffuser** is a diffusion model over 3D dynamics: given a point cloud of the scene, it predicts the future trajectories of **object particles and the gripper** together — for rigid objects and deformable ones alike, without needing a separate model class for each.

Done at Carnegie Mellon University with Prof. [Katerina Fragkiadaki](https://www.cs.cmu.edu/~katef/).

## What it does

**A single dynamics model across object types.** Representing the scene as particles rather than meshes or poses means rigid and deformable objects are the same kind of thing to the model. The diffusion model predicts where those particles — and the gripper acting on them — go next.

**Planning by guidance, not search.** Instead of bolting a sampling-based planner on top, I built a **goal-conditioned guided-diffusion controller**: the goal steers the denoising process directly. Against an MPC baseline this reached **3× lower MSE** and **20× faster planning**.

**Long horizons.** I extended the guidance across prediction chunks so plans compose beyond a single prediction window, and validated that the resulting behavior transfers **sim-to-real**.

<!-- TODO(visuals): needed — (1) predicted vs. ground-truth particle rollout (rigid + deformable), (2) guided vs. unguided denoising toward a goal, (3) MSE/planning-time bar chart vs. MPC, (4) real-robot rollout frames. -->

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/8.jpg" title="placeholder" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder — to be replaced with particle rollout visualizations.
</div>
