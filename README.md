# GD32VF103 Firmware Library

## Build instructions ##

This repo uses the `meson` build engine, and has been tested with
version `0.54.3`.

To build this repo, first build [the RISC-V GNU Toolchain for
MCUs](https://github.com/riscv-mcu/riscv-gnu-toolchain) and deploy to
your preferred root (I use `/opt/riscv`.)

In the repo's main folder, run:
```
meson out --cross cross.ini --default-library=static --prefix=/opt/riscv
```
This will generate the build directory, `./out`, and will define the
install directory for the compiled library and headers as a standard
tree under `/opt/riscv`.

Switch directories into `./out`, and run `meson install` to build and
install the SDK library in `/opt/riscv/lib`, with headers placed in
`/opt/riscv/include/gd32vf103`.

## Original README:

This is the directory to save original GD32VF103 Firmware Library
For more comprehensive information, please visit www.riscv-mcu.com


