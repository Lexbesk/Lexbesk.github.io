---
layout: page
title: RobotArena ∞
description: Unlimited robot benchmarking via real-to-sim translation — ICLR 2026
img: assets/img/publication_preview/RobotArena.png
importance: 1
category: research
related_publications: true
---

Evaluating a robot policy honestly is expensive. Real-world evaluation does not scale, and hand-authored simulation benchmarks cover a narrow, hand-picked slice of the world. **RobotArena ∞** takes a third route: turn the robot video that already exists — millions of teleoperation episodes sitting in public datasets — into physics-consistent simulated environments you can evaluate in, perturb, and re-run without limit.

The work was done at Carnegie Mellon University with Prof. [Katerina Fragkiadaki](https://www.cs.cmu.edu/~katef/), and was accepted to **ICLR 2026** {% cite jangir2026robotarena %}.

## My contributions

**Real-to-sim pipeline.** I built the path from a teleoperation video to a simulated environment you can actually run a policy in: generative scene modeling to recover 3D geometry and appearance, and differentiable rendering to make the reconstruction agree with the observed pixels. The output is not a pretty scene — it is a _physics-consistent_ one, with object poses and contacts that hold up when a policy starts interacting with them.

**Automatic camera–robot calibration.** Calibration is the quiet blocker in real-to-sim: if the camera-to-robot transform is wrong, everything downstream is wrong, and the standard fix is a human with a checkerboard. I designed a calibration method built on **3D Gaussian Splatting** that recovers the transform with **sub-centimeter pose error and no manual supervision**. Running it over **BridgeV2**, **DROID** and **RH20T** produced **more than 10,000 calibrated trajectories** — the raw material the rest of the pipeline consumes.

<!-- TODO(visuals): replace with (1) real→sim side-by-side frames, (2) calibration overlay showing reprojected robot mesh, (3) a scale bar / error plot for the sub-cm claim. -->

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/RobotArena.png" title="RobotArena real-to-sim translation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Real teleoperation video is translated into a simulated counterpart that policies can be evaluated in at scale.
</div>

## Links

[Project page](https://robotarenainf.github.io/) · [arXiv:2510.23571](https://arxiv.org/abs/2510.23571)
