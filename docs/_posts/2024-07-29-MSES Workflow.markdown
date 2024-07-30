---
layout: post
title:  "MSES to SOLIDWORKS"
date:   2024-07-29 07:46:00 -0400
categories: jekyll update
---
2D panel-based methods are far superior to traditional commercial CFD solvers when it comes to numerical accuracy and solution speed. XFOIL and MSES have the added benefit of not having to worry about correct fluid domain sizing and grid refinement. What one student could do in 30 minutes with a commercial solver, the other can do in 3. [Mark](https://aeroastro.mit.edu/people/mark-drela/), I thank you for your genius.

The following serves as an in-depth tutorial for MAC Formula Electric. I hope this makes it clear how to make effective and efficient use of the software.

---
# airset
Go to [airfoiltools.com](http://airfoiltools.com/) and find your profile(s) of preference. Download the "Selig format dat file" for each profile you will be using. For this tutorial, I will be creating an arbitrary dual-element setup using 2 S1223 profiles.

![s1223](/assets/images/s1223.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 1 Selig S1223</i></font></p>

Save the file in the same folder as your MSES installation.

![seligdatfile](/assets/images/seligdatfile.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 2 Storing seligdatfile in the directory with all MSES programs</i></font></p>

Open airset.

![airset](/assets/images/airset.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 3 airset</i></font></p>

![airset1](/assets/images/airset1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 4 airset menu</i></font></p>

Type "Adde" and hit enter to add the first profile to your setup. Type in the name of the file. You should see a GUI pop up with your airfoil in unit length.

![adde](/assets/images/adde.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 5 adde</i></font></p>

![gui](/assets/images/gui.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 6 GUI of airfoil</i></font></p>

We are now in the .POSI menu, which can be seen in Figure 3. Type "R" and hit enter to re-size your GUI if it does not sit nicely on your screen.

![gui1](/assets/images/gui1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 7 Re-sized GUI</i></font></p>

There are many commands to enter now, however practically you don't really want to move the first element away from the origin. Most of the time, you would only want to change the angle of the first element.

So, type "A" and hit enter. Positive values are CW, negative values are CCW. Hit enter.

![angle10](/assets/images/angle10.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 8 AoA of +10deg</i></font></p>

Once you are happy with your primary element's AoA, hit enter. You may now enter the filename of the second element. The GUI will now display 2 elements.

![element2](/assets/images/element2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 9 Second element</i></font></p>

![2elements](/assets/images/2elements.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 10 2 elements in the GUI</i></font></p>

Now, type "M" to move it to your desired coordinate. Type in your X and Y coordinates as shown below, and hit enter.

![coords](/assets/images/coords.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 11 "M" command</i></font></p>

![coordsGUI](/assets/images/coordsGUI.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 12 Secondary element moved to desired coordinates</i></font></p>

I'm going to change the AoA of the second element to +30deg using "A."

![AoA2](/assets/images/AoA2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 13 AoA to 30deg</i></font></p>

![AoA3](/assets/images/AoA3.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 14 AoA updated in GUI</i></font></p>

If you want to scale it down, type "S" and type in your scaling about the element's point. I highly recommend uniform scaling so you don't morph the established profile into some other shape you don't want.

![scale](/assets/images/scale.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 15 Scaling second element down to desired size</i></font></p>

Once you are happy with your second element, you can hit enter again and type in the filename of another profile to continue adding airfoils to your setup.

Once you are done setting up your airfoils, hit enter twice to get back to the airset menu. Note, that in any menu, you can type "?" to view a list of commands.

Once back in airset, type "Save" to save your airfoil setup. Enter "blade" as the filename. If it is anything other than blade it will not work, and at the current point in time I'm not sure why.

Just type "blade" and hit enter.

![blade](/assets/images/blade.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 16 Always make the filename "blade"</i></font></p>

You can now close the airset terminal.

**Section summary**
- Download the "Selig format dat file" for your profile(s) from airfoiltools.com
- Use airset and it's list of commands to add and modify your airfoil geometry as you see fit
- When saving your airfoil setup, name it "blade"

---
# mset

Open mset.

![mset](/assets/images/mset.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 17 Open mset</i></font></p>

You will be greeted with a menu of 16 commands. Each command is issued with the associated number.

![cmds](/assets/images/cmds.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 18 mset commands</i></font></p>

Command 1 is used to specify an AoA of the **entire setup**. Considering the AoA of each element was already setup using airset, it's quite rare you want to change the full setup AoA (but there is a chance you might want to, for some reason).

For now, I'm going to use the AoAs specified in airset.

Type "1" and hit enter. Enter your desired setup AoA, and hit enter. A GUI should pop up which looks like the one below.

![setupaoa](/assets/images/setupaoa.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 19 Entering full setup AoA</i></font></p>

![streamlines](/assets/images/streamlines.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 20 Streamlines</i></font></p>

Type "2" to generate the grid (aka mesh). It will ask you if you are okay with the current mesh shown in the GUI. The generated meshes are usually very good, however if you run into problems/unrealistic values in your solution later on, it would be a good idea to re-visit this step.

Hit enter for each element after you have checked the grid.

![grid](/assets/images/grid.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 21 Grid generation</i></font></p>

![e1grid](/assets/images/e1grid.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 22 GUI showing the generated grid. The generated grid is usually good enough for a very accurate solution</i></font></p>

Type "3" and hit enter to smooth the grid.

![gridsmooth](/assets/images/gridsmooth.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 23 Smoothing the grid to be easily computed during the solution</i></font></p>

Type "4" and hit enter to generate the "mdat" file. This is the file which stores your final solution.

Type "14" and hit enter to generate the "mses" file. This file contains boundary conditions for your simulation. The ones which concern us are the Mach number and Reynolds number.

Find "mses" in your project folder (the file, not the program) and open it with notepad.

![mses](/assets/images/mses.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 24 Generated mses file</i></font></p>

You should see the following in notepad. We are mainly concerned with changing our "MACHin" and "REYNin" variables to what we want.

![msesvar](/assets/images/msesvar.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 25 MACHin and REYNin</i></font></p>

You might be wondering why it takes in the Mach number to begin with. When it comes to aircraft, the air flowing over the low pressure side of an airfoil could well exceed Mach 1, despite the incoming freestream air being below Mach 1. High Mach numbers introduce compressibility effects, shock waves, and drastic changes in the fluid properties. Reynold's number alone won't capture these phenomenon, which is why the "mses" file asks for it.

For FSAE, the Mach number is entirely irrelevant to the numerical solution, however we are still going to calculate it and input it into our "mses" file for our own knowledge.

From [Justification for Aerodynamics](https://pidduuu.github.io/jekyll/update/2023/10/01/Justification-for-Aerodynamics.html) we already determined the average FSAE cornering speed is 13.33mps. I'm going to use 15mps since it is a nicer number. Inputting this into a [Mach number calculator](https://www.omnicalculator.com/physics/mach-number) with [SATP](https://www.techtarget.com/whatis/definition/standard-temperature-and-pressure-STP#:~:text=Like%20STP%20and%20NTP%2C%20standard,%3A%201%20atm%20(101.325%20kPa)) taken into account for air temperature, we get Mach=0.04334. Input this value into "mses."

![machnum](/assets/images/machnum.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 26 Mach number calculation</i></font></p>

![msesmach](/assets/images/msesmach.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 27 Inputting Mach number into "mses" file</i></font></p>

bleh :P















