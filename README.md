# radxa-penta package
All testing is done on a *RADXA Rock 5C v1.1*

### Reimplmentation of the [rockpi-penta](https://github.com/radxa/rockpi-penta) control program by radxa for the [RADXA Penta SATA Top Board](https://radxa.com/products/accessories/penta-sata-top-board).

![Radxa SATA HAT Top Board](https://radxa.com/storage-expansion/ra005-tb/marked_penta_sata_top_board.webp "Radxa SATA HAT Top Board")

[Cabin](https://cabinpkg.com/) is used as the package manager in build system.
> [!CAUTION]
> Cabin is still under development and may contain a bunch of bugs.

Using [lcdgfx](https://github.com/lexus2k/lcdgfx) for controlling the display.


### Checkout alteranative forks and reimplementations:

- https://github.com/radxa/rockpi-penta
- https://github.com/kYc0o/radxa-penta-sata-hat-top-board-ctrl-c
- https://github.com/Pudel-des-Todes/rockpi-penta
- https://github.com/andrewheberle/rockpi-penta

Trying to solve radxa issue [#18](https://github.com/radxa/rockpi-penta/issues/18) for my test board.

clang-format and clang-tidy copied from [ken-matsui](https://github.com/ken-matsui).

**Features:**

- [ ] Smart fan control
- [ ] OLED display pages
- [ ] Button navigation
- [ ] Systemd integration with journal logging
- [ ] SSD temperature monitoring
- [ ] Publish as compliant deb


### Hardware

https://docs.radxa.com/en/rock5/rock5c/hardware-design/hardware-interface

<details>
  <summary>40 PIN GPIO Header</summary>

  ### GPIO voltage
  
  | GPIO | Voltage | Max Voltage |
  | --- | --- | --- |
  | All GPIO | 3.3V | 3.63V |
  | SARADC_IN | 1.8V | 1.98V |
  
  ### GPIO Pinout
  
  | GPIO number | Function7 | Function6 | Function5 | Function4 | Function3 | Function2 | Function1 | Pin# | Pin# | Function1 | Function2 | Function3 | Function4 | Function5 | Function6 | Function7 | GPIO number |
  | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
  |  |  |  |  |  |  |  | +3.3V | 1 | 2 | +5.0V |  |  |  |  |  |  |  |
  | 63 |  |  |  | PWM15_IR_M3 | I2C8_SDA_M2 | UART1_CTSN_M1 | GPIO1_D7 | 3 | 4 | +5.0V |  |  |  |  |  |  |  |
  | 62 |  |  |  | PWM14_M2 | I2C8_SCL_M2 | UART1_RTSN_M1 | GPIO1_D6 | 5 | 6 | GND |  |  |  |  |  |  |  |
  | 43 |  |  |  |  |  | UART4_TX_M2 | GPIO1_B3 | 7 | 8 | GPIO0_B5 | UART2_TX_M0 | I2C1_SCL_M0 |  |  | I2S1_MCLK_M1 |  | 13 |
  |  |  |  |  |  |  |  | GND | 9 | 10 | GPIO0_B6 | UART2_RX_M0 | I2C1_SDA_M0 |  |  | I2S1_SCLK_M1 |  | 14 |
  | 139 |  | I2S1_SDO2_M0 |  | PWM15_IR_M1 |  | UART8_CTSN_M0 | GPIO4_B3 | 11 | 12 | GPIO4_A1 | UART9_CTSN_M1 |  |  |  | I2S1_SCLK_M0 | SPI0_MOSI_M1 | 129 |
  | 138 | SPI0_CS0_M1 | I2S1_SDO1_M0 |  | PWM14_M1 |  | UART8_RTSN_M0 | GPIO4_B2 | 13 | 14 | GND |  |  |  |  |  |  |  |
  | 140 |  | I2S1_SDO3_M0 | SPDIF0_TX_M1 | PWM11_IR_M1 |  | UART9_TX_M1 | GPIO4_B4 | 15 | 16 | GPIO1_A5 |  |  |  |  |  | SPI2_MOSI_M0 | 37 |
  |  |  |  |  |  |  |  | +3.3V | 17 | 18 | GPIO1_B0 |  |  |  |  |  | SPI2_CS1_M0 | 40 |
  | 33 | SPI4_MOSI_M2 |  |  |  | I2C2_SCL_M4 | UART6_TX_M1 | GPIO1_A1 | 19 | 20 | GND |  |  |  |  |  |  |  |
  | 32 | SPI4_MISO_M2 |  |  |  | I2C2_SDA_M4 | UART6_RX_M1 | GPIO1_A0 | 21 | 22 | GPIO1_B5 | UART7_TX_M2 |  |  |  |  | SPI0_CS1_M2 | 45 |
  | 34 | SPI4_CLK_M2 |  |  | PWM0_M2 | I2C4_SDA_M3 | UART6_RTSN_M1 | GPIO1_A2 | 23 | 24 | GPIO1_A3 | UART6_CTSN_M1 | I2C4_SCL_M3 | PWM1_M2 |  |  | SPI4_CS0_M2 | 35 |
  |  |  |  |  |  |  |  | GND | 25 | 26 | GPIO1_A4 |  |  |  |  |  | SPI2_MISO_M0 | 36 |
  | 23 | SPI0_MISO_M0 | I2S1_SDI2_M1 |  | PWM6_M0 | I2C6_SDA_M0 | UART1_RTSN_M2 | GPIO0_C7 | 27 | 28 | GPIO0_D0 | UART1_CTSN_M2 | I2C6_SCL_M0 | PWM7_IR_M0 |  | I2S1_SDI3_M1 | SPI3_MISO_M2 | 24 |
  | 42 | SPI0_MOSI_M2 |  |  |  |  | UART4_RX_M2 | GPIO1_B2 | 29 | 30 | GND |  |  |  |  |  |  |  |
  | 41 | SPI0_MISO_M2 |  |  |  |  |  | GPIO1_B1 | 31 | 32 | GPIO4_B0 | UART8_TX_M0 | I2C6_SDA_M3 |  |  | I2S1_SDI3_M0 | SPI2_CS1_M1 | 136 |
  | 44 | SPI0_CS0_M2 |  |  |  |  | UART7_RX_M2 | GPIO1_B4 | 33 | 34 | GND |  |  |  |  |  |  |  |
  | 128 | SPI0_MISO_M1 | I2S1_MCLK_M0 |  |  |  | UART9_RTSN_M1 | GPIO4_A0 | 35 | 36 | GPIO4_A2 |  |  |  |  | I2S1_LRCK_M0 | SPI0_CLK_M1 | 130 |
  |  |  |  |  |  |  |  | SARADC_VIN2 | 37 | 38 | GPIO4_A5 | UART3_TX_M2 | I2C3_SDA_M2 |  |  | I2S1_SDI0_M0 |  | 133 |
  |  |  |  |  |  |  |  | GND | 39 | 40 | GPIO4_B1 | UART8_RX_M0 | I2C6_SCL_M3 |  | SPDIF1_TX_M1 | I2S1_SDO0_M0 | SPI0_CS1_M1 | 137 |

</details>

#### GPIO device info (libgpiod)

<details>
  <summary>Parsed output</summary>
  
  ##### gpiodetect
  
  ```console
  radxa@rock-5c:~$ gpiodetect  
  gpiochip0 [gpio0] (32 lines)
  gpiochip1 [gpio1] (32 lines)
  gpiochip2 [gpio2] (32 lines)
  gpiochip3 [gpio3] (32 lines)
  gpiochip4 [gpio4] (32 lines)
  gpiochip5 [rk806-gpio] (3 lines)
  ```
  ##### gpioinfo
  
  ```console
  radxa@rock-5c:~$ gpioinfo  
gpiochip0 - 32 lines:
        line   0:      unnamed "wifibt-power" output active-high [used]
        line   7:      unnamed  "interrupt"   input  active-high [used]
        line  13:      "PIN_8"       unused   input  active-high 
        line  14:     "PIN_10"       unused   input  active-high 
        line  21:      unnamed "vcc3v3-pcie" output active-high [used]
        line  23:     "PIN_27"       unused   input  active-high 
        line  24:     "PIN_28"       unused   input  active-high 
        line  28:      unnamed "vcc5v0-otg-regulator" output active-high [used]
gpiochip1 - 32 lines:
        line   0:     "PIN_21"       unused   input  active-high 
        line   1:     "PIN_19"       unused   input  active-high 
        line   2:     "PIN_23"       unused   input  active-high 
        line   3:     "PIN_24"       unused   input  active-high 
        line   4:     "PIN_26"       unused   input  active-high 
        line   5:     "PIN_16"       unused  output  active-high 
        line   8:     "PIN_18"       unused   input  active-high 
        line   9:     "PIN_31"       unused   input  active-high 
        line  10:     "PIN_29"       unused   input  active-high 
        line  11:      "PIN_7"       unused   input  active-high 
        line  12:     "PIN_33"       unused   input  active-high 
        line  13:     "PIN_22"       unused   input  active-high 
        line  21:      unnamed   "i2s-lrck"   input  active-high [used]
        line  30:      "PIN_5"       unused   input  active-high 
        line  31:      "PIN_3"       unused   input  active-high 
gpiochip2 - 32 lines:
gpiochip3 - 32 lines:
        line  20:      unnamed  "user-led1"  output  active-high [used]
        line  25:      unnamed      "reset"  output  active-high [used]
        line  29:      unnamed  "user-led2"  output  active-high [used]
gpiochip4 - 32 lines:
        line   0:     "PIN_35"       unused   input  active-high 
        line   1:     "PIN_12"       unused   input  active-high 
        line   2:     "PIN_36"       unused   input  active-high 
        line   3:      unnamed    "vcc-5v0"  output  active-high [used]
        line   5:     "PIN_38"       unused   input  active-high 
        line   8:     "PIN_32"       unused   input  active-high 
        line   9:     "PIN_40"       unused   input  active-high 
        line  10:     "PIN_13"       unused   input  active-high 
        line  11:     "PIN_11"       unused   input  active-high 
        line  12:     "PIN_15"       unused   input  active-high 
        line  13:      unnamed "vcc5v0-host-regulator" output active-high [used]
        line  14:      unnamed     "enable"  output  active-high [used]
gpiochip5 - 3 lines:
  ```
</details>

