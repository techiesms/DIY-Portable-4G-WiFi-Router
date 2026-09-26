# 📶 DIY Portable 4G WiFi Router

**Insert a 4G SIM → power it up → get WiFi anywhere.**

A portable 4G LTE WiFi router built with just two readily available modules: a **Quectel EC200U-CN 4G board** and a **Raspberry Pi Zero W**. Connect your phone or laptop to it and browse or stream on the go.

🎥 **Watch the full build:** [YouTube Video](https://youtu.be/cQ6IcNhCyQ8)
🛒 **Get the components:** [techiesms.com](https://techiesms.com)

---

## ✨ Features

- Works with any 4G SIM that has an active data plan
- Creates its own WiFi hotspot (default SSID: `PiRouter`)
- Built-in **web configuration portal**: change the WiFi name, WiFi password and APN from your phone, no SSH needed
- WiFi and the portal stay available even if LTE is down, the SIM is missing or the APN is wrong
- Starts automatically on boot
- **Ready-to-flash OS image** (coming soon), so you can build it without typing a single command

---

## 🧰 Hardware Required

| Component | Link |
|---|---|
| 4G GNSS Board – Quectel EC200U-CN | [Buy](https://techiesms.com/product/capuf-ec200u-cn-4g-modem-with-gnss-gps/) |
| Raspberry Pi Zero W | [Buy](https://techiesms.com/product/pi-zero-w-board-india/) |
> **Note:** The EC200U-CN is an LTE Cat 1 module (up to 10 Mbps down / 5 Mbps up). In our tests we got around 4 Mbps, which is enough for browsing and YouTube streaming. Actual speed depends on your network coverage.

---

## 🏗️ How It Works

```
Internet ⇄ Mobile Network ⇄ SIM ⇄ Quectel EC200U ──USB──► Raspberry Pi Zero W ──WiFi──► Phone / Laptop
                                                              │
                                                              └─ Web portal: http://10.42.0.1:5000
```

- **ModemManager** talks to the EC200U
- **NetworkManager** runs the cellular connection and the WiFi hotspot, and shares internet between them
- **Flask** serves the local configuration and status webpage

---

## 📂 Repository Contents

| File | Description |
|---|---|
| `docs/EC200U-USB-Dongle-macOS-Guide.pdf` | Use the EC200U-CN as a USB internet dongle on macOS (native ECM mode, no vendor driver, no VM) |
| `docs/PiRouter-Setup-Guide.pdf` | Complete step-by-step guide to turn a Raspberry Pi into a 4G WiFi router with a web config portal |
| `os-image/` | Ready-to-flash PiRouter OS image — **coming soon** |

---

## 🚀 Quick Start (Ready-Made OS Image)

> ⏳ The OS image will be uploaded soon. Star ⭐ or watch this repo to get notified.

### 1. Flash the OS
1. Download the PiRouter OS image from this repo.
2. Open **Raspberry Pi Imager**.
3. **Choose Device** → Raspberry Pi Zero.
4. **Choose OS** → *Use Custom* → select the downloaded image file.
5. **Choose Storage** → select your **64GB microSD card**.
6. Click **Next** and confirm. Flashing and verification take a while.

### 2. Connect & Configure
1. Insert the SIM into the 4G module and the SD card into the Pi, then power it up.
2. On your phone or laptop, connect to WiFi:
   - **SSID:** `PiRouter`
   - **Password:** `12345678`
3. Open **http://10.42.0.1:5000** in your browser.
4. Enter your SIM's **APN** and set your own **WiFi name and password**.
5. Click **Save & Apply**, then reconnect to your new WiFi name.

**Common APNs in India:**

| Carrier | APN |
|---|---|
| Jio | `jionet` |
| Airtel | `airtelgprs.com` |
| Vi | `www` |

> 🔐 Change the default WiFi password on first use.

---

## 🛠️ Build It From Scratch

Prefer to set everything up yourself? Follow [`docs/PiRouter-Setup-Guide.pdf`](docs/PiRouter-Setup-Guide.pdf). It covers:

- Installing NetworkManager, ModemManager and Flask
- Verifying the LTE modem
- Creating the WiFi hotspot and cellular connections
- Building the web configuration portal
- Reliable auto-start on boot
- Diagnostics and troubleshooting
- Creating your own master SD card image

---

## 💻 Bonus: Use the EC200U as a USB Dongle on Mac

Want to use the 4G module directly with your Mac? [`docs/EC200U-USB-Dongle-macOS-Guide.pdf`](docs/EC200U-USB-Dongle-macOS-Guide.pdf) shows how to use it as a native USB internet connection, with no vendor driver and no Linux VM.

---

## 🩺 Troubleshooting

| Problem | What to check |
|---|---|
| `PiRouter` WiFi not showing | Wait 1–2 minutes after power-up; check the power supply |
| WiFi connects but no internet | Check the APN in the portal, the SIM data plan and signal strength |
| Portal not opening | Make sure you're connected to the Pi's WiFi and use `http://` (not https) |
| Modem not detected | Check the USB/OTG connection and the power to the 4G module |

For detailed diagnostics, see section 16 of the PiRouter Setup Guide.

---

## 🔮 What's Next

We're limited by the Cat 1 speed of the EC200U. Know a faster 4G module we should try for V2? Let us know in the YouTube comments or on WhatsApp!

---

## 🤝 Connect with Techiesms

- 🌐 Store: [techiesms.com](https://techiesms.com)
- 🎓 Courses: [techiesms.graphy.com](https://techiesms.graphy.com)


If this project helped you, give the repo a ⭐. It really helps!
