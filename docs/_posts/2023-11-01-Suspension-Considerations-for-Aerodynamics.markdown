---
layout: post
title:  "Suspension Considerations for Aerodynamics"
date:   2023-11-01 02:52:00 -0400
categories: jekyll update
---
I'd like to preface this design update with a huge thank you to everyone who works on [designjudges.com](https://www.designjudges.com/). This collection of articles has been invaluable to myself and everyone at MAC Formula Electric over the past year and a half. It has opened our eyes to more things we need to consider in our subsystem designs.

Also, special thank you to Noah Dropkin for writing [Aero Placement and Mounting](https://www.designjudges.com/articles/aero-placement-and-mounting). The following design update owes its contents to this article.

To anyone on MAC Formula Electric who may be reading this, **read a relevant article on design judges before starting a new design!**

---
# Pitch, Roll, and Heave
In my first year of university, I never thought more of the ride height a race car was set at. 1 inch off the ground? Go for it. 1mm off the ground? Looks cool!

What I failed to realize at the time was how important suspension behaviours are for aerodynamic device placement, especially for ground effect devices such as the front wing and undertray. This importance is amplified due to FSAE Rules 2024 V.1.4.1.

![V.1.4.1](/assets/images/V.1.4.1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 V.1.4.1</i></font></p>

We are not a Formula 1 team. We do not have a skid block, and we can't make sparks every other corner out of fear of being disqualified.

Your ride height is never your ground clearance in a dynamic state. There will always be pitch, roll, and heave to bring the chassis and front wing ever so slightly closer to the ground. This is very well illustrated from [Aero Placement and Mounting](https://www.designjudges.com/articles/aero-placement-and-mounting).

![aeroPlacement](/assets/images/aeroPlacement.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 2 Pitch, roll, and heave</i></font></p>

From here I began finding the maximum pitch, roll, and heave values for EV5. After a discussion with the suspension subteam, we will not exceed 2deg of roll due to the addition of an anti-roll bar in both the front and rear. One value down.

Heave is another easy one. Worst case scenario we assume maximum heave allowable by the suspension, which for our springs is 57mm/2=28.5mm to allow at least 1 inch of wheel travel in rebound and compression to satisfy FSAE Rules 2024 V.3.1.1.

![V.3.1.1](/assets/images/travel.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 3 V.3.1.1</i></font></p>

Dive and squat angles took a little while to calculate, though. Firstly, we had to get a realistic value for our mu for our tires. The TTC had data for our slicks which is great, however under braking from 33.33mps we were pulling about 2.1G longitudinally (assuming no change in mu due to tire load sensitivity). Using intuition this was not correct.

After some digging through the TTC Round 9 documentation (as well as previous tire data analysis experiences) I realized this was due to a correction factor of 0.66 that had to be multiplied to the raw data to achieve realistic results for mu. After re-calculating we were acheiving 1.7G longitduinally with aero and 1.05G longitudinally without aero which seemed much more realistic. 1500N of downforce and 500N of drag were assumed at 33.33mps based on other teams claimed full car L/D ratios.

From here I was able to calculate the dive angle through basic kinematics.

![FBD](/assets/images/FBD.JPEG)
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 4 FBD of EV5</i></font></p>

![FBDcalcs](/assets/images/FBDcalcs.JPEG){:style="display:block; margin-left:auto; margin-right:auto"}

![excelCalculator](/assets/images/excelCalculator.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 5 and 6 Raw calculations (top) which I then transferred into an excel calculator (bottom)</i></font></p>

For the time being we will assume squat angle of 3.5deg as well to save time. This should be calculated as well though.

Now that we have the pitch, roll, and heave values, we can create a representative ground clearance surface in Solidworks. After modelling a preliminary full car CAD with the front and rear wings placed in their bounding boxes from FSAE Rules 2024 V1 T.7.7.2, I immediately noticed a problem.

![aeroBB](/assets/images/aeroBB.png){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 7 Bounding boxes from T.7.7.2</i></font></p>

![FWground](/assets/images/FWground.png){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 8 The front wing fancies the ground</i></font></p>

<<<<<<< HEAD
This prompted us to ask about the feasability of anti-dive geometry for EV5. After a brief discussion with the suspension subteam, 1.5deg of dive angle was achievable. Adjusting the effective ground clearance surface in the CAD to reflect this yielded encouraging results.
=======
This prompted us to ask about the feasability of anti-dive geometry for EV5. After a breif discussion with the suspension subteam, 1.5deg of dive angle was deemed achievable. Adjusting the effective ground clearance surface in the CAD to reflect this yielded encouraging results.
>>>>>>> b6a5dd1e6d272562dadd583c5654378321dd1f0c

![FWground2](/assets/images/FWground2.png){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 9 No interference with the ground with 1.5deg of dive, 2deg of roll, and 28.5mm of heave</i></font></p>

---
# Full Car Model for Ansys
Once I was satisfied with the ground clearance I began making a simplified full car model for external analysis in Ansys. At the time of creating the CAD model there was no suspension CAD done, so we just modelled some simple arms in place of it.

At the time of making the model the suspension subteam was consdiering a double-wishbone pullrod system for the front, and double-wishbone pushrod system for the rear, so we modelled something to mimic that until they finalized their geometry and created a CAD model.