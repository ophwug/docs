# Unofficial documentation of unofficial fixes and tweaks to comma and unofficial openpilot hardware

The [comma.ai Discord][cdiscord] isn't really a good place to store _answers_ or guidance to questions about repairing and maintaining the hardware.
Discord's search is terrible, and the content inside of it isn't accessible to search engines.
This is an attempt to document some of the common issues and fixes that were discussed in the Discord onto the public internet so that they can be found by search engines.

> [!TIP]
> This document is very long, clocking in at **50+** pages if printed out. You are absolutely not expected to read it all with full attention in one sitting. **Use 🤖 AI assistants to help you find the relevant sections faster.**
>
> We recommend [DeepWiki](https://deepwiki.com/ophwug/docs) as it is a good choice for querying with citations and references.
>
> * DeepWiki may lag behind the latest copy of the document by a week.
> * Consult the original sections of the document as DeepWiki may not be able to see or show images.
>
> To use DeepWiki, just go to the link below and enter your question in the chat interface:
>
> https://deepwiki.com/ophwug/docs
>
> [![demo animation of deepwiki](https://github.com/user-attachments/assets/f14e8dda-f7ca-457c-a358-3a2fc1a666ae)](https://deepwiki.com/ophwug/docs)
>
> [![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/ophwug/docs) about openpilot hardware!
>
> You are encouraged to share DeepWiki conversations links in Discord if you aren't sure it is interpreting this document correctly.
>
> Of course, other 🤖 AI assistants such as [ChatGPT](https://chat.openai.com/chat), [Claude](https://claude.ai/), or [Gemini](https://gemini.google.com) can also be used once you pass them the URL of this repository: https://github.com/ophwug/docs

> [!WARNING]
> **Always verify with original sources**: When using DeepWiki or any AI assistant, remember to check the original cited text and images in this document. AI assistants may not be able to properly interpret images or diagrams, and their understanding of visual content may be incomplete or inaccurate. They may also have biases that are incorrect within the openpilot community. Always cross-reference important information with the original source material. This is a warning that applies to all AI assistants, not just DeepWiki and not specific to this document.
>

[This document may also include links to other non-comma.ai Discords as well.](#discords-and-discussions-of-note)

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
      - [Panda](#panda)
      - [comma.ai Harness](#commaai-harness)
  - [Common to all comma devices](#common-to-all-comma-devices)
    - [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case)
    - [The Bad OBD-C Port Case](#the-bad-obd-c-port-case)
    - [The Bad Car Harness Case](#the-bad-car-harness-case)
    - [The Bad IR Blaster Case](#the-bad-ir-blaster-case)
    - [The Running Too Old Of An OS Case](#the-running-too-old-of-an-os-case)
  - [Common to all comma two family devices](#common-to-all-comma-two-family-devices)
    - [The Can't Proceed To Installation Because Wi-Fi Can't Connect To Internet Case On My comma two Case](#the-cant-proceed-to-installation-because-wi-fi-cant-connect-to-internet-case-on-my-comma-two-case)
  - [Common to all comma three family devices](#common-to-all-comma-three-family-devices)
    - [The Build Error On Boot Case](#the-build-error-on-boot-case)
    - [The OS is Messed Up Case](#the-os-is-messed-up-case)
    - [The Blown Fuse Case](#the-blown-fuse-case)
    - [The Bad Supercapacitor Case](#the-bad-supercapacitor-case)
    - [The Screen Doesn't Work or is Dying Case](#the-screen-doesnt-work-or-is-dying-case)
    - [The Fan Death Case](#the-fan-death-case)
    - [The Uncleaned Fan Flux Case](#the-uncleaned-fan-flux-case)
    - [The Poor GPS Signal Case](#the-poor-gps-signal-case)
    - [The Bad or Dead SOM Case](#the-bad-or-dead-som-case)
    - [The Damaged Ribbon Cable Case](#the-damaged-ribbon-cable-case)
    - [The SIM Card Is Stuck Case](#the-sim-card-is-stuck-case)
    - [The Stuck On Registration Case](#the-stuck-on-registration-case)
    - [The Bad EMI Filters Case](#the-bad-emi-filters-case)
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
    - [The Bad Step Down DC/DC Regulator Case](#the-bad-step-down-dcdc-regulator-case)
  - [comma four (C4)](#comma-four-c4)
- [See Also](#see-also)
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
* If your device is under return or warranty period, [you should contact comma.ai support first.](https://comma.ai/support)
  * The warranty period for new comma devices is 1 year from the date of package arrival. ([Source](https://comma.ai/shop/comma-3x))
  * [⏱️ "for anyone worried about slipping out of warranty, you’re good if the ticket was opened before the return/warranty period." - adeeb, comma staff lead](https://www.reddit.com/r/Comma_ai/comments/1nhs5ho/comment/nedq5kl/?context=3)
  * If you select the option "happens while driving" (paraphrased) when submitting a support ticket, there will be a question about providing a "route" in order to proceed with the ticket. If you follow up to step 5 of this the quick usage guide for the op-replay-clipper tool (https://github.com/nelsonjchen/op-replay-clipper), you will end up with a URL. You may skip step 4 about uploading. You can provide that URL to comma support as the "route" they are requesting. Unfortunately, comma has not fixed a long standing issue about describing what a route is or how to get one, so that tool's instructions are the best available documentation for now.
    * If you don't see anything in comma connect or cannot generate a route, just select the negative about "happens while driving" and explain instead it actually does happen while driving.
* If your C3X is out of warranty, the rough cost to repair from comma [is $500 for their C3X Out Of Warranty Repair service](https://comma.ai/shop/comma-3x-out-of-warranty-repair).
  * Unfortunately there is no warranty for the repair.
  * However, search rifkers in this doc under [The Blown Fuse Case](#the-blown-fuse-case) and apparently they were able to get an extended warranty from their Chase Sapphired Preferred card. YMMV.
* [They do not repair the C3 anymore. They only offer a trade-in program for C3 to get a C3X for $750.](https://comma.ai/shop/comma-3x-trade-in)
* A lot of the information in this document is based on user experience and may not be accurate.
* Mobile Repair, Video Game hardware repair shops, PCB electronics repair places, and other similar operations may be able to help with hardware repairs. Your mileage may vary and to be honest, these devices aren't common but with specific instructions, they might be amenable to helping you out.
* Unplug and power down the device for 30 minutes before assessing if the issue is persistent.
* Even if you plan to contract out the repair, you should own a multimeter. They're so handy not just for this but also other home improvement and domestic projects.
  * You don't need a fancy one. A simple ~$30 one from Amazon or a big box store is sufficient. Example: https://amzn.to/3IBI4LF
* Make sure the issue is not with your vehicle. Disconnect and reconnect all vehicle connectors back to stock to make sure your vehicle is still operating properly.
* If you're disassembling something yourself, make sure to have a good clean workspace to keep track of all parts you take apart and to be able to put everything back together without missing pieces. This may mean screw mats and small containers.
* It is important to diagnose the issue properly before attempting any repairs. Attempting to repair the wrong component may lead to further damage.

## Preventative and Recommended Measures

You don't need to do all these things, but they may help extend the life of your device or preserve access.

The comma devices are not invincible. They follow the [bathtub curve of failure](https://en.wikipedia.org/wiki/Bathtub_curve), just like humans and everything else in life.

![Bathtub curve diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Bathtub_curve.svg/960px-Bathtub_curve.svg.png)

On a long enough timeline, all devices will fail.

* Have a way remove the device from the car when not in use or in high heat.
  * Stock comma hardware is not designed to be removed often as it is meant to be a permanent installation. Removing the device may cause wear to the OBD-C (USB-like) cable in particular.
  * Use a magnetic or quick-remove mount if you want to remove the device often.
    * These will help preserve the integrity of the cables and connectors.
    * [Look to comma's #hw-unofficial channel for some suggestions.](https://discord.com/channels/469524606043160576/534139378772082749)
    * There is also a specific thread under the #hw-unofficial channel for [magnetic mounts](https://discord.com/channels/469524606043160576/1130905705784803510)
    * Use a silicone case to protect the device from bumps and scratches.
      * [Soft Silicone Case (Only for Openpilot Comma3X) – Janka's Workshop](https://janquick.com/products/soft-silicone-case-only-for-c3x)
* When removing the device, be careful with the OBD-C cable. In addition to being physically careful with it, hiding it, including the tip from the sun's damaging rays will also help prolong its life.
* When removing the device, be careful with the OBD-C port. It is a weak point in the design and can be damaged if you are not careful. This far harder to fix than the OBD-C cable. Look into magnetic mounts to minimize the wear on the OBD-C port.
* SSH in and backup the contents of `/persist/comma/id_rsa` on a genuine comma device.
  * https://spektor56.github.io/OpenpilotToolkit/ is an easy tool to do this.
  * More manual steps can be found at https://github.com/commaai/openpilot/wiki/SSH but the UI seems to shift around a lot. The broad strokes are the same.
  * In case you ever need to replace the System-On-Module (SOM) — the main processing unit containing the CPU, memory, and other essential components — you can use this file to restore access to comma's servers. It is otherwise impossible to get access to the servers again without this file. **It is your license to comma's servers and [comma connect](https://connect.comma.ai). comma will never replace the license file for you if it is lost.**
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

#### Panda

The panda is the CAN interface that a computer can use to talk to the car, while the harness is the vehicle interface. Sometimes people mistake the comma harness for the panda, but they are different things. On the comma two and newer devices, the panda is integrated into the device itself. The exception is the external [red panda](https://comma.ai/shop/panda), which is used with the comma three on CAN-FD vehicles.

It's called that because the [original panda dongle or adapter was black and white.](https://techcrunch.com/2017/07/07/comma-ai-launches-an-88-universal-car-interface-called-panda/)

#### comma.ai Harness

**Harness V3 with relay box, harness cable, and comma power (Shipping since ~June 2024)**:

![Image](https://github.com/user-attachments/assets/e7fc1e9f-071b-46f7-a5db-6964a0fb4522)

**Harness V1 with Box that has physical relays (you'll hear clicks under normal operation), the harness cable, and comma power**:

![Image](https://github.com/user-attachments/assets/83a7e287-c6bc-43ab-800d-5763098b1645)

![Image](https://github.com/user-attachments/assets/6e630048-13fb-453d-9401-bf75709209c2)

![Image](https://github.com/user-attachments/assets/eab842c7-edaf-4125-b9ab-b55c82579502)

Plus a flat CAT6 7ft cable. https://www.monoprice.com/product?p_id=43077

Visually and physically, the Harness V1 and V3 are very different. The Harness V3 relay box has a molded non-3D printed enclosure, the relay box itself is much smaller, the harness connector port connecting to the relay/harness box is smaller and thinner, and the comma power portion does not use a CAT6 or Ethernet cable to connect to OBD-2 port. V3 is generally smaller overall. V3 relay box is also solid state and does not have physical relays which helps resist [The Bad Car Harness Case](#the-bad-car-harness-case).

Harness V1 car harnesses are not compatible with Harness V3 and vice versa. They share the same OBD-C cable and port as an output though.

The comma two is only compatible with the Harness V1. Both Harness V1 and Harness V3 are compatible with the older comma three and newer comma threex devices. Be aware that old versions of openpilot on a comma three device may not work with the Harness V3 as they require Harness V1's comma power, so you should always use the latest openpilot version.

If you're switching vehicles or replacing parts of your car harness portion and if you're a Harness V1 user, you will need to replace the entire Harness V1 with a Harness V3 if you're buying from comma.ai's shop. This is because comma.ai does not sell Harness V1 hardware anymore. Unfortunately, they do not make this explicitly clear on their shop, so you will have to trust this document on this. If you have a more common brand, you may be able to find a Harness V1-compatible car harness from third-party vendors such as [Mr. One](https://oneclone.net/product/harness/) or [Konik.ai](https://konik.ai/shop/?v=0b3b97fa6688).

> [!WARNING]
> **Mr. One harnesses may differ from stock comma.ai V1 harnesses in their wiring:**
>
> Some Mr. One harnesses, particularly the Mazda variant, use the IGN line for 12V power instead of following the stock V1 wiring scheme. This causes the harness box to continuously send power to the LKAS camera regardless of the vehicle's ignition state, which can drain your car's battery when parked.
>
> If you're using a Mr. One harness and experience this issue, you'll need to rewire the harness to match the stock V1 wiring. While this is a relatively straightforward fix for those with electrical experience, it may not be immediately obvious to users unfamiliar with harness wiring differences.

Note that the vehicle harnesses part after the relay box may look very different for certain vehicles from the pretty shots above, particularly those that intercept at a location other than the camera. They are much longer or can even look like a comma power.

Please see https://github.com/commaai/hardware/ for more details on the harnesses.

## Common to all comma devices

### The Bad OBD-C Cable Case

OBD-C is a [comma.ai standard](https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf) that uses a OBD-C cable between the comma harness box and the comma device. comma produces, ships, and sells a OBD-C cable but select and many USB-C cables are electrically and physically compatible and can be used in its place.

**Preventative Measures**:

* Use a magnetic or quick-release mount to minimize the mechanical wear of the OBD-C cable.

**Symptoms**:

* The device does not go into "[on-road]" mode. It is stuck at the home screen.

   * According to the [standard](https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf), the IGN line comes out as a combination of SBU1 and SBU2 and one or both isn't making its way through the OBD-C cable properly.
* You substituted a random USB-C cable from your cable collection that isn't USB 3.1 Gen 2 instead of using comma's cable (e.g., because the original cable was missing or broken) and the device shows "Vehicle Online" but never transitions to "[on-road]" mode.
* You get random errors in openpilot such as, but not limited to:
  * "Harness Relay Malfunction"
  * "Check Hardware"
  * "Car Unrecognized"
  * "CAN Bus Error"
  * "CAN Bus Disconnected"
* The cable has visible damage such as cracking.
* The cable has invisible damage such as missing wires or broken wires when viewed with a USB-C cable tester.
  * **You must test with a _simple_ USB-C cable tester for this. No exceptions.**
  * If you have access to Amazon, a simple USB-C cable tester will ship and arrive quicker than comma support will answer. Get it now if you don't have one. https://amzn.to/40hvt5D
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
  * If you have access to Amazon, a simple USB-C cable tester will ship and arrive quicker than comma support will answer. Get it now if you don't have one.
* https://caberqu.com/home/20-42-c2c-caberqu-746052578813.html#/26-with_or_without_case-without_case - As seen in Nabeel's video above.

**Resolution**:

* A quick and dirty solution is to flip the OBD-C cable. This might not be permanent, but it may help you get the device working again. Of course, depending on what is and how it is broken, this may not be sufficient.
* If the OBD-C cable is damaged, replace it with a new one. The OBD-C cable used for comma three devices is unique with a long angled neck so that the cable is able to plugged into the recessed port of the comma three devices. For best fit and to not obstruct the cameras, you should use a cable that is specifically designed for the comma three devices.
  * If you can't find a replacement OBD-C cable, but need one in a pinch very quickly you can use a USB 3.1 Gen 2 cable or higher (Thunderbolt 3 or 4) as a substitute. These can be found at big box stores or online. They do not have an angled neck so order one from comma or Mr. One in the meantime.
    * Best Buy: https://www.bestbuy.com/product/insignia-3-3-usb-c-to-usb-c-3-2-gen-2-superspeed-10gbps-cable-black/J2FPJKSZGR - Best Buy's store brand, Insignia, is a good option if you need to pick one up in-store immediately.
    * Wal-Mart: Unfortunately, they do not seem to stock compatible cables in-store.
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
* Konik.ai: https://konik.ai/shop/usb-c-cable/ - Konik.ai's cables are physically different from comma's and Mr. One's and are specific to their hardware clones which do not have a recessed port. However, they're nothing special underneath, so consider getting something compatible from Amazon or locally.

**Examples**:

* [Nabeel's C3](https://discord.com/channels/469524606043160576/871838269405556736/1383173273466179727)
  * https://www.youtube.com/watch?v=2NPTUW2f6Os
* [0pointjd's C3](https://discord.com/channels/469524606043160576/524592892627517450/1330161284049535036)
* [thinkpad4by3's C3](https://discord.com/channels/469524606043160576/871838269405556736/1419877307807699017)
  * Ground pin/wire was disconnected. Wiggling the cable would make it work temporarily. See related entry in [The Blown Fuse Case](#the-blown-fuse-case).
* [johntthesmith's C3](https://discord.com/channels/469524606043160576/871838269405556736/1433136778721628261)
  * Went all the way to replacing the harness but should have tested the cable first.

### The Bad OBD-C Port Case

This case is much worse than the above and an easy and/or reliable resolution is not really available. It's documented here for completeness. If you've got the skills and have ruled out [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) and/or [The Bad Car Harness Case](#the-bad-car-harness-case), you may want to look at this, but I don't blame you if you give up here.

**Preventative Measures**:

* Use a magnetic or quick-release mount to minimize the mechanical wear of the OBD-C port.

**Symptoms**:

The symptoms are in general very similar to the [Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) but the issue is not with the cable but with the OBD-C port itself.

* The OBD-C port is physically damaged.
* You've ruled out the [Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) and [The Bad Car Harness Case](#the-bad-car-harness-case).
* The device does not go into "[on-road]" mode. It is stuck at the home screen.
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

* The device does not power on.
* The OBD-C cable is known to be good and/or has been recently replaced. In other words, [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) has been ruled out. Please do this first.
* You get random errors in openpilot such as, but not limited to:
  * "Car Unrecognized"
  * "CAN Bus Error"
  * "CAN Bus Disconnected"
  * "Harness Relay Malfunction"
  * "Check Hardware"
* You hear unusual noises from the relay box or harness area. Of course, what is "unusual" can vary. Working V1 harnesses will click when the device is powered on and off, but if you hear a constant clicking or buzzing, that is not normal.

**Resolution**:

* _The below steps are a bit on the economical in hardware side, and you are welcome to just skip forward and just simply get a [complete car harness](https://comma.ai/shop/car-harness) from comma and swap it out for testing if time is of the essence. At worst, you're out the cost of shipping back the hardware (~$10 in US) if it is not the issue._
* Rule out the [Bad OBD-C Cable Case](#the-bad-obd-c-cable-case). It is easy and cheap to do.
* Check the car's own fuses. A blown fuse in the car can prevent the comma device from powering up.
* Identify what harness revision you have: V1 or V3.
* Using a multimeter's continuity test, check your vehicle-specific harness connector's pinout with https://github.com/commaai/hardware/tree/master/harness
  * If this is bad, repair or replace the [vehicle specific harness connector](https://comma.ai/shop/harness-connector).
* Harness V1:  After testing that the vehicle specific harness connector is good, the only current real way to test it is to purchase a [complete car harness](https://comma.ai/shop/car-harness) from comma and swap it out. You can [return](https://shop.comma.ai/a/returns) the new hardware if this is not the issue.
  * Unfortunately, comma does not sell V1 harness hardware anymore, so you will have to try/buy a complete Harness V3 car harness for this resolution.
* Harness V3: After testing that the vehicle specific harness connector is good, the only current real way to test it is to purchase a [new harness relay box](https://comma.ai/shop/harness-box) from comma and swap it out. You can [return](https://shop.comma.ai/a/returns) the new hardware if it is not the issue.
  * In some cases, like rattail98's, the issue may be a failed resistor inside the harness box itself, which can be replaced by those with electronics repair skills. See [the schematic for harness box v3](https://github.com/commaai/hardware/blob/master/harness/v3/Harness_Box.pdf) for more details.
* Test the new harness with your vehicle.

Hopefully that _is_ the issue and it is resolved.

**Examples**:

- [wakywayne's C3](https://discord.com/channels/469524606043160576/871838269405556736/1397560030256955533)
  - Replaced the OBD-C cable too, but the issue persisted until the complete harness was replaced from V1 to V3.
- [Yan's C3](https://github.com/commaai/openpilot/issues/32179#issuecomment-2053766029)
  - Met up in person to replace and swap hardware. It took a lot of convincing for comma support to replace his relay box under warranty. This was a V1 harness to V1 harness replacement.
- [rattail98's C3X](https://discord.com/channels/469524606043160576/524592892627517450/1399544048879927418)
  - Thoroughly debugged and narrowed it down to just the V3 relay box.
  - [Initially replaced the V3 relay box, harness, and OBD-C cable from support](https://discord.com/channels/469524606043160576/524592892627517450/1403142981489528993), but [the issue persisted](https://discord.com/channels/469524606043160576/524592892627517450/1403416357004906701).
  - [After further debugging and replacing the OBD-C cable and Subaru A harness](https://discord.com/channels/469524606043160576/524592892627517450/1415049990870405140), the issue was narrowed down to the harness box.
  - Upon inspection of the harness box, resistor R4 was found to have failed and was not showing continuity.
  - The failed 1k ohm resistor was replaced with a 2.2k ohm resistor to prevent future failures. This resolved the issue.
  - It is suspected that voltage spikes on the IGN line may have caused the resistor to fail, possibly due to prior front-end damage and repair on the vehicle.
  - The harness box is secured by a single screw hidden under the adhesive.

### The Bad IR Blaster Case

**Symptoms**:

* The device yells at you to pay attention after dusk.
* An under or unfiltered phone camera shows the IR blasters are not working.

**Resolution**:

This is a workaround, not a fix. A proper fix would be to repair the IR LEDs which is a TODO with regards to details for this section.

* Buy a security camera IR blaster and mount it on your steering column.
 * Example: https://amzn.to/3WomsWm
* Power it with a 12-volt adapter plugged into your car's 12-volt system.

**Examples**:

* [Ry's C3X](https://discord.com/channels/469524606043160576/905950538816978974/1431553007555711101)

### The Running Too Old Of An OS Case

comma.ai will only support the latest "release", "nightly", and specific WIP branches of comma openpilot on their hardware. And those branches will cause a recent or newest OS to be installed on the device.

From time to in time, comma.ai will "evolve" the hardware for reliability, supply chain, cost reduction, and other reasons. This means that the hardware may not be compatible with older versions of openpilot and the OS. In advance of this, they will update their OS and their openpilot branches to support the new hardware. See the "Evolutions" sections under [comma three (C3)](#comma-three-c3) and [comma threex (C3X)](#comma-threex-c3x) for more details on hardware changes that may require a newer OS.

By their nature, forks, old branches, and even YouTube instructions for installing openpilot or its various forks may lag behind the latest OS and openpilot version for their base.

Unfortunately, comma does not provide a way for installation to detect and block installation of an incompatible OS or openpilot version. Their view is that you are an advanced user and should know what you are doing if you stray away from their release and nightly branches. Also unfortunate is the amount of documentation and instructions that are out there that are not up to date, or can't be up to date, or how accessible YouTube videos are but are still out of date. Oh well, the world is not perfect.

**Symptoms**:

These can be very varied since by its nature, it's very undefined and this is incomplete.

* You just got your device ["repaired" by comma.ai](https://comma.ai/shop/comma-3x-out-of-warranty-repair). They actualy really just ship you a newly constructed device.
* Run a few minutes, and then the screen will freeze and then the device will reset.
  * e.g. Wi-Fi driver out of date
* The screen is completely visible and a good brightness and other times the brightness is super dark and the screen is barely visible.
  * e.g. Sensor driver out of date
* The device overheats.
  * e.g. Fan control driver out of date
* Most distributions of openpilot or openpilot forks usually auto-update. That said, old openpilot with an old OS on older hardware revisions that are the result of auto-update not working somehow or disabled usually do not falter but you may still want to update for a fix.

**Resolution**:

You must run an openpilot codebase that installs a compatible OS.

* Uninstall by tapping the screen madly on boot and selecting "Uninstall".
* If you can't do that, go through [The OS is Messed Up Case](#the-os-is-messed-up-case).
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
> If you're starting out in this community, you should get a comma threex or similar device as the communities around openpilot have moved on to the comma threex family of devices for ongoing support and current development.

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

**Resolution**:

This can happen on comma's branches or forks. Try resetting by tapping the screen madly on boot and selecting "Reset". Reinstall openpilot.

### The OS is Messed Up Case

**Symptoms**:

* The device does not seem to boot or gets stuck for whatever reason.
* Tapping the screen madly on boot and selecting "Reset" does not get the device back to factory state.

**Resolution**:

Reflash with https://flash.comma.ai/.

https://flash.comma.ai may not work sometimes. In that case, try using this Windows-specific and Qualcomm software alternative from Mr. One, a C3 clone maker:

https://mr-one.cn/?post=24

Archive: https://web.archive.org/web/20250520040523/https://mr-one.cn/?post=24

### The Blown Fuse Case

_Blown Fuse Case may be a bit of a misnomer as the fuse should be self-resetting, but it may fail to reset properly or behaves unexpectedly. The name is kept this for historical, linking, and archival reasons._

**Symptoms**:

> [!IMPORTANT]
> Before assuming a blown fuse, it is crucial to check for other **signs of life**. A device with a dead screen can often be mistaken for a device that won't power on. See [The Screen Doesn't Work or is Dying Case](#the-screen-doesnt-work-or-is-dying-case) for symptoms to check for, such as fan noise, blinking lights, or the device engaging.

* Device does not power on when connected
* Device does not stay on
* The self-resetting fuse's resistance is stuck high. (e.g. 0.3-43 ohms, when it should be about 0.02 ohms at most from the datasheet(s)). Note that 0.3 ohms is just a value seen in some problematic devices; technically, anything above 0.02 ohms is out of spec.
* With a heat gun applied to the fuses, the resistance gets elevated to bad levels.
* (V1 harness) relay box sounds like a maraca when shaken on failed boot.
* There is a large voltage drop across the fuse when powered on. (See dazoe's case below for more details.)
* Blue light in the back may still blink.
* Flashing with https://flash.comma.ai sometimes fails with connection lost screen.

**Causes**:

* We're not exactly sure why this happens, but the hardware generally has components that aren't exactly within spec for automotive use cases.
* We do know that the hardware in enviroments like a car, can run at temperatures much higher than the specified operating temperature of the fuse from the datasheet(s). 85C vs 125C in a vehicle exposed to the sun directly. This may cause the fuse to degrade over time and eventually fail.
* We also know that vehicles typically run at 14+ volts on their 12-volt systems, which is higher than the 12V max rating of the fuse from the datasheet(s). This may also cause the fuse to degrade over time and eventually fail.
  * [converstation with Le_Potato, someone who is involved with OEM automotive electronics design. (OPC)](https://discord.com/channels/771493367246094347/771493367779295304/1425279455609360487)
* In the resolution section below, we specify the OEM fuses to replace blown fuses. It is an unknown mystery if you can use automotive-grade fuses instead of the OEM ones. A solder blob does not count 😂. If you do try this, please report back your findings to the community.

**Diagnosis**:

The component we're looking at should be able to self-reset but for whatever reason, it doesn't.

It is located near the OBD-C port and under the SOM (System-On-Module) board — the main processing unit of the device. It may not be immediately visible until you remove the heatsink which you will need to do.

In the image below, it is circled in green. There are other colored circled components nearby which may be other fuses which may or may not be present in the revision of the hardware you have.

C3:

![Blown Fuse circled in green near OBD-C port and SOM, underneath the heatsink that is to be removed. (C3)](https://github.com/user-attachments/assets/af59106f-57d4-4c3f-b993-2731b1ee6e0d)

[Image is courtesy of posterduck on Discord.](https://discord.com/channels/469524606043160576/871838269405556736/1408484686044598505)

C3X:

![Blown Fuse circled in green near OBD-C port and SOM, underneath the heatsink that is to be removed. (C3X)](https://github.com/user-attachments/assets/20ae0654-c34f-4268-a953-cf72975209f4)

[Image is courtesy of zum114 on Discord.](https://discord.com/channels/469524606043160576/871838269405556736/1426460252383215658)

Known variants of the fuse to exist:

* [S12: MF-NSML350/12](https://bourns.com/docs/product-datasheets/mf-nsml-x.pdf?sfvrsn=31b87ef6_12)
* [V12: MF-NSML380/12](https://bourns.com/docs/product-datasheets/mf-nsml-x.pdf?sfvrsn=31b87ef6_12)
* [CT: 1206L350/12SL](https://www.littelfuse.com/products/fuses-overcurrent-protection/polyswitch-resettable-pptc-devices/surface-mount-polyswitch-resettable-pptc-devices/low-rho-smd/1206l350-12sl)

There may also be other fuses like this nearby, not just that circled green one such as the blue and red ones. You can replace those too if you'll like but that really only the green one probably needs to be replaced. The rest should probably left as-is though one is welcome to measure those too.

If the fuses test good, but you have a short and a C3X, see [The Bad Step Down DC/DC Regulator Case](#the-bad-step-down-dcdc-regulator-case).


> [!WARNING]
> A visual inspection of the fuse is not sufficient for diagnosis. You must use a multimeter to measure the resistance of the fuse to determine if it is blown.

> [!TIP]
> **Measuring Fuse Resistance with a Multimeter**
>
> **You do NOT need to desolder the fuse for testing.** This diagnosis can be performed by anyone with basic multimeter skills. You do need to open up and disassemble the device to access the fuse, though.
>
> For those new to using a multimeter, here's how to check a fuse:
>
> 1.  **Set your multimeter:** Turn the dial to the resistance setting (often marked with the Omega symbol: Ω). **It is critical to select the lowest possible resistance range (e.g., 200 Ω) to measure the small decimal values of a good fuse.** If your multimeter is not auto-ranging and the range is set too high, you may see a reading of "0" even on a good fuse.
> 2.  **Measure lead resistance:** Before testing the fuse, touch the tips of your multimeter probes firmly together. The multimeter should display a very low resistance value (e.g., 0.1-0.5 Ω). This is the internal resistance of your multimeter and leads. Note this value down.  Most multimeters will beep when you do this.
> 3.  **Warm up the device first:** Before testing, plug the device in and let it run for a minute or two to "warm up" the fuse. **This is important because some fuses can read as "normal" when cold but will show their true faulty state after warming up.** After warming up, proceed to the next step.
> 4.  **Power off the device:** Ensure that the device is completely powered off and disconnected to avoid inaccurate readings or damage.
> 5.  **Measure the fuse:** Touch one probe to each end of the fuse while it is still mounted on the board (in-circuit measurement).
> 6.  **Interpret the reading:**
>     *   **Good Fuse:** The multimeter will show a very low resistance, ideally very close to the lead resistance you measured in step 2. If your multimeter beeped in step 2, it should also beep now.
>     *   **Blown Fuse:** The multimeter will show a high resistance (e.g., 0.3-43 Ω) or an open circuit (OL or ∞), indicating the fuse is blown.
> 7.  **Measure the new fuse:** Before disassembling the device and replacing the fuse, measure the new one to make sure it works.
>
> Remember to subtract the lead resistance (from step 2) from the fuse reading for the most accurate measurement of the fuse itself.
>
> **Advanced Diagnosis Notes:** These instructions may not cover all fuse issues, such as those that might fail only if temperature is elevated or under load. Please look at dazoe's case in the Examples section below for some details. Diagnosing dazoe's C3 was a bit more involved than just measuring the fuse resistance and required more advanced and more dangerous techniques. While this diagnosis can be performed by anyone with basic multimeter skills, actual fuse replacement may require professional help, but can be done in a couple hours DIY with some electronics experience and the correct tools (see below).

**Resolution**:

To fix this issue, you will need to replace the blown self-resetting fuse with a new one. You can contact a repair service or attempt a DIY repair if you have the necessary skills and tools.

**Repair Services**:

* Drago
  * Services:
    * $99 for fuse replacement
    * $30 diagnostic fee + shipping, if unsure if fuse is blown
  * * Contact via Direct message link on Discord (Preferred): https://discord.com/channels/@me/1412275471479209984
  * Contact via Discord DM: `awuf`
* Somebody local who can do board level repair can follow the instructions in **DIY Repair** below. YMMV on cost.

**DIY Repair**:

If you're comfortable with soldering, you can replace the fuse yourself.

Look for replacement fuses at trustworthy electronic vendors such as Mouser, Digi-Key, or Newark. Buy a bunch of them as shipping is the real cost.

*   S12: Bourns `MF-NSML350/12-2` - **Mouser:** https://www.mouser.com/ProductDetail/Bourns/MF-NSML350-12-2?qs=u16ybLDytRaRX65cJT5NUA%3D%3D
*   S12: Bourns `MF-NSML350/12-2` - **Digi-Key:** https://www.digikey.com/en/products/detail/bourns-inc/MF-NSML350-12-2/9859203
*   S12: Bourns `MF-NSML350/12-2` - **Newark:** https://www.newark.com/bourns/mf-nsml350-12-2/ptc-resettable-fuse-12v-1206/dp/72AC9028
*   V12: Bourns `MF-NSML380/12-2` - **Mouser:** https://www.mouser.com/ProductDetail/Bourns/MF-NSML380-12-2?qs=u16ybLDytRZuQwI5f126Qg%3D%3D
*   V12: Bourns `MF-NSML380/12-2` - **Digi-Key:** https://www.digikey.com/en/products/detail/bourns-inc/MF-NSML380-12-2/9859204
*   V12: Bourns `MF-NSML380/12-2` - **Newark:** https://www.newark.com/bourns/mf-nsml380-12-2/pptc-resettable-fuse-3-8a-12v/dp/95AC1557
*   CT: Littelfuse `1206L350/12SLWR` - **Mouser:** https://www.mouser.com/ProductDetail/Littelfuse/1206L350-12SLWR?qs=7MVldsJ5UawvCRT8CTYI7Q%3D%3D
*   CT: Littelfuse `1206L350/12SLWR` - **Digi-Key:** https://www.digikey.com/en/products/detail/littelfuse-inc/1206L350-12SLWR/12807048


**Required Tools:**
- Multimeter to read resistance
- 1.3mm and 1.5mm allen bits/keys
- Soldering iron (with very fine tip) + leaded solder
- Desoldering wick (with flux)
- Fine-point tweezers
- Possibly small cutters if the old fuse doesn't come off easily
- At least two replacement fuses (for when you destroy the first). See the Vendors section below.

**Step 1: Disassembly**

> [!TIP]
> **Take photos at every step!** Before disconnecting anything, take clear photos of how connectors are positioned, where wires are routed, and the overall layout. These reference photos will be invaluable during reassembly to ensure everything goes back exactly where it belongs.

1. **Remove connectors for easier access:** Unplug the GPS antenna U.FL connector, GPS JST connector, fan plug, and the other U.FL connector under the heat sink to completely remove the heat sink. This makes everything much easier to access. They should all re-connect pretty easily.

2. **Handle screws carefully:** Be careful with the 1.3mm hex screws for the GPS mount. Use a bit of pressure to properly seat the screwdriver bit before unscrewing to avoid stripping. Apply firm downward pressure while turning.

3. **Remove heat sink:** Once all connectors are unplugged, the heat sink can be fully removed for better access to the fuse area.

**Step 2: Fuse Replacement**

> [!WARNING]
> **Handle replacement fuses carefully:** If using tweezers to seat the fuse, don't push too hard - they crush pretty easily.

1. **Prepare for desoldering:** **Desoldering wick with flux is a must-have tool.** Add a small bit of fresh solder to each side of the old fuse first, then wick it off. This helps with heat transfer and removal.

2. **Remove old fuse:** Even with proper preparation, the old fuse may not come off very easily. In some cases, the top half comes off first, requiring you to carefully scrape the bottom part off with small snips or cutters.

3. **Clean the pads:** Make sure to add a small amount of solder to the pads once the old fuse is completely removed (just enough to tin them, not a blob), and ensure all remnants of the old fuse are gone. This makes soldering the new fuse much easier.

4. **Install new fuse:** Carefully position the new fuse and solder in place. If pressing down on the fuse to hold it in place, be very gentle to avoid crushing it.

**Step 3: Reassembly**

> [!WARNING]
> **Critical reassembly steps:** Missing any of these steps will cause mounting issues or overheating.

1. **Don't forget the plastic plate:** There's a plastic plate that goes between the chips and the heat sink. If you forget this, the heat sink will not mount correctly and you'll need to disassemble everything again.

2. **Apply thermal paste:**
   - Clean old thermal paste off with a microfiber cloth (**not paper towel!**) and rubbing alcohol
   - Apply new thermal paste - it's better to use slightly more rather than too little since this device needs all the cooling help it can get

3. **Handle the RF shield carefully:** The RF shield (little metal box connected with foil tape) underneath the GPS mount can be finicky. Be gentle and patient when clipping it back in place. Some clips may need to be slightly re-bent if they've deformed.

4. **Route the U.FL wire correctly:** When reassembling, make sure to run the other U.FL wire (that goes to the PCB mounted to the heat sink) *around* the heat sink, not underneath it. There's a small notch in the plastic plate where it should be routed. If run underneath, the heat sink won't mount properly.

5. **Connect the middle U.FL connector:** This "other U.FL wire" connects to the middle U.FL connector on the board under the heat sink. Look for an arrow marking on the board indicating the correct connector.

**Additional Photos**:

<img src="https://github.com/user-attachments/assets/ac314868-e601-4ce9-85e6-1e1000711b7f" width="500"/>
<img src="https://github.com/user-attachments/assets/86a5fea5-8cfe-4c71-87e2-1edee90d0fc8" width="500"/>
<img src="https://github.com/user-attachments/assets/96b5149a-a7b9-4eed-a89b-f5d98e95c76e" width="500"/>
<img src="https://github.com/user-attachments/assets/c0726345-812c-4585-89b4-aac84f3a9d93" width="500"/>
<img src="https://github.com/user-attachments/assets/c1daa5ed-2a0c-436c-98f7-3b52971bc947" width="500"/>

**Resources**:

* USB-C/OBD-C port repair teardown part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C port repair teardown part 2: https://www.youtube.com/live/gTw_Qq8scqo

**Examples**:

* [katsu's C3 (OPC) ✅](https://discord.com/channels/771493367246094347/771493367779295304/1368055272488308797)
* [idnot's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1372254806449848412)
* [Le Potatos's C3 (OPC) ✅](https://discord.com/channels/771493367246094347/771493367779295304/1374310506088628235) - Alternatively shunted it. Note that this C3 might also have other issues such as a broken fan, necessitating shunting the fuse.
* [Nabeel's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1382502275460890755) - Also possibly caused by a broken OBD-C cable.
  * See [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) for more details.
* [wferr's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1383249237739049080)
* [dazoe's C3 ⚠️](https://discord.com/channels/469524606043160576/871838269405556736/1382566915465150464)
  * NOTE: C3's fuse read normally when powered off but otherwise showed a huge resistance when powered on. It only showed voltage drop when powered on.
  * ⚠️ Diagnosing dazoe's C3 was a bit more involved than just measuring the fuse resistance and required more advanced techniques. Seek more knowledgeable help if you are not comfortable with the following.
  * ["My C3 was acting un-stable, when checking the fuse (just above the OBD USB-C in your picture) it wasn't until after I let the fuse "warm up" that i got a reading of 0.8-1 ohm. I also carefully measured the voltage drop across the fuse while the board was running. It wouldn't fully boot up but just idle on a screen that said "press any key to shutdown". The voltage drop was all over, ranging from 0.5-up to 2.5v which means the resistance of the fuse was changing."](https://discord.com/channels/469524606043160576/871838269405556736/1383803066536431768)
  * ["Having it powered up with out heat sink alone risks over heating. the higher risk is with power going to it one slip and you could do serious damage. It's a tight place to get probes in and with it being right next to the usb port's shield you risk shorting out the power supply. If you did add it I would put a big bold warning on it. The basic concept is to have multi meter in voltage mode, probes on each side of the fuse, when powered the voltage should stay close to 0."](https://discord.com/channels/469524606043160576/871838269405556736/1383848416626479165)
* [dimdom69's C3X (OPC) ✅](https://discord.com/channels/771493367246094347/834826173795139584/1388357047522689045)
  * "I measured 2.0 ohms on the bad one, with the new one measuring 0.0 ohms."
  * [Also possibly caused by a broken OBD-C cable?](#the-bad-obd-c-cable-case)
* [wabash's C3, though the diagnosis and resolution was pretty unclean ❓](https://discord.com/channels/469524606043160576/871838269405556736/1395147642581024789)
  * Err'd in removing the fuse for measuring, not knowing it is not necessary, and before measuring and instead accidentally melting the fuse.
  * Not sure if the fuse was actually blown or not.
  * Still has radar issues, so it is not clear if the fuse was the only issue.
  * Also has GPS Issues
* [chaheeto's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1400252232544551085)
  * Measured 1 ohms on the fuse, replaced it with a new one, and now it works.
* [/u/AlekWishes's C3X ✅](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56u9tn/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * "I purchased a konik AI replacement SOM, and I used the supplied blue paste and grey paste. The original paste was applied to the side, not giving proper coverage, in particular the wifi RF cage had almost no paste on it. I have a 3X. I wouldn't be surprised if more people are seeing similar overheating issues due to poor QC on the thermal paste application. Like you said, the thermals are good, just needs proper thermal paste application. In my initial repair attempt I did find a PMIC cap had gone short, replacing it resulted in no current draw, tried replacing the PMIC no change, so I gave up and replaced the whole SOM. Shortly after I found my 12v resettable fuse for the USB port was failing due to the previous excessive current draw, replaced it and now everything has been working great for a few months."
  * Related to [The Bad Or Dead SOM Case](#the-bad-or-dead-som-case)
* [/u/Crabs2336's C3X ✅](https://www.reddit.com/r/Comma_ai/comments/1mg0miu/comment/n7bqfrk/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * Went for shunting the fuse instead of replacing it.
* [Catloaf's C3 ❌](https://discord.com/channels/469524606043160576/871838269405556736/1403834860828622909)
  * Replaced 3 blown fuses and device worked fine with wall 5V power
  * When plugged into car, device started booting but then emitted smoke and blew 3 different car fuses
  * Car became unable to start after the incident
  * [Car was repaired by replacing fuses](https://discord.com/channels/469524606043160576/525718620517564446/1403833844762677360)
  * No longer using the C3.
  * **Warning**: This repair isn't for the faint of heart - even experienced users can encounter serious issues
* [silverwing's C3 🛑 (OPC)](https://discord.com/channels/771493367246094347/771501905507123200/1405664424693600346)
  * Had a huge amount of trouble locating the fuses.
  * Not much electrical knowledge.
  * Measured "`0`" resistance on the fuses. Kinda low amount of decimal places TBH.
  * Gave up and will be sending it to comma for "repair".
* [balsa's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1407407484980953321)
  * [Thought it was the capacitor](https://discord.com/channels/469524606043160576/871838269405556736/1402027821215387668)
  * [0.2 ohm, 0.8 ohm](https://discord.com/channels/469524606043160576/871838269405556736/1405600027644002407)
  * [Had some issues flashing](https://discord.com/channels/469524606043160576/871838269405556736/1405659939602432170)
  * [Shunted with a solder blob](https://discord.com/channels/469524606043160576/871838269405556736/1405600064029720707)
  * "Mine with the part removed and a bridge put in, its working pretty well now"
  * Same C3 in [Fan Death Case](#the-fan-death-case)
* [sidthebear's C3 🛑](https://discord.com/channels/469524606043160576/871838269405556736/1407510430305357946)
  * "So after about 3 years, my c3 has started boot looping. When it's very hot, it will boot get to the traffic screen, then immediately reboot. And this will go on for about 10  to 30 minutes before it will stay turned on."
  * Measured 18.2 ohms
  * Could not put back together.
  * [Tossed it on `#for-sale` for $100](https://discord.com/channels/469524606043160576/1407749221242900604/1407750793049800864)
  * Replaced with a new C3X
  * ["Doing a private for sale rather than a trade-in? Just easier. I didn't feel like dealing with the hassle of trying to put it back together again, trying to reload the software to base op, or anything else. Especially not for whatever paltry discount would be offered for it as a trade-in device."](https://discord.com/channels/469524606043160576/1407749221242900604/1407750473544499231)
* [rifker's C3 (unknown if really was case) ❓](https://discord.com/channels/469524606043160576/871838269405556736/1408153264641413245)
  * Left in drawer for a year, did not boot again.
  * Went with comma's repair service, Chase Sapphired Preferred's Extended Warranty approved doing a warranty on the repair.
  * Was going to measure fuse, but two screws already stripped.
* [bscholer's C3 (detailed instructions above) ✅](https://discord.com/channels/469524606043160576/871838269405556736/1408908722193039521)
  * Left mounted to windshield in a hot car for a week, and no longer booted after.
    * *Note: The device showed the boot logo briefly one time after this, for about a half-second. It still did not function though.*
  * Measured 30 ohms for the fuse.
  * After replacing fuse, the C3 works perfectly!
  * Bought extra fuses, DM if you need a couple in the US, happy to mail them for free.
  * ["Yep, just that one fuse. Didn't test the others, so glad it fixed the problem 😅"](https://discord.com/channels/469524606043160576/871838269405556736/1410054918894784583)
  * Contributed much of the repair guide above!
* [posterduck's C3 ❌](https://discord.com/channels/469524606043160576/871838269405556736/1410462125846958110)
  * Went through bscholer's guide.
  * "It lives!"
  * [Unfortunately, it seems to have fried the fuse again overnight.](https://discord.com/channels/469524606043160576/871838269405556736/1410972090341003274)
  * ["It appears my C3 is officially dead. All fuses are showing fine, but the C3 shows no signs of life when plugged in 🙁"](https://discord.com/channels/469524606043160576/871838269405556736/1413005716146622617)
* [thinkpad4by3's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1411598315656839169)
  * "Ive just replaced all 4 of the PTC fuses with brand new ones and the fault still exists. c3 gives up total control, screen black, alarm on, ACC disengages, etc. the odd part to if I unplug it and replug it back in, the relay automatically opens but the c3 does NOT boot. It won't boot for a while after."
  * [Mr One: "It seems that there is a problem with your CPU
"](https://discord.com/channels/469524606043160576/871838269405556736/1411625935547007016)
  * [The Bad Or Dead SOM Case](#the-bad-or-dead-som-case)
  * Asked if the resistances are still the same post-repair on the fuses.
  * [Continued to use it afterwards with Always On Lateral from frogpilot still at ~60F ambient temperature, but no usage of ACC.](https://discord.com/channels/469524606043160576/871838269405556736/1412187801650331670)
  * ["i think it ended up being a combo of both, but after swapping out all my fuses and replacing my OBD-C cable, i have had 0 failures in the last like 4-5 weeks"](https://discord.com/channels/469524606043160576/871838269405556736/1418306528108089475)
  * See also: [The Bad OBD-C Cable Case](#the-bad-obd-c-cable-case) as a contributor to this case.
* [xyrx's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1413628340681703455)
  * "I got it working with a burnt thumb and 2 hours of really bad soldering"
* [nisparks's device ❌](https://discord.com/channels/469524606043160576/871838269405556736/1425561727746969730)
  * Measured ~2.6+ ohms on the top fuse (other fuses measured 0.6-1.0 ohms)
  * Ordered 10 V12 (Bourns MF-NSML380/12-2) fuses from Digikey for ~$15.50 shipped
  * [Working much more than before post-repair](https://discord.com/channels/469524606043160576/871838269405556736/1430332221696380968)
  * ["Now the device works with random freezes, a very audible alarm, then reboots and all is well for sometimes 40 mins, sometimes longer. "](https://discord.com/channels/469524606043160576/871838269405556736/1434652515730849883)
* [FrogsGoMoo's C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1434992550153814096)
  * Repaired by Drago, with high praise for the quick and effective fix after other shops were unable to help.

### The Bad Supercapacitor Case

**Symptoms**:

* Device does not power on when connected
* Device does not stay on
* Similar symptoms to [The Blown Fuse Case](#the-blown-fuse-case), but the fuse tests good
* The device may show signs of a short circuit or power issues

**Diagnosis**:

While [The Blown Fuse Case](#the-blown-fuse-case) is much more common, there are rare instances where a supercapacitor failure occurs on comma three family devices. Both the comma 3 and comma 3X use supercapacitors as part of their power architecture. The comma 3X specifically uses them with a boost regulator for voltage stability.

> [!WARNING]
> Before suspecting a bad supercapacitor, **always check the fuse first** following the instructions in [The Blown Fuse Case](#the-blown-fuse-case). The fuse is much more commonly the culprit and is easier to diagnose and replace.

> [!IMPORTANT]
> Diagnosing and replacing supercapacitors requires electronics repair skills and equipment, including:
> - Ability to identify and measure larger capacitor components
> - Soldering iron with appropriate tips
> - Multimeter with capacitance measurement capability
> - Knowledge of power circuit analysis
>
> **Unlike fuses, supercapacitors typically need to be removed from the board for accurate testing.** This makes diagnosis more complex than fuse testing, which can be done in-circuit.
>
> If you are not experienced with component repair, consider:
> - Seeking help from a professional electronics repair service
> - Using comma's out-of-warranty repair service

**Resolution**:

If the fuse has been verified to be good and you have ruled out other causes, a failed supercapacitor may be the issue. This typically requires:

1. **Identification**: Locate the failed supercapacitor through visual inspection (bulging, discoloration, leakage) or electrical testing (short circuit, out-of-spec capacitance).
2. **Replacement**: Remove the failed supercapacitor and replace it with an appropriate replacement part.
   * Original: [Tecate Group, 2.7V, 1.5F , blue exterior](https://www.tecategroup.com/products/data_sheet.php?i=TPLH-2R7/1.5WR6X15)
   * Alternative (with higher temperature rating): Knowles DGH155M2R7 (1.5F 2.7V), see ereish64's example below for details.
3. **Verification**: Test the board to ensure the short or power issue is resolved.

Supercapacitors are larger components compared to typical surface-mount capacitors and may be more accessible for diagnosis and replacement.

**Examples**:

* [ereish64's C3X](https://github.com/ophwug/docs/issues/25) ✅
  * Reported symptoms consistent with power issues
  * Investigation indicated supercapacitor involvement (1.5F capacitors)
  * Successfully replaced supercapacitors and device is working
  * Alternative Replacement part: Knowles DGH155M2R7 (1.5F 2.7V) from [Mouser](https://www.mouser.com/ProductDetail/Knowles-Illinois-Capacitor/DGH155M2R7?qs=iLbezkQI%252BshcZvBCu9GXdg%3D%3D)
    * Note: Replacement parts don't quite fit the original footprint but can work with careful installation
    * Replacement part has higher temperature rating (85C vs original 65C) "The capacitors I used as a replacement have a max temperature of +85C. The original capacitor appears to have a max of +65C..."
  * See [issue](https://github.com/ophwug/docs/issues/25) for detailed discussion and photos

**Vendors**:

* comma OEM: TPLH-2R7/1.5WR6X15
  * Datasheet: https://www.tecategroup.com/products/data_sheet.php?i=TPLH-2R7/1.5WR6X15
  * Digikey: https://www.digikey.com/en/products/detail/tecate-group/TPLH-2R7-1-5WR6X15/9930255
* ereish64 higher temperature rating alternative: DGH155M2R7
  * https://www.mouser.com/ProductDetail/Knowles-Illinois-Capacitor/DGH155M2R7?qs=iLbezkQI%252BshcZvBCu9GXdg%3D%3D
  * Please consult his image in the [issue](https://github.com/ophwug/docs/issues/25)

### The Screen Doesn't Work or is Dying Case

**Symptoms**:

* `openpilot` still engages
* You still hear sounds from the speaker
* Fans are moving/audible
* LEDs on the device are blinking (e.g., red then blue on boot)
* The screen does not turn on
* purple splotches on the screen
* Screen burn-in
* Device still appears on home network
* Any other sign that the Linux OS AGNOS has booted and working.
* If it is not a power issue (see [The Blown Fuse Case](#the-blown-fuse-case))

**Non-Symptoms**:

* Screen tearing - [This was/is a software issue that affects openpilot and openpilot forks for a certain period.](https://github.com/commaai/openpilot/issues?q=is%3Aissue%20state%3Aopen%20tearing) . Please update to the latest comma openpilot or openpilot fork.

![Image](https://github.com/user-attachments/assets/91e0bcc8-f625-4640-8aeb-2a227f18d523)

**Resolution**:

First, make sure to try to reseat the connection for the screen. If that does not work, you will need to replace the screen.

Inspect the MOSFETs around for any signs of failure. See [The Burned MOSFET Case](#the-burned-mosfet-case).

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
* Find/use any panel that is for the "Huawei Mate 10 Pro". Quality will vary. Not all screens will work. AMOLED version are the ones that are known to work. TFT and cheap models may not.
  * You can fill in the unused camera cutout with nail polish 💅.

**Examples**:

* [radko's C3](https://discord.com/channels/469524606043160576/871838269405556736/1407751155680804914)
  * "The screen replacement was a breeze. Good job to the HW team who made the sticky tape easily removable and the mark where to bend the ribbon cable was a nice touch 🥰"
  * "c3 bought November 2022. Screen died due to user error (slid down the dashboard and hit the car's infotainment screen). After a few days the screen completely died. Worked flawlessly prior to being smacked."
  * ["DIY. Heated it with a hair dryer slowly for 2minutes and the  glue let the original screen go quite easily. Re-used the original glue as it was still tacky. Upon inspecting the broken screen I haven't found any cracks, guess it hit the *right* spot and released the organic matter in the OLED behind it. Interestingly the touch panel also had ghost touches but not as frequently to cause reset on boot (running OBD disconnected to save the 12V), in the picture above I managed to reset calibration upon repositioning it."](https://discord.com/channels/469524606043160576/871838269405556736/1407944207108145245)
* [chichum's C3](https://discord.com/channels/469524606043160576/871838269405556736/1438958679968972851)
  * Device was unplugged for about five days and would not turn back on.
  * When plugged in, the unit blinked red quickly and then blinked blue. The screen never turned on, but the fans were moving.
  * After trying different cables and plugs, the user suspected a blown fuse and ordered replacements.
  * The issue was ultimately a bad screen. The user determined this because the device was plugged into the car, and the car started driving itself when openpilot was enabled with the steering wheel, indicating the device was fully functional except for the display.
  * This case highlights the importance of checking for signs of life (blinking lights, fan noise, and openpilot engagement) before assuming a power issue like a blown fuse.
  * Their screen was cracked from the first day due to a drop, which may have contributed to the failure years later.
  * They are not replacing the screen and will likely trade in the device for a comma four.

### The Fan Death Case

**Symptoms**:

* The device overheats
* The fan makes horrible noises
* The fan does not spin

Not the Korean kind of fan death!

**Resolution**:

Comma unfortunately does not sell replacement fans by themselves. Users have been replacing them with various fans to differing success. OEM part may be from ADDA, not sure if off the shelf. Mr. One sells a replacement fan with heatsink for the C3.

See also: [The Uncleaned Fan Flux Case](#the-uncleaned-fan-flux-case)

**Examples**:

* [redmapleleaf's C3, Noctua](https://discord.com/channels/469524606043160576/871838269405556736/1328667993047040010)
* [Pandus's C3, Scavenged ZOTAC fan](https://discord.com/channels/469524606043160576/871838269405556736/1364305247723589734)
* [Balsa's C3, Mr. One's C3 Fan Replacement Heatsink](https://discord.com/channels/469524606043160576/871838269405556736/1415378929899798569)
  * Note that it has pictures of the replacement fan but it seems a standalone non-square shroud version can't be found
  * [He has also run the fan testing script](https://discord.com/channels/469524606043160576/871838269405556736/1415385666597945517)
  * Same Balsa as in [The Blown Fuse Case](#the-blown-fuse-case)

**Vendors**:

* Mr. One: https://oneclone.net/product/c3-heatsink-replacement-parts/
  * Replacement fan with heatsink for the C3
  * While Mr. One does have a C3XL that is a "clone" of a C3X, it is physically similar to a C3 still and is not compatible for a comma C3X.

**Reference**:

* Fan Test: https://www.youtube.com/watch?v=4BmkMEpBcLY
* https://discord.com/channels/469524606043160576/871838269405556736/1350189845758218417
* comma: https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644

### The Uncleaned Fan Flux Case

**Symptoms**:

* The fan has inconsistent speed, even when set to a fixed level.
* The fan's RPM reading is 0 in panda scripts.
* Disconnecting the fan's blue speed control wire does not cause it to run at maximum speed; it continues to oscillate.

> "flux not cleaned on fan pins of comma three rev I - 08/31/21"

<img width="640" height="360" alt="flux" src="https://github.com/user-attachments/assets/578d4338-2139-426d-b793-740d4f451051" />

**Resolution**:

After cleaning the flux from the fan pins, the fan should operate correctly.

See also: [The Fan Death Case](#the-fan-death-case)

**Examples**:

* [alesatobrazilsp's friend's C3](https://discord.com/channels/469524606043160576/871838269405556736/1408258565726015590 )
  * [original issue post](https://discord.com/channels/469524606043160576/871838269405556736/1397284881054306364)

### The Poor GPS Signal Case

**Symptoms**:

* The device has an alert about poor GPS signal
* The device seems to not be able to locate itself well on [comma connect]
* Environmental Conditions:
  * A magnetic mount is used.

   * The car's windshield is heated.

**Resolution**:

There are multiple solutions to this problem.

* Newer openpilot does not care about GPS being an alertable requirement. https://github.com/commaai/openpilot/pull/35585
  * Update to a codebase that has this change.
  * This will still result in wonky map behavior recorded in [comma connect] but it will not cause an ongoing alert.
* Hardware issues:
  * Check the GPS antenna connections internally.
  * Make sure the GPS module has power connections.
* Heated windshields can cause issues with GPS reception.
  * It has not been explored, but there are GPS repeaters that can be used to help with this. Please report if you have success with this.

**Examples**:

* [Nabeel's C3](https://discord.com/channels/469524606043160576/871838269405556736/1383159801365790932)
  * "I discovered why GPS wasn't working in my C3 after my repair… This… was sitting on my desk... That's the cable that connects the GPS module to the main board."

### The Bad or Dead SOM Case

The System-On-Module (SOM) is the main processing unit of your comma device, containing the CPU, memory, and other essential computing components. If the SOM fails or becomes corrupted, the device will not function.

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
  * "I purchased a konik AI replacement SOM, and I used the supplied blue paste and grey paste. The original paste was applied to the side, not giving proper coverage, in particular the wifi RF cage had almost no paste on it. I have a 3X. I wouldn't be surprised if more people are seeing similar overheating issues due to poor QC on the thermal paste application. Like you said, the thermals are good, just needs proper thermal paste application. In my initial repair attempt I did find a PMIC cap had gone short, replacing it resulted in no current draw, tried replacing the PMIC no change, so I gave up and replaced the whole SOM. Shortly after I found my 12v resettable fuse for the USB port was failing due to the previous excessive current draw, replaced it and now everything has been working great for a few months."
  * Related to [The Blown Fuse Case](#the-blown-fuse-case)

**Vendor**:

* comma.ai: They do not sell their SOMs.
* Mr. One: https://oneclone.net/product/thundercomm-d845-som-4gb64/
* konik.ai: https://konik.ai/shop/thundercomm-d845-som-4gb64/
  * There is an option for an 8GB version but it is not necessary for openpilot.

### The Damaged Ribbon Cable Case

**Symptoms**:

* "long story short my small brain used way to long a screw to put the ssd in and I heard a crunching sound and this is what I saw"
* small brain

![IMG_1289](https://github.com/user-attachments/assets/ad788299-3c63-427d-b260-f4b5126e6e23)

**Resolution**:

Replace the damaged ribbon cable.

**Vendors**:

* [DigiKey](https://www.digikey.com/)

**Examples**:

* [xyrx's C3](https://discord.com/channels/469524606043160576/954493346250887168/1406453677891387454)
  * [Followup in finding the correct or very similar ribbon on DigiKey.](https://discord.com/channels/469524606043160576/871838269405556736/1409000268837683282 )
  * "I just had to count the pins and measure the length"
  * Found https://www.digikey.com/en/products/detail/molex/0151660271/3281152
  * A straight cable like this was probably easy to find.

### The SIM Card Is Stuck Case

Maybe it's a bit of a design flaw on comma's part but the plastic on the comma three family device doesn't always have the best or precise opening needed for the tiny SIM card to be removed easily after pushing in on it.

**Symptoms**:

* The SIM card is stuck in the device after pushing on it.

**Resolution**:

* Use a plier to get the card out.
* In more serious cases, take apart the device with a screwdriver to get more access.

**Examples**:

* [Vrabetz's C3X](https://discord.com/channels/469524606043160576/871838269405556736/1416214544304443473)
* [h3lix213412's C3X](https://discord.com/channels/469524606043160576/871838269405556736/1416073425675358279)
  * "the sim slot was stuck, so I had to unscrew two screws to get to the point to remove the sim with a little force"
* [cookiemonster's C3X](https://discord.com/channels/469524606043160576/524592892627517450/1414868691643924512)
  * "disassembled it and noticed my sim card tray gets quite tight with more resistance as it gets closer to fully seat. when it is fully seated, the spring is barely strong enough to push it out. I hope i dont need to change my sim card any time soon 🫠"

### The Stuck On Registration Case

It is suspected that comma's endpoint for C3 registration might be a bit unreliable. On newer C3s and C3Xs, the devices are preloaded with a dongle id, but older and earlier C3s may not have this. Some devices may also be missing the dongle id in /persist for other reasons.

**Symptoms**:

* Registration is stuck spinning

**Resolution**:

If you're using a C3X, try updating to the latest comma openpilot or openpilot fork. Newer versions have fixed some registration issues.

If not, there is a more surgical, but [non-recommended from comma solution.](https://discord.com/channels/469524606043160576/819046761287909446/1335013586027942065)

Find your dongle id in https://connect.comma.ai or https://useradmin.comma.ai .

Replace your dongle id below and run this script:

```bash
DONGLE_ID="REPLACE_THIS_WITH_YOUR_DONGLE_ID"
sudo mount -o remount,rw /persist
echo "$DONGLE_ID" > /persist/comma/dongle_id
sudo mount -o remount,ro /persist
sudo reboot
```

### The Bad EMI Filters Case

![EMI Filter](https://github.com/user-attachments/assets/a6f31f61-0725-4b43-a9ea-613c55c6a797)

**Symptoms**:

* Screen does not turn on
* A working screen replacement does not fix the issue
* Device does boot otherwise (fans spin, LEDs light up, openpilot engages, etc)
* EMI filters look burnt or damaged

**Resolution**:

* Extremely hard to replace, requires advanced soldering skills and equipment.
* Needs hot air rework station, solder wick, flux, magnifying glass or microscope, steady hands, and patience.

Replace the EMI filters (PCMF3USB3S) next to the screen connector with a new one.

**Vendors**:

Numerous, search for "PCMF3USB3S" on your favorite electronics component website.

**Examples**:

* [Drago's customer's C3](https://discord.com/channels/469524606043160576/871838269405556736/1439435620304031764)
  * [Extremely hard to replace](https://discord.com/channels/469524606043160576/871838269405556736/1439063062744404110)
  * Currently not comfortable but if you want to try, reach out to Drago for an attempt.


## comma three (C3)

Released: 2021-07-31

Discontinued: 2023-10-12

Codename: tici

comma openpilot support dropped: 2025-08-26

https://blog.comma.ai/comma-three-press-release/

The comma three is comma's first device designed from the ground up that isn't based upon a hacked-up cell phone.
It was relatively expensive. It was the first with three cameras.

Variants of the comma three may include no SSD but 32GB of onboard eMMC System on Module storage, 256GB of NVME SSD storage, or 1TB of NVME SSD storage.

The only OEM SSD supported is the [Samsung 980 Non-Pro SSD](https://www.amazon.com/Technology-Intelligent-Turbowrite-MZ-V8V1T0B-AM/dp/B08V83JZH4?th=1). Other SSDs may not work or have other weird unsupported issues; embedded devices are much more picky about SSDs than a desktop or laptop.

**Evolutions**:

* Early C3 had dedicated u-blox GPS module
* 32GB of onboard eMMC storage with no SSDs were introduced later
* [Panda] was changed from an internal USB connection to a SPI connection
* Cameras were changed from AR0231 to OS04C10 near the end of the C3's life cycle.


The dates and times of these changes are not well documented, but they are known to exist.

**Resources**:

* https://enjoi.dev/posts/2021-12-20-comma-3-teardown/ - Good general teardown of the comma three in written form.
* https://www.youtube.com/watch?v=Y3Z4j466CsE - Installing a SSD
* USB-C/OBD-C port repair teardown part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C port repair teardown part 2: https://www.youtube.com/live/gTw_Qq8scqo

### The Swampy No Panda Case

**Symptoms**:

* No [Panda]

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

Note that both vendors only sell the OX03C10 variant.

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

Codename: tizi

https://blog.comma.ai/comma3X/

The comma 3X is comma's first major hardware revision of the comma three. It has gone through a major cost reduction and is now cheaper to manufacture.

* Cameras are no longer on separate boards but are now soldered onto the main board.
* The NVMe SSD has been removed in favor of 128GB of onboard eMMC storage.
* Speakers have been overhauled to be two speakers.
* It is significantly lighter.
* It uses a mount that's smaller than the comma three's mount.
* A Red Panda is now included with the device, which now includes built-in CAN-FD support.
* Camera changed to OX03C10
* The power architecture was upgraded to use a boost regulator with the supercapacitors for more stable voltage and reliability.

**Evolutions**:

* Real-Time-Clock removed and not populated, to be filled in by GPS soon after boots.
* comma switched from [off-the-shelf Thundercomm D845 SOM](https://www.thundercomm.com/product/d845-som/) to their [in-house custom LightningHard SOM.](https://fcc.report/FCC-ID/2BFC6-LIGHTNINGH)
  * [Modified PMIC to better handle thermals](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56rj4i/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
* ["No chiplet" Red Panda](https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644)
* ~ April 2025: [Different Panels that need more commands to start up in high heat](https://github.com/commaai/openpilot/issues/34971#issuecomment-2778764248)


### The No Panda on C3X Case (Software)

**Symptoms**:

* No [Panda]

**Resolution**:

Run through https://github.com/commaai/openpilot/issues/33016

Note: Use the `nightly` branch of openpilot. `master-ci` is not available anymore.

**Examples**:

* [Ed Moore's C3X](https://discord.com/channels/469524606043160576/1263672324973138033/1270345888950124671)

### The No Panda on C3X Case (Hardware)

**Symptoms**:

* No [Panda]
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

### The Bad Step Down DC/DC Regulator Case

**Symptoms**:

* Behavior is similar to [The Blown Fuse Case](#the-blown-fuse-case)
* Fuse reading short to ground
* [Fuses themselves are good](#the-blown-fuse-case)
* With a thermal camera, a specific chip is identified as the source of the short.

![Regulator and Thermal Camera View](https://github.com/user-attachments/assets/be2e76e0-cf4f-4b3e-ab10-6687a16dae46)


**Diagnosis**:

A short to ground was detected on the fuse. After removing the fuse, the short was traced to a step-down buck regulator chip. By injecting 1V to the VN side of the diode side, a thermal camera was used to trace the short back to this chip. With the buck regulator removed, the short was no longer present.

**Resolution**:

Replace the faulty SY8368AQQC chip. It's a tight 3x3mm QFN3x3-12 package though.

Datasheet: https://www.lcsc.com/datasheet/C207642.pdf

Unfortunately, it does not seem there has been a sucessful repair with this case yet. If you have success, please report it here.

**Vendors**:

* Just search for SY8368AQQC on your favorite electronics part vendor. The last 3 letters are just a date code and will vary.

**Additional Notes**:

It is recommended to also check the integrity of the "L" inductor to avoid burning the MOSFET of the new MCU.

**Examples**:

* [ZUM(zum114)'s C3X 🛑](https://discord.com/channels/469524606043160576/871838269405556736/1423032049136173056)
  * [Initial Post](https://discord.com/channels/469524606043160576/871838269405556736/1422027156829241386)
  * ["Little short video from the thermal cam on the buck chip"](https://discord.com/channels/469524606043160576/871838269405556736/1423040186769608857)
  * ["Welp, same chip popped again so I give up "](https://discord.com/channels/469524606043160576/871838269405556736/1426776980443107328)

## comma four (C4)

Released: 2025-11-08

Codename: mici

TODO: put blog link here

The comma four was announced at [COMMA_CON 2025](https://www.reddit.com/r/Comma_ai/comments/1nr5zvn/comma_con_2025/).

It is comma's first major form factor redesign. Instead of a large landscape phone on windshield form factor, it is now shaped like a small windshield dashcam with a much smaller but touch GUI display about the size of a radar detector's display.

[Some specifications include](https://discord.com/channels/469524606043160576/1436852432503046294/1437501443253866558):

* Tiny form factor.
* OLED touchscreen (536x240).
* Upgraded speaker.
* Snapdragon 845 with enhanced cooling system such as a Noctua fan and better thermal design.
* SOM and Panda are on the same board now.
* A Red Panda is included with the device for built-in CAN-FD support.
* Cameras are on separate boards.
* No supercapacitors, for improved power stability.
* Re-introduced u-blox GPS module, which was deleted on later C3s and the C3X.
* Onboard eSIM, replacing the physical SIM slot though a physical SIM slot on the board is still present but you'll need to take off the top of the device to access it.
* 3x OS04C10 cameras with improved night performance.
* New mount with instant cure adhesive.
  * It has more surface area contact with the windshield for better adhesion.
  * It is lighter
* 128GB storage still, but the camera records with smaller file sizes for longer recording times.
* New flexible OBD-C cable.
* Reduced number of parts for higher reliability.


# See Also

* https://docs.comma.ai/concepts/glossary/ - An official glossary of terms

# References

* https://mr-one.cn/?post=24
* https://mr-one.cn/?post=25

[cdiscord]: https://discord.comma.ai/
[on-road]: https://docs.comma.ai/concepts/glossary/#onroad
[comma connect]: https://docs.comma.ai/concepts/glossary/#comma-connect
[Panda]: https://docs.comma.ai/concepts/glossary/#panda
