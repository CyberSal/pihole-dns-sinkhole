# 🛡️ Raspberry Pi DNS Sinkhole with Pi-hole  
*A personal cybersecurity project to block ads and trackers network-wide using a Raspberry Pi 4 and Pi-hole.*

---

## 🧠 Overview

This project transforms a Raspberry Pi into a **DNS sinkhole** using [Pi-hole](https://pi-hole.net/). It blocks ads, trackers, and malicious domains at the DNS level — across all devices on a local network. This project was completed as part of my hands-on learning while studying for the **CCNA** certification and building real-world networking + security experience.

---

## 💻 Tech Stack

- **Hardware**: Raspberry Pi 4 Model B  
- **OS**: Raspberry Pi OS Lite (headless setup)  
- **DNS Filter**: Pi-hole  
- **Network**: Eero Router (Metronet ISP)  
- **Control**: SSH from Windows  
- **Optional Tools**: OBS for screen recording (YouTube content), iPhone for mobile testing  

---

## ⚙️ Setup Instructions

### 1. Flash Pi OS Lite to SD Card
- Used **Raspberry Pi Imager**
- Enabled SSH by adding an empty file named `ssh` to the boot partition

### 2. Connect Pi to Network
- Used **Ethernet** to connect to Eero router
- Found IP address in **Eero app** (`192.168.4.80`)
### 3. SSH into Raspberry Pi

```bash
ssh pi@192.168.4.80
```

### 4. Install Pi-Hole
```curl -sSL https://install.pi-hole.net | bash```

During setup:

Chose Cloudflare (1.1.1.1) as upstream DNS

Enabled web admin interface

Accepted default blocklists

### 5. Reserve Static IP in Eero
Open Eero app

Go to: Settings → Network Settings → Reservations

Reserve: 192.168.4.80 for Raspberry Pi

This prevents the Pi's IP from changing after a reboot.

### 6. Set Pi-hole as Network DNS
In your Eero app:

```Navigate to:
Settings → Network Settings → DNS → Custom DNS
Primary DNS: 192.168.4.80
Secondary DNS: 8.8.8.8
