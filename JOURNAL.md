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

![block diagram](./journal%20assets/Basic%20block%20diagram.png)

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

![detailed block diagram](./journal%20assets/Detailed%20Block%20Diagram.png)

**Total time spent: 2.5h**

# July 15th: Ordering Parts and Designing the Keyboard

Ordered the e-ink display and sd card early for testing. The project is likely going to go over $150 anyways so making these purchases without the grant money should be fine.

To keep the work going, I started work on the keyboard portion of the device. I decided to use mx spacing (19.05mm x 19.05mm) and created a keyboard layout similar to the JD40.
![keyboard layout](./journal%20assets/keyboard%20layout.png)

Heres the schematic I created in KiCad
![early keyboard schematic](./journal%20assets/starting%20keyboard%20design.png)

After doing some research, I belive that FFC cables will be the best to use in connecting the keyboard with the rest of the computer. As a design consideration, a slot will need to be cut into the mainboard to ensure that connections dont get reversed.

**Total time spent: 4h**

# July 17th: FFC Connector and Laying Out the Keyboard

After sourcing a JST connector from JLC, I created and recreated the symbol and footprint of the FFC connector...
![connector symbol and footprint](./journal%20assets/ffc%20symbol%20and%20footprint.png)

...then updated the schematic with the new connector.
![completed keyboard schematic](./journal%20assets/finished%20keyboard.png)
Then I went through the tedious process of laying out componenets and routing traces. Because I'm using choc switches with MX spacing, I had to create new footprints based off of Scottokeeb's hotswap choc footprint.
![completed keyboard layout](./journal%20assets/keyboard%20layout.png)
I may try to make the keyboard even smaller by moving the FCC connector, but for now I am quite satisfied with my design.

**Total time spent: 5h**

# July 18th: Fixes and OLED

I realized I actually misoriented the connector so I decided to just redo the entire system again, making everything more compact in the process.
![even more completed keyboard layout](./journal%20assets/improved%20finished%20keyboard.png)

Another conclusion that I came to is that the motherboard should be split into component modules—the lack of ability to prototype within this project and timeframe means that parts will definetly not work on the first try. By making parts swappable, I can mitigate the damage of each iteration.

I also decied to use a differnet OLED module that is now 64*256px. While that means I'll need another SPI peripheral instead of I2C, this module should be easier to implement and display more data.

**Total time spent: 1h**

# July 19th: Power Management
I created the usb-c port program the ESP32-s3-wroom module with.
![usb schematic](./journal%20assets/usb+power.png)
Because the battery module I plan to use outputs 4.5-3v, I settled on the TPS79533DCQR to regulate 3.3v to the ESP32-s3-wroom-u. It has a ~105mV dropout voltage and low noise—perfect for the ESP32.
![power system block diagram](./journal%20assets/Power%20System.png)


**Total time spent: 3h**

# July 20th: ESP32

With the power situation figured out, I added in the esp32 and its basic peripherals to the schematic. I had some confusion about the power system and how everything was going to be grounded, but I believe that my schematic works properly now.
![esp added to schematic](./journal%20assets/esp32ed.png)

**Total time spent: 3h**

# July 22nd: OLED Testing

The OLED module arrived so I took the time to test it and gain some familiarity with using SPI on the ESP32. I (messily) created a small test circuit on a breadboard...
![oled and esp32 on breadboard](./journal%20assets/oled%20breadboard.jpg)

and wrote some basic code using U8g2lib. The idea is to have text be centered and have the font shrink when the text gets too big to fit on the OLED...

![display text code](./journal%20assets/displaytext.png)

For a small test of the OLED module, I am quite satisfied wtith the result!

![oled test](./journal%20assets/oled%20works.gif)

**Total time spent: 4h**

# Month Day: Title

[actual journal content - what did you do?]

[insert pictures of what you're working on!]

**Total time spent: time**