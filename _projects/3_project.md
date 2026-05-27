---
layout: page
title: Semantic Segregation using VLMs and execution using motion planning
description: Open-vocabulary object sorting with a Vision-Language Model and a Franka robotic arm
img: assets/img/semantic_seg_cover.jpg
importance: 1
category: recent
---

16662 - Robot Autonomy course, Spring 2026, Carnegie Mellon University.

Teammates: Aman Tambi, Kushal Agarwal, Narayanan Palghat Parameshwaran, Shubh Jain


This project integrates a Vision-Language Model (VLM) with a Franka Emika Panda arm to perform open-vocabulary semantic sorting — no category-specific training required. The robot picks up an object, shows it to a RealSense camera, queries the VLM with the image and current rack state, and places it in the semantically appropriate slot.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/sem_seg_setup.png" title="Demo setup with Franka arm, two racks, and Intel RealSense" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/sem_seg_pipeline.png" title="System pipeline diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Physical setup — Franka arm centered between two three-shelf racks with the Intel RealSense mounted on the right column. Right: The six-stage pipeline from pickup through VLM reasoning to placement.
</div>

---

## Motivation

Traditional robots struggle to identify and sort novel objects in unstructured environments because they rely on fixed object taxonomies and task-specific training. Using a VLM bridges human-like visual reasoning with precise physical action, enabling intuitive open-vocabulary pick-and-place without retraining for every new category.

---

## System Overview

The pipeline runs as follows: the arm picks up an object and moves to an inspection pose visible to the camera. An RGB image is captured and sent to the VLM alongside a JSON record of the current rack state. The model returns a target slot and a natural-language explanation. The arm then deposits the object and resets for the next cycle.

The rack audit JSON persists across the full session so the VLM can maintain consistent semantic groupings as the rack fills up.

---

## VLM Benchmarking

Three models were evaluated on 10 identical placement trials each:

| Model | Correct Placements | Success Rate |
|---|---|---|
| Gemini 2.5 Pro | 9/10 | 90% |
| Claude 3.5 Sonnet | 8/10 | 80% |
| Qwen3 VL | 7/10 | 70% |

Gemini 2.5 Pro was selected as the primary model for end-to-end trials.

---

## Results

The system was evaluated across nine objects: a keychain fob, wooden letter blocks, an orange, a plush keychain toy, a travel power adapter, a video game controller, an apple, and a stapler. Eight of nine placements were semantically correct and physically stable.

<div class="video-container" style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;max-width:100%;">
  <iframe src="https://www.youtube.com/embed/7pE_sq3b1KA" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
</div>
The failure revealed a gap in the rack audit: the JSON records slot occupancy by category but carries no information about remaining physical capacity. Adding a per-slot item count would fix this directly.

---

## Final Rack State

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/sem_seg_final.jpg" title="Final rack configuration after all nine trials" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Final rack after nine trials. Distinct semantic clusters: personal accessories and toys (top shelf), food (middle shelf), electronics (bottom left), stationery (top right).
</div>

---

## Motion Planning

Safe operation in the confined workspace used four layers: a static PRM-based collision model built offline, straight-line joint-space planning at runtime (with PRM fallback on collision detection), trajectory caching to disk, and virtual wall constraints above and in front of the workspace.

---

## Team

**Primary Implementation** — Aman Tambi, Kushal Agarwal, Shubh Jain: motion planning on the physical Franka arm, trajectory caching.

**Framework & Testing** — Narayanan Palghat Parameshwaran, Karthik Srinivasan: VLM benchmarking and integration, prompt engineering, rack audit JSON state machine, object-level testing.