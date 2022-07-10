# General Roadmap for Upcoming Additions

### Next Planned Future Additions: Section One - The Base

##

### Part 1: PfSense: Network Setup, Segrigation and Security

##### 1. Network Setup and Configration Section for a PfSense VM within Proxmox 

##### 2. PfSense: Network Segrigation and Security (VLANs, Firewall Rules, etc) 

##### 3. Smart Switch General Configration and Security (VLAN tagging, Port Security, etc) 

##### 4. Flashing a Router with DD-WRT  and Configuring the Wireless AP for your PfSense Network, Connected to either your Smart Switch or directly to your PfSense/Proxmox Host 

## 

### Part 2: Network Attached Storage

#### 1. Determining your Needs and Picking your Base:

* Proxmox Itself
* Synology Nas/DSM 
* Western Digital NAS
* TrueNAS Core
* OpenMediaVault
* Windows Network Share 

#### 2. Files and Folders: Structure, Naming Conventions, Duplicate Removals And A Few Good Practices  

#### 3. Nas: Initial Configuration

* Redundancy: Raid and Backups
* Network Optimization and Security
* Share(s) Creation 
* User Account Creation
* Configuration Permissions and Access, then testings

#### 4. Nas: Automated Jobs and Maintenance 

#### 5. Nas: Working with Multiple Network Attached Storage Devices

##

### Part 3: PiHole and Local DNS Records for your Services

#### 1. PiHole Setup and Config

##### a. LXC Setup

##### b. Ubuntu Server, with Portainer setup 

#### 2. Nginx Proxy Manager Setup and Config 

#### 3. PfSense: Changing your DNS Servers to Point to PiHole

#### 3. Creating Local DNS Entries for your services, shares, etc 

##

### Part 4: Remote Access: VPN  

#### 1. PfSense: OpenVPN Access Server Setup and Config 

#### 2. Other Ways to Host a VPN: Docker Container 

##

### Part 5: Exposing Services

#### 1. Domain Name Providers (see Porkbun) 

#### 2. Securing your Services with SSL (See Cloudflare) 

#### 3. Using an External Proxy (See Cloudflare) 

#### 4. Using an Interal Proxy (See Nginx Proxy Manager) 

#### 5. A DMZ, Network Segrigation, HunnyPots, Firewall Rules and Intrusion Alerts 

##

### Part 6: Specific VM Creation

#### 1. Windows 11 VM [See Here](https://github.com/mycroftwilde/Lab/tree/main/adds/VM_Windows11)

##

### Part 7: Specific LXC Creation

#### 1. [TTeck Scripts](https://github.com/tteck/Proxmox)

##

### Next Planned Future Additions: Section Two

##

### Part 1: Configuring User Clients

#### 1. a. Windows 11

#### 1. b. Windows 10

#### 2. Android

#### 3. iOS

#### 4. Linux - Ubuntu Desktop 

##

### Part 2: Configuring Device Clients and IoT

##

#### Section A: Multimedia Devices

##

* 1. Roku
* 2. OpenSourceMediaCenter
* 3. Kodi 

##

#### Section B: IoT Devices

##

* 1. Lights
* 2. Smart Switches
* 3. Motion Sensors 
* 4. Tablet Panels
* 5. Air, Noise, Humidity, and Tempurature Sensors
* 6. Cameras
* 7. Smart Speakers
* 8. Smart Displays
* 9. Smart TVs
* 10. Game Consoles

#### Section C: Shared Devices 

* 1. Kiosk PC
* 2. Guest Tablet

#

#### [Main Repository Page](https://github.com/mycroftwilde/portainer_templates)

