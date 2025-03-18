

```markdown
# 🌐 Ubuntu Server Network Configuration Commands (PowerEdge R720)

This file contains essential **networking commands** for managing **Ubuntu Server** on a **Dell PowerEdge R720**.

---

## **🔹 1. Check Network Interfaces**
### List all network interfaces:
```bash
ip a
```
or
```bash
ip link show
```

### Show active network connections:
```bash
nmcli device status
```

### Show detailed network settings:
```bash
sudo netplan get
```

---

## **🔹 2. Enable & Restart Network Services**
### Restart the network service:
```bash
sudo systemctl restart systemd-networkd
```

### Enable networking to start on boot:
```bash
sudo systemctl enable systemd-networkd
```

### Check network service status:
```bash
sudo systemctl status systemd-networkd
```

---

## **🔹 3. Configure a Static IP Address**
### Edit the Netplan configuration file:
```bash
sudo nano /etc/netplan/00-installer-config.yaml
```
### Example Static IP Configuration:
```yaml
network:
  ethernets:
    eno1:  # Change this to your actual network interface
      dhcp4: false
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]
  version: 2
```
### Apply Changes:
```bash
sudo netplan apply
```

---

## **🔹 4. Configure DHCP (Automatic IP)**
### Enable DHCP for an interface:
1. Edit the Netplan file:
```bash
sudo nano /etc/netplan/00-installer-config.yaml
```
2. Use this DHCP configuration:
```yaml
network:
  ethernets:
    eno1:
      dhcp4: true
  version: 2
```
3. Apply the configuration:
```bash
sudo netplan apply
```

---

## **🔹 5. Bring Up or Down a Network Interface**
### Enable (Bring Up) an Interface:
```bash
sudo ip link set eno1 up
```
### Disable (Bring Down) an Interface:
```bash
sudo ip link set eno1 down
```

---

## **🔹 6. Test Internet Connectivity**
### Check if the server can reach the internet:
```bash
ping -c 4 8.8.8.8
```

### Resolve a domain name:
```bash
nslookup google.com
```
or
```bash
dig google.com
```

---

## **🔹 7. Show Routing Table**
```bash
ip route show
```

---

## **🔹 8. Configure DNS Servers**
1. Open the resolv.conf file:
```bash
sudo nano /etc/resolv.conf
```
2. Add custom DNS servers:
```ini
nameserver 8.8.8.8
nameserver 1.1.1.1
```
3. Save & exit (`CTRL+X`, `Y`, `Enter`).

---

## **📌 Notes**
- Use **`ip a`** to identify your active network interface (e.g., `eno1`, `eno2`).
- Changes in **Netplan** require **`sudo netplan apply`** to take effect.
- If networking fails, restart the server:
  ```bash
  sudo reboot
  ```

---

## **📂 Optional: Sync to GitHub**
To keep this file backed up, push it to your **GitHub repository**:
```bash
git add network-commands.md
git commit -m "Added Ubuntu Network Commands"
git push origin main
```

---

### **💾 Save & Use**
- To create this file, run:
```bash
nano network-commands.md
```
- **Paste the content** above and save it (`CTRL+X`, `Y`, `Enter`).

---

Now you have a **complete reference for Ubuntu network commands**! 🚀
```

### **✅ How to Use This**
1. **Copy the entire text above**.
2. Run:
   ```bash
   nano network-commands.md
   ```
3. **Paste the text** into the terminal.
4. **Save the file** (`CTRL+X`, `Y`, `Enter`).


