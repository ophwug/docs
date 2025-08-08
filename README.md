# Unofficial documentation of unofficial fixes and tweaks to comma and unofficial openpilot hardware

The [comma.ai Discord][cdiscord] isn't really a good place to store _answers_ or guidance to questions about repairing and maintaining the hardware.
Discord's search is terrible, and the content inside of it isn't accessible to search engines.
This is an attempt to document some of the common issues and fixes that were discussed in the Discord onto the public internet so that they can be found by search engines.

This document is a bit long, you may want to put the URL of this document into your 🤖 AI assistant of choice, such as [ChatGPT](https://chat.openai.com/chat), [Claude](https://claude.ai/), or [Gemini](https://gemini.google.com) to ask it questions about the contents of this document.

<img width="919" height="611" alt="image" src="https://github.com/user-attachments/assets/d271abb5-52b6-4341-9dc3-738bdf973146" />

This document may also include links to other non-comma.ai Discords as well.

The format of this document is of a case-by-case basis. Please feel free to add your own cases, pull requests, and solutions.

This is not an official document and is not endorsed by comma.ai. However, it is supported by users and readers like you so please do feel free to make suggestions and submit pull requests!

Also, please do report back if the remedies work or don't work. Discord, GitHub issues, etc. **This is a living document!**

Be aware Amazon links are Amazon Affiliate links. If you buy something through them, I may get a small commission at no extra cost to you. This helps support purchasing some of the supplies, services, and tools to document these cases.

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

  - [Discords and Discussions of Note](#discords-and-discussions-of-note)
  - [General Notes](#general-notes)
  - [Preventative and Recommended Measures](#preventative-and-recommended-measures)
  - [Hardware Documentation](#hardware-documentation)
    - [Official Hardware Documentation](#official-hardware-documentation)
    - [Reverse Engineered Community Clones and Alternative Hardware Documentation](#reverse-engineered-community-clones-and-alternative-hardware-documentation)
    - [Taxonomy](#taxonomy)
      - [comma.ai Harness](#commaai-harness)
  - [Common to all comma devices](#common-to-all-comma-devices)
    - [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case)
    - [The Bad OBD-C Port Case](#the-bad-obd-c-port-case)
    - [The Bad Car Harness Case](#the-bad-car-harness-case)
    - [The Running Too Old Of An OS Case](#the-running-too-old-of-an-os-case)
  - [Common to all comma two family devices](#common-to-all-comma-two-family-devices)
    - [The Can't Proceed To Installation Because Wi-Fi Can't Connect To Internet Case On My comma two Case](#the-cant-proceed-to-installation-because-wi-fi-cant-connect-to-internet-case-on-my-comma-two-case)
  - [Common to all comma three family devices](#common-to-all-comma-three-family-devices)
    - [The Build Error On Boot Case](#the-build-error-on-boot-case)
    - [The OS is Messed Up Case](#the-os-is-messed-up-case)
    - [The Blown Fuse Case](#the-blown-fuse-case)
    - [The Screen Doesn't Work or is Dying Case](#the-screen-doesnt-work-or-is-dying-case)
    - [The Fan Death Case](#the-fan-death-case)
    - [The Poor GPS Signal Case](#the-poor-gps-signal-case)
    - [The Bad or Dead SOM Case](#the-bad-or-dead-som-case)
  - [comma three (C3)](#comma-three-c3)
    - [The Swampy No Panda Case](#the-swampy-no-panda-case)
    - [The Screen Colors Are Really Off Case](#the-screen-colors-are-really-off-case)
    - [The Burned MOSFET Case](#the-burned-mosfet-case)
    - [The Camera Malfunction Case (C3)](#the-camera-malfunction-case-c3)
    - [The NVMe drive not mounted Case](#the-nvme-drive-not-mounted-case)
  - [comma threex (C3X)](#comma-threex-c3x)
    - [The No Panda on C3X Case (Software)](#the-no-panda-on-c3x-case-software)
    - [The No Panda on C3X Case (Hardware)](#the-no-panda-on-c3x-case-hardware)
    - [The Wide Camera Malfunction Case (C3X)](#the-wide-camera-malfunction-case-c3x)
- [References](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Discords and Discussions of Note

There will be links to Discord conversations.

You must join the server with an invite linked for links to channels to work.

* [comma.ai Discord (If unmarked and a link to Discord, it will be this)](https://discord.comma.ai/)
  * [#hw-three-3x](https://discord.com/channels/469524606043160576/871838269405556736)
* [openpilot enthusiasts Discord (OPC), a degenerate community offshoot Discord](https://discord.gg/rRB7eDKccy)

This document is generally discussed here and there in [#hw-three-3x](https://discord.com/channels/469524606043160576/871838269405556736). However, you're welcome to just make issues and discuss in the [GitHub issues](https://github.com/ophwug/docs/issues) of this repository too.

## General Notes

* **Always install stock or comma openpilot first to make sure the issue is not software related as a starting point.**
  * comma.ai support will not help you if you are not running stock or comma openpilot.
  * The comma Discord (outside of #custom-forks) will only support comma openpilot.
  * If you can't install stock or comma openpilot (like for vehicle support reasons), talk in #custom-forks or visit your fork's Discord and discuss the issue.
* If your device is under warranty, [you should contact comma.ai support first.](https://comma.ai/support)
* If your C3X is out of warranty, the rough cost to repair from comma [is $500](https://comma.ai/shop/comma-3x-out-of-warranty-repair).
* [They do not repair the C3 anymore. They only offer a trade-in program for C3 to get a C3X for $750.](https://comma.ai/shop/comma-3x-trade-in)
* A lot of the information in this document is based on user experience and may not be accurate.
* Mobile Repair, Video Game hardware repair shops, PCB electronics repair places, and other similar operations may be able to help with hardware repairs. Your mileage may vary and to be honest, these devices aren't common but with specific instructions, they might be amenable to helping you out.
* Unplug and power down the device for 30 minutes before assessing if the issue is persistent.
* Even if you plan to contract out the repair, you should own a multimeter. They're so handy not just for this but also other home improvement and domestic projects.
* If you're disassembling something yourself, make sure to have a good clean workspace to keep track of all parts you take apart and to be able to put everything back together without missing pieces. This may mean screw mats and small containers.

## Preventative and Recommended Measures

You don't need to do all these things, but they may help extend the life of your device or preserve access.

The comma devices are not invincible. They follow the [bathtub curve of failure](https://en.wikipedia.org/wiki/Bathtub_curve), just like humans and everything else in life.

![Bathtub](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Bathtub_curve.svg/960px-Bathtub_curve.svg.png)

On a long enough timeline, all devices will fail.

* Have a way remove the device from the car when not in use or in high heat.
  * Stock comma hardware is not designed to be removed often as it is meant to be a permanent installation. Removing the device may cause wear to the OBD-C (USB-like) cable in particular.
  * Use a magnetic or quick-remove mount if you want to remove the device often.
    * These will help preserve the integrity of the cables and connectors.
    * [Look to comma's #hw-unofficial channel for some suggestions.](https://discord.com/channels/469524606043160576/534139378772082749)
    * There is also a specific thread under the #hw-unofficial channel for [magnetic mounts](https://discord.com/channels/469524606043160576/1130905705784803510)
* When removing the device, be careful with the OBD-C cable. In addition to being physically careful with it, hiding it, including the tip from the sun's damaging rays will also help prolong its life.
* When removing the device, be careful with the OBD-C port. It is a weak point in the design and can be damaged if you are not careful. This far harder to fix than the OBD-C cable. Look into magnetic mounts to minimize the wear on the OBD-C port.
* SSH in and backup the contents of `/persist/comma/id_rsa`.
  * https://spektor56.github.io/OpenpilotToolkit/ is an easy tool to do this.
  * More manual steps can be found at https://github.com/commaai/openpilot/wiki/SSH but the UI seems to shift around a lot. The broad strokes are the same.
  * In case you ever need to replace the System-On-Module (SOM), you can use this file to restore access to comma's servers. It is otherwise impossible to get access to the servers again without this file. **It is your license to comma's servers and [comma connect](https://connect.comma.ai). comma will never replace the license file for you if it is lost.**
  * [Newer versions of comma openpilot require this file for activation to be present in order to activate the self-driving features.](https://github.com/commaai/openpilot/commit/f4b017a75b0ba59bb1540347b101293c3db7364d) Forks can choose to not require this file though.
* Do not use magnetic cable adapters. Use purpose-built magnetic or quick release mounts as OBD-C is far more sensitive to pins connecting to the wrong thing than USB-C.

## Hardware Documentation

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

### Taxonomy

Just a small incomplete bit of small local documentation on the taxonomy of comma devices, clones, and hardware.

Please refer to their respective documentation for more details.

#### comma.ai Harness

**Harness V3 with relay box, harness cable, and comma power (Shipping since ~June 2024)**:

![Image](https://github.com/user-attachments/assets/e7fc1e9f-071b-46f7-a5db-6964a0fb4522)

**Harness V1 with Box that has physical relays (you'll hear clicks under normal operation), the harness cable, and comma power**:

![Image](https://github.com/user-attachments/assets/83a7e287-c6bc-43ab-800d-5763098b1645)

![Image](https://github.com/user-attachments/assets/6e630048-13fb-453d-9401-bf75709209c2)

![Image](https://github.com/user-attachments/assets/eab842c7-edaf-4125-b9ab-b55c82579502)

Visually and physically, the Harness V1 and V3 are very different. The Harness V3 relay box has a molded non-3D printed enclosure, the relay box itself is much smaller, the harness connector port connecting to the relay/harness box is smaller and thinner, and the comma power portion does not use a CAT6 or Ethernet cable to connect to OBD-2 port. V3 is generally smaller overall. V3 relay box is also solid state and does not have physical relays which helps resist [The Bad Car Harness Case](#the-bad-car-harness-case).

Harness V1 car harnesses are not compatible with Harness V3 and vice versa. They share the same OBD-C cable and port as an output though.

The comma two is only compatible with the Harness V1. Both Harness V1 and Harness V3 are compatible with the older comma three and newer comma threex devices. Be aware that old versions of openpilot on a comma three device may not work with the Harness V3 as they require Harness V1's comma power, so you should always use the latest openpilot version.

If you're switching vehicles or replacing parts of your car harness portion and if you're a Harness V1 user, you will need to replace the entire Harness V1 with a Harness V3 if you're buying from comma.ai's shop. This is because comma.ai does not sell Harness V1 hardware anymore. Unfortunately, they do not make this explicitly clear on their shop, so you will have to trust this document on this. If you have a more common brand, you may be able to find a Harness V1-compatible car harness from third-party vendors such as [Mr. One](https://oneclone.net/product/harness/) or [Konik.ai](https://konik.ai/shop/?v=0b3b97fa6688).

Note that the vehicle harnesses part after the relay box may look very different for certain vehicles from the pretty shots above, particularly those that intercept at a location other than the camera. They are much longer or can even look like a comma power.

Please see https://github.com/commaai/hardware/ for more details on the harnesses.

## Common to all comma devices

### The Bad OBD-C Cable Case

OBD-C is a [comma.ai standard](https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf) that uses a ODB-C cable between the comma harness box and the comma device. comma produces, ships, and sells a ODB-C cable but select and many USB-C cables are electrically and physically compatible and can be used in its place.

**Preventative Measures**:

* Use a magnetic or quick-release mount to minimize the mechanical wear of the OBD-C cable.

**Symptoms**:

* The device does not go into "on-road" mode. It is stuck at the home screen.
  * According to the [standard](https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf), the IGN line comes out as a combination of SBU1 and SBU2 and one or both isn't making its way through the OBD-C cable properly.
* You get random errors in openpilot such as, but not limited to:
  * "Car Unrecognized"
  * "CAN Bus Error"
  * "CAN Bus Disconnected"
* The cable has visible damage such as cracking.
* The cable has invisible damage such as missing wires or broken wires when viewed with a USB-C cable tester.
  * **You must test with a _simple_ USB-C cable tester for this. No exceptions.**
* **Power issues are usually not a Bad OBD-C Cable Case**, as the cable has 4 redundant pairs of lines and wires for power and ground. While of course some pairs could be broken, that cable can probably still be considered relatively good and usable. If the device is not powering on though, it is likely a [Blown Fuse Case](#the-blown-fuse-case).
  * Blown Fuse Case may not be related or is coincidental from wear due to this (See [The Blown Fuse Case](#the-blown-fuse-case) for more details)
* Car fuse is blown. While it's great there are 4 redundant pairs of lines and wires for power and ground, there is a flip side in that there is also an increased chance for these to get shorted. You'll need to use a multimeter with the pads exposed by the tester to check for crossed wires.

Check the OBD-C cable for visible and invisible damage. In the image below, `TX2+` of USB-C is `CAN2_H` in OBD-C and is broken. The cable otherwise looks fine externally.

![PXL_20250625_151254911 MP](https://github.com/user-attachments/assets/362e359f-d6f4-4b57-9d16-7e08e475b7e5)

Here is a video demonstration of damage, courtesy of Nabeel and note that Nabeel's case only manifested itself when the cable is shifted a bit and in a vehicle, that is very common:

https://www.youtube.com/watch?v=2NPTUW2f6Os

This image below, from a cable donated by adenta, has a cable that is cracking in the exterior, but all necessary wires are connected. **For diagnosis, you must test with a _simple_ USB-C cable tester.**

![PXL_20250625_062251389](https://github.com/user-attachments/assets/116f6aa9-764d-403f-a573-61fd4d73540b)

OBD-C Cable Pinout: https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf

Nearly all pins are expected to be connected. Sometimes people use a cable from their own collection but if it does not work, it is usually due to missing wires/pins. There is not much redundancy for data lines in the OBD-C cable, so if it is partially damaged or incomplete, the comma device will not work properly. The lines are also rather small and thin. USB-C is more tolerant and might even downgrade successfully, OBD-C is less tolerant and cannot.

Simple and cheap USB-C Cable Testers (no smarts, just pin testing, and heed the warnings on it to never plug it into a real device):

* https://amzn.to/40hvt5D
* https://caberqu.com/home/20-42-c2c-caberqu-746052578813.html#/26-with_or_without_case-without_case - As seen in Nabeel's video above.

**Resolution**:

* A quick and dirty solution is to flip the OBD-C cable. This might not be permanent, but it may help you get the device working again. Of course, depending on what is and how it is broken, this may not be sufficient.
* If the OBD-C cable is damaged, replace it with a new one. The OBD-C cable used for comma three devices is unique with a long angled neck so that the cable is able to plugged into the recessed port of the comma three devices. For best fit and to not obstruct the cameras, you should use a cable that is specifically designed for the comma three devices.
  * If you can't find a replacement OBD-C cable, but need one in a pinch very quickly you can use a USB 3.1 Gen 2 cable or higher (Thunderbolt 3 or 4) as a substitute. These can be found at big box stores or online.
  * It is possible to get use a set of angled adapters with existing cables: https://amzn.to/3TcV389
* If your installation of the OBD-C cable is pinched, use a USB 3.1 Gen 2 extension cable so it can be routed in a way that is not pinched under the cover.
  * https://amzn.to/4n7BZ8V
    * This one has variants
  * https://amzn.to/3ZI82lR
    * This one has an on-off switch!
* If you are removing the device often, consider using a purpose-built magnetic or quick-release mount to minimize the mechanical wear of the OBD-C cabling. See #hw-unofficial on the [comma.ai Discord](https://discord.comma.ai)
* If the cable is good from testing with a USB-C cable tester, check out [The Bad Car Harness Case](#the-bad-car-harness-case) and [The Bad OBD-C Port Case](#the-bad-obd-c-port-case) as the issue may be with the car harness.

**Vendors**:

* comma.ai: https://comma.ai/shop/obd-c-cable
  * [Their long versions of the cables for brands such as Rivian, Ford, and Tesla also use TPU instead nowadays.](https://discord.com/channels/469524606043160576/954493346250887168/1390435764772409495)
* Mr. One: https://oneclone.net/product/obd-c-cable-for-c3/
* Konik.ai's cables are physically different from comma's and Mr. One's and are specific to their hardware clones which do not have a recessed port.

**Examples**:

* [Nabeel's C3](https://discord.com/channels/469524606043160576/871838269405556736/1383173273466179727)
  * https://www.youtube.com/watch?v=2NPTUW2f6Os
* [0pointjd's C3](https://discord.com/channels/469524606043160576/524592892627517450/1330161284049535036)

### The Bad OBD-C Port Case

This case is much worse than the above and an easy and/or reliable resolution is not really available. It's documented here for completeness. If you've got the skills and have ruled out [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) and/or [The Bad Car Harness Case](#the-bad-car-harness-case), you may want to look at this, but I don't blame you if you give up here.

**Preventative Measures**:

* Use a magnetic or quick-release mount to minimize the mechanical wear of the OBD-C port.

**Symptoms**:

The symptoms are in general very similar to the [Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) but the issue is not with the cable but with the OBD-C port itself.

* The OBD-C port is physically damaged.
* You've ruled out the [Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) and [The Bad Car Harness Case](#the-bad-car-harness-case).
* The device does not go into "on-road" mode. It is stuck at the home screen.
* You get random errors in openpilot such as, but not limited to:
  * "Car Unrecognized"
  * "CAN Bus Error"
  * "CAN Bus Disconnected"

**Resolution**:

If you know how, you know how.

[Unfortunately, there seems to be an anecdote about how a reflow only buys a little bit of time.](https://discord.com/channels/469524606043160576/954493346250887168/1302002657937854556)

**Examples**:

Cases seem to be rare and follow ups haven't been said publiclly. If you have a case that you would like to add, please do so in a pull request or issue.

* C2
  * [defy's c2](https://discord.com/channels/469524606043160576/954493346250887168/1302031683284893840)
* C3
  * [minty's c3](https://discord.com/channels/469524606043160576/1121848816870641775/1124891817566023680)

**Resources**:

* USB-C/OBD-C port repair teardown part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C port repair teardown part 2: https://www.youtube.com/live/gTw_Qq8scqo

### The Bad Car Harness Case

Your comma device connects to your vehicle via a [comma.ai harness](#commaai-harness) via the OBD-C cable.

Unfortunately, the harness may go bad, especially on V1 harnesses which use physical relays in the relay box.

Please see [the local taxonomy section on the comma.ai harness](#commaai-harness) for identifying the harness you have.

**Symptoms**:

* The OBD-C cable is known to be good and/or has been recently replaced. In other words, [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) has been ruled out. Please do this first.
* You get random errors in openpilot such as, but not limited to:
  * "Car Unrecognized"
  * "CAN Bus Error"
  * "CAN Bus Disconnected"
* You hear unusual noises from the relay box or harness area. Of course, what is "unusual" can vary. Working V1 harnesses will click when the device is powered on and off, but if you hear a constant clicking or buzzing, that is not normal.

**Resolution**:

* _The below steps are a bit on the economical in hardware side, and you are welcome to just skip forward and just simply get a [complete car harness](https://comma.ai/shop/car-harness) from comma and swap it out for testing if time is of the essence. At worst, you're out the cost of shipping back the hardware (~$10 in US) if it is not the issue._
* Rule out the [Bad OBD-C Cable Case](#the-bad-obd-c-cable-case). It is easy and cheap to do.
* Identify what harness revision you have: V1 or V3.
* Using a multimeter's continuity test, check your vehicle-specific harness connector's pinout with https://github.com/commaai/hardware/tree/master/harness
  * If this is bad, repair or replace the [vehicle specific harness connector](https://comma.ai/shop/harness-connector).
* Harness V1:  After testing that the vehicle specific harness connector is good, the only current real way to test it is to purchase a [complete car harness](https://comma.ai/shop/car-harness) from comma and swap it out. You can [return](https://shop.comma.ai/a/returns) the new hardware if this is not the issue.
  * Unfortunately, comma does not sell V1 harness hardware anymore, so you will have to try/buy a complete Harness V3 car harness for this resolution.
* Harness V3: After testing that the vehicle specific harness connector is good, the only current real way to test it is to purchase a [new harness relay box](https://comma.ai/shop/harness-box) from comma and swap it out. You can [return](https://shop.comma.ai/a/returns) the new hardware if it is not the issue.
* Test the new harness with your vehicle.

Hopefully that _is_ the issue and it is resolved.

**Examples**:

- [wakywayne's C3](https://discord.com/channels/469524606043160576/871838269405556736/1397560030256955533)
  - Replaced the OBD-C cable too, but the issue persisted until the complete harness was replaced from V1 to V3.
- [Yan's C3](https://github.com/commaai/openpilot/issues/32179#issuecomment-2053766029)
  - Met up in person to replace and swap hardware. It took a lot of convincing for comma support to replace his relay box under warranty. This was a V1 harness to V1 harness replacement.
- [rattail98's C3X](https://discord.com/channels/469524606043160576/524592892627517450/1399544048879927418)
  - Throughly debugged and narrowed it down to just the V3 relay box.
  - [Replaced the V3 relay box, harness, and ODB-C cable from support and it worked.](https://discord.com/channels/469524606043160576/524592892627517450/1403142981489528993)

### The Running Too Old Of An OS Case

comma.ai will only support the latest "release", "nightly", and specific WIP branches of comma openpilot on their hardware. And those branches will cause a recent or newest OS to be installed on the device.

From time to time, comma.ai will "evolve" the hardware for reliability, supply chain, cost reduction, and other reasons. This means that the hardware may not be compatible with older versions of openpilot and the OS. In advance of this, they will update their OS and their openpilot branches to support the new hardware.

By their nature, forks, old branches, and even YouTube instructions for installing openpilot or its various forks may lag behind the latest OS and openpilot version.

Unfortunately, comma does not provide a way for installation to detect and block installation of an incompatible OS or openpilot version. Their view is that you are an advanced user and should know what you are doing. Also unfortunate is the amount of documentation and instructions that are out there that are not up to date, or can't be up to date, or how accessible YouTube videos are but are still out of date. Oh well, the world is not perfect.

**Symptoms**:

These can be very varied since by its nature, it's very undefined and this is incomplete.

* You just got your device ["repaired" by comma.ai](https://comma.ai/shop/comma-3x-out-of-warranty-repair). They actualy really just ship you a newly constructed device.
* Run a few minutes, and then the screen will freeze and then the device will reset.
  * e.g. Wi-Fi driver out of date
* The screen is completely visible and a good brightness and other times the brightness is super dark and the screen is barely visible.
  * e.g. Sensor driver out of date
* The device overheats.
  * e.g. Fan control driver out of date

**Resolution**:

You must run an openpilot codebase that installs a compatible OS.

* Uninstall by tapping the screen madly on boot and selecting "Uninstall".
* Install the latest comma openpilot.
* If you must use a fork, see the tip below.

> [!TIP]
>
> **Current Known Status of Some Popular Forks**:
>
> Last Update: July 2025
>
> This is a living document, please check in with their communities for the latest status and if you can, help update this section.
>
> * sunnypilot - Do not install `release-c3`, install `staging-c3-new`.
> * frogpilot - Should be fine. They've backported OS changes to their fork's OS.

* Be mindful of YouTube videos and instructions that are not up to date. It is impossible to update YouTube videos.
  * If you ended up here from a YouTube video, contact the author of the video and ask them to pin a comment to the top of the video with the latest instructions.
  * Videos with this issue:
    * [Comma 3X OpenPilot & SunnyPilot Install - 2024 Kia EV6 GT
](https://www.youtube.com/watch?v=YhYEYcfNL5o)
* Last but not least, for fork users, you need to consult your fork's _written_ documentation. YouTube videos or alternative instructions may not be up to date and may not work with the latest OS or openpilot version. They may still be a great supplement to the written documentation though.

**Examples**:

* [Magnetar's C3X](https://discord.com/channels/469524606043160576/524592892627517450/1398669054809608345)
   * "I've already tried to factory reset and reinstalling and everything. It'll work fine for sometimes a few seconds up to about 5 minutes. Then the screen will freeze for a few seconds and I'll get the reboot with the comma symbol "
 * [/u/Unable-Grape2361's C3X](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comma_3x_recovery_mechanism_after_overheating/)
   * "Unfortunately, the replacement unit has been plagued by overheating problems that never occurred with the original."

## Common to all comma two family devices

The comma two family is the second generation of comma's hardware, and it is based upon a modified Leeco Le Pro 3 with the battery removed, thermal solution filled in, front camera replaced with IR-filter-less variants and an integrated comma panda PCB providing supporting CAN communication, fan support, and providing supporting hardware/software hacks to trick the phone hardware such as battery emulation and bootkick.

> [!NOTE]
> If you're starting out in this community, you should get a comma three or similar device as the communities around openpilot have moved on to the comma three family of devices for ongoing support and current development.

> [!NOTE]
> Unfortunately, this section needs to be written. If you have any cases that you would like to add, please do so in a pull request or issue. For now, you'll have to search the #hw-two-eon channel on [comma's Discord](https://discord.comma.ai)

### The Can't Proceed To Installation Because Wi-Fi Can't Connect To Internet Case On My comma two Case

![Image](https://github.com/user-attachments/assets/8f1e1e07-e359-421f-b399-5c0a46b61538)

**Symptoms**:

* After setting up Wi-Fi on the comma two device, it fails to connect to the internet and its blocked from proceeding.

**Resolution**:

* Use https://github.com/ophwug/c2-neos-alt-fix-install with your computer.
* If the above does not work, follow the instructions at https://github.com/jyoung8607/neos-manual-install.

## Common to all comma three family devices

The comma three family is the third generation of comma's hardware, and it is the first generation to be designed from the ground up by comma.ai.

### The Build Error On Boot Case

**Symptoms**:

* You get some sort of build error on boot.

![Image](https://github.com/user-attachments/assets/6bd09b68-c379-4451-802b-05ad57fcf9bb)

This can happen on comma's branches or forks. Try resetting by tapping the screen madly on boot and selecting "Reset". Reinstall openpilot.

### The OS is Messed Up Case

**Symptoms**:

* The device does not seem to or gets stuck for whatever reason.
* Tapping the screen madly on boot and selecting "Reset" does not get the device back to factory state.

**Resolution**:

Reflash with https://flash.comma.ai/.

https://flash.comma.ai may not work sometimes. In that case, try using this Windows-specific and Qualcomm software alternative from Mr. One, a C3 clone maker:

https://mr-one.cn/?post=24

Archive: https://web.archive.org/web/20250520040523/https://mr-one.cn/?post=24

### The Blown Fuse Case

**Symptoms**:

* Device does not power on when connected
* Device does not stay on
* The self-resetting fuse's resistance is stuck high. (e.g. 0.5-43 ohms, when it should be about 0.02 ohms at most from the datasheet(s))
* With a heat gun applied to the fuses, the resistance gets elevated to bad levels.
* There is a large voltage drop across the fuse when powered on. (See dazoe's case below for more details.)

> [!TIP]
> **Measuring Fuse Resistance with a Multimeter**
>
> **You do NOT need to desolder the fuse for testing.** This diagnosis can be performed by anyone with basic multimeter skills.
>
> For those new to using a multimeter, here's how to check a fuse:
>
> 1.  **Set your multimeter:** Turn the dial to the resistance setting (often marked with the Omega symbol: Ω). Start with the lowest resistance range if your multimeter isn't auto-ranging.
> 2.  **Measure lead resistance:** Before testing the fuse, touch the tips of your multimeter probes firmly together. The multimeter should display a very low resistance value (e.g., 0.1-0.5 Ω). This is the internal resistance of your multimeter and leads. Note this value down.
> 3.  **Power off the device:** Ensure that the device is completely powered off and disconnected to avoid inaccurate readings or damage.
> 4.  **Measure the fuse:** Touch one probe to each end of the fuse while it is still mounted on the board (in-circuit measurement).
> 5.  **Interpret the reading:**
>     *   **Good Fuse:** The multimeter will show a very low resistance, ideally very close to the lead resistance you measured in step 2.
>     *   **Blown Fuse:** The multimeter will show a high resistance (e.g., 0.5-43 Ω) or an open circuit (OL or ∞), indicating the fuse is blown.
>
> Remember to subtract the lead resistance (from step 2) from the fuse reading for the most accurate measurement of the fuse itself.
>
> Note: These instructions may not cover all fuse issues, such as those that might fail only if temperature is elevated or under load.
> Please look at dazoe's case in the Examples section below for some details. Diagnosing dazoe's C3 was a bit more involved than just measuring the fuse resistance and required more advanced and more dangerous techniques. While this diagnosis can be performed by anyone with basic multimeter skills, actual fuse replacement may require professional help.

The component we're looking at should be able to self-reset but for whatever reason, it doesn't.

It is located near the ODB-C port and next to the SOM. In the image below, it is circled in red.

![Fuse](https://github.com/user-attachments/assets/9639cd26-faea-419a-b088-f8183c5b0a4f)

Known variants of the fuse to exist:

https://bourns.com/docs/product-datasheets/mf-nsml-x.pdf?sfvrsn=31b87ef6_12

https://www.littelfuse.com/products/fuses-overcurrent-protection/polyswitch-resettable-pptc-devices/surface-mount-polyswitch-resettable-pptc-devices/low-rho-smd/1206l350-12sl

* S12: MF-NSML350/12
* V12: MF-NSML380/12
* CT: 1206L350/12SL

There may also be other fuses like this nearby, not just that circled red one. It should have the same markings.

**Resolution**:

To fix this issue, you will need to replace the blown self-resetting fuse with a new one.

**Examples**:

* [katsu's C3 (OPC)](https://discord.com/channels/771493367246094347/771493367779295304/1368055272488308797)
* [idnot's C3](https://discord.com/channels/469524606043160576/871838269405556736/1372254806449848412)
* [Le Potatos's C3 (OPC)](https://discord.com/channels/771493367246094347/771493367779295304/1374310506088628235) - Alternatively shunted it. Note that this C3 might also have other issues such as a broken fan, necessitating shunting the fuse.
* [Nabeel's C3](https://discord.com/channels/469524606043160576/871838269405556736/1382502275460890755) - Also possibly caused by a broken ODB-C cable.
  * See [The Bad ODB-C Cable Case](#the-bad-odb-c-cable-case) for more details.
* [wferr's C3](https://discord.com/channels/469524606043160576/871838269405556736/1383249237739049080)
* [dazoe's C3 ⚠️](https://discord.com/channels/469524606043160576/871838269405556736/1382566915465150464)
  * NOTE: C3's fuse read normally when powered off but otherwise showed a huge resistance when powered on. It only showed voltage drop when powered on.
  * ⚠️ Diagnosing dazoe's C3 was a bit more involved than just measuring the fuse resistance and required more advanced techniques. Seek more knowledgeable help if you are not comfortable with the following.
  * ["My C3 was acting un-stable, when checking the fuse (just above the ODB USB-C in your picture) it wasn't until after I let the fuse "warm up" that i got a reading of 0.8-1 ohm. I also carefully measured the voltage drop across the fuse while the board was running. It wouldn't fully boot up but just idle on a screen that said "press any key to shutdown". The voltage drop was all over, ranging from 0.5-up to 2.5v which means the resistance of the fuse was changing."](https://discord.com/channels/469524606043160576/871838269405556736/1383803066536431768)
  * ["Having it powered up with out heat sink alone risks over heating. the higher risk is with power going to it one slip and you could do serious damage. It's a tight place to get probes in and with it being right next to the usb port's shield you risk shorting out the power supply. If you did add it I would put a big bold warning on it. The basic concept is to have multi meter in voltage mode, probes on each side of the fuse, when powered the voltage should stay close to 0."](https://discord.com/channels/469524606043160576/871838269405556736/1383848416626479165)
* [dimdom69's C3X (OPC)](https://discord.com/channels/771493367246094347/834826173795139584/1388357047522689045)
  * "I measured 2.0 ohms on the bad one, with the new one measuring 0.0 ohms."
  * [Also possibly caused by a broken ODB-C cable?](#the-bad-obd-c-cable-case)
* [wabash's C3, though the diagnosis and resolution was pretty unclean](https://discord.com/channels/469524606043160576/871838269405556736/1395147642581024789)
  * Err'd in removing the fuse for measuring, not knowing it is not necessary, and before measuring and instead accidentally melting the fuse.
  * Not sure if the fuse was actually blown or not.
  * Still has radar issues, so it is not clear if the fuse was the only issue.
  * Also has GPS Issues
* [chaheeto's C3](https://discord.com/channels/469524606043160576/871838269405556736/1400252232544551085)
  * Measured 1 ohms on the fuse, replaced it with a new one, and now it works.
* [/u/AlekWishes's C3X](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56u9tn/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * Related to [The Bad Or Dead SOM Case](#the-bad-or-dead-som-case)
* [/u/Crabs2336's C3X](https://www.reddit.com/r/Comma_ai/comments/1mg0miu/comment/n7bqfrk/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * Went for shunting the fuse instead of replacing it.

**Resources**:

* USB-C/OBD-C port repair teardown part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C port repair teardown part 2: https://www.youtube.com/live/gTw_Qq8scqo

**Vendors**:

Look for the fuses at trustworthy electronic vendors such as Mouser, Digi-Key, or Newark. Buy a bunch of them as shipping is the real cost.

*   S12: Bourns `MF-NSML350/12-2` - **Mouser:** https://www.mouser.com/ProductDetail/Bourns/MF-NSML350-12-2?qs=u16ybLDytRaRX65cJT5NUA%3D%3D
*   S12: Bourns `MF-NSML350/12-2` - **Digi-Key:** https://www.digikey.com/en/products/detail/bourns-inc/MF-NSML350-12-2/9859203
*   S12: Bourns `MF-NSML350/12-2` - **Newark:** https://www.newark.com/bourns/mf-nsml350-12-2/ptc-resettable-fuse-12v-1206/dp/72AC9028
*   V12: Bourns `MF-NSML380/12-2` - **Mouser:** https://www.mouser.com/ProductDetail/Bourns/MF-NSML380-12-2?qs=u16ybLDytRZuQwI5f126Qg%3D%3D
*   V12: Bourns `MF-NSML380/12-2` - **Digi-Key:** https://www.digikey.com/en/products/detail/bourns-inc/MF-NSML380-12-2/9859204
*   V12: Bourns `MF-NSML380/12-2` - **Newark:** https://www.newark.com/bourns/mf-nsml380-12-2/pptc-resettable-fuse-3-8a-12v/dp/95AC1557
*   CT: Littelfuse `1206L350/12SLWR` - **Mouser:** https://www.mouser.com/ProductDetail/Littelfuse/1206L350-12SLWR?qs=7MVldsJ5UawvCRT8CTYI7Q%3D%3D
*   CT: Littelfuse `1206L350/12SLWR` - **Digi-Key:** https://www.digikey.com/en/products/detail/littelfuse-inc/1206L350-12SLWR/12807048

### The Screen Doesn't Work or is Dying Case

**Symptoms**:

* `openpilot` still engages
* The screen does not turn on
* purple splotches on the screen

**Non-Symptoms**:

* Screen tearing - [This was/is a software issue that affects openpilot and openpilot forks for a certain period.](https://github.com/commaai/openpilot/issues?q=is%3Aissue%20state%3Aopen%20tearing) . Please update to the latest comma openpilot or openpilot fork.

![Image](https://github.com/user-attachments/assets/91e0bcc8-f625-4640-8aeb-2a227f18d523)

**Resolution**:

First, make sure to try to reseat the connection for the screen. If that does not work, you will need to replace the screen.

Konik.ai has a screen replacement guide for their devices which should be similar for the C3X: https://www.youtube.com/watch?v=ieyz4pxaHxU

The high level instruction is still the same for any device, not even just the C3/C3X. You unscrew everything and try to make sure you don't damage the cables.

* If replacing with an official comma.ai screen, make sure you take and archive the picture of the QR code sticker as it has color calibration data on it.
* Comma.ai does not sell replacement screens _with case_ for the C3. Buy a bare screen from them or a third party and have a mobile repair shop replace the existing screen.
* The replacement options with the "front case" options don't need mobile repair shop help or similar experience as it is a glue-less repair experience.
* Without "front case", "can be placed with B7000 glue onto the frame" (quote from Konik.ai).
* You may want to check out [The Screen Colors Are Really Off Case](#the-screen-colors-are-really-off-case) as well.

**Vendors**:

* comma.ai: https://comma.ai/shop/comma-device-screen
  * They sell with a front case for the C3X. C3 with front case has long been out of stock.
* Mr. One: https://oneclone.net/product/kidney-beans-organic/
* Konik.ai: https://konik.ai/shop/a1-amoled-screen/
* Find/use any panel that is for the "Huawei Mate 10 Pro". Quality will vary.
  * You can fill in the unused camera cutout with nail polish 💅.

### The Fan Death Case

**Symptoms**:

* The device overheats
* The fan makes horrible noises
* The fan does not spin

Not the Korean kind of fan death!

**Resolution**:

Comma unfortunately does not sell replacement fans by themselves. Users have been replacing them with various fans to differing success. OEM part may be from ADDA, not sure if off the shelf. Mr. One sells a replacement fan with heatsink for the C3.

**Examples**:

* [redmapleleaf's C3, Noctua](https://discord.com/channels/469524606043160576/871838269405556736/1328667993047040010)
* [Pandus's C3, Scavenged ZOTAC fan](https://discord.com/channels/469524606043160576/871838269405556736/1364305247723589734)

**Vendors**:

* Mr. One: https://oneclone.net/product/c3-heatsink-replacement-parts/
  * Replacement fan with heatsink for the C3

**Reference**:

* https://discord.com/channels/469524606043160576/871838269405556736/1350189845758218417
* comma: https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644

### The Poor GPS Signal Case

**Symptoms**:

* The device has an alert about poor GPS signal
* The device seems to not be able to locate itself well on [comma connect](https://connect.comma.ai)
* Environmental Conditions:
  * A magnetic mount is used.
  * The car's windshield is heated.

**Resolution**:

There are multiple solutions to this problem.

* Newer openpilot does not care about GPS being an alertable requirement. https://github.com/commaai/openpilot/pull/35585
  * Update to a codebase that has this change.
  * This will still result in wonky map behavior recorded in [comma connect](https://connect.comma.ai) but it will not cause an ongoing alert.
* Hardware issues:
  * Check the GPS antenna connections internally.
  * Make sure the GPS module has power connections.
* Heated windshields can cause issues with GPS reception.
  * It has not been explored, but there are GPS repeaters that can be used to help with this. Please report if you have success with this.

**Examples**:

* [Nabeel's C3](https://discord.com/channels/469524606043160576/871838269405556736/1383159801365790932)
  * "I discovered why GPS wasn't working in my C3 after my repair… This… was sitting on my desk... That's the cable that connects the GPS module to the main board."

### The Bad or Dead SOM Case

> [!WARNING]
> This section is a WIP and in construction

**Symptoms**:

* The device does not boot.
* The device does not power on.
* The fuses are good. (See [The Blown Fuse Case](#the-blown-fuse-case) for more details.)
* Over serial, the device TODO: fill in with examples of bad boot messages

**Resolution**:

> [!NOTE]
> Fill in with instructions on how to extract keys from the old SOM. https://discord.com/channels/469524606043160576/1346999805624320084/1355086750724128929

Replace the System-On-Module (SOM) with a new one.

Flash it.

**Examples**:

* [/u/AlekWishes](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56u9tn/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * Related to [The Blown Fuse Case](#the-blown-fuse-case)

**Vendor**:

* comma.ai: They do not sell their SOMs.
* Mr. One: https://oneclone.net/product/thundercomm-d845-som-4gb64/
* konik.ai: https://konik.ai/shop/thundercomm-d845-som-4gb64/
  * There is an option for an 8GB version but it is not necessary for openpilot.

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
* Cameras were changed from AR0231 to OS04C10 near the end of the C3's life cycle.

The dates and times of these changes are not well documented, but they are known to exist.

**Resources**:

* https://enjoi.dev/posts/2021-12-20-comma-3-teardown/ - Good general teardown of the comma three in written form.
* https://www.youtube.com/watch?v=Y3Z4j466CsE - Installing a SSD
* USB-C/OBD-C port repair teardown part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C port repair teardown part 2: https://www.youtube.com/live/gTw_Qq8scqo

### The Swampy No Panda Case

**Symptoms**:

* No Panda

Device was in extremely humid conditions and corrosion formed on the Panda's MCU.

![Image](https://github.com/user-attachments/assets/41717469-bcf0-4eec-88c1-a0da962cc76f)

**Resolution**:

Clean the board and remove corrosion.

**Examples**:

* [sparra215's C3](https://discord.com/channels/469524606043160576/871838269405556736/1359585271041233077)

### The Screen Colors Are Really Off Case

**Symptoms**:

* The screen has been replaced from factory.
* The colors are off. Too blue.

**Resolution**:

Take a look at this thread: https://discord.com/channels/469524606043160576/1354453342000255199

There are numerous `color_cal` files you can install onto your C3 to fix the colors. You may also have success just trying a few different ones if you don't have an official comma.ai screen replacement.

### The Burned MOSFET Case

**Symptoms**:

* The screen does not power on after being replaced.
* A burned MOSFET is visible on the board.

<img width="403" alt="Image" src="https://github.com/user-attachments/assets/d2b22aaa-6be4-45a0-900d-fe59ba6cb919" />

**Resolution**:

Replace burned MOSFET with a new one.

**Examples**:

* [A Brazilian acquaintance of Ale Sato's C3.](https://discord.com/channels/469524606043160576/871838269405556736/1359678982207045672)

### The Camera Malfunction Case (C3)

**Symptoms**:

* Camera Malfunction Message with specific camera noted.

**Resolution**:

Replace the malfunctioning camera with a new one. Make sure it matches the other cameras's type e.g. OS04C10 or AR0231. You may be able to find a broken C3 to salvage the camera from. If you can't find a specific type, you may need to replace all cameras with the same type.

Some vendors sell replacement cameras for the C3. Make sure to get the right type of camera for your C3. They may only have one type of camera available, so you may need to replace all cameras with the same type.

Note: This is not possible or very hard to do on a C3X as the cameras are soldered onto the main board. Hence, why this case is only in the C3 section.

**Examples**:

* [sparra's C3](https://discord.com/channels/469524606043160576/871838269405556736/1359555578606780608)

**Vendors**:

* Mr. One: https://oneclone.net/product/c3-cameras/
* Konik.ai: https://konik.ai/shop/c3-cameras/

### The NVMe drive not mounted Case

**Symptoms**:

* Red error message saying the NVMe drive is not mounted.

![Image](https://github.com/user-attachments/assets/17e62a61-4591-499c-9084-87fe75720980)

**Resolution**:

Reseat the NVMe drive and clean the connectors with appropriate electronic contact cleaning solution.

**Examples**:

* [mikejake's C3](https://discord.com/channels/469524606043160576/871838269405556736/1194379197712441364)

**Resources**:

* https://www.youtube.com/watch?v=Y3Z4j466CsE - Installing a SSD

## comma threex (C3X)

Released: 2023-10-12

https://blog.comma.ai/comma3X/

The comma 3X is comma's first major hardware revision of the comma three. It has gone through a major cost reduction and is now cheaper to manufacture.

* Cameras are no longer on separate boards but are now soldered onto the main board.
* The NVMe SSD has been removed in favor of 128GB of onboard eMMC storage.
* Speakers have been overhauled to be two speakers.
* It is significantly lighter.
* It uses a mount that's smaller than the comma three's mount.
* A Red Panda is now included with the device, which now includes built-in CAN-FD support.
* Camera changed to OX03C10

**Evolutions**:

* Real-Time-Clock removed and not populated, to be filled in by GPS soon after boots.
* comma switched from [off-the-shelf Thundercomm D845 SOM](https://www.thundercomm.com/product/d845-som/) to their [in-house custom LightningHard SOM.](https://fcc.report/FCC-ID/2BFC6-LIGHTNINGH)
  * [Modified PMIC to better handle thermals](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56rj4i/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
* ["No chiplet" Red Panda](https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644)
* [Different Panels that need more commands to start up in high heat](https://github.com/commaai/openpilot/issues/34971#issuecomment-2778764248)


### The No Panda on C3X Case (Software)

**Symptoms**:

* No Panda

**Resolution**:

Run through https://github.com/commaai/openpilot/issues/33016

Note: Use the `nightly` branch of openpilot. `master-ci` is not available anymore.

**Examples**:

* [Ed Moore's C3X](https://discord.com/channels/469524606043160576/1263672324973138033/1270345888950124671)

### The No Panda on C3X Case (Hardware)

**Symptoms**:

* No Panda
* The software solution at https://github.com/commaai/openpilot/issues/33016 did not work after 10+ attempts.

**Resolution**:

Have comma openpilot installed.

Remove the SOM and reseat it.

Reboot and wait.

Was it possible that the SOM might not be seated properly?

**Examples**:

* [ceem0money's C3X](https://discord.com/channels/469524606043160576/1263672324973138033/1370771997188952116)

### The Wide Camera Malfunction Case (C3X)

**Symptoms**:

* "Camera Malfunction, wideRoadCamera"
* "Camera Frame Rate Low, Reboot Your Device"

**Resolution**:

Unlike the [The Camera Malfunction Case (C3)](#the-camera-malfunction-case-c3), this is a very hard to fix issue on the C3X as the cameras are soldered onto the main board.

Your choices are limited and one of them is not great either.

* Reseat the SOM (20% chance of fixing it)
* [Hack: Disable the use of the wide camera](https://discord.com/channels/469524606043160576/871838269405556736/1399198229861634098)
  * This definitely cripples something, but it is better than nothing.

**Examples**:

* [prabh123's C3X](https://discord.com/channels/469524606043160576/871838269405556736/1399198229861634098)
  * [jyoung8607's log analysis](https://discord.com/channels/469524606043160576/871838269405556736/1398377902051164170)
    * "Took a look at your route. We do get an image from your ecamera, but only intermittently. **If and only if you can replicate this on current upstream openpilot** I would guess the actual image sensor is okay, but I suspect one of the four CSI data transfer lanes is dropping out. Your best option is probably comma's out-of-warranty flat rate repair service. There have been extremely large changes in camera support code recently, and this hypothesis is **not applicable** while running potentially outdated forks."
  * Reseating the SOM didn't work.
  * Opted for and produced the hack to disable the wide camera on sunnypilot to resolve issue. Still works.
    * "Yeah, I'm not gonna lie. It's the same on the highway. Right turns in roads are worse, but they were never any good anyway. We always use Pause Lateral on turns, so it's all good"


# References

* https://mr-one.cn/?post=24
* https://mr-one.cn/?post=25

[cdiscord]: https://discord.comma.ai/
