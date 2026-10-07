---
layout: page
title: background
permalink: /background/
description: Experience, projects, publications, education and skills.
nav: true
nav_order: 2
---

<style>
  .bg { --bg-card: var(--global-card-bg-color); --bg-line: var(--global-divider-color); --bg-acc: var(--global-theme-color); --bg-mut: var(--global-text-color-light); --bg-chip: color-mix(in srgb, var(--global-theme-color) 14%, transparent); }
  .bg h2.bg-h { display: flex; align-items: center; gap: .6rem; font-size: 1.35rem; font-weight: 800; letter-spacing: -.01em; margin: 3rem 0 1.2rem; border: 0; padding: 0; }
  .bg h2.bg-h::after { content: ""; flex: 1; height: 1px; background: var(--bg-line); }
  .bg h2.bg-h i { color: var(--bg-acc); font-size: 1.05rem; }
  .bg-nav { display: flex; flex-wrap: wrap; gap: .6rem; margin-bottom: .5rem; }
  .bg-nav a { display: inline-flex; align-items: center; gap: .5rem; font-size: .95rem; font-weight: 600; padding: .5rem 1.1rem; border-radius: 999px; border: 1px solid color-mix(in srgb, var(--bg-acc) 35%, transparent); background: color-mix(in srgb, var(--bg-acc) 14%, transparent); color: var(--global-text-color); text-decoration: none; transition: all .15s; }
  .bg-nav a i { color: var(--bg-acc); font-size: .9rem; }
  .bg-nav a:hover { background: var(--bg-acc); border-color: var(--bg-acc); color: #fff; transform: translateY(-1px); }
  .bg-nav a:hover i { color: #fff; }
  html { scroll-behavior: smooth; }
  .bg .publications h2.bibliography { display: none; }
  .bg .publications ol.bibliography { margin: 0; padding: 0; }
  .bg .publications ol.bibliography li { margin: 0; }
  .bg .publications .row { align-items: center; }
  .bg .publications .abbr { max-width: 110px; }
  .bg .publications .abbr figure { margin: 0; }
  .bg .publications .title { font-size: 1rem; }
 position: relative; padding-left: 1.6rem; }
  .tl::before { content: ""; position: absolute; left: .45rem; top: .4rem; bottom: .4rem; width: 2px; background: var(--bg-line); }
  .job { position: relative; margin-bottom: 1.25rem; padding: 1.1rem 1.25rem; border: 1px solid var(--bg-line); border-radius: 14px; background: var(--bg-card); }
  .job::before { content: ""; position: absolute; left: -1.55rem; top: 1.5rem; width: 12px; height: 12px; border-radius: 50%; background: var(--bg-acc); box-shadow: 0 0 0 4px var(--global-bg-color); }
  .job-top { display: flex; gap: .9rem; align-items: center; }
  .job-top img { width: 52px; height: 52px; object-fit: contain; border-radius: 10px; background: #fff; flex: none; }
  .job-who { flex: 1; min-width: 0; }
  .job-who b { display: block; font-size: 1.05rem; line-height: 1.25; }
  .job-who span { font-size: .9rem; color: var(--bg-mut); }
  .job-when { text-align: right; font-size: .82rem; color: var(--bg-mut); white-space: nowrap; }
  .job-when strong { display: block; color: var(--global-text-color); font-size: .86rem; }
  .job ul { margin: .85rem 0 .2rem; padding-left: 1.1rem; }
  .job li { margin-bottom: .4rem; line-height: 1.55; font-size: .95rem; }
  .job li::marker { color: var(--bg-acc); }
  .job li strong { color: var(--global-text-color); }
  .tools { display: flex; flex-wrap: wrap; gap: .35rem; margin-top: .75rem; }
  .tools span { font-size: .74rem; font-weight: 600; padding: .18rem .6rem; border-radius: 999px; background: var(--bg-chip); color: var(--bg-acc); }
  .role { margin-top: .9rem; padding-top: .8rem; border-top: 1px dashed var(--bg-line); }
  .role-h { display: flex; justify-content: space-between; gap: .5rem; flex-wrap: wrap; font-weight: 700; font-size: .95rem; }
  .role-h em { font-style: normal; font-weight: 500; font-size: .82rem; color: var(--bg-mut); }
  .bg-edu { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1rem; }
  .bg-edu .job { margin: 0; display: flex; flex-direction: column; }
  .bg-edu .job-top { min-height: 4.2rem; }
  .bg-edu details.ta { margin-top: auto; padding-top: .7rem; border-top: 1px dashed var(--bg-line); }
  .bg-edu details.ta summary { cursor: pointer; font-size: .85rem; font-weight: 600; color: var(--bg-acc); }
  .bg-edu details.ta ul { margin: .6rem 0 0; padding-left: 1.1rem; }
  .bg-edu details.ta li { font-size: .88rem; margin-bottom: .3rem; }
  .bg-edu details.ta li em { font-style: normal; color: var(--bg-mut); margin-left: .4rem; font-size: .8rem; }
  .bg-edu .job::before { display: none; }
  .skills { display: grid; grid-template-columns: repeat(4, minmax(0, 1fr)); gap: 1rem; }
  @media (max-width: 992px) { .skills { grid-template-columns: repeat(2, minmax(0, 1fr)); } }
  .skills > div { padding: 1rem 1.1rem; border: 1px solid var(--bg-line); border-radius: 14px; background: var(--bg-card); }
  .skills h3 { font-size: .72rem; letter-spacing: .12em; text-transform: uppercase; font-weight: 700; color: var(--bg-acc); margin: 0 0 .6rem; }
  .skills .tools { margin-top: 0; }
  .skills .tools span { background: transparent; border: 1px solid var(--bg-line); color: var(--global-text-color); font-weight: 500; }
  @media (max-width: 576px) { .job-top { flex-wrap: wrap; } .job-when { text-align: left; width: 100%; } .tl { padding-left: 1.2rem; } .job::before { left: -1.2rem; } }
</style>

<div class="bg">

<div class="bg-nav">
  <a href="#education"><i class="fa-solid fa-graduation-cap"></i>Education</a><a href="#skills"><i class="fa-solid fa-screwdriver-wrench"></i>Skills</a><a href="#publications"><i class="fa-solid fa-book-open"></i>Publications</a><a href="#experience"><i class="fa-solid fa-briefcase"></i>Experience</a><a href="#projects"><i class="fa-solid fa-flask"></i>Projects</a>
</div>

<h2 class="bg-h" id="education"><i class="fa-solid fa-graduation-cap"></i> Education</h2>

<div class="bg-edu">
  <div class="job">
    <div class="job-top">
      <img src="{{ '/assets/img/cmu_logo.png' | relative_url }}" alt="Carnegie Mellon University">
      <div class="job-who"><b>Carnegie Mellon University</b><span>MS in Robotic Systems Development</span></div>
      <div class="job-when"><strong>2025 – 2027</strong>CGPA 4.08 / 4</div>
    </div>
    <ul>
      <li>Coursework: <strong>Generative AI, Computer Vision, Robot Autonomy, Manipulation, Estimation and Control, Intro to Robot Learning*, Learning for 3D Vision*</strong> <span style="color:var(--bg-mut);font-size:.85rem">(* in progress)</span></li>
      <li>Capstone project: <a href="{{ '/projects/2_project/' | relative_url }}">mobile manipulator for laboratory automation</a>, with a team of 4. Advisor: <a href="https://www.cmu.edu/cbd/people/xu.html" target="_blank" rel="noopener">Dr. Min Xu</a>.</li>
    </ul>
    <details class="ta"><summary>Teaching assistantships (3)</summary>
      <ul>
        <li><strong>Robot Kinematics and Dynamics</strong>, Prof. Jeff Ichnowski <em>Fall 2026</em></li>
        <li><strong>Fundamentals of Robot Control</strong>, Prof. Hartmut Geyer <em>Spring 2026</em></li>
        <li><strong>Fundamentals of Control</strong>, Prof. Yorie Nakahira <em>Fall 2025</em></li>
      </ul>
    </details>
  </div>
  <div class="job">
    <div class="job-top">
      <img src="{{ '/assets/img/iitm_logo.jpg' | relative_url }}" alt="Indian Institute of Technology Madras">
      <div class="job-who"><b>IIT Madras</b><span>B.Tech Mechanical Engineering + M.Tech Data Science</span></div>
      <div class="job-when"><strong>2018 – 2023</strong>CGPA 9.36 / 10</div>
    </div>
    <ul>
      <li>Coursework: <strong>Deep Learning, Data Analytics, Modern Control Theory, Non-Linear Systems Analysis, Process Optimization</strong></li>
      <li>Thesis: <a href="{{ '/projects/4_project/' | relative_url }}">speed planning for electric truck platoons</a>, advised by Prof. Shankar Ram C S and Dr. Devika K B.</li>
      <li>Co-curricular: <strong>Team Captain, Raftar Formula Racing (Formula Student)</strong>. Led the team's transition from a combustion to an electric racecar and won the first design competition.</li>
    </ul>
    <details class="ta"><summary>Teaching assistantships (2)</summary>
      <ul>
        <li><strong>Measurements, Instrumentation and Control</strong>, Prof. Manish Anand <em>Spring 2023</em></li>
        <li><strong>Kinematics and Dynamics of Machinery</strong>, Prof. Manish Anand <em>Fall 2022</em></li>
      </ul>
    </details>
  </div>
</div>

<h2 class="bg-h" id="skills"><i class="fa-solid fa-screwdriver-wrench"></i> Skills</h2>

<div class="skills">
  <div><h3>Programming and data</h3><div class="tools"><span>Python</span><span>C++</span><span>SQL</span><span>Q / KDB+</span></div></div>
  <div><h3>Machine learning</h3><div class="tools"><span>PyTorch</span><span>Keras</span><span>TensorFlow</span></div></div>
  <div><h3>Robotics and simulation</h3><div class="tools"><span>ROS2</span><span>MoveIt</span><span>MuJoCo</span><span>IsaacSim</span><span>MATLAB</span><span>Simulink</span><span>ANSYS</span></div></div>
  <div><h3>Design and CAD</h3><div class="tools"><span>SolidWorks</span><span>Fusion 360</span><span>CATIA</span></div></div>
</div>

<h2 class="bg-h" id="publications"><i class="fa-solid fa-book-open"></i> Publications</h2>

<div class="publications">
  {% bibliography %}
</div>

<h2 class="bg-h" id="experience"><i class="fa-solid fa-briefcase"></i> Experience</h2>

<div class="tl">

  <div class="job">
    <div class="job-top">
      <img src="{{ '/assets/img/serve_logo.png' | relative_url }}" alt="Serve Robotics">
      <div class="job-who"><b>Serve Robotics</b><span>Machine Learning Intern, Autonomy</span></div>
      <div class="job-when"><strong>May 2026 – Aug 2026</strong>San Carlos, CA</div>
    </div>
    <ul>
      <li>Built a <strong>pedestrian behavior prediction model</strong> with a <strong>diffusion framework</strong> (NVIDIA TRACE), trained on real-world sidewalk deployment data to forecast pedestrian trajectories and dynamic obstacle interactions.</li>
      <li>Trained a privileged <strong>teacher navigation policy</strong> for a sidewalk delivery robot with <strong>online RL (PPO)</strong> in simulation, using the pedestrian predictions as an input and a custom <strong>reward model</strong> to enable socially aware maneuvers such as yielding on narrow sidewalks.</li>
    </ul>
    {% include chips.liquid methods="Diffusion models (NVIDIA TRACE)|Reinforcement learning (PPO)|Privileged teacher policy|Pedestrian behavior prediction" tools="PyTorch|Unreal Engine" %}
  </div>

  <div class="job">
    <div class="job-top">
      <img src="{{ '/assets/img/hsbc_logo.png' | relative_url }}" alt="HSBC">
      <div class="job-who"><b>HSBC Global Markets</b><span>Equities Execution Services</span></div>
      <div class="job-when"><strong>Jul 2023 – Jul 2025</strong>Bengaluru, India</div>
    </div>
    <div class="role">
      <div class="role-h">Senior Associate, Quantitative Modeling <em>Mar 2025 – Jul 2025</em></div>
      <ul>
        <li>Estimated <strong>hidden liquidity</strong> in cash equity markets and improved an execution algorithm to capture <strong>25% more liquidity</strong>.</li>
        <li>Investigated adding order aggressiveness as a metric to improve the existing <strong>Almgren Chriss</strong> market impact model.</li>
      </ul>
    </div>
    <div class="role">
      <div class="role-h">Associate, Quantitative Modeling <em>Jul 2023 – Mar 2025</em></div>
      <ul>
        <li>Awarded <strong>Rising Star of Q2 (2024)</strong> in the Markets and Securities Services division for exemplary performance.</li>
        <li>Introduced the <strong>equities execution platform</strong> for an emerging market based on quantitative research on market behaviour.</li>
        <li>Built a tool for <strong>post-trade analysis</strong> of orders that flags non-optimally executed orders to enable better troubleshooting.</li>
      </ul>
    </div>
    {% include chips.liquid methods="Market impact models" tools="Python|SQL|Q / KDB+" %}
  </div>

  <div class="job">
    <div class="job-top">
      <img src="{{ '/assets/img/mathlogic_logo.jpg' | relative_url }}" alt="Mathlogic Consulting Services">
      <div class="job-who"><b>Mathlogic Consulting Services</b><span>Deep Learning Intern</span></div>
      <div class="job-when"><strong>May 2022 – Jul 2022</strong>Gurugram, India</div>
    </div>
    <ul>
      <li>Proposed a model for a physician-focused clinical documentation improvement firm to <strong>predict the outcome of insurance claims</strong>.</li>
      <li>Implemented Transformer-based (<strong>SAINT</strong>) and Factorization Machines-based (<strong>DeepFM</strong>) neural networks for tabular data.</li>
      <li>Achieved <strong>7.5% and 10% improvement</strong> in ROC-AUC and F1 score over the incumbent XGBoost models.</li>
    </ul>
    {% include chips.liquid methods="Tabular deep learning (SAINT, DeepFM, XGBoost)" tools="PyTorch" %}
  </div>

  <div class="job">
    <div class="job-top">
      <img src="{{ '/assets/img/osu_logo.jpg' | relative_url }}" alt="Ohio State University">
      <div class="job-who"><b>Ohio State University</b><span>Research Intern, Movement Lab</span></div>
      <div class="job-when"><strong>Dec 2021 – Jan 2022</strong>Columbus, OH</div>
    </div>
    <ul>
      <li>Modeled the <strong>kinematics and multi-body dynamics</strong> of dice stacking by deriving first-principles equations (dynamic manipulation).</li>
      <li>Visualized the stacking sequences with a <strong>hybrid simulation in MATLAB</strong>, using the derived motion and force equations.</li>
    </ul>
    {% include chips.liquid methods="Dynamics|Simulation" tools="MATLAB" %}
  </div>

  <div class="job">
    <div class="job-top">
      <img src="{{ '/assets/img/tuberlin_logo.png' | relative_url }}" alt="TU Berlin">
      <div class="job-who"><b>Technische Universität Berlin</b><span>DAAD-WISE Research Intern, Control Systems Group</span></div>
      <div class="job-when"><strong>Jun 2021 – Aug 2021</strong>Berlin, Germany</div>
    </div>
    <ul>
      <li>Developed an optimized <strong>multi-agent cooperation algorithm</strong> using <strong>Iterative Learning Control</strong> in Python, letting a system of robots jointly learn and perform a maneuver. Tested in simulation on Two-Wheel-Inverted-Pendulum robots (TWIPR) performing a limbo under a bar.</li>
      <li>Tuned the weights of the different learners and achieved a <strong>35% performance improvement</strong> over the existing learning algorithm.</li>
    </ul>
    {% include chips.liquid methods="Iterative learning control|Multi-agent systems" tools="Python" %}
  </div>

</div>

<h2 class="bg-h" id="projects"><i class="fa-solid fa-flask"></i> Selected projects</h2>

<div class="row row-cols-1 row-cols-md-3">
  {% assign featured = "2_project,1_project,3_project" | split: "," %}
  {% for id in featured %}
    {% assign path = "_projects/" | append: id | append: ".md" %}
    {% assign project = site.projects | where: "path", path | first %}
    {% include projects.liquid %}
  {% endfor %}
</div>
<p style="text-align:right; font-size:.9rem;"><a href="{{ '/projects/' | relative_url }}">All projects &rarr;</a></p>

</div>
