---
layout: post
title:  "Preliminary Full Car Simulation"
date:   2023-11-11 02:52:00 -0400
categories: [formula SAE, CAD, 3D CFD]
---
This is a bit of a shorter design update, but an important one nonetheless. We are now starting to iterate on our designs based on the data from the following full car simulation.

---
# First 3D Full Car Simulation
This was a special milestone for myself and the team, as this was the first time a full car simulation had been done since the virtual FSAE competition in 2020.

![ansys1](/assets/images/ansys1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![ansys2](/assets/images/ansys2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![ansys3](/assets/images/ansys3.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![ansys4](/assets/images/ansys4.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 1, 2, 3, and 4 Pathline visualizations of EV5 full car simulations. Tire contact patch was modelled but we still need to do rotating tires before design close</i></font></p>

| Cl (-) | -1.3
| Cd (-) | 1.0

<p align = "center"><font size = "2" color="#00aaff"><i>Table 1 Cl and Cd for first full car simulation</i></font></p>

Going back to [Justification for Aerodynamics](https://pidduuu.github.io/jekyll/update/2023/10/01/Justification-for-Aerodynamics.html) the target was set at Cl=4.6 and Cd=1.92. There are optimizations that need to be made, but before that, some calculations need to be re-visited that will help us improve the performance of the front wing.

---
# Recalculated Dive Angle
From [Suspension Considerations for Aerodynamics](https://pidduuu.github.io/jekyll/update/2023/11/01/Suspension-Considerations-for-Aerodynamics.html) we calculated a pitch angle of approximately 3.5deg under braking from 120kph. A lot of assumptions were made in order to calculate that angle, including the downforce and drag values. That angle should be less now that we know where our Cl and Cd are currently at.

Firstly, are we actually going to hit 120kph at FSAE Michigan endurance? After quickly revisiting our MATLAB sim and finding the maximum speed around the track, no, we will hit around 90kph maximum. That's one variable that needs to change in our dive angle calculation.

Second, our downforce and drag values need to change. From the [lift equation](https://www.grc.nasa.gov/www/k-12/rocket/lifteq.html#:~:text=The%20lift%20equation%20states%20that,times%20the%20wing%20area%20A.&text=For%20given%20air%20conditions%2C%20shape,Cl%20to%20determine%20the%20lift.) and Cl=-1.3 we can calculate L=-431N. Similarly calculating drag we have D=331N. Reference area=0.82m^2 from full car simulation.

Now, recalculating our longitudinal deceleration we have 1.30g and a dive angle of approximately 2.72deg. Assuming 20% anti-dive based on an updated design target from the suspension subteam, that angle is further reduced to 2.18deg.

---
# Adjusting the Pitch, Roll, and Heave Surface
With the updated dive angle we can adjust our effective ground clearance in CAD to see how much larger we can make the front wing. Below we can see just how much more space we have gained.

![6mm](/assets/images/6mm.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 5 About 6mm gained</i></font></p>

So we can say we gained about a 1/4 of an inch to enlarge the front wing. That might not sound like a lot, but we have to keep in mind these are under the maximum operating conditions of the suspension.

**P.S.** the only reason we aren't curving our primary element for additional ground clearance is because we are restricted by our manufacturing method which can be viewed in [this video](https://www.youtube.com/watch?v=jsT561opKrU&t=321s&ab_channel=EasyCompositesLtd). We don't have time (or money) to currently make a hot wire cutter this year so we're waterjetting our foam profiles instead. We will eventually be able to pursue tapered geometry once we [build a 3 axis CNC hot wire foam cutter](https://howtomechatronics.com/projects/arduino-cnc-foam-cutting-machine/) which sounds like a summer of 2024 project.

---
# Areas to Improve the Design of the Wings, Adjusted Design Targets
On top of enlarging the front wing we should pursue a third element on the front wing using the higher bounding box inboard of the front tires, as can be seen in FSAE Rules 2024 T.7.7.2.

![largerFW](/assets/images/largerFW.png){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 6 Can add a third front wing element inside the bounding box highlighted in T.7.7.2</i></font></p>

We also still have a lot of room to enlarge the rear wing, even with the main roll hoop design this year being tilted 10deg rearwards. The MRH will most likely also be moving forwards by about 10-15mm in the next week which should give us even more space to enlarge the rear wing and potentially add a third element to keep the center of pressure as neutral as possible.

![RWroom](/assets/images/RWroom.png){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 7 Can move the rear wing downwards and add a third element. Beam wing is also possible however might not be effective without a diffuser</i></font></p>

Initially our target was a L/D=2.4 and Cl=4.6. That's looking less likely now that we have a better idea of what our wings are capable of. Our goal is to now achieve a L/D=1.6 or greater so we can actually plot our vehicle on the graph we generated in [Justification for Aerodynamics](https://pidduuu.github.io/jekyll/update/2023/10/01/Justification-for-Aerodynamics.html).

Design freeze is December 10th, preliminary CAD deadline is tomorrow. Lots to do, high targets to hit, but we can do it.