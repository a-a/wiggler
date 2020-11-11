# wiggler
Inspired by COVID-19, USB HID emulation to wiggle your mouse to stop your laptop sleeping and VPN disconnecting....

Problem: work laptop keeps sleeping every time I want to take a dump or make a coffee.
Solution: ~~ask IT to fix it~~  I am IT and I have no real powers, so I have to make some dumb thing to workaround corporate bullshit, they must love me for shit like this


> I am **not** responsible if you get your ass kicked for using this.
 
# Hardware

wiggler has been built to target the STM32F103C8T6 series microcontroller because they're cheap and commonly available and have USB and some libraries to make that USB useful.
So far it has only been tested on the STM32 "**Blue Pill**" development board, but I see no reason why it can't work on other things. 
(If somebody tries flashing this to an ST-Link clone let me know - that's a nice form factor. I just haven't tried it yet since the blue pill worked well enough for me!)


## Flashing

### Flashing to a STM32 Blue Pill
You will need:
* STM32F Blue Pill Devboard
* ST-Link V2 adapter
* The binary from the Releases tab, or from the Release folder if you've just rebuilt the code.

[Todo: insert diagram for flashing here]
[Todo: insert instructions for flashing with OpenOCD here]
[Todo: put OpenOCD configs in the repo to make it nice and stuff]

# Software

## How it works:
wiggler uses the STM32Cube libraries to emulate a USB HID device. It then sits in a loop, wiggles the mouse 1px up and 1px down in quick succession, then goes to sleep for a bit, before going back to the start of the loop. That's all it does.
You may find you need to modify timings if it doesn't work well for you - see main.c for that, but in my case it kept my work laptop from sleeping so I can't complain.

## How to build
wiggler was built using STM32CubeMX V1.3.1 under Windows. Elsewhere, your mileage may vary.
Once imported, in its default configuration it just builds for me when you hit F5. Binaries end up in the "Release" folder.


# Licences

| Component                       | License              | Copyright |
|:---------                       |:-------              |:----------|
| CMSIS                           | Apache License 2.0   | Copyright (c) 2009-2017 ARM Limited. All rights reserved. |
| CMSIS Device                    | Apache License 2.0   | ARM Limited - STMicroelectronics |
| STM32F1 HAL                     | BSD-3-Clause         | STMicroelectronics |
| STM32_USB_Device_Library        | ST SLA0044           | STMicroelectronics |
| the crap i put in main.c        | [WTFPL](http://www.wtfpl.net/about/)                | ¯\_(ツ)_/¯ | 



