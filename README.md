# Unofficial documentation of unofficial fixes and tweaks to comma and unofficial openpilot hardware

The [comma.ai Discord][cdiscord] isn't really a good place to store _answers_ or guidance to questions about repairing and maintaining the hardware.
Discord's search is terrible, and the content inside of it isn't accessible to search engines.
This is an attempt to document some of the common issues and fixes that were discussed in the Discord onto the public internet so that they can be found by search engines.

This may also include links to other non-comma.ai Discords as well.

The format of this document is of a case-by-case basis. Please feel free to add your own cases, pull requests, and solutions.

This is not an official document and is not endorsed by comma.ai. However, it is supported by users and readers like you so please do feel free to make suggestions and submit pull requests!

Also, please do report if the remedies work or don't work.

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Unofficial documentation of unofficial fixes and tweaks to comma and unofficial openpilot hardware](#unofficial-documentation-of-unofficial-fixes-and-tweaks-to-comma-and-unofficial-openpilot-hardware)
  - [Table of Contents](#table-of-contents)
  - [Discords of Note](#discords-of-note)
  - [General Notes](#general-notes)
  - [Preventative and Recommended Measures](#preventative-and-recommended-measures)
  - [Common to all comma devices](#common-to-all-comma-devices)
    - [Official Hardware Documentation](#official-hardware-documentation)
    - [Reverse Engineered Community Clones and Alternative Hardware Documentation](#reverse-engineered-community-clones-and-alternative-hardware-documentation)
  - [Common to all comma three family devices](#common-to-all-comma-three-family-devices)
    - [Build Error On Boot Case](#build-error-on-boot-case)
    - [The OS is Messed Up Case](#the-os-is-messed-up-case)
    - [The Blown Fuse Case](#the-blown-fuse-case)
    - [The Screen Doesn't Work or is Dying Case](#the-screen-doesnt-work-or-is-dying-case)
    - [The Fan Death Case](#the-fan-death-case)
  - [comma three (C3)](#comma-three-c3)
    - [The Swampy No Panda Case](#the-swampy-no-panda-case)
    - [The Screen Colors Are Really Off Case](#the-screen-colors-are-really-off-case)
    - [The Burned MOSFET Case](#the-burned-mosfet-case)
    - [The Camera Malfunction Case (C3)](#the-camera-malfunction-case-c3)
    - [NVMe drive not mounted](#nvme-drive-not-mounted)
  - [comma threex (C3X)](#comma-threex-c3x)
    - [The No Panda on C3X Case (Software)](#the-no-panda-on-c3x-case-software)
    - [The No Panda on C3X Case (Hardware)](#the-no-panda-on-c3x-case-hardware)
- [References](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Discords of Note

There will be links to Discord conversations.

You must join the server with an invite linked for links to channels to work.

* [comma.ai Discord (If unmarked and a link to Discord, it will be this)](https://discord.comma.ai/)
  * [#hw-three-3x](https://discord.com/channels/469524606043160576/871838269405556736)
* [openpilot enthusiasts Discord (OPC), a degenerate community offshoot Discord](https://discord.gg/rRB7eDKccy)

This document is generally discussed here and there in [#hw-three-3x](https://discord.com/channels/469524606043160576/871838269405556736). However, you're welcome to just make and discuss in the [GitHub issues](https://github.com/ophwug/docs/issues) of this repository too.

## General Notes

* If your device is under warranty, [you should contact comma.ai support first.](https://comma.ai/support)
* If your C3X is out of warranty, the rough cost to repair from comma [is $500](https://comma.ai/shop/comma-3x-out-of-warranty-repair).
* [They do not repair the C3 anymore. They only offer a trade-in program for C3 to get a C3X for $750.](https://comma.ai/shop/comma-3x-trade-in)
* A lot of the information in this document is based on user experience and may not be accurate.
* Always install stock or comma openpilot first to make sure the issue is not software related as a starting point.
* Mobile Repair, Video Game hardware repair shops, PCB electronics repair places, and other similar operations may be able to help with hardware repairs. Your mileage may vary and to be honest, these devices aren't common but with specific instructions, they might be amenable to helping you out.
* Unplug and power down the device for 30 minutes before assessing if the issue is persistent.
* Even if you plan to contract out the repair, you should own a multimeter. They're so handy not just for this but also other home improvement and domestic projects.
* If you're disassembling something yourself, make sure to have a good clean workspace to keep track of all parts you take apart and to be able to put everything back together without missing pieces. This may mean screw mats and small containers.

## Preventative and Recommended Measures

You don't need to do all these things, but they may help extend the life of your device or preserve access.

The comma devices are not invincible. They follow the [bathtub curve of failure](https://en.wikipedia.org/wiki/Bathtub_curve), just like humans.

![Bathtub](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Bathtub_curve.svg/960px-Bathtub_curve.svg.png)

On a long enough timeline, all devices will fail.

* Have a way remove the device from the car when not in use or in high heat.
  * Unfortunately, the stock comma hardware is not designed to be removed as it is meant to be a permanent installation. Removing the device may cause wear to the OBD-C (USB-like) cable in particular.
  * Use a magnetic or quick-remove mount.
    * These will help preserve the integrity of the cables and connectors.
    * [Look to comma's #hw-unofficial channel for some suggestions.](https://discord.com/channels/469524606043160576/534139378772082749)
* SSH in and backup the contents of `/persist/comma/id_rsa`.
  * In case you ever need to replace the System-On-Module (SOM), you can use this file to restore access to comma's servers. It is otherwise impossible to get access to the servers again without this file. **It is your license to comma's servers and [comma connect](https://connect.comma.ai). comma will never replace it for you if it is lost.**
* Do not use magnetic cable adapters. Use purpose-built magnetic or quick release mounts as OBD-C is far more sensitive to pins connecting to the wrong thing than USB-C.

## Common to all comma devices

### Official Hardware Documentation

comma.ai keeps public documentation of some of their hardware at https://github.com/commaai/hardware/ .

A non-exhaustive list of stuff there:

* Pinouts for harnesses
* 3D STLs for mounts
  * 3X: https://github.com/commaai/hardware/tree/master/comma_3X/mount
* [The schematic for harness box v3.](https://github.com/commaai/hardware/blob/master/harness/v3/Harness_Box.pdf)
  * Solid State Relays

### Reverse Engineered Community Clones and Alternative Hardware Documentation

This is not official documentation but they may be close enough for reference.

* https://github.com/lukasloetkolben/OpenpilotHardware
  * [Harness Box v1](https://github.com/lukasloetkolben/OpenpilotHardware/tree/main/HarnessBox)
    *  Physical Relays
  * And more!

## Common to all comma three family devices

The comma three family is the third generation of comma's hardware, and it is the first generation to be designed from the ground up by comma.ai.

### Build Error On Boot Case

**Symptoms**:

* You get some sort of build error on boot.

![Image](https://github.com/user-attachments/assets/6bd09b68-c379-4451-802b-05ad57fcf9bb)

This can happen on comma's branches or forks. Try resetting by tapping the screen madly on boot and selecting "Reset". Reinstall openpilot.

### The OS is Messed Up Case

**Symptoms**:

* The device does not seem to or gets stuck for whatever reason.
* Tapping the screen madly on boot and selecting "Reset" does not get the device back to factory state.

Reflash with https://flash.comma.ai/.

https://flash.comma.ai may not work sometimes. In that case, try using this Windows-specific and Qualcomm software alternative from Mr. One, a C3 clone maker:

https://mr-one.cn/?post=24

Archive: https://web.archive.org/web/20250520040523/https://mr-one.cn/?post=24

### The Blown Fuse Case

**Symptoms**:

* Device does not power on when connected
* Device does not stay on
* The self-resetting fuse's resistance is stuck high. (e.g. 0.5-43 ohms, when it should be about 0.02 at most from the datasheet(s))
* There is a large voltage drop across the fuse when powered on. (See dazoe's case below for more details.)

> [!TIP]
> **Measuring Fuse Resistance with a Multimeter**
>
> For those new to using a multimeter, here's how to check a fuse:
>
> 1.  **Set your multimeter:** Turn the dial to the resistance setting (often marked with the Omega symbol: Ω). Start with the lowest resistance range if your multimeter isn't auto-ranging.
> 2.  **Measure lead resistance:** Before testing the fuse, touch the tips of your multimeter probes firmly together. The multimeter should display a very low resistance value (e.g., 0.1-0.5 Ω). This is the internal resistance of your multimeter and leads. Note this value down.
> 3.  **Isolate the fuse:** Ensure that the device is completely powered off and disconnected to avoid inaccurate readings or damage.
> 4.  **Measure the fuse:** Touch one probe to each end of the fuse.
> 5.  **Interpret the reading:**
>     *   **Good Fuse:** The multimeter will show a very low resistance, ideally very close to the lead resistance you measured in step 2.
>     *   **Blown Fuse:** The multimeter will show a very high resistance, often "OL" (Over Limit), "Open," or "∞" (infinity), indicating the fuse's internal wire is broken.
>
> Remember to subtract the lead resistance (from step 2) from the fuse reading for the most accurate measurement of the fuse itself.
>
> Note: These instructions may not cover all fuse issues, such as those that might fail only if temperature is elevated or under load.
> Please look at dazoe's case in the Examples section below for some details. Diagnosing dazoe's C3 was a bit more involved than just measuring the fuse resistance and required more advanced and more dangerous techniques.

The component we're looking at should be able to self-reset but for whatever reason, it doesn't.

It is located near the ODB-C port and next to the SOM. In the image below, it is circled in red.

![Fuse](https://github.com/user-attachments/assets/9639cd26-faea-419a-b088-f8183c5b0a4f)

**Resolution**:

To fix this issue, you will need to replace the blown self-resetting fuse with a new one.

There may also be other fuses like this nearby, not just that circled red one. It should have the same markings.

**Known variants of the fuse to exist**:

https://bourns.com/docs/product-datasheets/mf-nsml-x.pdf?sfvrsn=31b87ef6_12

https://www.littelfuse.com/products/fuses-overcurrent-protection/polyswitch-resettable-pptc-devices/surface-mount-polyswitch-resettable-pptc-devices/low-rho-smd/1206l350-12sl

* S12: MF-NSML350/12
* V12: MF-NSML380/12
* CT: 1206L350/12SL

**Examples**:

* [katsu's C3 (OPC)](https://discord.com/channels/771493367246094347/771493367779295304/1368055272488308797)
* [idnot's C3](https://discord.com/channels/469524606043160576/871838269405556736/1372254806449848412)
* [Le Potatos's C3 (OPC)](https://discord.com/channels/771493367246094347/771493367779295304/1374310506088628235) - Alternatively shunted it. Note that this C3 might also have other issues such as a broken fan, necessitating shunting the fuse.
* [Nabeel's C3](https://discord.com/channels/469524606043160576/871838269405556736/1382502275460890755) - Also possibly caused by a broken ODB-C cable.
* [wferr's C3](https://discord.com/channels/469524606043160576/871838269405556736/1383249237739049080)
* [dazoe's C3 ⚠️](https://discord.com/channels/469524606043160576/871838269405556736/1382566915465150464)
  * NOTE: C3's fuse read normally when powered off but otherwise showed a huge resistance when powered on. It only showed voltage drop when powered on.
  * ⚠️ Diagnosing dazoe's C3 was a bit more involved than just measuring the fuse resistance and required more advanced techniques. Seek more knowledgeable help if you are not comfortable with the following.
  * ["My C3 was acting un-stable, when checking the fuse (just above the ODB USB-C in your picture) it wasn't until after I let the fuse "warm up" that i got a reading of 0.8-1 ohm. I also carefully measured the voltage drop across the fuse while the board was running. It wouldn't fully boot up but just idle on a screen that said "press any key to shutdown". The voltage drop was all over, ranging from 0.5-up to 2.5v which means the resistance of the fuse was changing."](https://discord.com/channels/469524606043160576/871838269405556736/1383803066536431768)
  * ["Having it powered up with out heat sink alone risks over heating. the higher risk is with power going to it one slip and you could do serious damage. It's a tight place to get probes in and with it being right next to the usb port's shield you risk shorting out the power supply. If you did add it I would put a big bold warning on it. The basic concept is to have multi meter in voltage mode, probes on each side of the fuse, when powered the voltage should stay close to 0."](https://discord.com/channels/469524606043160576/871838269405556736/1383848416626479165)

### The Screen Doesn't Work or is Dying Case

**Symptoms**:

* `openpilot` still engages
* The screen does not turn on
* purple splotches on the screen

**Non-Symptoms**:

* Screen tearing - [This is a currently a software issue.](https://github.com/commaai/openpilot/issues?q=is%3Aissue%20state%3Aopen%20tearing)

![Image](https://github.com/user-attachments/assets/91e0bcc8-f625-4640-8aeb-2a227f18d523)

Replace the Screen.

One reference: https://mr-one.cn/?post=25

* If replacing with an official comma.ai screen, make sure you take and archive the picture of the QR code sticker as it has color calibration data on it.
* Comma does not sell replacement screens for the C3. Buy a bare screen from them or a third party and have a mobile repair shop replace the existing screen.
* You may want to check out [The Screen Colors Are Really Off Case](#the-screen-colors-are-really-off-case) as well.

**Vendors**:

* comma.ai: https://comma.ai/shop/comma-device-screen

### The Fan Death Case

**Symptoms**:

* The device overheats
* The fan makes horrible noises
* The fan does not spin

Not the Korean kind of fan death!

Comma unfortunately does not sell replacement fans by themselves. Users have been replacing them with various fans to differing success. OEM part may be from ADDA, not sure if off the shelf.

**Examples**:

* [redmapleleaf's C3, Noctua](https://discord.com/channels/469524606043160576/871838269405556736/1328667993047040010)
* [Pandus's C3, Scavenged ZOTAC fan](https://discord.com/channels/469524606043160576/871838269405556736/1364305247723589734)

**Reference**:

* https://discord.com/channels/469524606043160576/871838269405556736/1350189845758218417
* comma: https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644

## comma three (C3)

Released: 2021-07-31

Discontinued: 2023-10-12

https://blog.comma.ai/comma-three-press-release/

The comma three is comma's first device designed from the ground up that isn't based upon a hacked-up cell phone.
It was relatively expensive. It was the first with three cameras.

Variants of the comma three may include no SSD but 32GB of onboard eMMC System on Module storage, 256GB of NVME SSD storage, or 1TB of NVME SSD storage.

The only OEM SSD supported is the [Samsung 980 Non-Pro SSD](https://www.amazon.com/Technology-Intelligent-Turbowrite-MZ-V8V1T0B-AM/dp/B08V83JZH4?th=1). Other SSDs may not work or have other weird unsupported issues; embedded devices are much more picky about SSDs than a desktop or laptop.

**Evolutions**:

* Early C3 had dedicated u-blox GPS module
* 32GB of onboard eMMC storage with no SSDs were introduced later
* Panda was changed from an internal USB connection to a SPI connection
* Cameras were changed from AR0231 to OS04C10

The dates and times of these changes are not well documented, but they are known to exist.

### The Swampy No Panda Case

**Symptoms**:

* No Panda

Device was in extremely humid conditions and corrosion formed on the Panda's MCU.

![Image](https://github.com/user-attachments/assets/41717469-bcf0-4eec-88c1-a0da962cc76f)

Clean the board and remove corrosion.

**Examples**:

* [sparra215's C3](https://discord.com/channels/469524606043160576/871838269405556736/1359585271041233077)

### The Screen Colors Are Really Off Case

**Symptoms**:

* The screen has been replaced from factory.
* The colors are off. Too blue.

Take a look at this thread: https://discord.com/channels/469524606043160576/1354453342000255199

There are numerous `color_cal` files you can install onto your C3 to fix the colors. You may also have success just trying a few different ones if you don't have an official comma.ai screen replacement.

### The Burned MOSFET Case

**Symptoms**:

* The screen does not power on after being replaced.
* A burned MOSFET is visible on the board.

<img width="403" alt="Image" src="https://github.com/user-attachments/assets/d2b22aaa-6be4-45a0-900d-fe59ba6cb919" />

Replace burned MOSFET with a new one.

**Examples**:

* [A Brazilian acquaintance of Ale Sato's C3.](https://discord.com/channels/469524606043160576/871838269405556736/1359678982207045672)

### The Camera Malfunction Case (C3)

**Symptoms**:

* Camera Malfunction Message with specific camera noted.

Replace the malfunctioning camera with a new one. Make sure it matches the other cameras's type e.g. OS04C10 or AR0231. You may be able to find a broken C3 to salvage the camera from.

Note: This is not possible or very hard to do on a C3X as the cameras are soldered onto the main board. Hence, why this case is only in the C3 section.

**Examples**:

* [sparra's C3](https://discord.com/channels/469524606043160576/871838269405556736/1359555578606780608)

### NVMe drive not mounted

**Symptoms**:

* Red error message saying the NVMe drive is not mounted.

![Image](https://github.com/user-attachments/assets/17e62a61-4591-499c-9084-87fe75720980)

Reseat the NVMe drive and clean the connectors with appropriate electronic contact cleaning solution.

**Examples**:

* [mikejake's C3](https://discord.com/channels/469524606043160576/871838269405556736/1194379197712441364)

## comma threex (C3X)

Released: 2023-10-12

https://blog.comma.ai/comma3X/

The comma 3X is comma's first major hardware revision of the comma three. It has gone through a major cost reduction and is now cheaper to manufacture.

* Cameras are no longer on separate boards but are now soldered onto the main board.
* The NVMe SSD has been removed in favor of 128GB of onboard eMMC storage.
* Speakers have been overhauled to be two speakers.
* It is significantly lighter.
* It uses a mount that's smaller than the comma three's mount.
* A Red Panda is now included with the device, which now includes built-in CAN-FD support. Unlike the Red Panda, it is also a "no chiplet" design.
* Camera changed to OX03C10

**Evolutions**:

* Real-Time-Clock removed and not populated, to be filled in by GPS soon after boots.
* comma switched from [off-the-shelf Thundercomm D845 SOM](https://www.thundercomm.com/product/d845-som/) to their [in-house custom LightningHard SOM.](https://fcc.report/FCC-ID/2BFC6-LIGHTNINGH)


### The No Panda on C3X Case (Software)

**Symptoms**:

* No Panda

Run through https://github.com/commaai/openpilot/issues/33016

Note: Use the `nightly` branch of openpilot. `master-ci` is not available anymore.

**Examples**:

* [Ed Moore's C3X](https://discord.com/channels/469524606043160576/1263672324973138033/1270345888950124671)

### The No Panda on C3X Case (Hardware)

**Symptoms**:

* No Panda
* The software solution at https://github.com/commaai/openpilot/issues/33016 did not work after 10 attempts.

Remove the SOM and reseat it.

Was it possible that the SOM might not be seated properly?

**Examples**:

* [ceem0money's C3X](https://discord.com/channels/469524606043160576/1263672324973138033/1370771997188952116)


# References

* https://mr-one.cn/?post=24
* https://mr-one.cn/?post=25

[cdiscord]: https://discord.comma.ai/
