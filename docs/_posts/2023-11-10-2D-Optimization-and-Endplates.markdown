---
layout: post
title:  "2D Optimization and Endplates"
date:   2023-11-10 02:52:00 -0400
categories: jekyll update
---

---
# Preliminary 2D Multi-Element Optimization
After selecting our wing element profiles from [EV5 Aerodynamics Justification](https://pidduuu.github.io/jekyll/update/2023/10/23/EV5-Aerodynamics-Justification.html) I started optimizing the 2D placement of the wing elements, starting with the front wing.

I kept the primary element at its minimum AoA given in the optimal free stream ranges I found, as this would lead to more vertical clearance to fit the secondary element inside the bounding box at a higher AoA. Keeping the primary element at its minimum AoA also meant enhanced ground effect since a larger portion of the chord would be closer to the ground.

![groundEffect](/assets/images/groundEffect.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 Ground Effect</i></font></p>

Due to the internal design freeze being December 10th, I unfortunately did not have time this year to pursue an iterative MATLAB algorithm to determine the optimal wing setup given some basic parameters like the bounding box, air speed, and target L/D ratio. This is typically what teams do. Instead, we brute forced our way through it and ran 45 2D CFD simulations in Ansys Fluent to draw some general conclusions about what we should change if we want more downforce and less drag.

| ![AoADF](/assets/images/AoADF.jpg) | ![AoAD](/assets/images/AoAD.jpg)
| ![OverlapDF](/assets/images/OverlapDF.jpg) | ![OverlapD](/assets/images/OverlapD.jpg)
| ![SGDF](/assets/images/SGDF.jpg) | ![SGD](/assets/images/SGD.jpg)

<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 2, 3, 4, 5, 6, and 7 General trends of airfoil parameters. We isolated one parameter (e.g. AoA) and kept the others constant (e.g. overlap and slot gap) to understand the effects of each parameter</i></font></p>

Using these general trends we tested combinations of these parameters to try and achieve the highest amount of downforce. Since the plan is to only use wings this year, achieving our target of Cl=4.6 will require some aggressive setups. 4.6 may not even be possible with just wings, especially since we don't have time to optimize the lift of the chassis, however we want to see how close we can get.

Eventually, through more 2D CFD at 13.33mps, we converged to preliminary setups for the front and rear wings.

| ![FWvelocity](/assets/images/FWvelocity.jpg) | ![FWpressure](/assets/images/FWpressure.jpg)
| Downforce (N) | 186.85
| Drag (N) | 2.22

<p align = "center"><font size = "2" color="#00aaff"><i>Table 1 Front wing velocity and pressure contour plots</i></font></p>

| ![RWvelocity](/assets/images/RWvelocity.jpg) | ![RWpressure](/assets/images/RWpressure.jpg)
| Downforce (N) | 224.40
| Drag (N) | 4.83

<p align = "center"><font size = "2" color="#00aaff"><i>Table 2 Rear wing velocity and pressure contour plots</i></font></p>

---
# Preliminary Endplate Designs
With the wing setups optimized, I turned my attention to justifying and modelling preliminary endplates.

Endplates are commonplace in race car aerodynamics, however I still wanted to quantify change in downforce and drag with and without endplates to be thorough. I want future members to understand why we are spending extra money and man power to manufacture endplates.

|  | w/o Endplates | w/ Flat Endplates
| Images | ![noEP](/assets/images/noEP.jpg) | ![EP](/assets/images/EP.jpg)
| Cl (-) | -5.21 | -5.65
| Cd (-) | 0.93 | 0.91

<p align = "center"><font size = "2" color="#00aaff"><i>Table 3 Endplates vs. no endplates. Reduced flow mixing with endplates improves downforce and drag</i></font></p>