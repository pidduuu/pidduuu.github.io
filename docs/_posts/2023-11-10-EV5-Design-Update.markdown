---
layout: post
title:  "EV5 Design Update"
date:   2023-11-10 02:52:00 -0400
categories: jekyll update
---
After selecting our wing element profiles from [EV5 Aerodynamics Justification](https://pidduuu.github.io/jekyll/update/2023/10/23/EV5-Aerodynamics-Justification.html) I started optimizing the 2D placement of the wing elements, starting with the front wing.

I kept the primary element at its minimum AoA given in the optimal free stream ranges I found, as this would lead to more vertical clearance to fit the secondary element inside the bounding box at a higher AoA. Keeping the primary element at its minimum AoA also meant a greater chance of ground effect since a larger portion of the chord would be closer to the ground.

![groundEffect](/assets/images/groundEffect.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 Ground Effect</i></font></p>