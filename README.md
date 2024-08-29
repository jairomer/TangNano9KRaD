# Tang Nano 9k FPGA R&D

This is a repository I will use to store links and information related to my journey of learning how to code FPGAs, which is a necessary step in order to understand the basics of hardware development.

## Tang Nano 9k

You can find every file about this component in `docs`.

### Open Toolchain

The first step to begin work is to remove ourselves from the artificial limitations and rent-seeking practices applied by the manufacturer of this device.

It is possible to synthesize verilog code for the Tang Nano 9K using `yosys`, `nextpnr-gowin`, `gowin_pack` and `openFPGALoader`.

Here is an example  for `blinky.v`.
```
yosys -D LEDS_NR=6 -p "read_verilog blinky.v; synth_gowin -json blinky.json"

nextpnr-gowin --json blinky.json --write pnrblinky.json --device GW1NR-LV9QN88PC6/I5 --family GW1N-9C --cst tangnano9k.cst

gowin_pack -d GW1N-9C -o pack.fs pnrblinky.json

openFPGALoader -b tangnano9k pack.fs
```

- [Source](https://www.geeklan.co.uk/?p=2919)

## Training

I will be following [this course](https://zipcpu.com/tutorial/) for the exercises, notes and demonstrations.
