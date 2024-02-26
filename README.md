KiCad 8 projects with schematics containing ngspice simulations, created by [Holger Vogt](https://forum.kicad.info/u/holger), originally published in a [KiCad forum post](https://forum.kicad.info/t/more-simulation-examples-for-kicad-eeschema-ngspice/45546)

:warning: Directories in this repository are named after the top level folder name in the original 7z file and may differ from the xxx.7z file name and the contained xxx.kicad_pro project file. This should probably be refactored to follow KiCad best practices of naming the folder the same as the contained `.kicad_pro` file. This is not a trivial task, as several of the original 7z archives contain multiple `.kicad_pro` project files.

The section below is reconstructed from the [original post](ttps://forum.kicad.info/t/more-simulation-examples-for-kicad-eeschema-ngspice/45546) (as of 2024-02-26)

# More simulation examples for KiCad/Eeschema/ngspice

This time I am using KiCad 7.99. The new simulator interface is offering a lot of enhancements, which make it absolutely worthwile to have a look at this development. ngspice-41 is typically involved. Sometimes I am using ngspice-42 to benefit from the ngspice improvements.

The previous examples (KiCad 6, ngspice-38) are visible at https://forum.kicad.info/t/simulation-examples-for-kicad-eeschema-ngspice/34443 .

The examples provided should run out-of-the-box: Extract the *.7z file into a directory of your choice. Open the project (or directly open the *.kicad_sch in Eeschema 7.99) --> Inspect --> Simulator --> Run (green triangle).

The circuits shown below are not optimized, but may serve as a good starting point.

## [Boost Converter](Boost)
The first example is a simple boost converter, powering up 2.5 V to about 6 to 7 V. The switch is a power MOS device, the load is switched from 120 to 60 Ohms.


**IMG**


**IMG**


See [Boost](Boost)

## Regulated boost converter
The previous example has been a 'free-running' converter. Load-switching and variation in input voltage will require some regulation. The following example adds a reference voltage, an error amplifier and a PWM (pulse-width modulation) stage to the simple boost converter. Here ngspice-42 is required, as it contains an improved PWM generator.

**IMG**
The output load is switched at 13ms from 60 to 20 Ohms. The two cursors clearly show that the output voltage regulation is working.

**IMG**

See [boost-complete](boost-complete)
Here is a version which does not need ngspice-42, as it relies on a pwm generator made with the vernerable one-shot code model.

See [boost-regulated-os](boost-regulated-os)


## Buck Converter
A simple buck converter with power NMOS


**IMG**


See [Buck](Buck)


## [Royer Converter](Royer/)
The next one is a Royer converter, as described in https://www.mikrocontroller.net/articles/Royer_Converter (in German).

**IMG**

See [Royer](Royer)

## LLC Converter
The next one is a resonant LLC converter:

**IMG**
The look is a little ugly, as for the lack of a voltage controlled switch symbol I have used relay symbols. But there are ngspice switch models attached to these symbols!

See [LLC](LLC)

## Digital PWM amplifier
This is the very basic prototype of a digital amplifier. You have a sine source, a PWM modulator with digital ouput, an anlog filter and the analog load.

**IMG**
The digital output consists of two inverse digital signals dn and dp:

**IMG**
The analog plot compares the sine input versus the differential output voltage on the load resistor R1:

**IMG**


See [pwm-audio](pwm-audio)

## Digital PWM amplifier update
This is an update to the basic class D amplifier: Use parameters for the PWM modulator, increase the output voltage to 200V: this yields in an output power of 2.7 kW. And nothing explodes (a benefit of the simulation)!

**IMG**



See [pwm-audio-2](pwm-audio-2)

This one benefits again from the new PWM generator in ngspice-42, as the old one shows some dimples in the output, due to missing pulses.

## Another Class-D 2.5 kW audio amplifier
with half bridge MOS driver and a 'home made' audio driver circuit model (pwm, non-inverted and inverted outputs, dead-time, hi-side and low-side outputs).

**IMG**
The simple Class-D-s uses the one-shot PWM (already available in ngspice-41 and older), the slightly more complex Class-D uses the somewhat faster new PWM from ngspice-42.


See [Class-D](Class-D)



## Analog multiplier
A circuit to demonstrate using a code model inside of a subcircuit.


**IMG**
The ouput is dressed in beautiful colors:

**IMG**

See [analog-multiplier](analog-multiplier)
You may do amplitude modulation studies, e.g. by setting V2 to `dc=0 ampl=1 f=100k` and V1 to `dc=0.6 ampl=0.4 f=1k`, just to obtain


**IMG**


## Generic symbols with generic models
The next circuit uses symbols and models from the Simulation_Spice library (opamp and npn transistor). So for a quick analysis there is no need to search for specific device models. Transient and small signal ac is simulated.

**IMG**




See [intro4](intro4)

## IBIS interface simulation
Some "finger execises" in the new IBIS module are shown next. IBIS allows to simulate drivers and receivers (the I/O of ICs and their connections) without resorting to the inner functions of the participating ICs. Typically a sequence "Driver -- Interconnecting tracks -- Receiver" is simulated. Still somewhat experimental.


**IMG**


See [ibis-test](ibis-test)


**IMG**

## Amplifier with controlled gain
using the TI TCA810.

**IMG**

See [gain-ctrl-amp](gain-ctrl-amp)

## Up-Down Counter
The up-down counter uses a home-made symbol, a home-made counter model exploiting the ngspice/XSPICE state machine, and user-defined signals for plotting. Please have a look at README before starting the project.


**IMG**

**IMG**

See [up-down-counter](up-down-counter)

## Triangle generator with MAX9000

**IMG**

See [MAX9000](MAX9000)

## The venerable ICL8038
THis project contains a new spice model for the ICL8038, some info how to create such a model from the circuit diagram in the data sheet, the project to create a subcircuit for the model and an example circuit.

See [ICL8038](ICL8038)

The model circuit

**IMG**

The example circuit

**IMG**
The output, scaled

**IMG**
**IMG**

## Generating a negative voltage from a positive supply with LTC1044
LTC1044.lib contains a new behavioral ngspice model. The project is

See [LTC1044](LTC1044)
The circuit

**IMG**
and some output of a transient simulation

**IMG**

## Some more circuits from my previous post, here now tested/updated for KiCad 7.99

:todo: Add title and description/images from previous post(s)

* See [Q17](Q17)
* See [LM3886-Tian](LM3886-Tian)
* See [rel_osc](rel_osc)
* See [bip-osc-2](bip-osc-2)
* See [CMOS555_4](CMOS555_4)
* See [PassLabsF5](PassLabsF5)
* See [FullBridge](FullBridge)
* See [741](741)
