# Install XFCE Desktop Environment on WSL Ubuntu with XRDP

This guide helps you set up the lightweight **XFCE desktop environment** and enables remote desktop access via **XRDP** on your WSL (Windows Subsystem for Linux) Ubuntu installation.

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Step 1: Update & Upgrade Your System](#step-1-update--upgrade-your-system)
- [Step 2: Install XFCE and XRDP](#step-2-install-xfce-and-xrdp)
- [Step 3: Configure XRDP](#step-3-configure-xrdp)
- [Step 4: Set XFCE as Default Session](#step-4-set-xfce-as-default-session)
- [Step 5: Edit XRDP Startup Script](#step-5-edit-xrdp-startup-script)
- [Step 6: Enable and Start dbus & XRDP](#step-6-enable-and-start-dbus--xrdp)
- [Step 7: Check XRDP Status](#step-7-check-xrdp-status)
- [Connect to Your WSL Desktop](#connect-to-your-wsl-desktop)
- [Troubleshooting](#troubleshooting)

---

## Prerequisites

- Windows 10/11 with [WSL2](https://docs.microsoft.com/en-us/windows/wsl/install) installed
- Ubuntu installed on WSL

---

## Step 1: Update & Upgrade Your System

```bash
sudo apt update && sudo apt -y upgrade
```

## Step 2: Install XFCE and XRDP
```bash
sudo apt-get install -y xfce4
```
>If "E: Unable to locate package xfce4-goodiese" <br>
>Run <br>
>sudo add-apt-repository main <br>
>sudo add-apt-repository universe <br>
>sudo add-apt-repository restricted <br>
>sudo add-apt-repository multiverse <br>
>sudo apt update <br>

## Step 3: Configure XRDP

```bash
sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
```
```bash
sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
```
```bash
sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
```
```bash
sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini
```

## Step 4: Set XFCE as Default Session
```bash
echo xfce4-session > ~/.xsession
```
## Step 5: Edit XRDP Startup Script
```bash
sudo nano /etc/xrdp/startwm.sh
```

Add this line <br>

startxfce4

## Step 6: Enable and Start dbus & XRDP
```bash
sudo systemctl enable dbus
sudo /etc/init.d/dbus start
sudo /etc/init.d/xrdp start
```
## Step 7: Check XRDP Status
```bash
sudo /etc/init.d/xrdp status
```
