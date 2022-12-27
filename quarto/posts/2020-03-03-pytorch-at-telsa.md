---
title: "Pytorch at Tesla"
author: "Manu Hegde"
date: "2020-03-23"
categories: [neural networks, tesla, electric cars]
---
# Pytorch at Tesla
This is an old video back in nov 2019.
- They use their own homegrown HydraNet
  - (2,960,1280) meaning 1280x960 colour images (video frames) with ResNet-50 like dilated backbones
  - FPN/DeepLab/Unet heads for ~15 tasks
  - fyi hydra is a mythiological serpant monster that has one body and many heads
- 8 Hydra nets for 8 cameras. 
  - they make basic detections like road edge, side roads, markings, vehicles etc
  - this data is then taken and stitched together by another recurrent net to produce a larger understanding of the environment i.e like the layout of the area, where are the cross/side roads, etc.
  - i.e for ex: right camera sees a road, then that means there is a road perpendicular to the current road
- all tasks are trained in parallel on a async pool of worker nodes 
  - For autopilot 2.0: 48 networks, 1000 predictions, 72,000 gpu hours
  - operation vacation: if data is labelled regularly, everything else is automated (so essesntially engineers can go on vacay)
- operational stats:
  - 50,000+ smart summon sessions
  - 1 Bn miles, 200,000 auto lane changes across 50+ countries

![](https://raw.githubusercontent.com/manuhg/ramblings/master/images/Screenshot%202020-03-03%20at%206.49.07%20PM.png) Hydranet Overview

---

Misc:
- Tesla's FSD - Full Self Driving (Capabality)
- dojo - area of training (originally judo but generally all experiments, setting hair on fire etc?)

---

Images:  
![](https://raw.githubusercontent.com/manuhg/ramblings/master/images/Screenshot%202020-03-03%20at%206.44.37%20PM.png) *Operation Vacation*
![](https://raw.githubusercontent.com/manuhg/ramblings/master/images/Screenshot%202020-03-03%20at%206.46.48%20PM.png) *FSD Computer*

---

Source: [Pytorch at Tesla](https://www.youtube.com/watch?reload=9&v=oBklltKXtDE&feature=youtu.be)
