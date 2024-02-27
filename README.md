# KiCad 8 Simulation Projects

The subfolders contain KiCad 8 projects with schematics containing ngspice simulations, created by [Holger Vogt](https://forum.kicad.info/u/holger), originally published in a [KiCad forum post](https://forum.kicad.info/t/more-simulation-examples-for-kicad-eeschema-ngspice/45546)

:warning: Directories in this repository are named after the top level folder name in the original 7z file and may differ from the xxx.7z file name and the contained xxx.kicad_pro project file. This should probably be refactored to follow KiCad best practices of naming the folder the same as the contained `.kicad_pro` file. This is not a trivial task, as several of the original 7z archives contain multiple `.kicad_pro` project files.

# Simulation examples for KiCad/Eeschema/ngspice

The new simulator interface in KiCad 8 is offering a lot of enhancements, which make it absolutely worthwile to have a look at this development.

The previous examples (KiCad 6, ngspice-38) are published in [this KiCad forum post](https://forum.kicad.info/t/simulation-examples-for-kicad-eeschema-ngspice/34443), some of which have been updated and included below.

The examples provided should run out-of-the-box: locate the project subfolder, open the `*.kicad_pro` project (or directly open the `*.kicad_sch` file in Eeschema 8.0) > `Inspect` -> `Simulator` -> `Run` (green triangle).

## Circuits
The circuits shown below are not optimized, but may serve as a good starting point.

* **Boost Converter** See [Boost](Boost)
* **Regulated boost converter** See [boost-complete](boost-complete)
* **Regulated boost converter** See [boost-regulated-os](boost-regulated-os)
  Version which does not need ngspice-42, as it relies on a pwm generator made with the vernerable one-shot code model.  
* **Buck Converter** See [Buck](Buck)
* **Royer Converter** See [Royer](Royer)
* **LLC Converter** See [LLC](LLC)
* **Digital PWM amplifier** See [pwm-audio](pwm-audio)
* **Digital PWM amplifier update** See [pwm-audio-2](pwm-audio-2)
* **Another Class-D 2.5 kW audio amplifier** See [Class-D](Class-D)
* **Analog multiplier** See [analog-multiplier](analog-multiplier)
* **Generic symbols with generic models** See [intro4](intro4)
* **IBIS interface simulation** See [ibis-test](ibis-test)
* **Amplifier with controlled gain** See [gain-ctrl-amp](gain-ctrl-amp)
* **Up-Down Counter** See [up-down-counter](up-down-counter)
* **Triangle generator with MAX9000** See [MAX9000](MAX9000)
* **The venerable ICL8038** See [ICL8038](ICL8038)
* **Generating a negative voltage from a positive supply with LTC1044** See [LTC1044](LTC1044)

## More circuits from previous posts, here now tested/updated for KiCad 7.99

* **Integrated linear amp (LM3886), simple, real, Tian Probe** See [LM3886-Tian](LM3886-Tian)
* **A bipolar 741 operational amplifier** See [741](741)
* **Q17, a redesign of the famous QUAD405 High-End Audio Amplifier** See [Q17](Q17)
* **Digital Simulation**, see [QEI_public_799](QEI_public_799)
* **rel_osc (missing documentation)** See [rel_osc](rel_osc)
* **bip-osc-2 (missing documentation)** See [bip-osc-2](bip-osc-2)
* **CMOS555_4 (missing documentation)** See [CMOS555_4](CMOS555_4)
* **FullBridge (missing documentation)** See [FullBridge](FullBridge)
