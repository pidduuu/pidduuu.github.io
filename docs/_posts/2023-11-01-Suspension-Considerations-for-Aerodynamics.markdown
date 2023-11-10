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
In my very first year of university, I never thought more of the ride height a race car was set at. 1 inch off the ground? Go for it. 1mm off the ground? Looks cool!

What I failed to realize at the time was how important suspension behaviours are for aerodynamic device placement, especially for ground effect devices such as the front wing and undertray. This importance is amplified due to FSAE Rules 2024 V.1.4.1.

![V.1.4.1](/assets/images/V.1.4.1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 V.1.4.1</i></font></p>

We are not a Formula 1 team. We do not have a skid block, and we can't make sparks every other corner out of fear of being disqualified.

Your ride height is never your ground clearance in a dynamic state. There will always be pitch, roll, and heave to bring the chassis and front wing ever so slightly closer to the ground. This is very well illustrated from [Aero Placement and Mounting](https://www.designjudges.com/articles/aero-placement-and-mounting).

![aeroPlacement](/assets/images/aeroPlacement.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 Pitch, roll, and heave</i></font></p>

From here I began finding the maximum pitch, roll, and heave values for EV5. After a discussion with the suspension subteam, we will not exceed 2deg of roll due to the addition of an anti-roll bar in both the front and rear. One value down.

Heave is another easy one. Worst case scenario we assume maximum heave allowable by the suspension, which for our springs is 57mm/2=28.5mm to allow at least 1 inch of wheel travel in rebound and compression to satisfy FSAE Rules 2024 V.3.1.1.

![V.3.1.1](/assets/images/travel.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 V.3.1.1</i></font></p>

Dive and squat angles took a little while to calculate, though. 