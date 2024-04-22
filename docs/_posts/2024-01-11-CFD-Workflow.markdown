---
layout: post
title:  "CFD Workflow"
date:   2024-04-20 07:42:00 -0400
categories: jekyll update
---
I want to get more into the specific CFD workflow the team and I followed this season. The following serves as a blend of business-casual documentation, and a tutorial for future members of the team.

---
# Geometry Cleanup in Ansys SpaceClaim
Taking the simplified CAD model from [Suspension Considerations for Aerodynamics](https://pidduuu.github.io/jekyll/update/2023/11/01/Suspension-Considerations-for-Aerodynamics.html) we export a STEP AP214 file and import it into Ansys Fluent. From here, we use various tools to clean up the geometry and preapre it for meshing.

I prefer to use Fluid Flow (Fluent with Fluent Meshing) since it has a very nice integrated workflow for both pre and post-processing.

First order of business is to use SpaceClaim. I haven't had good experiences with the stability of Discovery, and DesignModeler is very old at this point. SpaceClaim is relatively more stable from my experience, and after using it 30-40 times over it becomes intuitive.

![useSpaceclaim](/assets/images/useSpaceclaim.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 Use SpaceClaim, it causes the least headaches (as long as you know how to use it)</i></font></p>

SpaceClaim has a number of great tools to repair geometry. I personally like to run split edgews and extra edges, which usually allows Ansys to find things it doesn't like. Be sure to use these before performing any meshing to ensure you have an easy time meshing everything. 

![repairTools](/assets/images/repairTools.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 2 My preferred SpaceClaim repair tools. You may need to return to this stage and run more tools if you have trouble with meshing down the line</i></font></p>

After running repairs I model tire contact patches. Right now these are crude rectangles drawn 2mm underneath each wheel, and extruded upwards. We only need to sketch 2 rectangles on the right-side wheels since we apply the symmetry condition when solving.

![sketchRectangle](/assets/images/sketchRectangle.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![pullRectangle](/assets/images/pullRectangle.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 3 and 4 Sketching and pulling crude rectangles to model tire contact patches. This stage of the process needs optimizing (i.e. is there a better way to do this?)</i></font></p>

Next create a symmetry plane, easy enough to do. After that, model an enclosure using the enclosure tool. Decent dimensions are given below however "decent" is not an engineering term. We need to research [blockage ratios](https://www.youtube.com/watch?v=gope2XlBwA4&ab_channel=AirShaper) for next season and understand how to properly model a virtual tunnel to avoid [artificial acceleration](https://en.wikipedia.org/wiki/Continuity_equation#Fluid_dynamics) of the fluid.

![carTunnel](/assets/images/carTunnel.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 5 EV5 tunnel sizing. Needs to be researched and improved</i></font></p>

Ansys should have processed the enclosure nicely if you repaired your geometry well enough. If it didn't work, undo your enclosure and go back to the repair tab and use more repair tools. If that doesn't work, go back to SW since something is most likely fundamentally messy about your model.

Hide the enclosure and ground plane and make a rectangular sketch on the symmetry plane which roughly encompasses the model. No dimensions needed for this part. Pull the rectangle out to create your boi-nearfield which will be used for mesh refinement. Create a copy of your nearfield, pull out the whole cube by an additional 500mm and name it boi-farfield. You should have 2 rectangular prisms now, the nearfield and the farfield.

![tunnel](/assets/images/tunnel.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 6 Everything we have so far. Make your BOIs transparent to check if everything looks good inside of them</i></font></p>

Now comes some optimization. We cut the tunnel at the symmetry and ground planes to reduce compute and model [ground effect](https://en.wikipedia.org/wiki/Ground_effect_(cars)#:~:text=In%20racing%20cars%2C%20a%20designer%27s,the%20name%20%22ground%20effect%22.), respectively. Use the split body tool for this.

![cutTunnel](/assets/images/cutTunnel.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 7 Final tunnel</i></font></p>

Hide the planes, CAD, the 2 solid bodies for the contact patches we modelled, and suppress both the CAD and contact patches for physics since the enclosure has already captured a negative of the entire model.

![suppressPhysics](/assets/images/suppressPhysics.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 8 Right click to suppress physics</i></font></p>

Go to groups and start making your named selections. Below are mine which I recommend following, since I've broken it down to make meshing easier later on. **Double check** the surfaces you are highlighting, as it is very easy to add the same surface to 2 unique NS, or to completely miss out on a surface altogether. This step requires practice and extreme patience. Get this right.

![nS](/assets/images/nS.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 9 Named selections</i></font></p>

Ctrl-S, close SpaceClaim and you're good to start meshing.

---
# Meshing and Mesh Sensitivity
Import your geometry and add local sizing. This is the stage where we're going to make a refined mesh for each part of the car.

After having to spend 2 weeks learning how to setup a host server for our new Ansys sponsorship, and writing a new installation tutorial for the team (since they didn't give us one), I wasn't left with much time to document the mesh sensitivity studies I performed. For now, just take my word on it that for our current models a boi-nearfield of 16mm and farfield of 32mm achieves [grid independence](https://www.cfd-online.com/Forums/fluent/40902-what-meant-grid-independence-study.html) to within 5% error of 8mm and 16mm.

As for the surface mesh I found that I could just apply a curvature constraint to every part of the car (i.e. all "car" related named selections from earlier) and this was sufficient in outputting a reasonable answer relative to other FSAE teams running our specific aero configuration. Further refinements can be made and should be explored.

![nearfieldSizing](/assets/images/nearfieldSizing.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![farfieldSizing](/assets/images/farfieldSizing.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![curvatureSizing](/assets/images/curvatureSizing.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 10, 11, and 12 Local sizing applied to EV5</i></font></p>

Generate a surface mesh of min=0.5mm and max=256mm. One thing to note is I had to change cells per gap to 0.5 since the trailing edges of the airfoils were too thin for Ansys to fit a cell inside. If you chamfer the airfoils by about 2mm instead of 1mm you should be able to fit a full cell. Comparing solutions between these 2 different modelling choices should be studied.

Insert an improve surface mesh task to bring face skewness to 0.7 or below. I tried running a solution at 0.85 and it would've taken 5 days to solve. At 0.7 it's 24 hours for 1000 iterations.

Below is how I described my geometry. Your enclosure should be defined as a fluid.

![describeGeometry](/assets/images/describeGeometry.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![boundaryDefinitions](/assets/images/boundaryDefinitions.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 13 and 14 Describing geometry and setting boundary definitions</i></font></p>

For boundary layer meshing we've been using the [last ratio scheme](https://help.spaceclaim.com/dsm/6.0/en/Discovery/user_manual/meshing/mesh/t_mesh_choosing_layer_growth_method.html#:~:text=Last%20Aspect%20Ratio%20also%20calculates,Ratio%20(base%2Fheight).) since it was [recommended by Ansys](https://www.youtube.com/watch?v=ikecsOd09lI&list=PLtt6-ZgUFmMIshN9C0Moyx93VpunjKnUC&index=3&ab_channel=AnsysLearning). Design freeze was fast approaching and this was something we didn't have time to research and further justify. Boundary layer modelling needs to be significantly researched for next year for [obvious reasons](https://www.grc.nasa.gov/www/k-12/BGP/boundlay.html#:~:text=Engineers%20call%20this%20layer%20the,occurs%20in%20high%20speed%20flight.) (see: BL separation and wing stall). 

Volume mesh min=1mm and max=512mm (increased surface mesh by factor of 2) as per Ansys recommendation. Through experimentation this ensured stability while allowing a solvable solution in an expected amount of time (around 1-2 days) however, like many other things, needs to be understood and explored further.

We improved cell quality to 0.15 after the initial volume mesh and had to call it there. Time to solve.

---
# Solver Setup and Solution
Our solver settings have been pretty standard and we've left it that way for our first year of doing aero. Pressure-based, steady solver running k-omega SST with no relaxation for the turbulence model itself, and higher order terms. Second order upwind scheme for momentum and turbulent kinetic energy. Very basic, recommended by Ansys, needs to be understood further.

We've been running our inlet velocity at 15m/s since [that's the average FSAE cornering speed](https://pidduuu.github.io/jekyll/update/2023/10/01/Justification-for-Aerodynamics.html). Pressure-based outlet with gauge pressure set to 0. Same turbulent intensities and viscosities for both inlet and outlet.

The boundary walls get a little interesting. Translating ground at 15m/s to ensure ground effect plays a part for the front wing/underbody in our solution, and the wheels are rotating as well as can be seen through the setup below. Angular velocity determined through omega=v/r where v=15m/s and r=radius of our tires. Tunnel walls have a zero specific shear to avoid BL growth which could affect flow around the body.

![movingGround](/assets/images/movingGround.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![rearWheelMoving](/assets/images/rearWheelMoving.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![frontWheelMoving](/assets/images/frontWheelMoving.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 15, 16, and 17 Moving boundary walls, namely ground and wheels. Ground is moving in -Z direction since nose faces +Z. Note how the coordinates of the wheels are different for front and rear, this is an important step. Another important thing to note is only the wheel is rotating, not the tire contact patch. This is why they have separate named selections</i></font></p>

After this, I set my reference values. A_ref=0.46 since full car is 0.92 (remember we are using symmetry condition). This means the outputted Cl and Cd are that of the full car. Length=3m since this is the length of the car, and v=15m/s. Everything else is untouched.

4 report definitions are setup: Cl, Cd, lift, and drag. I also click the option to create a report file for each so the data can be brought into Excel for analysis.

![clReportDefinition](/assets/images/clReportDefinition.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 18 Cl report definition</i></font></p>

I then run the solution for 1000 iterations with an automatic time step. The current assumption is that 1000 iterations is sufficient in providing an accurate enough solution, and this is all we were able to do given the design freeze time constraints this year. In future years, 3000+ iterations should be done to guarantee convergence.

The resulting plots can be seen below.

![scaledResiduals](/assets/images/scaledResiduals.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![clPlot](/assets/images/clPlot.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

![cdPlot](/assets/images/cdPlot.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 19, 20, 21 Resulting plots after 1000 iterations</i></font></p>

---
# Post-Processing and Data Analysis
The first order of business is to take some very cool and very useful pictures, because that's the first thing any hyper-stimulated 20 y/o Adrian Newey wanna-be does at 3:00AM after running a simulation. Also great for marketing!

| ![isoVelocity](/assets/images/isoVelocity.jpg) | ![isoPressure](/assets/images/isoPressure.jpg)
| ![frontVelocity](/assets/images/frontVelocity.jpg) | ![frontPressure](/assets/images/frontPressure.jpg)
| ![coolVelocity](/assets/images/coolVelocity.jpg) | ![topPressure](/assets/images/topPressure.jpg)
| ![hahaPressure](/assets/images/hahaPressure.jpg) | ![rearPressure](/assets/images/rearPressure.jpg)

<p align = "center"><font size = "2" color="#00aaff"><i>Figs. 22, 23, 24, 25, 26, 27, 28, and 29 AERODYNAMICS WOOOOOOOOO</i></font></p>

Jokes aside, I just don't know how to extract meaningful results out of velocity pathline images yet. Static pressure plots are more useful to us for design iterations, since we can use them to conceptualize parts that increase/decrease static pressure at various locations. For example, we should look into extending our front wing endplates closer to the ground [(suspension allowing)](https://pidduuu.github.io/jekyll/update/2023/11/01/Suspension-Considerations-for-Aerodynamics.html) to better seal the outboard portions of the wing, to the benefit of downforce.

The data for Cl, Cd, lift, and drag are outputted to OUT files in this directory.

![outputFiles](/assets/images/outputFiles.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 30 Outputted files</i></font></p>

Import this data into Excel so we can obtain the average. Use the space delimiter with the **legacy wizard** to get nice data into your workbook. If you don't use the legacy wizard the data will all appear in one column. Or maybe it's just a skill issue on my part.

![excelSetup](/assets/images/excelSetup.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 31 Importing data into Excel, using AVERAGE function to take average. Multiply lift and drag forces by 2 to get full car forces. Be sure to start taking your average once the forces become more stable, don't take them straight from line 1</i></font></p>

This is the extent of our data analysis, and now we're at the end of the workflow. We primarily use the static pressure images to generate new design concepts, however learning how to use this data to continue to iterate on the design is something we need to learn how to do.

If this post proves anything, it's that we've come a long way, but we still have a long way to go.

It's 3:35AM, I'm done exams, and the Nordschleife DLC is waiting for me on ACC. Night.