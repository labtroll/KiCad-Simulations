## Digital PWM amplifier update
This is an update to the basic class D amplifier: Use parameters for the PWM modulator, increase the output voltage to 200V: this yields in an output power of 2.7 kW. And nothing explodes (a benefit of the simulation)!

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/606fa2dc-abce-4d02-978f-2667975ce5d4)

This one benefits again from the new PWM generator in ngspice-42, as the old one shows some dimples in the output, due to missing pulses.

