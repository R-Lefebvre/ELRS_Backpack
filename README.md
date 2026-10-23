# ExpressLRS Backpack

[![Release](https://img.shields.io/github/v/release/ExpressLRS/Backpack?include_prereleases)](https://github.com/ExpressLRS/Backpack/releases)
[![License](https://img.shields.io/github/license/ExpressLRS/Backpack)](https://github.com/ExpressLRS/Backpack/blob/master/LICENSE)
[![Chat](https://img.shields.io/discord/596350022191415318)](http://discord.gg/dS6ReFY)
[![Open Collective backers](https://img.shields.io/opencollective/backers/expresslrs?label=Open%20Collective%20backers)](https://opencollective.com/expresslrs)

The ExpressLRS Backpack adds ESP-NOW–based wireless communication between ExpressLRS TX modules and compatible FPV hardware, allowing for remote configuration, control, and telemetry exchange. Developed and maintained by **ExpressLRS LLC** and its passionate open source community, working together to advance reliable, high-performance radio control technology.

ExpressLRS Backpack is developed and maintained by **ExpressLRS LLC** and its passionate open source community, working together to advance reliable, high-performance radio control technology.

## Maxxum Robotics TX Backpack customization

This branch is based on stable Backpack 1.5.9 and uses the exact SSID
`MaxxumRobotics TelemAP` for both TX Backpack
firmware updates and MAVLink telemetry, without an identifier suffix. Other
Backpack types retain their upstream AP settings. The TX AP name is set
in `lib/WIFI/devWIFI.cpp`, and the binding phrase is set in `user_defines.txt`.
These AP settings do not configure a home Wi-Fi network.

Before building, create the ignored `super_defines.txt` file and add
`-DTX_BACKPACK_AP_PASSWORD=` followed by the password's comma-separated ASCII
byte values, without a trailing zero. The password must be 8 to 63 printable
ASCII characters. A TX Backpack build fails if this setting is missing.
Keep this local configuration and firmware binaries containing the password
out of public source control.

For the RadioMaster Nomad's ESP32-C3 Backpack, build with
`pio run -e ESP32C3_TX_Backpack_via_WIFI`. This builds without uploading.
The main ExpressLRS radio firmware is a separate build; its binding phrase and
the receiver's binding phrase must also be configured as intended.

## What is a "TX Backpack"?

Some of the ExpressLRS TX modules include an additional ESP8285 chip, which lets us communicate wirelessly with other ESP8285 enabled devices using a protocol called espnow. We call this chip the "TX-Backpack". The aim of the TX-Backpack is to allow wireless communication between ExpressLRS, and other FPV related devices for command and control, or for querying config.

## Sounds interesting... What type of FPV devices can it talk to?
 A prime use case is your video receiver module (or VRX). Currently there aren't many VRX modules that have an ESP8285 built in to allow them to communicate with ExpressLRS, so in most cases you need to add your own. A small ESP based receiver can be "piggybacked" onto your VRX module, which allows ExpressLRS to control the band and channel that your goggles are set to. We call this device the "VRX-Backpack". 

## Wow cool, so I'll be able to control the module via ELRS!? Which VRX modules does it work with?
The list of supported modules can be found on the wiki:
https://github.com/ExpressLRS/Backpack/wiki

## Great! I use one of the supported modules. How do I get a VRX-Backpack?
There are a few different options for both DIY or compatible off the shelf backpacks... check the wiki for the current list:
https://github.com/ExpressLRS/Backpack/wiki
