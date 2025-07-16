---
title: digital typewriter
author: umbra
description: A hybrid e-ink and OLED digital typewriter powered by ESP32
created_at: "2025-07-10"
---

# July 9th: Brainstorming and Components
Decided on project objectives and begun search to find components necessary to create the typewriter
> **Features**
> - File storage system
> - Basic formatting (bold, italics, bullets, headers)

_*more features could be added later, I would just like to get all the hardware figured out before i start getting overzealous with programming_

- ESP-32 S3 becuase I just want to learn more about the platform and move over from arduino
- Decided on a hybrid e-ink and OLED display (similar to Ashtf's pocket mage PDA) to conserve battery life and have a smooth typing experience
  - Using the same wide OLED from his new video!
- Found a cheap e-ink display commonly used for IOT labels
- Kailh low profile switches because a) they offer a good typing experience while still being small b) i have some 

![block diagram](./journal%20images/Basic%20block%20diagram.png)

**Total time spent: 2h**

# July 10th: More Componenets
More stuff? I dislike using modules, but I'll swallow my pride/succumb to laziness considering the budget and timeframe of this project (also modules mean I can do some prototyping on a breadboard)

- An SD card reader module
  - With two SPI componenets, I will need to figure out a system to alternate between updating the screen and saving things into memory; luckily e-ink displays are bistable
- Battery management with a bq25185 module
  - USB-C connectivity with power path management, suitable for a single 3.7V lipo
    - I will need to step down the voltage with an LDO (XC6210B332MR?) for the ESP32
- 3.7V single cell lipo
  - Current have a placeholder 1400mAh slim cell right for blocking
  - Not entirely sure what I'm going to use yet, probably going for something slim that can fit within the side of the screen with as much capacity as possible

Currently I'm leaning towards buying and prototyping with these modules, then combining everything with a proper PCB.

![detailed block diagram](./journal%20images/Detailed%20Block%20Diagram.png)

**Total time spent: 3h**

# July 15th: Ordering Parts and Designing the Keyboard

Ordered the e-ink display and sd card early for testing. The project is likely going to go over $150 anyways so making these purchases without the grant money should be fine.

To keep the work going, I started work on the keyboard portion of the device. I decided to use mx spacing (19.05mm x 19.05mm) and created a keyboard layout similar to the JD40.
![keyboard layout](./journal%20assets/keyboard%20layout.png)

Heres the schematic I created in KiCad
![early schematic](./journal%20assets/starting%20keyboard%20design.png)


**Total time spent: 3h**



# Month Day: Title

[actual journal content - what did you do?]

[insert pictures of what you're working on!]

**Total time spent: time**

https://imgbb.com/
