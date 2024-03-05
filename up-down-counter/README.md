# Up-Down Counter
This project contains a home-made symbol, a home-made subcircuit counter model, and a mix of digital and analog nodes.

Before running the project, please edit file state-machine-3b-count.lib:
In line 13 you will need to enter the absolute path of file state-3bit-count.in:
This need will be removed in a future KiCad version.

The subcircuit counter model is made by the built-in ngspice/XSPICE state machine.
This is a very simple method to run a programmable sequencer. The 'program'
is contained in file state-3bit-count.in.

Please see chapter 12.4.18 'State Machine' of the ngspice manual for more information.

The digital nodes of the state machine are interfaced to the analog world by D/A bridges.

When plotting the output, we use User-defined signals to allow plotting of
multiple signal vertically without overlap, thus emulating multiple panes.

## Schematics

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/89052c75-0811-4017-9129-463993c54934)

## Transient Analysis

![image](https://github.com/labtroll/KiCad-Simulations/assets/3527219/2702402e-70c9-48d8-9c3a-4b5fe40f2f17)
