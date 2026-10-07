---
layout: project
title: Automated Experimentation Laboratory Robot
description: An end-to-end automation system with a robotic arm integrated with lab machines to perform experiments autonomously.
img: assets/img/apex_robot_opentrons.jpg
importance: 1
methods: ["Imitation learning", "Action Chunking Transformer", "Motion planning (Informed RRT*)", "Visual servoing", "Perception (point cloud processing, YOLO26, SAM3 distillation)"]
tools: ["C++", "MoveIt", "ROS 2", "Isaac Sim"]
category: recent
related_publications: false
context: "MS in Robotic Systems Development capstone project, Carnegie Mellon University (2026)"
team:
  - name: Karthik Srinivasan
  - name: Arnav Kharbanda
  - name: Juan Muerto
  - name: Farnaz Alam Ahmed
advisor_label: Advisor
advisors:
  - name: Dr. Min Xu
    url: https://www.cmu.edu/cbd/people/xu.html
    role: Associate Professor, Computational Biology Dept., CMU
---

**APEX** (Automated Precision EXperimentation) is an integrated platform that couples a mobile manipulator with networked lab machines for autonomous experiment execution.

**My role:** planning and manipulation-integration lead - grasp planning (RRTConnect for the global approach, Cartesian planning for the final constrained descent), MoveIt + Isaac Sim hardware-in-the-loop simulation, live ZED point-cloud ingestion into the MoveIt collision environment as voxel occupancy maps, AprilTag-based target localization (camera-frame detection through extrinsic calibration to base-frame goal poses), and physical integration of the planning stack with the xArm6.

**Stack:** Python, ROS 2, MoveIt, OMPL, Isaac Sim, PyTorch (YOLO), ZED X stereo cameras, xArm6, behavior trees

---

## The Problem

Scientists lose an estimated 3 months per year to non-core, non-creative tasks. 70% of diagnostic mistakes occur in the pre-analytical phase, costing US labs 180,000 dollars annually. The direct lab automation market is projected to grow from 7.15B to 12.25B by 2033, with $1.6T in indirect potential in material and physical sciences.

---

## The Solution

APEX integrates perception, planning, manipulation, and lightweight lab-device APIs to automate routine wet-lab tasks. The system handles three core capabilities: workflow execution (running pre-programmed protocols without human intervention), material transport (autonomously moving samples between stations including liquid handlers and shakers), and active monitoring (detecting anomalies such as clogged pipettes and spilled liquids in real-time).

---

## Demo

<div class="video-container" style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;max-width:100%;">
  <iframe src="https://www.youtube.com/embed/vI8Z9WY06Nc" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
</div>

---

## Key Achievements

- Pick success rate improved from ~65% to ~99% after adding visual servo + force-feedback grasping with retry logic.
- Perception models achieved 99.5% mAP50 (top camera, YOLO trained on 2,000 images) and 99.4% mAP50 (gripper camera, 21k images) with zero false positives.
- Planning subsystem achieved 100% success rate (target: 95%) across all tested source-destination pairs, using sampling-based planning with path shortening and a midpoint-waypoint fallback.
- Demonstrated a repeatable end-to-end workflow (grasp, transport to liquid handler, dispense, shake, return) 13+ times in sequence at the Spring Validation Demonstration Encore.
- Awarded a $1,000 grant from the Swartz Center; top 20 applicants for the Gebhardt Sandbox Fund; advanced to round 2 of the McGinnis Venture Competition; showcased at National Robotics Week.

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
Sampling-based planners (RRTConnect and PRM via OMPL and MoveIt) consume voxelized point clouds from the live ZED feed and publish collision-free trajectories over ROS2. Gripper orientation is constrained throughout every trajectory to prevent liquid spillage, which shrinks the valid configuration space dramatically; reliability came from bounding the planning workspace, path shortening, and a Cartesian planner for the final constrained descent to the grasp. The system achieved a **100% planning success rate** (target: 95%) across all tested source-destination pairs.

<div class="row mt-2">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/motion_planning.png" title="Voxelized environment in RViz" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_voxel_scene.jpg" title="Live voxel map with the robot model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Voxelized environment loaded in RViz for obstacle-aware path generation (left), and the live voxel map built from the ZED point cloud around the robot model (right).</div>

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

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_arm_pipette_rack.jpg" title="Arm reaching into the liquid handler" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_base_cad_vs_real.jpg" title="Mobile manipulator: build and CAD" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Left: the arm working inside the Opentrons liquid handler. Right: the mobile manipulator as built, next to its CAD model.</div>


### Orchestration & Compute
A behavior tree acts as the central nervous system: it stores the experiment's execution sequence, coordinates asynchronous task execution, and routes commands between perception, planning, manipulation, and the lab machines. Compute is split across a Jetson Xavier (orchestrator) and a Jetson Thor (perception and planning), with an Opentrons OT-2 liquid handler and a custom PCB-driven shaker module as networked lab machines.

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

## Engineering Lessons

Real systems fail in ways simulation never shows. A few problems we hit and how we solved them:

- **The lighting deadlock.** Dim light made wellplate detection fail; brighter light created glare that filled the point cloud with noisy voxels. No lighting setting satisfied both. The fix was on the data side: fine-tuning the detectors on 2,000+ additional images across lighting conditions.
- **The planner saw the arm as an obstacle.** The live point cloud included the robot's own links, so the planner rejected valid paths as self-collisions. Solved with a robot-aware self-filter that projects the current joint configuration into the camera frame and masks those pixels before voxelization.
- **Design the failure point.** Early gripper collisions risked propagating impulse loads into the arm. We redesigned it as a two-part gripper: a metal body and a cheap 3D-printed part that is deliberately the weakest link, so a crash breaks a $2 part instead of a $5,000 arm.
- **Constrained planning is hard.** Keeping the gripper level to avoid spills eliminates most of the configuration space, and stochastic planners time out in the narrow corridors that remain. Bounding the planning workspace and falling back to Cartesian interpolation for constrained segments restored reliability.

---

## Gallery

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_me_explaining.jpeg" title="Spring validation demo" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_svd.JPG" title="Team H" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apex_team.png" title="Team H" class="img-fluid rounded z-depth-1" %}
    </div>
</div>  
<div class="caption">Spring Validation Demonstration - with mentor Dr. Min Xu.</div>

---

## Documents

- [Spring Validation Demonstration summary (PDF)](/assets/pdf/APEX_SVD_Summary.pdf)
- [Progress Review 4 slides (PDF)](/assets/pdf/APEX_Progress_Review_4.pdf)
- [Individual Lab Report 05, planning subsystem (PDF)](/assets/pdf/APEX_ILR05_Karthik.pdf)