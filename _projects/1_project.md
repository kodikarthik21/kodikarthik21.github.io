---
layout: page
title: Physics-guided human motion diffusion
description: Infusing a reward model at every denoising step to steer the model towards generating more physically plausible trajectories
img: assets/img/PRG_presentation.jpg
importance: 1
category: recent
related_publications: false
---

10623 - Generative AI course, Spring 2026, Carnegie Mellon University.

Teammates: Narayanan Palghat Parameswaran, Rahul Krishna Veerapandian

This project won 3rd prize in the poster session.

Text-to-motion diffusion models generate convincing animations but routinely break physical laws — feet float, joints penetrate the ground, and limbs slide when they should be planted. We built **PRG (Physics-guided Reward Guidance)**, an inference-time method that steers a frozen Motion Diffusion Model toward physically plausible output without retraining it or touching a simulator.

**How it works:** A lightweight contrastive reward model is trained offline on pairs of plausible and implausible HumanML3D motions. At inference, its gradient signal is injected at every denoising step, with a time-conditioned schedule that applies the strongest corrections once the motion estimate is well-formed.

**Results:** ~10–12% reduction in physics error (foot skating, ground penetration, floating) over the MDM baseline, with prompt fidelity preserved.

The key insight is that physical plausibility can be learned cheaply from generated data and applied as a gradient correction — no RL policy, no simulator, no fine-tuning.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/PRG_flow.png" title="Flow of inference for our approach - integrating a reward model with a diffusion model" %}
    </div>
</div>
<div class="caption">
    Flow of inference for our approach - integrating a reward model with a diffusion model
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/PRG_presentation.jpg" title="Poster Session 10623 CMU" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="caption">
        Poster Session 10623 CMU
    </div>
</div>