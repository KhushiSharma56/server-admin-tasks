# XCP-ng Installation & Setup on Bare-Metal Server

## 1. Introduction
This document provides step-by-step details on installing and configuring **XCP-ng (Xen Cloud Platform – Next Generation)** on a bare-metal server. The installation was carried out on an Acer system provided by the institute, which initially had Ubuntu OS installed. XCP-ng transforms the bare-metal system into a virtualization hypervisor, enabling VM creation and centralized management through **Xen Orchestra / XCP-ng Center**.

---

## 2. Prerequisites
- **Bare-metal system (Acer CPU with monitor, keyboard, mouse)**  
- **XCP-ng ISO** (downloaded from official [xcp-ng.org](https://xcp-ng.org))  
- **USB Drive (min 8 GB)** to make a bootable installer  
- **Rufus (Windows tool)** for creating bootable USB  
- **Basic BIOS/UEFI access** on server to change boot order  
- **Stable network connection** for post-install management  

---

## 3. Bootable USB Preparation
1. On a Windows system (lab machine):  
   - Insert USB drive.  
   - Use **DiskPart** to clean and assign a letter (if not detected).  
   - Open **Rufus**, select:  
     - Device: USB stick (≥8GB)  
     - Boot selection: XCP-ng ISO  
     - Partition scheme: **GPT**  
     - File system: **FAT32**  
   - Click **Start** → Write ISO.  
   - USB is now bootable with XCP-ng.  

---

## 4. BIOS/UEFI Configuration
1. Insert the prepared USB into the bare-metal server.  
2. Power on and press **F2 (Acer BIOS)**.  
3. Set boot priority to:  
   - **USB Flash Drive (UEFI mode)** → First.  
4. Save & Exit (**F10**).  

---

## 5. XCP-ng Installation
1. On boot, XCP-ng installer screen appears.  
2. Choose **Install XCP-ng**.  
3. Accept license agreements.  
4. Select the target hard disk for installation.  
5. Configure:  
   - Hostname  
   - Networking (IP via DHCP or Static)  
   - Root password  
6. Installation completes → Remove USB → Reboot.  

---

## 6. Post-Installation & Dashboard Access
1. After reboot, XCP-ng console screen (on monitor) displays:  
   - Hostname  
   - Assigned IP address  
   - Login instructions  
2. From a client system (same network):  
   - Open a browser and go to:  
     ```
     https://<XCP-ng-IP>
     ```  
   - Access the **Xen Orchestra dashboard** (management interface).  
3. Verified successful access to dashboard and basic functionality.  

---

## 7. Outcome
- The bare-metal Acer system is now running as a **dedicated hypervisor with XCP-ng**.  
- Dashboard accessible via browser confirms installation success.  
- Ready for creating & managing Virtual Machines.  

---

## 8. Notes
- BIOS key for Acer: **F2** (Boot Menu: **F12**)  
- If USB boot fails, try plugging into **USB 2.0 port**.  
- For remote management, install **Xen Orchestra (XO Lite)** from the XCP-ng dashboard.  
- Keep root password safe; required for system maintenance.  
