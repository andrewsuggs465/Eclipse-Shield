# Eclipse Shield
## Intro
 - ### What is Meshtastic?
 - ### How does it work?
 - ### Why should you get involved?

## Build
 - ### Choose a configuration
 - ### Order parts (more to come)
 - ### Assembly
 - ### Firmware installation
 - ### Case

## Finish
 - ### App overview/tips
 - ### Get involved!
 - ### Project Hub


<br>
<br>


## Intro
###  What Is Meshtastic?  
[Meshtastic](https://meshtastic.org/docs/introduction/) is an open-source, decentralized communication system that uses LoRa (Long Range) radio technology to enable encrypted, low-power digital messaging between devices known as nodes. Nodes can take several forms, including handheld devices with integrated displays, compact Bluetooth-enabled units that interface with smartphones, or permanently installed high-power stations designed for wide-area coverage. Meshtastic is commonly used by hobbyists, outdoor enthusiasts operating beyond cellular coverage, and for emergency or resilient communications during network outages. Its decentralized architecture and low cost make it well suited as an educational platform for students.
![Meshtastic Diagram Visual](https://meshtastic.org/assets/images/lora-topology-2-c80684f1eafdf2a71fbaf26e494fb26d.webp)
 - [SE Mesh Network](https://meshinfo.almesh.net/map.html) <br>
 - [Worldwide map](https://meshmap.net/)


## How does it work?
In North America, Meshtastic operates in the unlicensed 915 MHz ISM band. LoRa modulation enables long-range communication at very low power levels by trading data rate for sensitivity and range. Payload sizes are typically limited to 256 bytes per message. <br>
The maximum permitted effective isotropic radiated power (EIRP, or power outputted by the transceiver) in this band is +30 dBm (1W peak envelope power or PEP), or +36 dBm EIRP (with ~5.8 dBi gain from antenna) operating outside of these specifications is strictly prohibited by the [FCC](https://docs.fcc.gov/public/attachments/FCC-02-151A1.pdf). <br>
Meshtastic supports multiple radio presets, ranging from short-range, high-bandwidth modes to long-range, low-bandwidth configurations. The most commonly used open-channel preset is Long / Fast (1.07 kbps, 250 kHz), which balances throughput and coverage. Most people use the Long/Fast preset, which is default behavior.<br>
Nodes form a self-healing mesh network by rebroadcasting messages. A configurable hop limit controls how many times a packet may be relayed, allowing the network to scale while limiting congestion and signal degradation. <br>
Channels like longfast are encrypted using AES-256 in CTR mode with a pre-shared channel key. Direct messages use private/public key for e2e encryption. The messages are signed individually using this unique private key, allowing recipients to verify the sender’s identity. Packet headers remain unencrypted to allow routing and rebroadcasting. <br>
Optionally, Meshtastic supports MQTT bridging, which tunnels mesh traffic over the internet. This allows geographically separated mesh networks to interconnect, at the cost of relying on grid infrastructure. <br>


## Why should you get involved?
Building a Meshtastic node offers a hands-on introduction to the exciting world of microcontrollers, radio frequency (RF) technology, and even 3D printing. Whether you’re just getting started or already have some experience, this project is accessible and provides valuable knowledge in hardware configuration, serial firmware flashing, RF principles, filters, and antennas. Thanks to the affordability of the hardware and its scalable difficulty, there’s plenty of room for growth as you dive deeper into the project.
<br>
The ultimate goal is to spark innovation within the Auburn engineering community, inspiring students to become passionate about learning, inventing, and creating. Our community is welcoming and always eager to help. So, join us in building a robust network, and discover a world of engineering that could open your eyes to new possibilities!


## Build
 
### Choose a configuration
When choosing your Meshtastic node configuration, you can prioritize different features like connectivity (Wi-Fi, BLE), GPS, sensor integration, or screen/display options. The choice of microcontroller (MCU) will affect your node’s capabilities, size, and compatibility with other components.

Here are some **MCU options** commonly used in Meshtastic projects:

### **1. ESP32-Based MCUs**

- **Popular ESP32 Variants:**
  - [Seeed Studio Wio-SX1262 with Xiao ESP32S3](https://www.seeedstudio.com/Wio-SX1262-with-XIAO-ESP32S3-p-5982.html) (~$10)
  - [Heltec WiFi LoRa 32 V4](https://heltec.org/project/wifi-lora-32-v4/) (~$20)

- **Features:**
  - **Connectivity:** Wi-Fi, BLE, LoRa
  - **Advantages:** Good processing power - can integrate with various sensors (temperature, humidity, motion), displays, and buttons
  - **Limitations:** Higher power consumption, especially with wifi

### **2. nRF52840-Based MCUs**

- **Popular nRF52840 Variants:**
  - [RAKWirless RAK4631 Kit](https://store.rakwireless.com/products/wisblock-meshtastic-starter-kit?index=6&intsource=rak_store&intmedium=organic&intcampaign=meshtastic_collection_page&intterm=hot_deals&intcontent=product_image&variant=43884034621638) ~$30

- **Features:**
  - **Connectivity:** Bluetooth Low Energy (BLE), LoRa radio
  - **Advantages:** Excellent power efficiency
  - **Limitations:** No wifi, limited processing power

### **3. RP2040-Based MCUs**

- **Popular RP2040 Variants:**
  - [Raspberry pi pico](https://www.raspberrypi.com/products/raspberry-pi-pico/)

- **Features:**
  - **Connectivity:** Can be paired with LoRa radio modules and sensors
  - **Flexibility:** Highly customizable; low-cost and low-power. Can work with Bluetooth and Wi-Fi using external modules.
  - **Advantages:** Cost-effective, community-built libraries, low power consumption, moderate performance
  - **Limitations:** Lacks built-in wifi/bt and LoRa chip

### **4. Linux-Based Systems**

- **Supported Platforms:**
  - Raspberry Pi Zero 2W or Pi 3/4
  - Linux-based systems (with Wi-Fi, Ethernet, etc.)

- **Features:**
  - **Connectivity:** Full Linux environment allows for easy integration with Wi-Fi, Ethernet, GPS, and other modules.
  - **Flexibility:** Supports the full Meshtastic stack, MQTT bridges, and the ability to run more advanced software.
  - **Advantages:** Powerful platform for advanced networking, easy to connect to the internet, and can host additional services like MQTT bridges.
  - **Limitations:** Less portable than other nodes (needs power supply), larger in size, and consumes more power.

### **Pre-Built Nodes (for Simplicity)**  

If you're not interested in building a custom node from scratch, there are numerous nodes like the Heltec V3/V4, Wismesh Pocket V2/Tag, and T Echo -- some of which come fully assembled with a case.

### **Useful Resources**

Here are some helpful resources for building and configuring your Meshtastic node:

- **[Comprehensive device guide from Meshtastic](https://meshtastic.org/docs/hardware/devices/)** – A full guide on supported devices and build options.
  
- **[RAKWireless](https://store.rakwireless.com/collections/meshtastic)** – For pre-built devices and modules for Meshtastic.
  
- **[LILYGO](https://lilygo.cc/collections/lilygo-with-meshtastic)** – A range of affordable and customizable Meshtastic devices.
  
- **[Heltec](https://heltec.org/product-category/lora/meshtastic/)** – Explore Heltec’s offerings for reliable and feature-packed nodes.
  
- **[Seedstudio](https://www.seeedstudio.com/meshtastic-products)** – Seeed Studio offers affordable options for easy-to-use Meshtastic devices.
  
- **[Amazon](https://www.amazon.com/meshtastic-devices/s?k=meshtastic+devices)** – Find various Meshtastic nodes and accessories on Amazon.



### **Online Build Tool**

- **[Meshtastic Designer](https://meshtastic-designer.rakwireless.com/)** – A helpful online tool to assist you in designing and configuring your custom Meshtastic node, including selecting hardware and settings.

### Order parts
Join student projects and research committee ([SPARC](http://sparc.eng.auburn.edu/)) to get projects like this fully funded!
*Makerspace collab?
### Assembly
### Firmware installation
### Case
## Finish


### App overview/tips

### Get involved!
Please share your builds to the discord to be posted here, and feel free to reach out if you have any questions. 

 - [AU Mesh Discord](https://discord.gg/PmmSCSw7Dn) <br>
 - [ALmesh](https://ALmesh.net) <br>
 - [ALMesh Discord](https://discord.gg/ws7EfK8u) <br>
 - [Birmingham Discord]( https://discord.gg/BuTd2Kad3K) <br>
 - [Georgia Discord](https://discord.gg/AFmn6rKtDg) <br>
### Into cyber security?
 - [DC256](https://DC256.org)
 - [DC205](https://www.dc205.org/)


### Project Hub

### Project Hub

