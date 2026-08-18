---
title: "Hall Effect Coil Control"
date: 2026-08-16
categories: HET
tags:
  - Power Electronics
  - HET
---

## Overview

The hall effect thruster that my club has been working on needs a way to supply its field producing electromagnets. 
I set about leading in designing and building the necessary circuitry to power the coils and control the coils.
The propulsion team gave us their requirements of 1-2 Amps and 1-5 Volts. Since our input power will be at 48 Volts a buck converter topology was selected. 
The TPS54360BQDDAQ1 was chosen as the central IC for the circuit. The TPS54360BQDDAQ1 generates its own drive signal internally. 
to control the voltage output of the buck converter initially I wanted to simply input an analog signal from our controller, 
but the controller would have had to have output a very specific voltage to the buck converter ICs FB pin. 
Instead a voltage divider design that uses a digital potentiometer and a potentiometer in place of static resistors was decided on.
The FB pin wants a specific voltage of around 0.811V, If it doesn't see this voltage then it will try to push the output 
higher if it sees lower than 0.811V or lower if it sees higher than its target voltage. 
By using a digital potentiometer in a voltage divider that originates from the converters output and feeds the FB pin a stable form of control can be achieved.
Below is and image of the final schematic. 

<img src="/assets/images/buck converter individual.png" width="80%">
