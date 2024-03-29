# Simulation Examples for KiCad 8.0 Using Ngspice

The subfolders contain KiCad 7.99/8.0 projects with schematics containing ngspice simulations, created by [Holger Vogt](https://forum.kicad.info/u/holger), originally published in a [KiCad forum post](https://forum.kicad.info/t/more-simulation-examples-for-kicad-eeschema-ngspice/45546)

:warning: Directories in this repository are named after the original 7z file name and may differ from the xxx.7z folder name and the contained xxx.kicad_pro project file. This should probably be refactored to follow KiCad best practices of naming the folder the same as the contained `.kicad_pro` file. This is, however, not a trivial task, as several of the original 7z archives contain multiple `.kicad_pro` project files.


## FOSDEM 2024 presentation

A number of these circuits were included in a presentation on [FOSDEM 2024](https://fosdem.org/2024/): [ngspice circuit simulator - stand-alone and embedded into KiCad](https://fosdem.org/2024/schedule/event/fosdem-2024-2834-ngspice-circuit-simulator-stand-alone-and-embedded-into-kicad/) ([slides](https://fosdem.org/2024/events/attachments/fosdem-2024-2834-ngspice-circuit-simulator-stand-alone-and-embedded-into-kicad/slides/22676/ngspice-HolgerVogt_tEfhemB.pdf))

[![FOSDEM 2024 - ngspice circuit simulator stand alone and embedded into kicad](https://img.youtube.com/vi/hnkTLkVplBI/0.jpg)](https://www.youtube.com/watch?v=hnkTLkVplBI)


## Ngspice User's Manual

For convenience, here are some useful links to ngspice documentation:
* [ngspice User's Manual](https://ngspice.sourceforge.io/docs/ngspice-html-manual/manual.xhtml)
* [Tutorial: ngspice simulation in KiCad/Eeschema](https://ngspice.sourceforge.io/ngspice-eeschema.html)


# Simulation Examples

The new simulator interface in KiCad 8.0 is offering a lot of enhancements, which make it absolutely worthwile to have a look at.

The examples provided should all run out-of-the-box:
1. Locate the project subfolder
2. Open the `*.kicad_pro` project or directly open the schemtic in the `*.kicad_sch` file
3. In the `KiCad Schematic Editor`: `Inspect` :arrow_right: `Simulator` :arrow_right: `Run` (green triangle).


## Simulation Circuits

The circuits shown below are not optimized, but may serve as a good starting point.

* **RC Low Pass Filter**, see [rc-filter](rc-filter)
* **Boost Converter**, see [Boost](Boost)
* **Regulated boost converter**, see [boost-complete](boost-complete)
* **Regulated boost converter**, see [boost-regulated-os](boost-regulated-os)  
  Version which does not need ngspice-42, as it relies on a pwm generator made with the vernerable one-shot code model.  
* **Buck Converter**, see [Buck](Buck)
* **Royer Converter**, see [Royer](Royer)
* **LLC Converter**, see [LLC](LLC)
* **Digital PWM amplifier**, see [pwm-audio](pwm-audio)
* **Digital PWM amplifier update**, see [pwm-audio-2](pwm-audio-2)
* **Another Class-D 2.5 kW audio amplifier**, see [Class-D](Class-D)
* **Analog multiplier**, see [analog-multiplier](analog-multiplier)
* **Generic symbols with generic models**, see [intro4](intro4)
* **IBIS interface simulation**, see [ibis-test](ibis-test)
* **Amplifier with controlled gain, using TI TCA810**, see [gain-ctrl-amp](gain-ctrl-amp)
* **Up-Down Counter**, see [up-down-counter](up-down-counter)
* **Triangle generator with MAX9000**, see [MAX9000](MAX9000)
* **The venerable ICL8038**, see [ICL8038](ICL8038)
* **Generating a negative voltage from a positive supply with LTC1044**, see [LTC1044](LTC1044)
* **Integrated linear amp (LM3886), simple, real, Tian Probe**, see [LM3886-Tian](LM3886-Tian)
* **A bipolar 741 operational amplifier**, see [741](741)
* **Q17, a redesign of the famous QUAD405 High-End Audio Amplifier**, see [Q17](Q17)
* **Quadrature Rotary Encoder (Digital Simulation)**, see [QEI_public_8_mod](QEI_public_8_mod)
* **40106-Based Oscillator**, see [rel_osc](rel_osc)
* **A simple Phase Shift, Single Bipolar Transistor Oscillator**, see [bip-osc-2](bip-osc-2)
* **CMOS555_4**, see [CMOS555_4](CMOS555_4)
* **Full Bridge N-CMOS Circuit**, see [FullBridge](FullBridge)
* **555 Bipolar**, see [555-bipolar](555-bipolar)
* **Pass Labs F5 Turbo V2 thermal simulation**, see [PassLabsF5](PassLabsF5)
* **[Sallen-Key low-pass Filter](sallen-key-lowpass)**
* **[Sallen-Key high-pass Filter](sallen-key-highpass)**
