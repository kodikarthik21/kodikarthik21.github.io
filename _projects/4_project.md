---
layout: project
title: Speed Planning of Autonomous Electric Truck Platoons
description: A deep learning encoder-decoder model for speed planning of autonomous electric truck platoons.
img: assets/img/heliyon_bigpicture.png
importance: 1
methods: ["Encoder-decoder LSTM", "Sliding mode control", "Speed planning"]
tools: ["Python", "MATLAB"]
category: recent
related_publications: false
context: "Dual degree project, IIT Madras (2022-2023). Published in Heliyon (Elsevier), 2024"
team:
  - name: Karthik Srinivasan
  - name: Rohith G.
  - name: K. B. Devika
  - name: Shankar C. Subramanian
---

**Stack:** Python, TensorFlow/Keras (encoder-decoder LSTM), MATLAB Simulink (platoon dynamics, Sliding Mode Control)

---


## Overview

Electric truck platooning reduces aerodynamic drag and extends driving range for long-haul freight - but optimizing platoon speed under real-world constraints (battery SOC, road conditions, vehicle mass, intervehicular spacing) is hard to solve from first principles. This paper presents a sequence-to-sequence encoder-decoder LSTM model that predicts the speed profile an autonomous electric truck platoon should follow to meet a desired state-of-charge (SOC) target while maintaining string stability.

*Proposed encoder-decoder LSTM speed planner integrated with the autonomous electric truck platoon framework.*

---

## Key Contributions

- An autonomous string-stable electric truck platoon simulation framework built in MATLAB Simulink, incorporating full longitudinal vehicle dynamics, tire model, motor model, and battery model.
- An encoder-decoder LSTM model that takes an instantaneous power consumption profile (derived from a desired SOC profile) as input and outputs the speed profile the platoon should follow.
- Training on four standard heavy-vehicle highway drive cycles (ETC, Millbrook, HWFET, HHDDT) across varied operating conditions - road friction, vehicle mass, and time headway.
- A case study demonstrating how predicted drive cycles can inform policy decisions on charging station placement, battery sizing, and route planning for electric truck fleets.

---

## Model Architecture

The model maps a desired energy (SOC) profile to a feasible speed trajectory - analogous to sequence-to-sequence translation in NLP. SOC is converted to instantaneous power consumption before being fed to the encoder, making the input independent across time steps. The decoder then generates the corresponding speed profile.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/heliyon_encdec.png" title="Encoder-decoder architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Encoder-decoder sequence-to-sequence architecture used for speed planning.
</div>

---

## Training & Results

The model was trained on data generated from the platoon simulation framework using four highway drive cycles. Hyperparameter tuning was performed over LSTM layers, units, learning rate, and batch size. The final model achieved:

- **RMSE: 12.62 km/h** on the high-speed validation window (250–1500 s)
- **MAPE: 13.25%** on the same window

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/heliyon_drivecycles.png" title="Drive cycles used for training" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/heliyon_comparison.png" title="Model comparison" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Highway drive cycles used for training and validation. Right: Comparison of predicted vs. actual speed profiles across model variants.
</div>


---

