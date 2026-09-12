---
layout: page
title: ParticleDiffuser
description: Generative 3D object-particle dynamics for planning
img: assets/img/projects/particlediffuser-teaser.png
importance: 2
category: research
---

A controller can only be as good as its model of what happens next. **ParticleDiffuser** is a diffusion model over 3D dynamics: given a point cloud of the scene, it predicts the future trajectories of **object particles and the gripper** together — for rigid objects and deformable ones alike, without needing a separate model class for each.

Done at Carnegie Mellon University with Prof. [Katerina Fragkiadaki](https://www.cs.cmu.edu/~katef/).

## What it does

**A single dynamics model across object types.** Representing the scene as particles rather than meshes or poses means rigid and deformable objects are the same kind of thing to the model. The diffusion model predicts where those particles — and the gripper acting on them — go next.

**Planning by guidance, not search.** Instead of bolting a sampling-based planner on top, I built a **goal-conditioned guided-diffusion controller**: the goal steers the denoising process directly. Against an MPC baseline this reached **3× lower MSE** and **20× faster planning**.

**Long horizons.** I extended the guidance across prediction chunks so plans compose beyond a single prediction window, and validated that the resulting behavior transfers **sim-to-real**.

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/particlediffuser-teaser.png" title="ParticleDiffuser overview" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    ParticleDiffuser is trained in simulation across soft, deformable and rigid objects. Noisy point-cloud and gripper-action trajectories are denoised together through a set of latent query vectors under a read–compute–write scheme, which keeps the bulk of computation off the particles themselves. The same model supports guided diffusion for motion planning and generalizes to object shapes it never saw in training.
</div>

## Planning by guidance beats planning by search

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/particlediffuser-guidance-vs-mpc.png" title="Guided diffusion vs MPC" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Guiding an object's centroid to a target. Each blue square is MPC at a given sample budget (3 to 100 rollouts); the orange star is a single guided-diffusion pass. Guidance lands below and to the left of the entire MPC frontier — better accuracy <em>and</em> less time, not a trade between them.
</div>

The numbers behind it: guided diffusion reaches **0.017 m** final-state MSE in
**69 s** per trajectory, against **0.053 m** for a GNN + MPC baseline — about
**3× lower error**. And because MPC has to buy accuracy with rollouts, closing
the gap by search costs it roughly **20× the planning time**, which is the
distance between the star and the right-hand end of the blue frontier above.

<!-- TODO(visuals): still wanted — real-robot sim-to-real rollout frames (paper Fig. 8) if we want a hardware shot on this page. -->
