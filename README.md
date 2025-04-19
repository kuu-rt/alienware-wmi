# alienware-wmi backport

This is an stripped, but otherwise fairily intact, version of the upstream
[alienware-wmi](https://git.kernel.org/pub/scm/linux/kernel/git/pdx86/platform-drivers-x86.git/tree/drivers/platform/x86/dell/alienware-wmi-wmax.c?h=for-next)
driver.

Development of this driver is done exclusively on the [platform-drivers-x86](https://lore.kernel.org/platform-driver-x86/)
mailing list, which is then merged into the [platform-drivers-x86 tree](https://git.kernel.org/pub/scm/linux/kernel/git/pdx86/platform-drivers-x86.git/)
and pulled into [Linux](https://github.com/torvalds/linux) on each merge window.

This repository exists just for testing purposes and may not be updated often
(if ever).

### AWCC Features

* Thermal profiles through the Platform Profile interface
* Manual fan control and sensor monitoring through the HWMON interface

For more info check the upstream [documentation](https://docs.kernel.org/next/admin-guide/laptops/alienware-wmi.html).

## Requirements

* Linux Kernel v6.14 or later.

## How to test

1. Clone this repository
2. Unload the alienware-wmi module if it's already loaded
```
sudo rmmod alienware_wmi
```
3. Compile the source
```
make
```
4. Load the module
```
sudo insmod alienware_wmi.ko
```

In case you want to test module parameters like:

* `force_platform_profile`
* `force_hwmon`

you can pass them directly to `insmod` like this:

```
sudo insmod alienware_wmi.ko force_platform_profile=1 force_hwmon=1
```

## Issues

Bugs and problems may be reported here or in the [platform-drivers-x86](https://lore.kernel.org/platform-driver-x86)
mailing list.

## For developers

### Documentation

* [WMI device documentation](https://docs.kernel.org/next/wmi/devices/alienware-wmi.html)

### DebugFS

This driver also exposes debug information through DebugFS
`/sys/kernel/debug/alienware-wmi-A70591CE-A997-11DA-B012-B622A1EF5492/`.

### How to contribute

If you'd like to contribute, please read through the [Kernel's Submitting Patches guide](https://docs.kernel.org/process/submitting-patches.html)
first. If further guidance is required you may open an issue here or contact the
author (me) directly.
