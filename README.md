# Custom Mouse

After completing ELEC1601 and being inspired to creating own snake game as my first physical microcontroller (arduino) project, I've decided to scale things up and build my own **wireless mouse**. I've specifically decided to utilise USB-C charging,[^1] and a transceiver / receiver system using 2.4GHz Radio[^2].

## **Components Used**
- Raspberry Pi Pico (USB-C)
- PixArt PAW3395 Sensor
- NRF24L01+ Transceiver + CH340 USB Receiver
- MT3608 2-24V to 5V DC Boost Converter
- 3.7V 1000mAh Lipo Battery + TP4056 Charger Module
- Omron D2F-01L Switch (x2)
- Jumper Wires
- 12V Multimeter

> [!NOTE]
> A multimeter is required to tune the DC boost converter to 5V.

### 1. **Component Configuration**
![component configuration uml diagram](images/mouse%20component%20config.png)

## **Steps taken:**
- Custom breakout board pcb for PAW3395 ordered (credit to [ufan's breakout board](https://github.com/ufan/paw3395_pmw3361_breakout))
- [KiCAD](https://www.kicad.org/download/windows/) used to review PCB and schematic
- Raspberry Pi Pico mounted (BOOTSEL) and .uf2 file uploaded (easier programming, can be downloaded [here](https://www.raspberrypi.com/documentation/microcontrollers/micropython.html) or in the repo files))
- [Thonny](https://thonny.org/) used to upload nrf24l01.py driver (for wireless transceiver, can be downloaded [here](https://github.com/micropython/micropython-lib/tree/master/micropython/drivers/radio/nrf24l01) or in the repo files)
- Bought a sensor with an LM19-LSI lens; ufan's breakout board layered in between sensor and lens ![exploded view of assembly with lm19-lsi lens](images/paw3395dm-t6qu%20exploded%20view.png)


## **Useful Links:**
- [NRF24L01 Pinout](https://howtomechatronics.com/wp-content/uploads/2017/02/NRF24L01-Pinout-NRF24L01-PA-LNA-.png)
- [Raspberry Pi Pico Pinout](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-pinout.svg)
- [PixArt PAW3395 Sensor Datasheet](https://www.codico.com/en/mpattachment/file/download/id/1236/) (contains assembly and schematic)
- [Pricesheet](https://1drv.ms/x/c/81566783f4b27a85/Eb886e1THZZElGMRDwNFMZEBl47CX9LvK6eldiMpxhTBGg?e=1K7VTB)

[^1]: The superior connector. Deciding between USB-C and Micro USB was trivial— USB-C is reversible, supports higher USB versions and power delivery, greater durability, faster data transfer. Generally USB-C is more expensive than Micro USB, however the cost difference was negligible.
[^2]: Deciding between Bluetooth and 2.4Ghz RF was simple— Bluetooth pairing actually uses 2.4GHz frequency as well; it wouldn't require a dongle and is slightly more efficient when it comes to power. However, using 2.4GHz RF means having a much shorter latency (from about 100-200ms to 1ms), greater connection range, less general interference and easier pairing.
