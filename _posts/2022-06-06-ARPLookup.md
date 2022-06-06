---
title: ARPLookup - Batu33TR's Project
date: 2022-06-06 21:46:00 UTC+3
categories: [Batu33TR's Projects]
tags: [ethical-hacking]
---

<img src="/assets/img/2022-06-06-ARPLookup/banner.png" alt="ARPLookup" />

Ever wanted to scan IP addresses on the network? With ARPLookup script, it's possible to detect devices connected to network with their MAC addresses.

A **Netdiscover** similar script collects information by _broadcasting ARP_ on the network and displays it in the form of a list. **Written with [Python 3](https://www.python.org/)**. It is completely open source and supporting _Linux, Windows and macOS_ (not tested) platforms. Requires administrator/sudo privileges to work. **[Source code are available here](https://github.com/Batu33TR/ARPLookup)**

## Installing on Linux

* Using this script on Linux is so easy. Install Python and Git with package manager

```bash
sudo apt install git python3 python3-pip # For Debian / Ubuntu
```
```bash
sudo pacman -S git python3 python3-pip # For Arch Linux / Manjaro
```
```bash
sudo zypper in git python3 python3-pip # For OpenSUSE
```

* Clone repository after install required packages

```bash
git clone https://github.com/Batu33TR/ARPLookup
```

* Switch cloned directory and install dependencies for Python

```python
sudo pip install -r requirements.txt
```

* And you're ready. Check installation with this command:

```bash
kali@kali~$ python3 ARPLookup.py
ARPLookup started
Usage: python3 arplookup.py -r <IP_RANGE>
```

## What about Windows?
<img src="/assets/img/2022-06-06-ARPLookup/1-no-pcap.png" alt="Windows says no libpcap provider available" />

As you can see in the picture, ARPLookup.py says **_There's no libpcap provider available!_**. But don't worry, solution is easy.

### Installing NPCAP to Windows

* **(Quotation) What is NPCAP:** Npcap is the Nmap Project's packet capture (and sending) library for Microsoft Windows. It implements the open Pcap API using a custom Windows kernel driver alongside our Windows build of the excellent libpcap library. This allows Windows software to capture raw network traffic (including wireless networks, wired ethernet, localhost traffic, and many VPNs) using a simple, portable API. Npcap allows for sending raw packets as well. Mac and Linux systems already include the Pcap API, so Npcap allows popular software such as Nmap and Wireshark to run on all these platforms (and more) with a single codebase.

* Go to [https://npcap.com/#download](https://npcap.com/#download)

<img src="/assets/img/2022-06-06-ARPLookup/2-npcap-site.png" alt="Npcap site" />

* Click **_Npcap Installer_** and download it.
* Follow the installation steps and npcap is ready.

### Python for Windows

* Now install [Python for Windows](https://www.python.org/downloads/) and don't for get to tick "Add Python to PATH"

<img src="/assets/img/2022-06-06-ARPLookup/3-python-for-windows.png" alt="Python for Windows" />

### Download source

* Download ARPLookup source as ZIP and extract to Desktop

<img src="/assets/img/2022-06-06-ARPLookup/4-arplookup-download-zip.png" alt="Download ARPLookup source as ZIP file" />

### And run it

* Open a **CMD/PowerShell as Administrator** and switch extracted folder. Example:

```powershell
PS C:\Users\Batu33TR> cd .\Desktop\ARPLookup
PS C:\Users\Batu33TR\Desktop\ARPLookup>
```
* Now test ARPLookup if script works correctly

```powershell
PS C:\Users\Batu33TR\Desktop\ARPLookup> python .\ARPLookup.py
ARPLookup started
Usage: python arplookup.py -r <IP_RANGE>
PS C:\Users\Batu33TR\Desktop\ARPLookup>
```

* And kaboom, ARPLookup is ready to use on Windows. Congratulations.

<img src="/assets/img/2022-06-06-ARPLookup/5-arplookup-ready-to-use.png" alt="ARPLookup ready to use on Windows"/>

## Usage

### Detecting subnet mask range

* First, open a terminal and type the following command:

```bash
kali@kali~$ ifconfig # For Linux
```
```powershell
PS C:\Users\Batu33TR> ipconfig # For Windows
```

<img src="/assets/img/2022-06-06-ARPLookup/6-detecting-subnetmask.png" alt="Detecting subnetmask on Linux" />
<img src="/assets/img/2022-06-06-ARPLookup/7-detecting-subnetmask-windows.png" alt="Detecting subnetmask on Windows" />

* As seen in the terminal output in the picture, the network interface name is eth0 and it uses **subnet 255.255.255.0 mask as 192.168.28.0** so this subnet is **24 bit**.

### Time to run script and detect devices

* Now, time to scan connected devices and detect IP with MAC. Switch to ARPLookup directory and run the script

```bash
kali@kali~$ sudo python3 ARPLookup.py -r 192.168.28.0/24
```

* After ~5 seconds, devices will be detect and listed by ARPLookup.

<img src="/assets/img/2022-06-06-ARPLookup/8-results.png" alt="Results" />

* Congratulations, ARPLookup run was successfully completed. As can be seen in the picture, devices connected to the network have been detected.

## Warning
* The devices shown in the pictures are **all is just virtual machines and connected to private virtual network**. **No 3rd party device, network or person is targeted here**. Use it only on networks you are authorized. This script is for **testing purposes only!**
