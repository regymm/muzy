# MUZY

AMD/Xilinx ZYNQ 7010/7020 SoC as generic FPGA development board, no DDR -- cheaper than your Artix 7! 

## MUZY-2

[BGA on 2-layers? It's possible and verified!](muzy2.md)

## MUZY-4

[Now on sale!]()

**Hardware**

- Zynq 7020 (xc7z020-clg400-1)

- RP2040-based JTAG blaster, with DirtyJTAG / XVC Pico firmware, working with OpenFPGALoader and Vivado

- Dual SD Card PS + PL

- Dual Video Out HDMI + VGA 

- Dual USB Host

- Dual PMOD

- 2 switches, 2 buttons, 4 LEDs

- 256 Mb (32 MB) SDRAM

Should be perfect for SoC development & work as a handhold FPGA computer! 

Open-source [Zynq](https://github.com/regymm/GenZ)/[FPGA](https://github.com/OpenXC7) toolchains recommended! 

**JTAG**

There're 3 ways to program the FPGA by JTAG: 

1. Use the standard 2x5 pin header with an external Xilinx dongle.
2. Use the on-board pluggable RP2040 module and [the dirtyJtag firwmare](https://github.com/regymm/pico-dirtyJtag), `./pico_fw/dirtyJtag.uf2`. This supports `openFPGALoader -c dirtyJtag bitstream.bit` style direct programming. Simultaneous UART access also available, usually `/dev/ttyACM0`. Vivado access (and thus ILA) not supported by this firmware. 
3. Use the on-board pluggable RP2040 module and [the xvcPico firmware](https://github.com/regymm/xvc-pico), `./pico_fw/xvcPico.uf2`. Then, launch the daemon in xvcPico (`xvcd-pico`) and 127.0.0.1:2542 for XVC access in Vivado. openFPGALoader can still be used with `openFPGALoader -c xvc-client  --ip 127.1 --port 2542 bitstrea.bit`. Simultaneous UART access also available, usually `/dev/ttyACM0`. 

- For RP Pico firmware update, press the BOOT button down while connecting the USB-C cable, a USB-like device will show up on PC for firmware uploading. 

**Software**

Tested: [Zynq PS No-DDR SD Boot](https://github.com/regymm/GenZ/tree/master/examples/6-noddr-sdboot), [RISC-V SoC Linux booting from SD Card](https://github.com/regymm/quasiSoC/tree/master/rtl/hart_transplant/openla500), Dual video output

**Gallery**

Video: [Linux UART with dual graphics test output](https://www.youtube.com/shorts/H9cZ7YbqNOI)

Pictures: 

![](doc/muzy4-1.png)

![](doc/muzy4-2.png)

![](doc/muzy4-3.png)

