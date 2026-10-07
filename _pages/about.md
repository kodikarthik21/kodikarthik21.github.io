---
layout: about
title: about
permalink: /
subtitle: 

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  more_info: '<div class="edu"><div class="edu-h">Education</div><div class="edu-r"><img src="/assets/img/cmu_logo.png" alt="CMU"><div><b>MS in Robotic Systems Development</b><span>Carnegie Mellon University</span><em>2025 - May 2027</em></div></div><div class="edu-r"><img src="/assets/img/iitm_logo.jpg" alt="IIT Madras"><div><b>B.Tech Mechanical Engineering + M.Tech Data Science</b><span>IIT Madras</span><em>2018 - 2023</em></div></div><div class="edu-h" style="margin-top:1.2rem">Experience</div><div class="edu-r"><img src="/assets/img/serve_logo.png" alt="Serve Robotics"><div><b>Machine Learning Intern, Autonomy</b><span>Serve Robotics</span><em>May 2026 - Aug 2026</em></div></div><div class="edu-r"><img src="/assets/img/hsbc_logo.png" alt="HSBC"><div><b>Senior Associate, Quantitative Modeling</b><span>HSBC</span><em>Jul 2023 - Jul 2025</em></div></div></div>'

# selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---

<style>
  .home-h { font-size: 1.2rem; overflow: hidden; font-weight: 700; margin: 2.2rem 0 .8rem; padding-bottom: .35rem; border-bottom: 1px solid var(--global-divider-color); }
  .work { display: flex; gap: 1.1rem; align-items: flex-start; padding: .9rem 0; }
  .work + .work { border-top: 1px solid var(--global-divider-color); }
  .work img { flex: none; width: 170px; height: 110px; object-fit: cover; border-radius: 8px; border: 1px solid var(--global-divider-color); }
  .work b { display: block; font-size: 1.02rem; line-height: 1.3; margin-bottom: .2rem; }
  .work b a { color: var(--global-text-color); }
  .work b a:hover { color: var(--global-theme-color); }
  .glance { display: grid; gap: .7rem; margin: 1.4rem 0 0; padding: 0; }
  .glance > div { display: grid; grid-template-columns: 6.5rem 1fr; gap: .75rem; align-items: baseline; font-size: .93rem; line-height: 1.5; }
  .glance > div > b { font-size: .68rem; letter-spacing: .1em; text-transform: uppercase; color: var(--global-theme-color); }
  .glance .chips { display: flex; flex-wrap: wrap; gap: .3rem; }
  .glance .chips span { font-size: .72rem; font-weight: 600; padding: .12rem .55rem; border-radius: 999px; background: color-mix(in srgb, var(--global-theme-color) 12%, transparent); color: var(--global-theme-color); }
  @media (max-width: 576px) { .glance > div { grid-template-columns: 1fr; gap: .2rem; } }
  .work p { margin: 0; font-size: .93rem; line-height: 1.5; color: var(--global-text-color-light); }
  @media (max-width: 576px) { .work { flex-direction: column; } .work img { width: 100%; height: auto; aspect-ratio: 16/9; } }
  .edu, .edu * { font-family: "Roboto", -apple-system, "Segoe UI", sans-serif; }
  .edu { text-align: left; margin-top: 1rem; }
  .edu-h { font-size: .75rem; letter-spacing: .12em; text-transform: uppercase; font-weight: 700; color: var(--global-theme-color); margin-bottom: .5rem; }
  .edu-r { display: flex; gap: .7rem; align-items: center; padding: .6rem 0; border-top: 1px solid var(--global-divider-color); }
  .edu-r img { flex: none; width: 42px; height: 42px; object-fit: contain; border-radius: 6px; }
  .edu-r div { line-height: 1.3; }
  .edu-r b { display: block; font-size: .88rem; color: var(--global-text-color); }
  .edu-r span { display: block; font-size: .82rem; color: var(--global-text-color-light); }
  .edu-r em { display: block; font-size: .78rem; font-style: normal; color: var(--global-text-color-light); }
  .post > article > p, .clearfix > p { font-size: .93rem; line-height: 1.6; font-weight: 400; }
  .publications h2.bibliography { display: none; }
  .publications ol.bibliography { margin-top: 0; }
</style>

I'm a Robotics Master's student at Carnegie Mellon University (MRSD, class of 2027). My coursework spans Generative AI, Robot Learning, Robot Autonomy and Learning for 3D Vision.

My interests lie in teaching robots to act intelligently with machine learning (RL, imitation learning), spanning **behavior prediction, manipulation, and navigation (driving)**.

I interned at Serve Robotics in Summer 2026, where I trained a **diffusion model** to predict pedestrian behavior and developed a framework for training an **RL** navigation policy in simulation (**PPO**, Unreal Engine) for moving around dense pedestrians. I am also working on the autonomy stack of a <a href="{{ '/projects/2_project/' | relative_url }}">mobile manipulator for automating lab experiments</a> as a part of my capstone project at CMU. I'm implementing an **Action Chunking Transformer** using **imitation learning** to place wellplates, with **Informed RRT\*** motion planning and **visual servoing** for grasping.

I am looking for **full-time new grad roles starting May 2027**. Please feel free to reach out if you have any relevant openings!

Outside work, I'm a foodie who enjoys exploring different cuisines and always up for trying something new! Feel free to send restaurant recommendations if we are in the same city :). I also enjoy playing badminton, tennis, and cricket recreationally, though I'm not formally trained in any of them. Let's connect on <a href="https://linkedin.com/in/srini-karthik">LinkedIn</a>, or see my <a href="{{ '/background/' | relative_url }}">background</a>.

<h2 class="home-h">Selected work</h2>
<div class="work">
  <img src="{{ '/assets/img/apex_robot_opentrons.jpg' | relative_url }}" alt="APEX">
  {% assign pj = site.projects | where_exp: "x", "x.path contains '/2_project.md'" | first %}<div><b><a href="{{ '/projects/2_project/' | relative_url }}">{{ pj.title }}</a></b><p>A mobile manipulator that runs wet-lab protocols on its own. I built the perception models, motion planner, and gripper.</p>{% include chips.liquid methods=pj.methods tools=pj.tools %}</div>
</div>
<div class="work">
  <img src="{{ '/assets/img/PRG_presentation.jpg' | relative_url }}" alt="PRG poster">
  {% assign pj = site.projects | where_exp: "x", "x.path contains '/1_project.md'" | first %}<div><b><a href="{{ '/projects/1_project/' | relative_url }}">{{ pj.title }}</a></b><p>A reward model steers every denoising step toward physically plausible motion. 3rd of 20 teams.</p>{% include chips.liquid methods=pj.methods tools=pj.tools %}</div>
</div>
<div class="work">
  <img src="{{ '/assets/img/semantic_seg_cover.jpg' | relative_url }}" alt="VLM sorting">
  {% assign pj = site.projects | where_exp: "x", "x.path contains '/3_project.md'" | first %}<div><b><a href="{{ '/projects/3_project/' | relative_url }}">{{ pj.title }}</a></b><p>A Franka arm sorts objects it has never seen using a vision-language model and PRM motion planning.</p>{% include chips.liquid methods=pj.methods tools=pj.tools %}</div>
</div>

<h2 class="home-h">Publications</h2>
<div class="publications">
  {% bibliography %}
</div>

