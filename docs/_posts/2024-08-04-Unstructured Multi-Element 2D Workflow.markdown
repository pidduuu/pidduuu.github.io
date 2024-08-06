---
layout: post
title:  "Unstructured Multi-Element 2D Workflow"
date:   2024-08-03 7:46:00 -0400
categories: jekyll update

---
MSES did not want to plot results for cases with large amounts of flow separation. For FSAE we need to be able to push into the flow separation regime to find the optimal multi-element wing setups.

Below is the new 2D CFD workflow MACFE will follow, and it uses unstructured meshes. Included in this article is the error between structured and unstructured meshes and [Selig's experimental data](https://m-selig.ae.illinois.edu/pd.html).

This one is less of a tutorial, more of a guide. 

---
# Geometry
Not using fluent meshing for this workflow since fluent currently does not support disconnected 2D surfaces (which is what this is).

![module](/assets/images/module.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 Non-fluent meshing</i></font></p>

Import geometry as .STEP file, change analysis type to 2D, and open in Spaceclaim. Fluid domain should be 15 chord lengths from the wing in all directions except the outlet. The outlet should be 30 chord lengths away from the airfoil. This is based on personal experimentation working well when lining up with the wind tunnel data.

Nearfield should be 5 chord lengths from wing. Extends to outlet. Farfield should be 10 chord lengths from wing. Extends to outlet.

**Note:** make sure to use the global chord length for multi-element setups. For this walkthrough I'm using single element since I need to compare it to wind tunnel data at the end.

![boi](/assets/images/boi.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 2 Domain sizing. Be sure to suppress the wing CAD for physics, since it is captured in the domain</i></font></p>

Create your named selections accordingly.

![nameds](/assets/images/nameds.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 3 Named selections</i></font></p>

---
# Mesh



