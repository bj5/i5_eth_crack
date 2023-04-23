# colorlight_i5_v7.0 with colorlight_dual_ethernet_board

j5liu

## hardware

- rx: Y2 (J1_1,or other), !! for  J1_1 (5V) level shift reason， connected an 640 ohm resistor to  3v3 usb-uart txd pin !!
- tx: U16

![rx mod](https://github.com/bj5/i5_eth_crack/blob/main/images/01_rxmod.jpg)

* [J1,J2,J3,J4 Pin Map](https://github.com/bj5/i5_eth_crack/blob/main/i5-eth-re.pdf "J1,J2,J3,J4 Pin MAP")
### i5 with eth_board

![i5_on_board](https://github.com/bj5/i5_eth_crack/blob/main/images/02_i5_on_board.jpg)

### Uart Crack

![uart_rx](https://github.com/bj5/i5_eth_crack/blob/main/images/03_uart_rx.jpg)
![uart annotated](https://github.com/bj5/i5_eth_crack/blob/main/images/04_uart_conn.jpg)

## software

### Use muselab colorlight_i5_ext_board to program colorlight_i5

* [muselab i5 ext board](https://github.com/wuxx/Colorlight-FPGA-Projects "i5 ext board")
* [litex-board  i5_eth_board fork ](https://github.com/bj5/litex-boards "i5_eth_board")

  ![i5 ext_board](https://github.com/bj5/i5_eth_crack/blob/main/images/05_i5_ext.jpg)

```
$git clone https://github.com/bj5/litex-boards
$cd  litex_boards/litex_boards/targets/
$./colorlight_i5.py --with-spi-sdcard  --with-video-terminal  --build
$cd build/colorlight_i5/gateware/
$ecpdap flash write --freq 5000 colorlight_i5.bit
```

### plug colorlight_i5 in  colorlight_dual_ethernet_board

```
$litex_term /dev/ttyUSB0 
       __   _ __      _  __
       / /  (_) /____ | |/_/
      / /__/ / __/ -_)>  <
     /____/_/\__/\__/_/|_|
   Build your hardware, easily!

 (c) Copyright 2012-2022 Enjoy-Digital
 (c) Copyright 2007-2015 M-Labs

 BIOS built on Nov 23 2022 21:06:51
 BIOS CRC passed (a509fbbf)

 LiteX git sha1: 38ee44a8

--=============== SoC ==================--
CPU:		VexRiscv @ 60MHz
BUS:		WISHBONE 32-bit @ 4GiB
CSR:		32-bit data
ROM:		128KiB
SRAM:		8KiB
L2:		8KiB
FLASH:		2048KiB
SDRAM:		8192KiB 32-bit @ 60MT/s (CL-2 CWL-2)

--========== Initialization ============--
Initializing SDRAM @0x40000000...
Switching SDRAM to software control.
Switching SDRAM to hardware control.
Memtest at 0x40000000 (2.0MiB)...
  Write: 0x40000000-0x40200000 2.0MiB   
   Read: 0x40000000-0x40200000 2.0MiB   
Memtest OK
Memspeed at 0x40000000 (Sequential, 2.0MiB)...
  Write speed: 22.1MiB/s
   Read speed: 30.2MiB/s

Initializing GD25Q16 SPI Flash @0x00200000...
Enabling Quad mode...
SPI Flash clk configured to 30 MHz
Memspeed at 0x200000 (Sequential, 4.0KiB)...
   Read speed: 3.1MiB/s
Memspeed at 0x200000 (Random, 4.0KiB)...
   Read speed: 1.5MiB/s

--============== Boot ==================--
Booting from serial...
Press Q or ESC to abort boot completely.
sL5DdSMmkekro
Timeout
Booting from SDCard in SPI-Mode...
Booting from boot.json...
Booting from boot.bin...
SDCard boot failed.
No boot medium found

--============= Console ================--

litex> 

```
