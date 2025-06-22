---
layout: post
title:  "EV6 Radiator Selection and Placement"
date:   2026-01-15 7:46:00 -0400
categories: [Formula SAE, 3D CFD, Aerodynamics, Cooling, Software Development]

---
The method to size the EV5 radiator was based on conservative assumptions and hand-calculations. While this was a decent way to justify the radiator size given we did not have an empirical overall HTC, the design and analysis process could benefit from less assumptions as well as an analytical way to calculate the overall HTC.

The method chosen for this year once again revolves around fundamental heat transfer calculations, however they are combined with the eNTU method to create a robust workflow to solve for hot fluid outlet temperatures. Assumptions are still required for some radiator dimensions (since we can't measure all of them in-person), however after seeing the outputs in MATLAB it can be said that this method provides a reasonable way for modelling radiators. An overall HTC is also obtained through the MATLAB script, which is then used for the eNTU temperature calculations.

---
# Program Structure


---
# Final Radiator and Fan Selection

---
# References
