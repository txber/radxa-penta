# radxa-penta package

> [!NOTE]
> All testing is done on a *RADXA ROCK 5C v1.1 Rockchip RK3588S*
>
> *UNDER DEVELOPMENT*

### Reimplementation of the [rockpi-penta](https://github.com/radxa/rockpi-penta) control program by radxa for the [RADXA Penta SATA Top Board](https://radxa.com/products/accessories/penta-sata-top-board).

![Radxa SATA HAT Top Board](https://radxa.com/storage-expansion/ra005-tb/marked_penta_sata_top_board.webp "Radxa SATA HAT Top Board")

[Cabin](https://cabinpkg.com/) is used as package manager and build system.

Using [lcdgfx](https://github.com/lexus2k/lcdgfx) for controlling the display.


### Checkout alternative forks and reimplementations:

- https://github.com/radxa/rockpi-penta
- https://github.com/kYc0o/radxa-penta-sata-hat-top-board-ctrl-c
- https://github.com/Pudel-des-Todes/rockpi-penta
- https://github.com/andrewheberle/rockpi-penta

Trying to solve radxa issue [#18](https://github.com/radxa/rockpi-penta/issues/18) for my test board.

clang-format and clang-tidy copied from [ken-matsui](https://github.com/ken-matsui).

### Environment files

Each compatible hardware has a seperate environment [file](env/) to specify the relevant pinouts.
Feel free to add files for additional hardware if tested.

|      Key     | Function |
|------------|--------|
| SDA          | |
| SCL          | |
| OLED_RESET   | vendor gpio translated from ```gpiofind PIN_#``` according to pinout header info |
| PWMCHIP      | If HARDWARE_PWM set the chip number corresponding to /sys/class/pwm/pwmchip1/ (pwmchip1 == 1) |
| BUTTON_CHIP  | Gpio chip ([Convert vendor gpio to libgpiod](https://docs.radxa.com/en/rock5/rock5c/app-development/gpiod?vendorTolibgpiod=Rockchip&lang=Python#convert-vendor-gpio-to-libgpiod) or use ```gpiofind PIN_#```) |
| BUTTON_LINE  | Gpio line ([Convert vendor gpio to libgpiod](https://docs.radxa.com/en/rock5/rock5c/app-development/gpiod?vendorTolibgpiod=Rockchip&lang=Python#convert-vendor-gpio-to-libgpiod) or use ```gpiofind PIN_#```) |
| HARDWARE_PWM | Is the board hardware pwm enabled? If yes set 1 |

### Hardware

>[!IMPORTANT]
> The Penta SATA HAT is designed for ROCK Pi 4, one model only.

#### Sata head GPIO header info collection

##### ROCK Pi 4 Pinout for 40PIN GPIO header from [wiki](https://wiki.radxa.com/Penta_SATA_HAT)

|      Description     |  Function | Pin# | Pin# |   Function  | Description |
|:--------------------:|:---------:|:----:|:----:|:-----------:|:-----------:|
|                      |           | 1    | 2    | VCC5V0_SYS  |             |
| OLED I2C             | I2C_SDA   | 3    | 4    | VCC5V0_SYS  |             |
| OLED I2C             | I2C_SCL   | 5    | 6    |             |             |
|                      |           | 7    | 8    |             |             |
|                      |           | 9    | 10   |             |             |
| top board key        | GPIO4_C2  | 11   | 12   |             |             |
|                      | GPIO4_C6  | 13   | 14   |             |             |
|                      |           | 15   | 16   | GPIO4_D2    | reset OLED  |
|                      |           | 17   | 18   |             |             |
|                      |           | 19   | 20   |             |             |
|                      |           | 21   | 22   |             |             |
|                      |           | 23   | 24   |             |             |
|                      |           | 25   | 26   | ADC_IN0     | temperature |
|                      | SDA       | 27   | 28   | SCL         |             |
|                      |           | 29   | 30   |             |             |
|                      |           | 31   | 32   |             |             |
| control tb-fan speed | PWM_33    | 33   | 34   |             |             |
|                      |           | 35   | 36   |             |             |
|                      |           | 37   | 38   |             |             |
|                      |           | 39   | 40   |             |             |

##### ROCK 5C v1.1 Pinout for 40PIN GPIO header by [txber](https://github.com/txber)

|      Description     |  Function | Pin# | Pin# |   Function  | Description |
|:--------------------:|:---------:|:----:|:----:|:-----------:|:-----------:|
|                      |           | 1    | 2    |             |             |
|                      |           | 3    | 4    |             |             |
|                      |           | 5    | 6    |             |             |
|                      |           | 7    | 8    |             |             |
|                      |           | 9    | 10   |             |             |
| top board key        | GPIO4_B3  | 11   | 12   |             |             |
|                      | GPIO4_B2  | 13   | 14   |             |             |
|                      |           | 15   | 16   | GPIO1_A5    | reset OLED  |
|                      |           | 17   | 18   |             |             |
|                      |           | 19   | 20   |             |             |
|                      |           | 21   | 22   |             |             |
|                      |           | 23   | 24   |             |             |
|                      |           | 25   | 26   | ADC_IN0     | temperature |
|                      | SDA       | 27   | 28   | SCL         |             |
|                      |           | 29   | 30   |             |             |
|                      |           | 31   | 32   |             |             |
|                      |           | 33   | 34   |             |             |
|                      |           | 35   | 36   |             |             |
|                      |           | 37   | 38   |             |             |
|                      |           | 39   | 40   |             |             |
