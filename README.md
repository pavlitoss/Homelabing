# Homelabing - My home server story

![Banner Image]([LINK TO A PHOTO OF YOUR FINISHED BUILD])
*> (Optional: A photo of your server on your desk)*

##  About This Project

Welcome to my first homelab build! This repository documents the process of creating a budget-friendly server for home use.

Since this was my first time setting up a local server, I have detailed not just the successes, but also the obstacles I faced and the lessons I learned along the way. My goal was to move away from cloud dependance and recycle some of my old computer hardware components that were not being used. I also wanted to learn more about how servers work, what services they can offer and expand skills like system administration, installing and deploying docker containers, etc.

This repository hosts:
1.  **3D Model Files:** Custom add-ons I designed to fit the case.
2.  **Hardware Specs:** The budget component list.
3.  **Build Log:** My experience setting up the software stack.

---

## ⚠️ Important: Compatibility & License

**This project is designed as an add-on.**

The core enclosure for this server relies on a design by **Reeal**. Due to the license of the original file (Standard Digital File License), I cannot redistribute the base files here. You must download the base unit from the link below:

* **Required Base Model:** https://makerworld.com/en/models/1749248-pc-testbench-for-matx-mainboard-and-atx-psu
* **My Contribution:** The files in *this* repository are custom accessories I designed from scratch to clip/screw onto that base model.

---

## ⚙️ Hardware Specifications

These are the components I used.

| Component | Model/Specs |
| :--- | :--- |
| **Motherboard** | Foxconn H67M-V MATX|
| **CPU** | Intel Core i5 2500|
| **RAM** | Mushkin DDR3 8gb (2x4 gb Dual-Channel) 1600MHz|
| **Storage** | Patriot 512GB SATA3 SSD |
| **Power Supply** | Corsair CX550M |

---

## 📝✂️ Materials

These are the components needed for the project.

| Component |
| :--- |
| 750gr of PLA+ or PETG|
| 42x M3 screws 3mm|
| 6x 5mm standoffs for m3 screws|
| Superglue|
| Zip - ties (cable management)|
| Tools (3d printer, screwdriver)|

---

## 🛠️ The 3D Printed Add-ons

I designed the following parts to enclose the build and protect it from dust.

### File Included
* **`server_all_parts.3mf`**: All the parts and some variations for building an enclosure for the server.

### Print Settings
* **Material:** PLA+ or PETG ~750 grams
* **Infill:** 15% Grid
* **Supports:** Not required

---

## 🏗️ The Build Process & Challenges

As this was my first build, things didn't go perfectly according to plan.

### Step 1: Assembling the Computer
* First of all Reeal's testbench needs to be printed.
* Then assemble the hardware (motherboard, cpu, cooler, ram, psu, ssd) on the testbench. It is a fairly straightforward process since it is an open design that allows for cables to pass through holes in the design. I used the M3 standoffs to hold the motherboard in place.

### Step 2: Basic setup
* I found it easier to go through the OS installation now because having an open computer is easier to troubleshoot than having to assemble and dissasemble a closed box.
* I used an external monitor, keyboard and mouse to install Ubuntu 24.04 LTS, setup a static IP, and install XRDP in order to make it easier to work with in the future, witout needing all the input/output devices.
* Make sure to disable auto power-off, a Ubuntu feature that shuts down the computer if it does not receive input in a long time
  ```bash
  sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

* Enable ssh (makes it easier for setup from another device).


### Step 3: Designing the rest of the enclosure
* Having an open pc on my house looks bad and is also in danger of collecting dust. That is why I decided to put my few Fusion 360 skills to the test and design a sleek , minimal case to surround the server.
* I could not find any other design that fit my motherboard size, so I created one from scratch. Since I did not know how much space I would eventually need for the server, I opted for an expandable approach. A 5-panel design that can fit the original test bench, and also be expanded upwards in the future in case I need to add more storage or a graphics card.
* Airflow was a very important factor to consider when making these. The pc is consisted of old components which means they might encounter quite some stress during runtime. This means that good airflow is critical in order to maintain stable temperatures.

### Step 4: Assembly
* The assembly process was pretty easy to walk through. After many failed prints and multiple parts tweaked, everything fits with millimeter level precision.
* First comes glueing the small 90 degree pieces on top of the test bench, one on every angle. I used superglue for this.
* After that, screw the 4 panels around the motherboard (make sure the connecting pieces have been placed correctly to fit the screw holes).
* Then add another 4 connectors on the top side of each panel for added rigidity.
* If the design can fit every component of the pc, screw the top cover. Else, glue another 4 connectors on top of the previous ones and repeat the process with extra panels.

### Step 5: Final Setup
* After having assembled everything, I used my laptop to connect remotely to the server.
* One of the first things I did was install Docker, because of its robust container system which offers a very clean self hosting approach.
* I decided to use casaOS, a docker image with a virtual dashboard that allows me to monitor the server's resources and manage all my containers.
* After that everything was set! I have now setup many services that I find usefull and also hosted some of my own web projects from time to time.
* I also made sure to acquire a domain and setup a Cloudflare tunnel in order to be able to access parts of my server from anywhere in the world.
  
---

## 💻 Software Stack

The server is currently running  Ubuntu Server 24.04.

**Services Running (Docker):**
* CasaOS - main dashboard
* Stremio - movies streaming
* Kuma - monitoring of all services
* N8n - AI agent automation with many simple tasks
* PostgreSQL - my own database for my projects
* Grafana - monitoring with realtime charts
* Ollama - my own watered-down llm hosted locally, used along with n8n for maximum data privacy 
* Reactive Resume - a user friendly resume creator

  I am also using the server as a NAS. CasaOS provides support for NAS natively so I did not have to do much to set this up. The server already contains many of the notes I used in different lessons on my university, and now I can access my study material from any device in my local network, even my phone! This was a real help during exam season.

---

## 🔮 Future Upgrades

* [ ] Add a secondary backup drive. I have already acquired 4 TBs of storage in order to run a RAID configuration and store more files locally.
* [ ] Improve cable management.
* [ ] Set up a VPN for remote access with Tailwind
* [ ] Install more of my own old projects so that I can have interactive demos of all my previous projects.
* [ ] Expand the server vertically along with the new storage addition. I will probably have to design hot swappable slots for HDDs.
* [ ] Upgrade the hardware and run bigger and more power hungry ai models. For now I am using tinyllama, one of the most lightweight ai models I could find.

---
I hope my work has inspired someone to try out themselves creating a local server. This project, despite its difficulties was a real challenge for me which helped me gain valuable experience and become a much better computer engineer.
*This project is for educational purposes.*
