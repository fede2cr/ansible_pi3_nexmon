# ansible_pi3_nexmon
If you want to use a Pi3's wireless as a security tool (monitor mode)

## Description

We plan to use Raspberry Pi3 as a tool for our Computer Security courses, but they have a huge disadvantage and it's that the wireless adapter included in the Pi3 does not support what is called "monitor mode" that is needed for wireless hacking.

This limitation is only in the default firmware provided by the Pi Foundation as well as distributions such as Raspbian and the NOOBS installer.

To change this, we use the Nexmon firmware project, that enables among other things, support for monitor mode in the bcm43438 chipset.

Yet, it is not integrated in distributions such as Raspian, and compiling the modules is a long process, requires quite a bit of space (won't fit on an 8GB SD card), so to speed up this process I have created this ansible recipe for automating the installation of the firmware in Pi3.

#### Note: This will not be required in the [next version of Kali Linux for the Pi](https://github.com/offensive-security/kali-arm-build-scripts/pull/92), or you can build yourself a fresh image

## Usage

You need Ansible installed in a manage computer, and on the Raspberries you only need python2 which is installed by default.
With an editor, modify the file ```inventory/hosts``` to add any extra raspberries IP, and then do an ssh-copy-id to those raspberries.
Then run the ansible-playbook like this:

```bash
ansible-playbook pi3-nexmon-install.yml -i inventory/hosts.example -K
```
It will as you for the sudo password of all of the Raspberries, and automatically install the software and kernel modules.

## Verifying

If the Ansible recipe worked well, you should be able to run this commands and tests your wifi interface in monitor mode:
![Monitor mode verification](https://github.com/fede2cr/ansible_pi3_nexmon/blob/master/doc/img/pi3-nexmon-verify.gif "Monitor mode verification")

## TODO

- [ ] Since compiling on a Pi is time consuming, a nice idea would be to create a Debian package with a PPA repository, that includes the bcm43438 chipset as well as the nexutil tool required for manipulating the monitor mode.
- [ ] In every tutorial available, you start by using airmon-ng that double checks that no other software is using the wireless adapter, and sets it in monitor mode. This, however is not necesary when using the nexmon firmware. So, I need to create a tutorial, plus update the class laboratories' content to reflect this.
