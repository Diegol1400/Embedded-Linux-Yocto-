# Embedded-Linux-Yocto-

This repository contains a **local configuration (`local.conf`)** for building a custom Embedded Linux image for the **BeagleBone Black** using the **Yocto Project**.

---

## Overview

Yocto allows you to build a **custom Linux distribution** for embedded devices with only the packages and features you need.

- Target hardware: **BeagleBone Black**  
- RAM: 512 MB DDR3  
- Storage: 4 GB eMMC + SD card  
- Interfaces: HDMI, GPIO, UART, SPI, I2C, Ethernet, USB  

More info: [Yocto Project](https://www.yoctoproject.org/) | [BeagleBoard Black Specs](https://beagleboard.org/black)

---

## Repository Structure

```

Yocto/
├── conf/
│   └── local.conf      # Custom local configuration for this build
└── README.md           # This file

````

> Only the configuration is included. Other directories like `poky/` and `build/` should be cloned from official Yocto repositories.

---

## Local Configuration Highlights

- **Machine:** `beaglebone-yocto`  
- **Sources directory:** `/home/diegol1400/Projects/Yocto/sources`  
- **TMPDIR / DL_DIR / SSTATE_DIR:** Configured for shared sources and cache  
- **Distribution:** `poky`  
- **Extra image features:** `debug-tweaks`  
- **Installed packages:** `python3`, `git`  
- **Clean old images after build:** `RM_OLD_IMAGE = "1"`  
- **Inherit:** `rm_work` (cleans temporary work directories)

---

## Build Instructions

1. **Clone Poky:**
```bash
git clone git://git.yoctoproject.org/poky -b kirkstone
cd poky
````

2. **Initialize the build environment:**

```bash
source oe-init-build-env
```

3. **Copy the local configuration:**

```bash
cp /path/to/this/repo/conf/local.conf build/conf/local.conf
```

4. **Build the image:**

```bash
bitbake core-image-full-cmdline
```

5. **Resulting image location:**

```bash
cd ../sources/tmp/deploy/images/beaglebone-yocto
# Image: core-image-full-cmdline-beaglebone-yocto.wic
```
