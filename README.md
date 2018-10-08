# nrf52832-recover
nrf52832 unlock or recover with Black Magic Probe

How to unlock nRF52832 2.4GHz Transceiver Wireless rf Module CDSENET E73-2G4M04S1B with Black Magic Probe or STM32F103C8T6(CB) 

board.

Official way from Nordic - use J-Link adapter and nrfjprog --recover --log

1. Get BMP or make it youself from Blue|Black|Red Pills or any STM32F103C8T6(CB) board with USB

https://github.com/blacksphere/blackmagic

2. Connect nrf52832 to Black Magic Probe (BMP)

BMP           NRF52

PA5           SWDCLK

PB14          SWDIO

3V3           3V3

GND           GND


3. Plugin USB connector BMP to your PC

  - ttyACM0 - GDB port of BMP
  
4. run arm-none-eabi-gdb

(gdb) target extended-remote /dev/ttyACM0

(gdb) set non-stop on

(gdb) mon swdp_scan

(gdb) attach 2

(gdb) mon erase_mass

It's all! Now you can program your nrf52832 with ST-Link and openocd

Open On-Chip Debugger 0.10.0-dev-00322-g406f4d1-dirty (2016-09-23-11:47)

Licensed under GNU GPL v2

For bug reports, read

    http://openocd.org/doc/doxygen/bugs.html
    
debug_level: 2

Info : The selected transport took over low-level target control. The results might differ compared to plain JTAG/SWD

adapter speed: 10000 kHz

Info : Unable to match requested speed 10000 kHz, using 4000 kHz

Info : Unable to match requested speed 10000 kHz, using 4000 kHz

Info : clock speed 4000 kHz

Info : STLINK v2 JTAG v17 API v2 SWIM v4 VID 0x0483 PID 0x3748

Info : using stlink api v2

Info : Target voltage: 3.273018

Info : nrf52.cpu: hardware has 6 breakpoints, 4 watchpoints

