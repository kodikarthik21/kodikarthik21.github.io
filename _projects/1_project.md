---
layout: project
title: Physics-guided human motion diffusion
description: Infusing a reward model at every denoising step to steer the model towards generating more physically plausible trajectories
img: assets/img/PRG_presentation.jpg
importance: 1
methods: ["Diffusion models", "Reward guidance", "Classifier guidance", "GRPO"]
tools: ["PyTorch"]
category: recent
related_publications: false
context: "10623 Generative AI, Spring 2026, Carnegie Mellon University"
team:
  - name: Karthik Srinivasan
  - name: Narayanan Palghat Parameswaran
  - name: Rahul Krishna Veerapandian
advisor_label: Instructors
advisors:
  - name: Matt Gormley
    url: https://www.cs.cmu.edu/~mgormley/
    role: Machine Learning Dept.
  - name: Aran Nayebi
    url: https://www.cmu.edu/ni/people/faculty/aran-nayebi
    role: Machine Learning & Neuroscience Institute
---

**Stack:** Python, PyTorch, Motion Diffusion Model (MDM), HumanML3D, Transformer reward model with AdaLN

🏆 This project won 3rd prize in the course poster session (20 teams).

---

## Overview

Text-to-motion diffusion models generate convincing animations but routinely break physical laws - feet float, joints penetrate the ground, and limbs slide when they should be planted. We built **PRG (Physics-guided Reward Guidance)**, an inference-time method that steers a frozen Motion Diffusion Model toward physically plausible output without retraining it or touching a simulator.

---

## How It Works

**1. Preference dataset generation.** MDM is run multiple times per text prompt with different random seeds; outputs are ranked by physics error (floating + foot skating + ground penetration) and the best and worst runs become contrastive pairs. Storing the full denoising trajectory makes every timestep a training sample - 5,000 training and 750 test pairs alongside HumanML3D (23k clips).

**2. Reward model training.** A lightweight time-conditioned Transformer (4 blocks, 128 channels) is trained on these pairs with a Bradley-Terry loss, learning to score physical plausibility at any noise level.

**3. Guided inference.** Following the Diffusion Posterior Sampling idea, the reward gradient is computed on the predicted clean estimate x̂₀ at each denoising step and added to the posterior mean of the frozen MDM - no retraining, no simulator. A monotonic guidance schedule concentrates corrections near the end of denoising, where x̂₀ is most reliable.

Compared to PhysDiff (NVIDIA), the strongest physics-guided alternative, which embeds a full physics simulator inside the denoising loop, PRG achieves its corrections with a single lightweight network forward/backward pass per step.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/PRG_flow.png" title="Flow of inference for our approach - integrating a reward model with a diffusion model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Flow of inference for our approach - integrating a reward model with a diffusion model.
</div>

---

## Results

- 26% reduction in the floating metric, the dominant failure mode of the MDM baseline.
- ~10–12% reduction across the physics error suite (foot skating, ground penetration, floating) overall.
- Prompt fidelity preserved: guidance corrects physics without hijacking the semantics of the motion.

### Generated samples

<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:.75rem;margin:1rem 0;">
  <figure style="margin:0;text-align:center;"><img src="/assets/img/prg_motion_5.gif" alt="Denoising step 0" loading="lazy" style="width:100%;border-radius:10px;"><figcaption>Step 0</figcaption></figure>
  <figure style="margin:0;text-align:center;"><img src="/assets/img/prg_motion_4.gif" alt="Denoising step 1" loading="lazy" style="width:100%;border-radius:10px;"><figcaption>Step 1</figcaption></figure>
  <figure style="margin:0;text-align:center;"><img src="/assets/img/prg_motion_3.gif" alt="Denoising step 2" loading="lazy" style="width:100%;border-radius:10px;"><figcaption>Step 2</figcaption></figure>
  <figure style="margin:0;text-align:center;"><img src="/assets/img/prg_motion_2.gif" alt="Denoising step 3" loading="lazy" style="width:100%;border-radius:10px;"><figcaption>Step 3</figcaption></figure>
  <figure style="margin:0;text-align:center;"><img src="/assets/img/prg_motion_1.gif" alt="Denoising step 4" loading="lazy" style="width:100%;border-radius:10px;"><figcaption>Step 4</figcaption></figure>
</div>
<div class="caption">Motion decoded at denoising steps 0 to 4 (the first five of 50), shown as 3D skeletons.</div>

**Observation: the motion is already recognizable after the first 10% of denoising steps (5 of 50). The core kinematic structure is set between steps 0 and 4, well before the final refinements of physical plausibility.**

---

## Key Insight

Physical plausibility can be learned cheaply from generated data and applied as a gradient correction - no RL policy, no simulator, no fine-tuning. The same recipe extends beyond human motion: any diffusion-based trajectory or policy generator can be steered at inference time by a lightweight learned critic, which is a direction I am actively exploring for robot manipulation policies.


---

## Documents

- [Course report (PDF)](/assets/pdf/PRG_Report.pdf)
- [Poster (PDF)](/assets/pdf/PRG_poster.pdf)
