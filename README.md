<h1 align="center">
      <!-- logo credit: https://www.vexels.com/png-svg/preview/325937/blue-computer-mouse-icon -->
      <img src="https://images.vexels.com/media/users/3/325937/isolated/preview/f3221834ed60ef29b8f0b2f37a708386-blue-computer-mouse-icon.png" width="96px" height="96px"/>

ZeroWire

<img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/palette/macchiato.png" width="600px"/> <br>
<div align="center">
            <a href="https://micropython.org/"><img src="https://img.shields.io/badge/MicroPython-stable-blue.svg?style=for-the-badge&labelColor=303446&logo=micropython&logoColor=white&color=b7bdf8&logoColor=cad3f5"></a>
            <a href="https://www.raspberrypi.com/"><img src="https://img.shields.io/badge/Raspberry%20Pi%20Pico-RP2040-green?style=for-the-badge&labelColor=363a4f&logo=raspberrypi&color=c6a0f6&logoColor=cad3f5"></a>
</div>
</h1>

**ZeroWire** is a custom-built wireless USB HID mouse with USB-C charging,[^1] and a transceiver / receiver system using 2.4GHz Radio.[^2]

## **Components Used**
> [!NOTE]
> **Note:** A multimeter is required to tune the DC boost converter to 5V.
- Raspberry Pi Pico (USB-C)
- PixArt PAW3395 Sensor
- NRF24L01 Transceiver + CH340 USB Receiver
- MT3608 2-24V to 5V DC Boost Converter
- 3.7V 1000mAh Lipo Battery + TP4056 Charger Module
- Omron D2F-01L Switch (x2)
- Jumper Wires
- 12V Multimeter

### 1. **Component Configuration**
![component configuration uml diagram](images/mouse%20component%20config.png)

## **Steps taken:**
- Custom breakout board pcb for PAW3395 ordered (credit to [ufan's breakout board](https://github.com/ufan/paw3395_pmw3361_breakout))
- [KiCAD](https://www.kicad.org/download/windows/) used to review PCB and schematic
- Raspberry Pi Pico mounted (BOOTSEL) and .uf2 file uploaded (easier programming, can be downloaded [here](https://www.raspberrypi.com/documentation/microcontrollers/micropython.html) or in [/files](https://github.com/aparkgh/custom-mouse/tree/main/files)))
- [Thonny](https://thonny.org/) used to upload nrf24l01.py driver (for wireless transceiver, can be downloaded [here](https://github.com/micropython/micropython-lib/tree/master/micropython/drivers/radio/nrf24l01) or in [/files](https://github.com/aparkgh/custom-mouse/tree/main/files))
- ufan's breakout board layered in between sensor and LM19-LSI lens ![exploded view of assembly with lm19-lsi lens](images/paw3395dm-t6qu%20exploded%20view.png)

## **Useful Links:**
- [NRF24L01 Pinout](https://howtomechatronics.com/wp-content/uploads/2017/02/NRF24L01-Pinout-NRF24L01-PA-LNA-.png)
- [Raspberry Pi Pico Pinout](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-pinout.svg)
- [PixArt PAW3395 Sensor Datasheet](https://www.codico.com/en/mpattachment/file/download/id/1236/) (contains assembly and schematic)
- [Pricesheet](https://1drv.ms/x/c/81566783f4b27a85/Eb886e1THZZElGMRDwNFMZEBl47CX9LvK6eldiMpxhTBGg?e=1K7VTB)

## **Things that went well:**
- Finding cheap general components. Aliexpress hosts a plethora of electronics for relatively inexpensive prices, despite the small caveat of longer shipping times.

## **Complications:**
- Getting started. Having almost no background knowledge in any of the components or micropython, I had to scrounge the internet for guides online. I purposely avoided YouTube or copying any existing projects so that I would be learning and problem solving through my own unique build. After forming a foundation, I then created a UML diagram of how all of the components would be wired together and an excel pricesheet tracking all gross expenses so that anyone attempting to recreate the project would be well aware of how much everything costs.
- Mounting the Raspberry Pi Pico using BOOTSEL requires a cable which transfers data. Unbeknownst to me at the time, the majority of the cables I owned only supported charging, with only one of them capable of data transfer.
- Having to find a custom PCB for the PAW3395 sensor, and then a manufacturer to print and ship it inexpensively, as it requires a breakout board to be in between the sensor and lens.

[^1]: The superior connector. Deciding between USB-C and Micro USB was trivial— USB-C is reversible, supports higher USB versions and power delivery, has greater durability, and supports faster data transfer. USB-C is generally more expensive than Micro USB, however the cost difference is negligible and well worth the improved feature set.
[^2]: Deciding between Bluetooth and 2.4GHz RF was simple— Bluetooth pairing wouldn't require a dongle and is slightly more efficient when it comes to power and actually uses 2.4GHz frequency as well; however using 2.4GHz RF means having a much shorter latency (from about 100-200ms to 1ms), greater connection range, less general interference and easier pairing- and ultimately I went with 2.4GHz RF.
