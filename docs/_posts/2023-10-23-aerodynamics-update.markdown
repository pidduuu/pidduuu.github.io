---
layout: post
title:  "Aerodynamics Update"
date:   2023-10-23 01:07:00 -0400
categories: jekyll update
---
The past month and a half has been extremely busy...
![EV5 1080P](/assets/images/EV5 1080P.JPG){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><i>Preliminary Render of EV5 Concept</i></p>

---
# It's All About Tires
Increasing the normal force increases the lateral force at a given slip angle. What EV5's operating slip angle range is needs to be determined, however this fundamental principle is the basis on which we are going to be developing the aerodynamics package. Some raw data from the FSAE TTC for my team's tires can be seen in the image below.
![43075](/assets/images/43075.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><i>Hoosier 43075 w/ 7" Rim Width</i></p>

From here we can interpolate % changes in lateral force with and without theoretical aerodynamic devices, assuming 196N (front wing) + 236N (rear wing) of downforce at 13.33mps, which through competitive analysis we have determined is the average FSAE speed around the FSAE Michigan endurance circuit.

| Slip Angle (deg) | Lateral Force w/o Aero (N)| Lateral Force w/ Aero (N) | Change (%)
| 1 | 404 | 436.4 | 8.02%
| 2 | 578.7 | 626.76 | 8.30% 
| 3 | 759.65 | 830.12 | 9.28%

From the % changes it's clear to see the improvement aerodynamic devices could make in lateral force. 

---
# Faster in the Corners, Slower on the Straights
Quantifying the change in performance in tires is important, but ensuring laptime is more sensitive to downforce rather than drag is equally as important. For this reason we developed an in-house lap simulation program using MATLAB since we would not be able to generate the required graph from OptimumLap. Full credits go to Sepehr Makarian Abdolahi for writing this program to quantify design constraints for the aerodynamics and powertrain subsystems.
![laptimeCl](/assets/images/laptimeCl.jpg){:style="display:block; margin-left:auto; margin-right:auto"}