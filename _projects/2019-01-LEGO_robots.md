---
layout: page
title: Robots
description: Reinforcement Learning with Autonomous Robots
img: assets/img/robots_thumbnail.png
category: work
date: 2019-01-01
---

In cooperation with famous danish toy-maker LEGO, a team of Master students of the University of Copenhagen was tasked to explore ways of enabling the LEGO Mindstorms robot platform to learn and adapt to various challenges using reinforcement learning. The resulting robots have been used to playfully demonstrate concepts of machine learning to a wide audience, and influence the further direction of LEGOs product line. The robots I have been heavily involved in are featured below.

Since my initial work on this project, further development on topics I suggested for future work has been performed in the form of multiple Master and Bachelor Thesis. The university is still in close collaboration with LEGO. I want to specifically highlight the contribution of Morten Trolle, who further developed both robots featured here. He leveraged a multi-agent learning approach to learn with multiple robots in parallel, drastically decreasing learning time and improving results.

Parts of the project are publicly accessible on <a href="https://github.com/SteffenCzolbe/LEGO-machine-learning">Github</a>.

### Swing Robot

This robot uses an evolutionary algorithm to learn how to swing. The motion was learned in 8 hours, over 75 generations with a total of 600 offspring evaluated. Demonstration of the results:

<iframe width="560" height="315" src="https://www.youtube.com/embed/6yY9P5vG-nA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Crawl Robot

This robot uses tabular Q-learning to learn a forward crawling motion. The motion is learned in 20 minutes. Timelapse of the training:

<iframe width="560" height="315" src="https://www.youtube.com/embed/NUTv-oNWEYo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
