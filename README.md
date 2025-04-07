# Custom Mouse

After completing ELEC1601 and being inspired to create my own snake game in a small arduino project, I've decided to scale up things and build my own **wireless mouse** using a **PAW3395 optical sensor**, **Raspberry Pi Pico**, and a **2.4GHz NRF24L01+ transceiver**. This project allows you to create your own custom USB HID mouse for your computer. I've specifically decided to utilise 2.4GHz to avoid bluetooth, and a battery charger with USB-C.

## 🖱️ **Features**
- **Wireless**: Using a 2.4GHz NRF24L01+ transceiver for wireless communication.
- **High Precision**: Powered by the **PAW3395 optical sensor** for precise tracking.
- **Portable**: Compact, powered by a **1000 mAh battery** with a **DC boost converter** for 5V operation.

## ⚙️ **Components Needed**
- **Raspberry Pi Pico** (Microcontroller)
- **PAW3395 Optical Mouse Sensor**
- **NRF24L01+ Transceiver**
- **MT3608 2-24V to 5V DC-DC Boost Converter**
- **3.7V 1000mAh LiPo Battery** (and **TP4056 charger module**)
- **Omron D2F-01L Mouse Switches**
- **Jumper Wires**
- **USB receiver for NRF24L01+ (CH340 USB Module)**

## 🔧 **Setup Instructions**

### 1. **Wiring the Components**
- **PAW3395 Sensor → Microcontroller**: Connect the optical sensor's data pins (SCL, SDA, etc.) to the Pico's corresponding GPIO pins.
- **Switches → Microcontroller**: Connect the **Omron D2F-01L** switches to the input pins of the Pico.
- **Battery → Boost Converter**: Connect your 3.7V **LiPo battery** to the **MT3608**'s input pins to power the boost converter.
- **Boost Converter → Microcontroller**: The output of the boost converter should be connected to the **5V** input on the Pico.
- **NRF24L01+ → Microcontroller**: Connect the **NRF24L01+** transceiver to the Pico's SPI pins for communication.

### 2. **Powering the Setup**
- Use the **TP4056 charger module** to safely charge the **LiPo battery** through a **USB-C** cable.
- Adjust the MT3608's potentiometer to output **5V** from the battery before powering the Raspberry Pi Pico.

### 3. **Receiver Setup**
- Use the **CH340 USB module** connected to your PC to receive signals from the NRF24L01+ transceiver.
- Install the necessary drivers for **CH340** and configure your computer to recognize the receiver.

## 🧑‍💻 **Code Setup**
The code to run the wireless mouse will include:
- **Pico Firmware**: Handling sensor input and transmitting data via NRF24L01+.
- **PC Receiver Code**: Interpreting signals from the **2.4GHz receiver** to simulate mouse movements and clicks.