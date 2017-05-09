# ansible_pi3_nexmon
If you want to use a Pi3's wireless as a security tool (monitor mode)

## Description

We plan to use Raspberry Pi3 as a tool for our Computer Security courses, but they have a huge disadvantage and it's that the wireless adapter included in the Pi3 does not support what is called "monitor mode" that is needed for wireless hacking.

This limitation is only in the default firmware provided by the Pi Foundation as well as distributions such as Raspbian and the NOOBS installer.

To change this, we use the Nexmon firmware project, that enables among other things, support for monitor mode in the bcm43438 chipset.

Yet, it is not integrated in distributions such as Raspian, and compiling the modules is a long process, requires quite a bit of space (won't fit on an 8GB SD card), so to speed up this process I have created this ansible recipe for automating the installation of the firmware in Pi3.

## TODO

- [ ] Since compiling on a Pi is time consuming, a nice idea would be to create a Debian package with a PPA repository, that includes the bcm43438 chipset as well as the nexutil tool required for manipulating the monitor mode.
- [ ] In every tutorial available, you start by using airmon-ng that double checks that no other software is using the wireless adapter, and sets it in monitor mode. This, however is not necesary when using the nexmon firmware. So, I need to create a tutorial, plus update the class laboratories' content to reflect this.
