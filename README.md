# u-boot

## U-boot compilation for RasberryPi 3 B on Ubuntu 16.04 build system:

Install build toolchain:
```
$sudo apt install gcc-arm-linux-gnueabihf
$sudo apt-get install u-boot-tools
```
Set build environment in current terminal:
```
$export CROSS_COMPILE=arm-linux-gnueabihf-
$export ARCH=arm
```
Clone u-boot and setup configuration. There had been compilation issue at master branch and so instead of master branch,
v2016.05 branch had been used. Also, rpi_3_config was not a success build and rpi_3_32b_config was taken. As my build system
is quad core, and boot source is good anought size to build quickly, make is executed with eight kernel thread without
hampering system performance.

```
$git clone git://git.denx.de/u-boot.git
$cd u-boot
$git checkout v2016.05 -b v2016.05
$make rpi_3_32b_config
$make -j8
```
