# Custom Mouse

After completing ELEC1601 and being inspired to creating own snake game as my first physical microcontroller (arduino) project, I've decided to scale things up and build my own **wireless mouse**. I've specifically decided to utilise a transceiver and receiver system using 2.4GHz to avoid using bluetooth, and incorporated USB-C charging.

## **Components Used**
- Raspberry Pi Pico (USB-C)
- PixArt PAW3395 Sensor
- NRF24L01+ Transceiver + CH340 USB Receiver
- MT3608 2-24V to 5V DC Boost Converter
- 3.7V 1000mAh Lipo Battery + TP4056 Charger Module
- Omron D2F-01L Switch (x2)
- Jumper Wires
- 12V Multimeter

## **Steps taken:**
- Custom breakout board pcb for PAW3395 ordered from JLCPCB (upload gerber files from [ufan's paw3395 repository](https://github.com/ufan/paw3395_pmw3361_breakout))
- [KiCAD](https://www.kicad.org/download/windows/) used to review PCB and schematic
- Raspberry Pi Pico mounted (BOOTSEL) and .uf2 file uploaded (easier programming, can be downloaded [here](https://www.raspberrypi.com/documentation/microcontrollers/micropython.html))
- [Thonny](https://thonny.org/) used to upload nrf24l01.py driver (can be downloaded [here](https://github.com/micropython/micropython-lib/tree/master/micropython/drivers/radio/nrf24l01)) (for wireless transceiver)

### 1. **Component Configuration**
![component configuration uml diagram](images/mouse%20component%20config.png)

> [!NOTE]
> A multimeter is required to tune the DC boost converter to 5V.
