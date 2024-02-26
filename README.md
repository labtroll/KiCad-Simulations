KiCad 8 projects with schematics containing ngspice simulations, created by [Holger Vogt](https://forum.kicad.info/u/holger), originally published in a [KiCad forum post](https://forum.kicad.info/t/more-simulation-examples-for-kicad-eeschema-ngspice/45546)

:warning: Directories in this repository are named after the top level folder name in the original 7z file and may differ from the xxx.7z file name and the contained xxx.kicad_pro project file. This should probably be refactored to follow KiCad best practices of naming the folder the same as the contained `.kicad_pro` file. This is not a trivial task, as several of the original 7z archives contain multiple `.kicad_pro` project files.

The section below is reconstructed from the [original post](ttps://forum.kicad.info/t/more-simulation-examples-for-kicad-eeschema-ngspice/45546) (as of 2024-02-26)

# More simulation examples for KiCad/Eeschema/ngspice

This time I am using KiCad 7.99. The new simulator interface is offering a lot of enhancements, which make it absolutely worthwile to have a look at this development. ngspice-41 is typically involved. Sometimes I am using ngspice-42 to benefit from the ngspice improvements.

The previous examples (KiCad 6, ngspice-38) are visible at https://forum.kicad.info/t/simulation-examples-for-kicad-eeschema-ngspice/34443 .

The examples provided should run out-of-the-box: Extract the *.7z file into a directory of your choice. Open the project (or directly open the *.kicad_sch in Eeschema 7.99) --> Inspect --> Simulator --> Run (green triangle).

The circuits shown below are not optimized, but may serve as a good starting point.

## Boost Converter
The first example is a simple boost converter, powering up 2.5 V to about 6 to 7 V. The switch is a power MOS device, the load is switched from 120 to 60 Ohms.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/a0f52cce-47e1-4e7d-aeef-eae7541fbfee)

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/1d862b1d-2371-4a9e-b05d-e739fe6cc158)

See [Boost](Boost)

## Regulated boost converter
The previous example has been a 'free-running' converter. Load-switching and variation in input voltage will require some regulation. The following example adds a reference voltage, an error amplifier and a PWM (pulse-width modulation) stage to the simple boost converter. Here ngspice-42 is required, as it contains an improved PWM generator.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/622b48f4-dff6-410a-b3c6-eef5cffdedc0)
The output load is switched at 13ms from 60 to 20 Ohms. The two cursors clearly show that the output voltage regulation is working.

See [boost-complete](boost-complete)

Here is a version which does not need ngspice-42, as it relies on a pwm generator made with the vernerable one-shot code model.

See [boost-regulated-os](boost-regulated-os)


## Buck Converter
A simple buck converter with power NMOS

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/f7c5ebdf-a9be-428c-9eaf-1609e729e342)

See [Buck](Buck)


## Royer Converter
The next one is a Royer converter, as described in https://www.mikrocontroller.net/articles/Royer_Converter (in German).

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/efaaa064-9f82-4b38-a782-36418f5f7800)

See [Royer](Royer)


## LLC Converter
The next one is a resonant LLC converter:

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/e792c2e4-84f8-444a-bf88-ea27e06cc430)

The look is a little ugly, as for the lack of a voltage controlled switch symbol I have used relay symbols. But there are ngspice switch models attached to these symbols!

See [LLC](LLC)


## Digital PWM amplifier
This is the very basic prototype of a digital amplifier. You have a sine source, a PWM modulator with digital ouput, an anlog filter and the analog load.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/02e60258-e178-45e6-a994-8c6a11459905)

The digital output consists of two inverse digital signals dn and dp:
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/71e1130b-ee6e-4ca3-8806-27e7ae728df0)

The analog plot compares the sine input versus the differential output voltage on the load resistor R1:
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/b026a2e5-3818-4bd5-b981-ac2f2961dffb)

See [pwm-audio](pwm-audio)


## Digital PWM amplifier update
This is an update to the basic class D amplifier: Use parameters for the PWM modulator, increase the output voltage to 200V: this yields in an output power of 2.7 kW. And nothing explodes (a benefit of the simulation)!

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/606fa2dc-abce-4d02-978f-2667975ce5d4)

This one benefits again from the new PWM generator in ngspice-42, as the old one shows some dimples in the output, due to missing pulses.

See [pwm-audio-2](pwm-audio-2)


## Another Class-D 2.5 kW audio amplifier
with half bridge MOS driver and a 'home made' audio driver circuit model (pwm, non-inverted and inverted outputs, dead-time, hi-side and low-side outputs).

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/43a48acf-3eef-420d-b34f-3d0f663f4341)

