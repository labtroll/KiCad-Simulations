## Regulated boost converter
The previous example has been a 'free-running' converter. Load-switching and variation in input voltage will require some regulation. The following example adds a reference voltage, an error amplifier and a PWM (pulse-width modulation) stage to the simple boost converter. Here ngspice-42 is required, as it contains an improved PWM generator.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/622b48f4-dff6-410a-b3c6-eef5cffdedc0)
The output load is switched at 13ms from 60 to 20 Ohms. The two cursors clearly show that the output voltage regulation is working.

Here is a version which does not need ngspice-42, as it relies on a pwm generator made with the vernerable one-shot code model.