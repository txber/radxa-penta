# radxa-penta package
All testing is done on a *RADXA Rock 5C v1.1*

Reimplmentation of the [rockpi-penta](https://github.com/radxa/rockpi-penta) control program by radxa for the [RADXA Penta SATA Top Board](https://radxa.com/products/accessories/penta-sata-top-board).

![Radxa SATA HAT Top Board](https://radxa.com/storage-expansion/ra005-tb/marked_penta_sata_top_board.webp "Radxa SATA HAT Top Board")

[Cabin](https://cabinpkg.com/) is used as the package manager in build system.
> [!CAUTION]
> Cabin is still under development and may contain a bunch of bugs.

Using [lcdgfx](https://github.com/lexus2k/lcdgfx) for controlling the display.


Checkout alteranative forks and reimplementations:

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

