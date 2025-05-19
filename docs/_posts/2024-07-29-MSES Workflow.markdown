---
layout: post
title:  "MSES to SOLIDWORKS"
date:   2024-07-29 07:46:00 -0400
categories: [formula SAE, 2D CFD]
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

When calculating Reynolds number, use the chord length of the **scaled up** airfoil setup as your reference length. In order to do this, we will need to create a copy of "blade" and modify it so that we can import it into SOLIDWORKS.

Make a copy of "blade" and name it "solidworks."

![sw](/assets/images/sw.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 28 Coordinate file we will use for SOLIDWORKS</i></font></p>

Copy and paste everything from "solidworks" into [TXTformat](https://txtformat.com/).

![txtformat](/assets/images/txtformat.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 29 Using TXTformat to get coordinate file ready for importing into SOLIDWORKS</i></font></p>

Delete the first 2 rows, and use the "Trim" tool to trim the first 6 characters of each line.

![txt1](/assets/images/txt1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 30 Your TXTformat should look like this</i></font></p>

Scroll through and find the line which contains "999.0" and delete it.

![y](/assets/images/y.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 31 Before deleting 999.0</i></font></p>

![y1](/assets/images/y1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 32 After deleting 999.0</i></font></p>

Use the "Replace" tool to replace "     " (5 spaces) with ", " (1 comma, 1 space). Use "Replace" again to replace "    -" (4 spaces, 1 negative sign) with ", -" (1 comma, 1 space, 1 negative sign).

![txt2](/assets/images/txt2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 33 Your TXTformat should look like this</i></font></p>

Use the "Add" tool to add ", 0" (1 comma, 1 space, one 0) to the **end** of each line.

![txt3](/assets/images/txt3.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 34 Your TXTformat should look like this</i></font></p>

Make a new notepad file, name it "solidworks1" and copy and paste your formatted text into it. Save "solidworks1" to your project folder. Be sure to save it as a .txt file.

![sw1](/assets/images/sw1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 35 solidworks1 contents</i></font></p>

![sw1yeah](/assets/images/sw1yeah.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 36 solidworks1 directory</i></font></p>

Within "solidworks1" find the coordinate which differentiates your elements. This can be easily identified by a large change in the x-coordinate. Make an empty line there.

![xcoord](/assets/images/xcoord.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 37 Large jumps in x-coordinate indicate a new element. Add an empty line between the 2 coordinates</i></font></p>

Make a new .txt file in notepad called "element1" and copy and paste the coordinates of the first element. Save the file to your project directory. Repeat this step for every element you have.

![e12](/assets/images/e12.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 38 Coordinate files for elements 1 and 2. Repeat for as many elements as you have in your setup</i></font></p>

Open SOLIDWORKS and make a new part file called "wing." Navigate to Insert --> Curve --> Curve Through XYZ Points.

![xyz](/assets/images/xyz.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 39 Tool used to insert airfoil coordinates</i></font></p>

![curve1](/assets/images/curve1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 40 XYZ Curves menu</i></font></p>

Click "Browse..." and find your first element file. Make sure to set the search restriction to text files in your file explorer window.

Open "element1" then click "OK."

![insert](/assets/images/insert.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 41 Inserting first element</i></font></p>

![swe1](/assets/images/swe1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 42 Inserted first element into SOLIDWORKS</i></font></p>

Repeat for all remaining elements.

![swe2](/assets/images/swe2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 43 Full wing setup in SOLIDWORKS</i></font></p>

Make a new sketch on the front plane and draw a horizontal centerline at the origin. Convert the curves to sketches, and mirror them about the centerline. Make sure to uncheck "copy" before you mirror the sketches, otherwise you will get errors.

![mirror](/assets/images/mirror.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 44 Mirrored wing setup</i></font></p>

Hide the curves, and delete the centerline. Navigate to Tools --> Blocks --> Make and turn the entire sketch into a block.

![mkblck](/assets/images/mkblck.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 45 Make a block</i></font></p>

![blk](/assets/images/blk.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 46 Block</i></font></p>

Left click on the block in the SOLIDWORKS GUI, and you should see a menu pop up on the left. Change "Block Scale" to the desired scale.

For example, if I wanted the primary element's chord length to be 500mm, I will enter a scale factor of 500.

Exit the sketch.

Make a new sketch on the front plane, and convert the block to a sketch as shown below.

![s2](/assets/images/s2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 47 Converting block to a sketch</i></font></p>

Hide the old sketch (the one which contains the block in it). Define the chord length of element 1 (which MACFE aerodynamics people should already know how to do!) and draw a line from the first element's leading edge to the last element's trailing edge. Measure the distance of this line. This is the **global chord length** of the wing.

![globalchord](/assets/images/globalchord.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 48 Global chord length of wing</i></font></p>

Save the part file, and close it.

We are now going to use this global chord length to calculate the Reynolds number of our wing.

Go to [Reynolds number calculator](http://airfoiltools.com/calculator/reynoldsnumber) and calculate Reynolds number under SATP. Below is the Reynolds number of the wing setup I am using for this tutorial.

![reyn](/assets/images/reyn.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 49 Reynolds number of wing setup</i></font></p>

Input this into the "mses" file.

![reynin](/assets/images/reynin.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 50 REYNin</i></font></p>

Save and close the "mses" file.

**Section summary**
- Use "mset" to generate your mesh, and your "mdat" and "mses" files
- Calculate "MACHin" using inlet velocity
- Calculate "REYNin" using inlet velocity and global chord length, which you get from the scaled up wing in SOLIDWORKS

---
# makespecfile

Open "makespecfile."

![msf](/assets/images/msf.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 51 makespecfile</i></font></p>

Hit enter when prompted to enter an extension. Type "5" and hit enter. Enter the full setup AoA twice (for this tutorial, the full setup AoA is 0deg). Enter "0.1" for the "delta parameter value." The program should automatically close.

![msfvalues](/assets/images/msfvalues.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 52 Values to enter into makespecfile</i></font></p>

---
# mses

Open "mses."

![msesapp](/assets/images/msesapp.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 53 Open mses (the application, not the file!)</i></font></p>

When prompted to enter the number of iterations, enter 50. The program should run for 50 iterations. Close the program after it is done running.

![iter](/assets/images/iter.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 54 Run mses for 50 iterations</i></font></p>

---
# mpolar

Open "mpolar." The program should run then close.

![mpolar](/assets/images/mpolar.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 55 mpolar</i></font></p>

---
# mplot

Open "mplot."











