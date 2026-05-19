---
title: "Halbach array augmented rail gun."
date: 2020-07-15
catagories:
  - railgun
tags:
  - electromagnetics
  - railgun
---

## Overview 
The Halbach Array Augmented Railgun or HAAR was meant to be my final prototype design; 
it was supposed to solve the two major problems of the common railgun: degradation of the rails due to electrical arcing, 
and the need for exorbitant amounts of current.  In the past I have called my solution to the arcing problem a solid armature design, 
but that does not fully explain it, I Find "integrated armature"(IA) to be a more fitting name 
(Integrated rail armature was my first choice, but the acronym for that is IRA). 
In an IA railgun, instead of the armature sliding between the rails, the "rails" 
are attached directly to the armature so when the armature moves the rails are pulled right along with it and since the rails are 
attached directly to the armature (technically making them an armature themselves) they do not move relative to the armature meaning 
no contact resistance and most importantly no arcing or degradation of the rails. In order for an IA design to work the rails need 
to be flexible so they can be bent to allow the armature motion through out the entire barrel. For the HAAR I used 10 strands of 
28 AWG wire, about 1 meter long, that I twisted together for each rail. I then soldered each of the two rails to each end of a 4 in. 
segment of 14 AWG wire, which would act as my armature. 

In order to reduce the amount of current I would need to power the HAAR I used a cylindrical nested Halbach array constructed from 24 1/2 in. N52, neodymium magnets. I had calculated the field at the center of the Halbach array to be above 2 T, but I was incorrect and in actuality it came out to only around .6 T - .1 T causing the design to not produce the forces I had originally expected. 
For the power supply of the HAAR I used a 450 Volt 15000 uF aluminium electrolytic capacitor.
for a constant current and magnetic field the equation for the force on an armature of a rail gun is given by, 

F = IBL 
(look at the railguns home page for a more in depth explanation)

but the HAAR's power source does not deliver a constant current so the equation for the current from a capacitor, at a given time, is given by

(V: initial voltage, R: resistance, C: capacitance in Farads and t: time)
I = (V/R) * e^(-t/RC)

meaning the force on the armature, given a constant magnetic field, with respect to time, is given by
F = ((V/R) * e^(-t/RC)) BL

and by simply dividing both sides by the mass of the armature and projectile we can get the armatures acceleration.
a = (((V/R) * e^(-t/RC)) BL) / m

Then by integrating with respect to time we should get an equation for the velocity of the armature and projectile. remember to use a definite integral with the minimum at 0 and the maximum at some value of t( I can't seem to find a way to type the integral symbol so I did all the integration behind the scenes.)

dx/dt =  (VBL/Rm) * ((RC) -(RC*e^-t/RC))

I found the best way to make sense of this equation was to plug all of my values in and graph the velocity across the y axis and t across the x axis by doing this you can easily see that the velocity will reach a maximum at a certain value of t.
given a field strength of 2 T an armature length of 3.5 in, a mass of .01 kg, a resistance of .03, an initial voltage of 440 and a capacitance of .015 Farads, I was able to calculate a maximum speed of around 117 m/s at time .006 s meaning we need a barrel length of aprox. .35 meters or around 14 in.
Before spending several hundred dollars on magnets and other materials for a 14 in. long barrel I figured I should check my numbers with a practical experiment, so I built a small and large demonstrator.   

## Build and Tests
Below you will see a proof of concept for the HAAR design that used only a single layer cylindrical Halbach array. it is made of two 1/2 in. 3D printed slices , that were glued together, and an inner barrel piece. My main fear with the HAAR design was that the magnetic fields of the individual Halbach arrays would cancel out because I was putting same pole to same pole, but the armature ran smoothly from one segment to the next meaning I did not have to worry about the fields canceling out.

<img src="/assets/images/Halbach11.jpg" width="27%">
<img src="/assets/images/Halbach12.jpg" width="27%">
<img src="/assets/images/halbach13.jpg" width="27%">

The final test barrel assembly can be seen in the pictures below. As you can see the Halbach array is held together by a 3D printed frame which also acts as the barrel for the armature and projectile. the large slots on the sides are where the rails would travel and the holes around the perimeter are to bolt the segments of the barrel together. The numbers I had calculated for the field inside the center of the Halbach array were incorrect; as mentioned before instead of 2 T I had an average field strength across the armature of .12 T and a field in the center of around .6 T. I was able to find the actual field strength of the array by testing the larger test assembly, recording the projectile velocity and then working back wards from there using the equations shown earlier. although the Halbach array augmentation did not work, as well as I had hoped, the Integrated armature worked perfectly.    

tests at 100 volts yielded an average velocity of 8 m/s

tests at 200 volts yielded an average velocity of 16 m/s

<img src="/assets/images/Halbach21.jpg" width="50%">

### 210 Volt test video
<iframe width="560" height="315"
src="https://www.youtube.com/embed/J9kzttJ7Sb0"
frameborder="0" allowfullscreen></iframe> 

### 110 Volt test video
<iframe width="560" height="315"
src="https://www.youtube.com/embed/7sNkqAYGIEo"
frameborder="0" allowfullscreen></iframe> 

In conclusion, the IA worked perfectly and the Halbach array worked, but unfortunately not as well as I had hoped. This design was definitely a step in the right direction, but in order to get the results I want I am going to need a stronger augmentation field.

Below is a simulation of the magnetic field strength of the double Halbach array. I was only able to figure out how to make these simulations after I had already built the prototype, but this now gives me greater incite into the reasons why it did not perform the way I had thought it would. I think the biggest problem is the gaps in the field where the the magnetic field is 2 to 4 times weaker than at the center.


