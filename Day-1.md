# Lab Environment Setup Guide

## Lab Components

- **Kali Linux**: Attacker machine (VirtualBox Appliance)
- **Splunk**: SIEM platform (.deb file for VM installation)
- **OWASP Juice Shop**: Target application (VirtualBox Appliance)
- **Ubuntu Server**: Base system for Splunk installation

---

## Step 1: Create Isolated Network

**Safety Note:** This is the most critical step for maintaining a secure lab environment.

1. Open Oracle VM VirtualBox Manager
2. Navigate to **File** → **Host Network Manager...**
3. Click the **Create** button (a new adapter `vboxnet0` will appear)
4. Ensure the **"Enable Adapter"** checkbox is selected
5. Leave the IP address settings at default (typically `192.168.56.1`)
6. Click **Close**

You've now established a private, host-only network that allows your VMs to communicate securely without connecting to your physical network.

---

## Step 2: Adding Kali Linux VM

### Understanding the Issue

The **"Import Appliance"** function only supports `.ovf` or `.ova` file formats. Your Kali Linux download consists of:
- A `.vbox` configuration file
- A `.vmdk` virtual disk file

These require a different approach than appliance import.

<img width="645" height="584" alt="image" src="https://github.com/user-attachments/assets/fdcc737a-7d70-4c21-b07a-2019d5588717" />


### Solution: Use the Add Method

1. Close any error messages and the import wizard
2. In the VirtualBox Manager main window, navigate to:
   - **Machine** → **Add...** (or use `Ctrl+A` shortcut)

3. In the file browser, navigate to your Kali Linux directory:
   - `D:/VM/kali-linux-2025.2-virtualbox-amd64/`

4. In the bottom-right corner, change the file filter from:
   - **"VirtualBox VM image files (.vbox)"** → **"All Files (*.*)"**

5. Select the configuration file:
   - `kali-linux-2025.2-virtualbox-amd64.vbox`
   - Click **Open**

### Why This Works

The `.vbox` file contains all the VM configuration details (RAM allocation, network settings, disk locations, etc.). The **"Add"** function registers this existing VM with your VirtualBox installation.

---

## Post-Installation Configuration

**Important:** Before starting the Kali Linux VM for the first time:

1. Right-click on the VM in your list
2. Go to **Settings** → **Network**
3. Change the network adapter to **"Host-Only Adapter"**
4. Apply changes and start the VM
