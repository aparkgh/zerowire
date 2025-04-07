# Custom Mouse

After completing ELEC1601 and being inspired to create my own snake game in a small arduino project, I've decided to scale up things and build my own **wireless mouse**. I've specifically decided to utilise 2.4GHz to avoid bluetooth, and a battery charger with USB-C.

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
- unfinished :( still waiting for parts to arrive

### 1. **Component Configuration**
![component configuration uml diagram](images/mouse%20component%20config.png)

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

> ![NOTE]
> A multimeter is required to tune the DC boost converter to 5V.