The simple Class-D-s uses the one-shot PWM (already available in ngspice-41 and older), the slightly more complex Class-D uses the somewhat faster new PWM from ngspice-42.

See [Class-D](Class-D)


## Analog multiplier
A circuit to demonstrate using a code model inside of a subcircuit.


![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/652d356a-97da-43c7-a8e1-5895c13a9a94)

The ouput is dressed in beautiful colors:
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/b9a6e1cd-ac05-4a9a-8388-4531b79239f0)

You may do amplitude modulation studies, e.g. by setting V2 to `dc=0 ampl=1 f=100k` and V1 to `dc=0.6 ampl=0.4 f=1k`, just to obtain
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/fc906f61-11e8-48a9-a34f-c03b97f8f456)

See [analog-multiplier](analog-multiplier)


## Generic symbols with generic models
The next circuit uses symbols and models from the Simulation_Spice library (opamp and npn transistor). So for a quick analysis there is no need to search for specific device models. Transient and small signal ac is simulated.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/50e2dc28-791b-48f8-8f12-d72a3d4b9d5d)

See [intro4](intro4)


## IBIS interface simulation
Some "finger execises" in the new IBIS module are shown next. IBIS allows to simulate drivers and receivers (the I/O of ICs and their connections) without resorting to the inner functions of the participating ICs. Typically a sequence "Driver -- Interconnecting tracks -- Receiver" is simulated. Still somewhat experimental.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/c76c178a-cc40-4502-80f4-f4b109f2441c)

See [ibis-test](ibis-test)

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/08610ea2-7bf9-433f-bf8d-27cc991c27f2)


## IMG

## Amplifier with controlled gain
using the TI TCA810.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/a5b9d018-19d7-430b-b048-3deed4207df8)

See [gain-ctrl-amp](gain-ctrl-amp)


## Up-Down Counter
The up-down counter uses a home-made symbol, a home-made counter model exploiting the ngspice/XSPICE state machine, and user-defined signals for plotting. Please have a look at README before starting the project.

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/89052c75-0811-4017-9129-463993c54934)

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/2702402e-70c9-48d8-9c3a-4b5fe40f2f17)

See [up-down-counter](up-down-counter)


## Triangle generator with MAX9000

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/694baca2-e380-43f4-a7e2-9f0eb8a3673e)

See [MAX9000](MAX9000)


## The venerable ICL8038
THis project contains a new spice model for the ICL8038, some info how to create such a model from the circuit diagram in the data sheet, the project to create a subcircuit for the model and an example circuit.

See [ICL8038](ICL8038)

The model circuit
[image](https://kicad-info.s3.dualstack.us-west-2.amazonaws.com/original/3X/0/e/0ea047b07c97f5ce2c888ac4456bb42f1e78ce44.png)

The example circuit
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/579bb401-43b4-40fd-b1ac-f8a087411e01)

The output, scaled
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/038ce876-6c1c-466e-ac86-df04aa73a349)

## Generating a negative voltage from a positive supply with LTC1044
LTC1044.lib contains a new behavioral ngspice model. The project is

The circuit
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/58bcc086-95af-49bc-820b-b5d76b7784a3)

and some output of a transient simulation
![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/52b569b4-c599-4c74-8676-12d288b192ca)

See [LTC1044](LTC1044)


# More circuits from previous posts, here now tested/updated for KiCad 7.99


## Integrated linear amp (LM3886), simple, real, Tian Probe

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/e5b2b180-956d-43ba-98cf-3ed748adbd1a)

The Tian probe may be used for a stability analysis of the feedback amplifier. More info is available in the attached project, file Tian.readme.

See [LM3886-Tian](LM3886-Tian)


## A bipolar 741 operational amplifier
Including a desription and example how to generate a subcircuit model for the 741 with help of the Eeschema internal circuit.

See [741](741)

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/dd9d5ccc-0837-4f5b-afff-cee75f2dd2e3)


## Q17, a redesign of the famous QUAD405 High-End Audio Amplifier, 
made by Tiberiu Vicol (https://www.diyaudio.com/community/threads/q17-a-quad405-audiophile-approach-to-perfect-sound.374507/). He designed circuit and PCB with KiCad, I have modified his files to enable simulation with KiCad/ngspice.
See [Q17](Q17)

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/040b5529-712d-443c-b6d0-863e76d1e2e6)


## rel_osc

:exclamation: No documentation found.

See [rel_osc](rel_osc)


## bip-osc-2

:exclamation: No documentation found.

See [bip-osc-2](bip-osc-2)


## CMOS555_4

:exclamation: No documentation found.

See [CMOS555_4](CMOS555_4)


## FullBridge

:exclamation: No documentation found.

See [FullBridge](FullBridge)


