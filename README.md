# Eclipse Shield

## Index
- [Intro](#intro)
  - [What is Meshtastic?](#what-is-meshtastic)
  - [How does it work?](#how-does-it-work)
  - [Why should you get involved?](#why-should-you-get-involved)
- [Build](#build)
  - [Choose a configuration](#choose-a-configuration)
  - [Order parts](#order-parts)
  - [Assembly and Firmware Installation](#assembly)
  - [Case](#case)
- [Finish](#finish)
  - [App overview & tips](#app-overview--tips)
  - [Get involved!](#get-involved)
  - [Project Hub](#project-hub)

---

## Intro

### What Is Meshtastic?
[Meshtastic](https://meshtastic.org/docs/introduction/) is an open-source, decentralized communication system that uses LoRa (Long Range) radio technology to enable encrypted, low-power digital messaging between devices known as *nodes*. Nodes can take several forms, including handheld devices with integrated displays, compact Bluetooth-enabled units that interface with smartphones, or permanently installed high-power stations designed for wide-area coverage.

Meshtastic is commonly used by hobbyists, outdoor enthusiasts operating beyond cellular coverage, and for emergency or resilient communications during network outages. Its decentralized architecture and low cost make it well suited as an educational platform for students.

![Meshtastic Diagram Visual](https://meshtastic.org/assets/images/lora-topology-2-c80684f1eafdf2a71fbaf26e494fb26d.webp)

- [SE Mesh Network](https://meshinfo.almesh.net/map.html)
- [Worldwide Mesh Map](https://meshmap.net/)

---

## How does it work?

In North America, Meshtastic operates in the unlicensed **915 MHz ISM band**. LoRa modulation enables long-range communication at very low power levels by trading data rate for sensitivity and range. Payload sizes are typically limited to **256 bytes per message**.

The maximum permitted effective isotropic radiated power (EIRP) in this band is **+30 dBm (1 W PEP)**, or **+36 dBm EIRP** when accounting for antenna gain. Operating outside of these limits is strictly prohibited by the [FCC](https://docs.fcc.gov/public/attachments/FCC-02-151A1.pdf).

Meshtastic supports multiple radio presets, ranging from short-range, high-bandwidth modes to long-range, low-bandwidth configurations. The most commonly used open-channel preset is **Long / Fast** (1.07 kbps, 250 kHz), which balances throughput and coverage and is the default configuration.

Nodes form a **self-healing mesh network** by rebroadcasting messages. A configurable hop limit controls how many times a packet may be relayed, allowing the network to scale while limiting congestion and signal degradation.

Channels such as *LongFast* are encrypted using **AES-256 (CTR mode)** with a pre-shared channel key. Direct messages use public/private key pairs for end-to-end encryption. Messages are cryptographically signed, allowing recipients to verify the sender’s identity. Packet headers remain unencrypted to support routing and rebroadcasting.

Optionally, Meshtastic supports **MQTT bridging**, which tunnels mesh traffic over the internet. This allows geographically separated mesh networks to interconnect, at the cost of relying on grid infrastructure.

---

## Why should you get involved?

Building a Meshtastic node offers a hands-on introduction to microcontrollers, radio frequency (RF) technology, and even 3D printing. Whether you’re just getting started or already have experience, this project provides practical exposure to hardware configuration, firmware flashing, RF principles, filters, and antennas.

The ultimate goal is to spark innovation within the Auburn engineering community by inspiring students to learn, invent, and build together. Our community is welcoming and eager to help—join us in building a resilient network and discovering new engineering possibilities.

---

## Build

### Choose a configuration

When choosing your Meshtastic node configuration, you can prioritize features such as connectivity (Wi-Fi, BLE), GPS, sensor integration, or display options. The choice of microcontroller (MCU) affects power consumption, performance, and expandability.

#### 1. ESP32-Based MCUs
- **Examples**
  - [Seeed Studio Wio-SX1262 + XIAO ESP32-S3](https://www.seeedstudio.com/Wio-SX1262-with-XIAO-ESP32S3-p-5982.html) (~$10)
  - [Heltec WiFi LoRa 32 V4](https://heltec.org/project/wifi-lora-32-v4/) (~$20)

- **Pros:** Wi-Fi, BLE, LoRa, good processing power  
- **Cons:** Higher power consumption, especially with Wi-Fi enabled

#### 2. nRF52840-Based MCUs
- **Example**
  - [RAKWireless RAK4631 WisBlock Kit](https://store.rakwireless.com/products/wisblock-meshtastic-starter-kit) (~$30)

- **Pros:** Excellent power efficiency  
- **Cons:** No Wi-Fi, limited processing power

#### 3. RP2040-Based MCUs
- **Example**
  - [Raspberry Pi Pico](https://www.raspberrypi.com/products/raspberry-pi-pico/)

- **Pros:** Low cost, flexible, low power  
- **Cons:** No built-in Wi-Fi, BLE, or LoRa

#### 4. Linux-Based Systems
- **Examples**
  - Raspberry Pi Zero 2 W, Pi 3/4

- **Pros:** Full Linux environment, MQTT bridging, advanced networking  
- **Cons:** Higher power consumption, less portable

#### Pre-Built Nodes
If you prefer a simpler option, consider pre-built devices such as the **Heltec V3/V4**, **WisMesh Pocket V2 / Tag**, or **T-Echo**, many of which include a case.

---

### Order parts

After selecting your configuration, order all required components, including a **battery, power switch, mounting hardware (screws), and any optional accessories** such as sensors or displays.

If you have access to the **makerspace or e-shop**, most components are available on campus. Many parts are also stocked in the **SPARC lab**.

You will likely need to assemble a **custom power harness**. Before connecting the battery, **double-check polarity** to avoid permanent damage.

To reduce or eliminate costs, consider joining the **Student Projects and Research Committee (SPARC)**—many projects like this can be fully funded.  
 - [SPARC](http://sparc.eng.auburn.edu/)


---

### Assembly

Before beginning assembly, locate the **device-specific assembly guide** for your hardware and read all instructions carefully.

- [Meshtastic – Getting Started](https://meshtastic.org/docs/getting-started/)

> ⚠️ **Important:** Never power on a LoRa radio **without an antenna attached**.  
> Doing so can permanently damage the RF front end.

For firmware installation, the **web flasher is strongly recommended** (Chromium-based browsers only). Advanced users may alternatively use the **Meshtastic CLI**.

---

### Case

We provide a **community-designed case** for the **WisBlock Meshtastic Starter Kit**, and many additional designs are available on [Printables](https://www.printables.com/tag/meshtastic).

If you are new to CAD:
- Download an existing case design
- Focus on basic slicing and printing

Recommended tools:
- **Bambu Studio** or **PrusaSlicer**
- Makerspace self-service station (after required training)

Alternatively:
- Submit a **prototype shop print request**
- Contact someone in the **SPARC lab** for assistance

---

## Finish

> ⚠️ **Important:** Never power on a LoRa radio without an antenna attached.

### App overview & tips

| Node Discovery | Conversations |
|---------------|---------------|
| ![Node Discovery](https://github.com/user-attachments/assets/1c851df6-a3ce-436b-beda-08740e145289) | ![Conversations](https://github.com/user-attachments/assets/c5301803-c47d-48bc-8fab-f305b6b75ca6) |

| Map View | Node Settings |
|---------|---------------|
| ![Map View](https://github.com/user-attachments/assets/7baf5a7e-6fc5-42ea-9f0e-1a3ea84599e9) | ![Node Settings](https://github.com/user-attachments/assets/e2a8bfdd-8a08-4c0f-906a-36b5db98a0ef) |

Install the Meshtastic app:
- **Android:** Google Play / F-Droid
- **iOS:** Apple App Store
- **Linux:** [Meshtasticd](https://meshtastic.org/docs/hardware/devices/linux-native-hardware/)

Power on your node *with the antenna attached*, then connect via Bluetooth or USB.

**Tips**
- Rename your node
- Verify region and frequency (FCC compliance)
- Confirm radio preset (Long/Fast recommended)
- Disable GPS if not needed to save power

---

### Get involved!

Share your builds on Discord and reach out with questions:

- [AU Mesh Discord](https://discord.gg/PmmSCSw7Dn)
- [ALMesh](https://almesh.net)
- [ALMesh Discord](https://discord.gg/ws7EfK8u)
- [Birmingham Mesh Discord](https://discord.gg/BuTd2Kad3K)
- [Georgia Mesh Discord](https://discord.gg/AFmn6rKtDg)
- [Meshtastic Reddit](https://www.reddit.com/r/meshtastic/)
- [Jeff Geerling on YouTube](https://www.youtube.com/watch?v=1_lbvqCQnMY)

### Into cybersecurity?
- [DC256](https://dc256.org)
- [DC205](https://www.dc205.org/)

---

### Project Hub

This is my personal node, built **10-01-2025**.

![PXL_20251001_184140442](https://github.com/user-attachments/assets/b510d343-c675-4101-a1ec-36681779b355)

spectralstrider
![IMG6432854799839528368](https://github.com/user-attachments/assets/89cfc164-8c33-4e62-8246-bc4d5bc38b9b)
kealpy
![PXL_20251202_002340046](https://github.com/user-attachments/assets/7551989e-ee80-47f9-a24d-384c92b04e76)
