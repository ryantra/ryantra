<!--
  HOW TO USE:
  1. Create a NEW public repo named exactly "ryantra" (same as your username).
  2. Add a README.md with the content below.
  3. GitHub automatically shows it at the top of your profile page.
  VERIFY: the LinkedIn URL below is a best guess — replace it with your real one.
-->

# Rupesh Majhi

**Embedded systems and firmware engineer.** I work close to the hardware — writing
peripheral drivers by hand from the reference manual, building real-time firmware on
microcontrollers, and developing device drivers inside the Linux kernel.

[![Email](https://img.shields.io/badge/Email-D14836?style=flat&logo=gmail&logoColor=white)](mailto:zoone.rupert@gmail.com)

## About my work

Most of my projects start from a datasheet rather than a library. I enjoy understanding
exactly what the silicon is doing — which register bit flips, when an interrupt fires,
how a task gets scheduled — and building up from there. Lately I've also been putting more
effort into testing and CI, because firmware that isn't verified isn't finished.

A few things I'm comfortable with:

- Bare-metal driver development for GPIO, SPI, I2C, and USART, written without a vendor HAL
- Real-time firmware on FreeRTOS — tasks, priorities, queues, semaphores, and ISR-safe design
- Zephyr RTOS — sensor-driver work with an upstream bug fix merged to mainline, plus devicetree and Kconfig
- Linux internals — character device drivers, kernel modules, and upstream contributions (an IIO sensor-driver bug fix + staging cleanups merged to mainline)
- IoT systems end to end, from an ESP8266 collecting sensor data to an MQTT dashboard
- Unit testing, coverage, and continuous integration

## Selected projects

| Project | What it shows |
|---|---|
| [Nucleof411xx_drivers](https://github.com/ryantra/Nucleof411xx_drivers) | STM32F411 GPIO, SPI, I2C, and USART drivers written from scratch — no vendor libraries |
| [FreeRTOS](https://github.com/ryantra/FreeRTOS) | Nine progressive RTOS labs: tasks, priorities, queues, timers, semaphores, notifications |
| [IoT-Soilless-Hydroponic-System](https://github.com/ryantra/IoT-Soilless-Hydroponic-System) | A smart-farm prototype: ESP8266 to MQTT to Raspberry Pi to a Node-RED dashboard |
| [linux_device_driver](https://github.com/ryantra/linux_device_driver) | Linux kernel modules and a character device driver with dynamic major/minor allocation |
| [Parallel-Computing](https://github.com/ryantra/Parallel-Computing) | Optimizing a physics engine with OpenMP and OpenCL — up to a 34x speedup |

## Open source

### Linux kernel

**Bug fix — IIO (pressure sensors):** `iio: pressure: dps310: fix NULL pointer dereference
on ACPI probe` — fixed a kernel crash during probe when the DPS310 is enumerated via its
ACPI HID (the i2c device-id lookup returned NULL and was dereferenced). Reviewed by the IIO
maintainers, applied to the IIO subsystem tree, and marked for stable backport.
[Patch on lore.kernel.org](https://lore.kernel.org/all/20260719000752.75936-1-zoone.rupert@gmail.com/)

**`drivers/staging` cleanups — merged to mainline:**
- [`d5c28c0`](https://github.com/torvalds/linux/commit/d5c28c0db2ef88132e4502108cac726bac1ab715) — `staging: sm750: rename CamelCase variable Bpp to bpp`
- [`e6900ce`](https://github.com/torvalds/linux/commit/e6900ce28cd312f8872ed3794b3e5e12fe911ecd) — `staging: rtl8723bs: rename shortGIrate to short_gi_rate` (rtw_ap.c)
- [`d9c2a00`](https://github.com/torvalds/linux/commit/d9c2a003912044b8adb695223c2a8ceb3b0bdf2d) — `staging: rtl8723bs: rename shortGIrate to short_gi_rate` (rtl8723b_hal_init.c)

### Zephyr RTOS

**Driver bug fix — BMI270 IMU:** `drivers: sensor: bmi270: guard any-motion against
missing feature set` — the driver silently failed to configure any-motion interrupts when
the default (max_fifo) feature set left the any-motion register pointers NULL. On Cortex-M,
address 0 is writable, so the write landed on an unintended feature page and returned false
success, leaving the trigger a no-op. The fix validates the feature set up front and returns
`-ENOTSUP` with a clear log message. Reviewed by Zephyr maintainers and merged to mainline.
[PR #114134](https://github.com/zephyrproject-rtos/zephyr/pull/114134) (fixes #112938)

**Credential:** [Zephyr Technical Contributor](https://www.credly.com/badges/86949fb0-6068-4c9b-89ab-95f6b2cfbba9/public_url) — official badge
issued by The Linux Foundation (July 2026) for code and documentation contributors to the
Zephyr Project.

- Earlier: [PR #114097](https://github.com/zephyrproject-rtos/zephyr/pull/114097) — documentation fix in the Getting Started guide.

## Tools I reach for

![C](https://img.shields.io/badge/C-00599C?style=flat&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=cplusplus&logoColor=white)
![ARM](https://img.shields.io/badge/ARM_Cortex--M-0091BD?style=flat&logo=arm&logoColor=white)
![STM32](https://img.shields.io/badge/STM32-03234B?style=flat&logo=stmicroelectronics&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![FreeRTOS](https://img.shields.io/badge/FreeRTOS-009900?style=flat&logo=freertos&logoColor=white)
![Zephyr](https://img.shields.io/badge/Zephyr_RTOS-7929D2?style=flat&logo=zephyrproject&logoColor=white)
![ESP8266](https://img.shields.io/badge/ESP8266-E7352C?style=flat&logo=espressif&logoColor=white)
![MQTT](https://img.shields.io/badge/MQTT-660066?style=flat&logo=mqtt&logoColor=white)
![Node-RED](https://img.shields.io/badge/Node--RED-8F0000?style=flat&logo=nodered&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

Domains: embedded firmware, RTOS, Linux kernel and drivers, sensor and signal I/O, IoT, and test automation.

<!--
  OPTIONAL: uncomment for GitHub stats cards.
  <p align="center">
    <img src="https://github-readme-stats.vercel.app/api?username=ryantra&show_icons=true&theme=default" height="165"/>
    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ryantra&layout=compact" height="165"/>
  </p>
-->
