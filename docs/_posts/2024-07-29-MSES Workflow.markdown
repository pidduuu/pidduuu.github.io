---
layout: post
title:  "MSES to SOLIDWORKS"
date:   2024-07-29 07:46:00 -0400
categories: jekyll update
---
2D Panel-based methods are far superior to traditional commercial CFD solvers when it comes to numerical accuracy and solution speed. XFOIL and MSES have the added benefit of not having to worry about correct fluid domain sizing and grid refinement. What one student could do in 30 minutes with a commercial solver, the other can do in 3. [Mark](https://aeroastro.mit.edu/people/mark-drela/), I thank you for your genius.

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

We are now in the .Posi menu, which can be seen in Figure 3. Type "R" and hit enter to re-size your GUI if it does not sit nicely on your screen.

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
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 10 2 elements on the GUI</i></font></p>

Now, type "M" to move it to your desired coordinate. Type in your X and Y coordinates as shown below, and hit enter.

![coords](/assets/images/coords.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 11 "M" command</i></font></p>

![coordsGUI](/assets/images/coordsGUI.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<p align = "center"><font size = "2" color="#00aaff"><i>Fig. 12 Secondary element moved to desired coordinates</i></font></p>

I'm going to change the AoA of the second element to +30deg using "A."



