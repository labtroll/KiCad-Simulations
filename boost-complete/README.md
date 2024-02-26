# Regulated boost converter
The previous example has been a ‘free-running’ converter. Load-switching and variation in input voltage will require some regulation. The following example adds a reference voltage, an error amplifier and a PWM (pulse-width modulation) stage to the simple boost converter. Here ngspice-42 is required, as it contains an improved PWM generator.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/fe952107-10dd-4470-9e65-131fcddc0b40)

The output load is switched at 13ms from 60 to 20 Ohms. The two cursors clearly show that the output voltage regulation is working.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/5d3def61-7011-4751-9c2c-8d7811d70bc6)
