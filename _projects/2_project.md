---
layout: page
title: Automated Experimentation Laboratory Robot
description: An end-to-end automation system with a robotic arm integrated with lab machines to perform experiments autonomously.
img: assets/img/apex_preview.jpg
importance: 1
category: recent
related_publications: false
---

MS in Robotic Systems Development — Capstone Project (Dec 2025 → Nov 2026)

Teammates: Arnav Kharbanda, Juan Muerto, Farnaz Alam Ahmed

Mentor: Dr. Min Xu

Project: APEX Labs — Automated Precision EXperimentation Laboratories, an integrated platform that couples a mobile manipulator with networked lab machines for autonomous experiment execution.

---

## The Problem

Scientists lose an estimated 3 months per year to non-core, non-creative tasks. 70% of diagnostic mistakes occur in the pre-analytical phase, costing US labs 180,000 dollars annually. The direct lab automation market is projected to grow from 7.15B to 12.25B by 2033, with $1.6T in indirect potential in material and physical sciences.

---

## The Solution

APEX Labs integrates perception, planning, manipulation, and lightweight lab-device APIs to automate routine wet-lab tasks. The system handles three core capabilities: workflow execution (running pre-programmed protocols without human intervention), material transport (autonomously moving samples between stations including liquid handlers and shakers), and active monitoring (detecting anomalies such as clogged pipettes and spilled liquids in real-time).

---

## Demo

<div class="video-container" style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;max-width:100%;">
  <iframe src="https://www.youtube.com/embed/vI8Z9WY06Nc" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
</div>

---

## Key Achievements

- Pick success rate improved from ~65% to ~99% after adding visual servo + force-feedback grasping with retry logic.
- Perception models achieved 99.5% mAP50 (top camera) and 99.4% mAP50 (gripper camera) with zero false positives.
- Planning subsystem achieved 100% success rate across all tested configurations.
- Awarded a $1,000 grant from the Swartz Center to support early prototyping.
- Selected among the top 20 applicants for the Gebhardt Sandbox Fund for early-stage founders.

---

## Architecture

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_functional_arch.png" title="Functional architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Functional architecture: from user input through perception, planning, manipulation, and lab machine integration to experiment results.</div>



---

## Subsystems

### Perception
Two ZED stereo cameras feed YOLO-based detectors. The overhead camera scans the environment and provides 3D positions of lab equipment to the planning module; the wrist camera guides close-range visual servo grasping.

<div class="row mt-2">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/perception_top_camera.png" title="Top camera detection" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/perception_gripper_camera.png" title="Gripper camera detection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Left: Top camera detecting a wellplate (99.5% mAP50), and the point cloud of the environment in RViz used for collision-aware planning. Right: Gripper camera centering on target (99.4% mAP50). </div>

### Planning
A PRM-based planner consumes voxelized point clouds and publishes collision-free trajectories over ROS2. Gripper orientation is constrained to prevent liquid spillage during transport. The system achieved a **100% planning success rate** (target: 95%) across all tested source-destination pairs.

<div class="row mt-2">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/motion_planning.png" title="Voxelized environment in RViz" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Voxelized environment loaded in RViz for obstacle-aware path generation.</div>

### Manipulation
A custom two-finger lead-screw gripper with fingertip FSRs uses Image-Based Visual Servoing (IBVS) via a PnP algorithm to center on the wellplate. Force sensor readings provide grasp verification and centering error correction, with automatic retries on failure. Achieved **100% success rate with retries** (target: 75%) across 15 grasps.

<div class="row mt-2">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_gripper.png" title="Custom gripper" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Mobile_base_in_IsaacSim.png" title="Mobile_base_in_IsaacSim" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Left: Custom gripper with fingertip force sensing in operation, Right: Mobile base in Isaac Sim</div>


### User Interface
A React UI streams live camera feeds and system status, supports natural language experiment input via GPT-5, and provides step-by-step experiment monitoring.

<div class="row mt-2">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/capstone_UI.png" title="User interface" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Web UI showing live experiment execution: step tracker, executor status, and multi-camera feeds with real-time YOLO detection overlays.</div>

---

## Results

All spring semester performance targets were met or exceeded:

| Subsystem | Target | Achieved |
|---|---|---|
| Recognize Lab Equipment | 90% accuracy | 100% (5/5) |
| Localize Lab Equipment | ≤ 3 cm error | < 1 cm error |
| Grasp Lab Equipment | 75% success | 100% (6/6) |
| Plan to Reach Equipment | 95% success | 100% (16/16) |
| Command Lab Machines | 100% accuracy | 100% (2/2) |

---

## Gallery

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_me_explaining.jpeg" title="Spring validation demo" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_svd.png" title="Team H" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_team.png" title="Team H" class="img-fluid rounded z-depth-1" %}
    </div>
</div>  
<div class="caption">Spring Validation Demonstration — with mentor Dr. Min Xu.</div>