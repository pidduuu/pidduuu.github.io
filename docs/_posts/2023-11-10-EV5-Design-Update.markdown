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

Due to the internal design freeze being December 10th, I unfortunately did not have time this year to pursue an iterative MATLAB algorithm to determine the optimal wing setup given some basic parameters like the bounding box, air speed, and target L/D ratio. This is typically what teams do. Instead, we brute forced our way through it and ran 45 2D CFD simulations in Ansys Fluent to draw some general conclusions about what we should change if we want more downforce and less drag.

| ![AoADF](/assets/images/AoADF.jpg) | ![AoAD](/assets/images/AoAD.jpg)
| ![OverlapDF](/assets/images/OverlapDF.jpg) | ![OverlapD](/assets/images/OverlapD.jpg)
| ![SGDF](/assets/images/SGDF.jpg) | ![SGD](/assets/images/SGD.jpg)

<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 2, 3, 4, 5, 6, and 7 General trends of airfoil parameters</i></font></p>