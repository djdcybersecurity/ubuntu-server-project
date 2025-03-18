# ubuntu-server-project

# 🚀 Ubuntu Server Project - PowerEdge R720

This repository documents my setup and configuration of **Ubuntu Server** on a **Dell PowerEdge R720**. The goal is to have a reference for all commands used during installation, networking, software setup, and system administration.

---

## **🖥️ Server Details**
- **Model:** Dell PowerEdge R720
- **OS:** Ubuntu Server 24.04 LTS
- **Boot Mode:** BIOS / UEFI
- **Storage:** Configured with RAID (if applicable)
- **Networking:** Configured with static IP or DHCP

---

## **🔹 1. Creating a Bootable Ubuntu USB**
### **On Windows (Using Rufus)**
1. Download **Ubuntu Server ISO**: [Ubuntu Server Download](https://ubuntu.com/download/server)
2. Use **Rufus** to create a bootable USB:
   - **Partition scheme:** `MBR` (for BIOS/UEFI compatibility) or `GPT` (for pure UEFI).
   - **File system:** `FAT32 (Default)`.
   - **Write mode:** `ISO Image Mode (Recommended)`.
3. Boot from the USB on the **PowerEdge R720** (`F11` → **One-time Boot Menu** → Select USB).

---

## **🔹 2. Installing Ubuntu Server**
1. Choose **Install Ubuntu Server**.
2. Set up **networking** (DHCP or manually assign a static IP).
3. Select **"Erase disk and install Ubuntu"** (this will remove existing OS like TrueNAS).
4. Create an **admin user and password**.
5. Install **OpenSSH Server** (recommended for remote access).
6. Complete installation and **reboot**.

---

## **🔹 3. First-Time Setup Commands**
After logging in, run:
```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Check network configuration
ip a

# Enable and check SSH service
sudo systemctl enable --now ssh
systemctl status ssh

# Find system hardware details
lscpu
lsblk
