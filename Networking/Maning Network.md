# Ubuntu Network Management Tutorial

## Objective:
Learn how to manage network settings in Ubuntu, including configuring network interfaces, setting up static and dynamic IP addresses, and troubleshooting common network issues.

## Duration:
2 hours

## Prerequisites:
- Basic understanding of Linux commands
- Access to an Ubuntu system

## Materials Needed:
- Ubuntu system (either physical or virtual)
- Terminal application

---

## Steps:

### Part 1: Checking Network Interfaces

1. **List all network interfaces:**
   ```bash
   ip link show
   ```
   This command will display all available network interfaces.

2. **Check the current IP address:**
   ```bash
   ip addr show
   ```
   Look for the interface you are interested in (e.g., `eth0`, `wlan0`).

### Part 2: Configuring Network Interfaces

1. **Identify the network interface you want to configure:**
   Use the output from the previous commands to identify the interface name (e.g., `eth0` for wired or `wlan0` for wireless).

2. **Editing the Netplan configuration (for Ubuntu 18.04 and later):**
   - Open the Netplan configuration file:
     ```bash
     sudo nano /etc/netplan/01-netcfg.yaml
     ```
   - Example configuration for a static IP address:
     ```yaml
     network:
       version: 2
       renderer: networkd
       ethernets:
         eth0:
           dhcp4: no
           addresses:
             - 192.168.1.100/24
           gateway4: 192.168.1.1
           nameservers:
             addresses: [8.8.8.8, 8.8.4.4]
     ```
   - Example configuration for a dynamic IP address (DHCP):
     ```yaml
     network:
       version: 2
       renderer: networkd
       ethernets:
         eth0:
           dhcp4: yes
     ```
   - Save and apply the configuration:
     ```bash
     sudo netplan apply
     ```

3. **Editing the interfaces file (for older Ubuntu versions):**
   - Open the interfaces configuration file:
     ```bash
     sudo nano /etc/network/interfaces
     ```
   - Example configuration for a static IP address:
     ```text
     auto eth0
     iface eth0 inet static
       address 192.168.1.100
       netmask 255.255.255.0
       gateway 192.168.1.1
       dns-nameservers 8.8.8.8 8.8.4.4
     ```
   - Example configuration for a dynamic IP address (DHCP):
     ```text
     auto eth0
     iface eth0 inet dhcp
     ```
   - Save and restart the network service:
     ```bash
     sudo systemctl restart networking
     ```

### Part 3: Wireless Network Configuration

1. **Install necessary tools:**
   ```bash
   sudo apt-get update
   sudo apt-get install wireless-tools wpasupplicant
   ```

2. **Scan for available wireless networks:**
   ```bash
   sudo iwlist wlan0 scan
   ```

3. **Connect to a wireless network:**
   - Open the WPA Supplicant configuration file:
     ```bash
     sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
     ```
   - Add your network details:
     ```text
     network={
         ssid="your_network_name"
         psk="your_network_password"
     }
     ```
   - Save and connect to the network:
     ```bash
     sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
     sudo dhclient wlan0
     ```

### Part 4: Troubleshooting Network Issues

1. **Check network status:**
   ```bash
   systemctl status network-manager
   ```

2. **Restart network services:**
   ```bash
   sudo systemctl restart NetworkManager
   ```

3. **Check routing table:**
   ```bash
   ip route
   ```

4. **Ping to test connectivity:**
   ```bash
   ping google.com
   ```

5. **Check DNS resolution:**
   ```bash
   nslookup google.com
   ```

### Part 5: Advanced Network Management

1. **Install and use `nmtui` for a text-based UI:**
   ```bash
   sudo apt-get install network-manager
   sudo nmtui
   ```
   Use `nmtui` to manage network connections easily through a text-based interface.

2. **Install and use `nmcli` for command-line management:**
   ```bash
   sudo apt-get install network-manager
   ```
   Example commands:
   - List all connections:
     ```bash
     nmcli con show
     ```
   - Connect to a Wi-Fi network:
     ```bash
     nmcli dev wifi connect your_ssid password your_password
     ```

### Conclusion:
You have now learned how to manage network settings in Ubuntu, including configuring network interfaces, setting up static and dynamic IP addresses, connecting to wireless networks, and troubleshooting common network issues. This knowledge is essential for maintaining a reliable network connection on your Ubuntu system.

## Questions:
1. What is the purpose of Netplan in Ubuntu?
2. How can you set up a static IP address using the `nmcli` command?
3. What are some common issues you might encounter when connecting to a wireless network?

Feel free to ask the instructor if you have any questions or need further assistance.