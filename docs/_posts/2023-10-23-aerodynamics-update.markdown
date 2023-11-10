---
layout: post
title:  "Aerodynamics Update"
date:   2023-10-23 01:07:00 -0400
categories: jekyll update
---
The past month and a half has been extremely busy...

![EV5 1080P](/assets/images/EV5 1080P.JPG){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. X Preliminary Render of EV5 Concept</i></font></p>

---
# It's All About Tires
Increasing the normal force increases the lateral force at a given slip angle. What EV5's operating slip angle range is needs to be determined, however this fundamental principle is the basis on which I am going to be developing the aerodynamics package. Some raw data from the FSAE TTC for my team's tires can be seen in the image below.

![43075](/assets/images/43075.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. X Hoosier 43075 w/ 7" Rim Width</i></font></p>

From here I can interpolate % changes in lateral force with and without theoretical aerodynamic devices, assuming 196N (front wing) + 236N (rear wing) of downforce at 13.33mps from a preliminary JavaFoil simulation with a dual-element airfoil setup. I determined 13.33mps is the average FSAE Michigan endurance cornering speed through competitive analysis (i.e. many, many hours of YouTube onboards watched and many, many papers read...)

| Slip Angle (deg) | Lateral Force w/o Aerodynamics (N)| Lateral Force w/ Aerodynamics (N) | Change in Lateral Force (%)
| 1 | 404 | 436.4 | 8.02%
| 2 | 578.7 | 626.76 | 8.30% 
| 3 | 759.65 | 830.12 | 9.28%

From the % changes it's clear to see the improvement aerodynamic devices could make in lateral force. 

---
# Faster in the Corners, Slower on the Straights
Quantifying the change in performance in tires is important, but ensuring laptime is more sensitive to downforce rather than drag is equally as important. For this reason we developed an in-house lap simulation program using MATLAB, since I would not be able to generate the required graph from OptimumLap. Full credits go to Sepehr Makarian Abdolahi for writing this program to quantify design constraints for the aerodynamics and powertrain subsystems of MAC EV5.

![laptimeCl](/assets/images/laptimeCl.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. X Lap Time vs. Cl for Various L/D Ratios</i></font></p>

This graph alone doesn't provide us with the Cd*A constraint required to start pursuing aerodynamic design. We also need to consider the fact that since the vehicle is electric, the energy density will be much lower than an ICE and ensuring minimal aerodynamic drag is essential to a successful design.

We generate a list of the power consumed for increasing Cl at L/D=2.4. Accumulator size is 6.2kWh and we assume 2kWh of regen per lap, which is a safe assumption to make after a discussion with the powertrain subteam and their goal this season to implement regen.

| Cl(-) | Lap Time (s) | Power(kWh)
| 4.3 | 64.716 | 6.069
| 4.4 | 64.676 | 6.105
| 4.5 | 64.636 | 6.134
| 4.6 | 64.597 | 6.180

<p align = "center"><font size = "2" color="#00aaff"><i>Table X Excerpt taken from MATLAB output. Assumed efficiencies are as follows: controller=98%, accumulator=90%, drivetrain=87%, motors=95%. Total efficiency=72.90%. Estimated reference area (frontal area)=1.19m^2</i></font></p>

Now we have a set target of Cl=4.6 and Cd=1.92, or more useful ClA=5.47 and CdA=2.28 with A=1.19m^2. These are admittedly very high values, especially for a team pursuing aerodynamic devices for the first time. However, we at least now know our drag ceiling that we can't exceed out of fear of running out of energy before endurance ends. During design we will aim as high as we can go without exceeding the Cl and Cd threshold.

---
# Airfoil Selection
The design philosophy this year is to keep it simple. No DRS, 10-element wings, sidepods, or Newey-esc undertrays. I simply want to understand everything there is to know about airfoils and airfoil selection before we pursue further devices. After all, bolting on a part you don't understand is worse than not bolting on the part at all. The goal is to be competitive **and** learn, not either or.

Since we want to keep it simple, we decided not to pursue our own airfoil design and instead look at commonly used FSAE airfoils. Some Google searches later and we converged to the NACA 6412 and 4412, Selig S1223, and Eppler E423.

To simplify polar plot analysis, I made some preliminary assumptions based on the aerodynamic bounding boxes from FSAE Rules 2024 V1 T.7.7.2.

![T.7.7.2](/assets/images/T.7.7.2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. X T.7.7.2</i></font></p>

|  | Front Wing Primary Element | Front Wing Secondary Element | Rear Wing Primary Element | Rear Wing Secondary Element
| Chord (mm) | 400 | 300 | 500 | 400
| Re (-) | 352,856 | 264,642 | 441,069 | 352,856

<p align = "center"><font size = "2" color="#00aaff"><i>Table X Air speed=13.33mps and NCrit=9 since it is commonly used. More wing elements can be pursued if more downforce is required to hit the initial design target of Cl=4.6</i></font></p>

After making these assumptions, I began to look at the polar plots of these airfoils at on [airfoiltools.com](http://airfoiltools.com/). The objective(s) of each wing element are summarized below.

|  | Front Wing Elements | Rear Wing Primary Element | Rear Wing Secondary Element
| Objective(s) | High downforce at low AoA | High downforce | High downforce at maximum L/D
| Reasoning | Want to minimize upwash, since more upwash would make it harder to direct airflow to other areas of the car (e.g. radiator(s), rear wing, etc.) during the design phase | From T.7.7.2, the bounding box for the rear wing is larger than the front wing, meaning we can have a larger rear wing, meaning more downforce. We should capitalize on this rule and ensure the rear wing produces a lot of downforce to meet our design target, which is why we will pay less attention to the AoA and pay more attention to the raw, peak Cl. A more rearwards CoP will also mean a more stable, although understeery car at medium-to-high speeds | The secondary element will be more exposed to the free stream air as the main roll hoop falls away, so we want to still ensure high downforce without losing too much energy to drag
| Relevant Polar Plots | Cl vs. Alpha, Cl/Cd vs. Alpha | Cl vs. Alpha | Cl vs. Alpha, Cl/Cd vs. Alpha

<p align = "center"><font size = "2" color="#00aaff"><i>Table X Qualitative analysis to determine high level wing objectives and plots relevant to said objectives</i></font></p>

The Eppler E423 was a clear choice for the FWPE, as it had nearly as high a Cl as the highest Cl airfoil, the Selig S1223, while having the best L/D ratio at 5.0deg AoA, as can be seen in the 2 plots below.

| ![FWPE1](/assets/images/FWPE1.jpg) | ![FWPE2](/assets/images/FWPE2.jpg)

<p align = "center"><font size = "2" color="#00aaff"><i>Figs. X and X</i></font><font size = "2" color="purple"><i>S1223</i></font><font size = "2" color="#00aaff"><i> and </i></font><font size = "2" color="orange"><i>E423</i></font><font size = "2" color="#00aaff"><i> at Re=500,000 (you can't input specific Re into airfoiltools.com unfortunately, so I had to round to the closest available Re)</i></font></p>

This method of qualitative analysis was used to determine the profiles of the remaining elements, which can be seen in the summary table below along with their optimal free stream AoA ranges.

|  | Front Wing Primary Element | Front Wing Secondary Element | Rear Wing Primary Element | Rear Wing Secondary Element
| Profile | Eppler E423 | Selig S1223 | Selig S1223 | Eppler E423
| Chord (mm) | 400 | 300 | 500 | 400
| Optimal AoA Range for Cl/Cd at 13.33mps (deg) | -5.0 to 10 | -2.5 to 10 | 0 to 10 | 0 to 10

<p align = "center"><font size = "2" color="#00aaff"><i>Table Y Final airfoil profile selections for MAC EV5</i></font></p>

We finished off our airfoil analysis by running some quick numbers on a single-element and dual-element front wing, with the element profiles we just determined. Each profile was set to its maximum AoA given from Table Y.