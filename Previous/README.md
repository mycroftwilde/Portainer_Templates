# Portainer Version 2 Template and Self-Hosting Cookbook

![BannerLogo](/branding/images/LogoBanner1.png?raw=true "Banner")

## Brand New Updates:

#### 6/26/2022 - Added a section for alternative Self-Hosting Cookbooks

#### 6/24/2022 - Added a Windows 11 section for Debloating apps, etc

#### 6/15/2022 - Added Pwndrop, Authentik, and Apprise-API. All code was obtained from the already noted template lists. Xneo1 and technorabilia. Future notations additions from other templates will just feature the template list I created. If a new template was used as a source it will be added and noted, however. 

#### 6/14/2022 - I've added the MeshCentral Docker Image by: gurucomputing to the Portainer Template. 

#### 6/14/2022 - I've added the Dockerholics Github Repo link to the Self-Hosting Links section. 

#

#### June, 2022 - I have added a section for Proxmox and Thin Clients, as well as links to external resources in that section.

#### June, 2022 - A number of container templates have been added -> sourced from [Xneo1's Template](https://raw.githubusercontent.com/xneo1/portainer_templates/master/Template/template.json)

His Github Repo Page: [xneo1's Portainer Template Repo Page](https://github.com/xneo1/portainer_templates) 

#### Please check out Xneo1's work and Star it! 

## Sort-of New Updates: 

#### June, 2022 - I have added Audiobookshelf to the Docker Template and it seems to work, but I haven't tested extensively. 

#### June, 2022 - I have added a list section for other Portainer Templates. You can access it here: [List of Portainer Templates](https://github.com/mycroftwilde/portainer_templates/tree/master/TemplatesList) 

#### June, 2022 - Various new Resource Links have been added to this main page.

#### June, 2022 - I am also working on a table of contents to easier access specific content. You can access it here: [Table of Contents](https://github.com/mycroftwilde/portainer_templates/tree/master/TableOfContents). 
  (Please note: The most up to date information will still reside on this main page until the full transition to the Table of Contents format.)

## Previous Updates: 

[See Here](https://github.com/mycroftwilde/portainer_templates/tree/master/TableOfContents/Updates/Previous)
 
## Useful Supplimental Software Links: 

* [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/)
* [mRemoteNG](https://mremoteng.org/)
* [7zip](https://www.7-zip.org/download.html)
* [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/)
* [Draw.io](https://www.draw.io)
* [BalenaEther](https://www.balena.io/etcher/)
* [Rufus](http://rufus.ie/en/)
* [Bulk Rename Utility](https://www.bulkrenameutility.co.uk/)

## Alternative Self-Hosting Cookbooks

* [Tborychowski's Docker Compose Self-Hosted Cookbook](https://github.com/tborychowski/self-hosted-cookbook)

## Windows 11

* [ThisIsWin11](https://github.com/builtbybel/ThisIsWin11)
* [LoveWindowsAgain](https://github.com/builtbybel/LoveWindowsAgain)
 
## Supplimental YouTube Videos:

Below is a YouTube playlist on various subjects around selfhosting. Some items, like the Proxmox install, have various videos on the same general subject. This has been done in case one presenter is preferable over another, and so things can be compared, if needed.  

[YouTube Playlist](https://youtube.com/playlist?list=PLGk2on7ccZOMMdaljjX8jeDpWhJGPzrcs)

In addition to this, here is LearnLinuxTV's full Proxmox VE Video Course on YouTube: 

[Course](https://youtube.com/playlist?list=PLT98CRl2KxKHnlbYhtABg6cF50bYa8Ulo)

 ## Helpful Youtube Channels for Self-Hosting:
 
 [DBTech](https://www.youtube.com/c/DBTechYT)
   
 [Techno Dad Life](https://www.youtube.com/channel/UCX2Vhc0LIzSS9aMzhGFZ7PA)
   
 [Techno Tim](https://www.youtube.com/channel/UCOk-gHyjcWZNj3Br4oxwh0A)
   
 [Lawrence Systems](https://www.youtube.com/user/TheTecknowledge)
   
 [Learn Linux TV](https://www.youtube.com/user/JtheLinuxguy)
   
 [Craft Computing](https://www.youtube.com/channel/UCp3yVOm6A55nx65STpm3tXQ)
  
## New Proxmox Host - Prep

 One of the best ways to host your servers is on an older machine you may have lying around. You can flash it/image it with Proxmox, and Proxmox will allow you to use all the hardware in your older machine for a number of little servers, as virtual machines, within proxmox itself. 
 
 * Prep the hardware -> Clean it, if needed. 
 
 * Flash a USB stick with an image from the Proxmox website: [Proxox Website](https://www.proxmox.com/en/downloads)
 
 * Image your old computer -> Have the computer boot from the USB stick, instead of it's internal harddrive, and then install Proxmox
 
 * After doing all of the install steps, reboot the machine at the noted time in the install instructions, and then navigate to your management interface. Often times, it's:
  
    * https://IPAddress:8006/  


## New Ubuntu Server/VM Setup Instructions - Prep

### Where to get the OS image:

* [Ubuntu Desktop](https://ubuntu.com/download/desktop)

* [Ubuntu Server](https://ubuntu.com/download/server)


### Commands to prep your system, after Install:

  Update the system:

  * sudo apt update

  * sudo apt upgrade

  If you want to Install Glances: 

  * sudo glances -w

  If you want to Install CFIS Utilities to Map Network Shares: 

  * sudo apt-get install cifs-utils

  If you want to Install GIT: 

  * sudo apt install git-all

  Install and test Docker:

  * sudo apt install docker.io

  * sudo systemctl enable docker

  * sudo systemctl start docker

  * sudo systemctl status docker

  Setup Portainer: 

  * sudo docker volume create portainer_data

  * sudo docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce

** How to Update Portainer, for when needed: **

  * sudo docker stop portainer
  
  * sudo docker rm portainer
  
  * sudo docker pull portainer/portainer-ce
  
  * sudo docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce

** How to install the Portainer Agent, for when needed: **

  * docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:2.6.3 
  
  [Reference for the above](https://docs.portainer.io/v/ce-2.6/start/install/agent/docker/linux)


** Further Ubuntu Setup items to be Added at a Later Time: **

   ## Supplemental steps for a PiHole Container, Ubtuntu Server
   
   After pulling the container image, and it failing to start, make the following adjustments: 

   * sudo systemctl stop systemd-resolved.service

   * sudo systemctl disable systemd-resolved.service

   Next, run the below and edit the name server:

   * sudo nano /etc/resolv.conf

   You can change the name server to OpenDNS normally

   * 208.67.222.222
   * 208.67.220.220

   ## Supplimental Setup Notes
   
   Commands for Mapping a Network Share, after installing the CFIS Utilities
   
   (Please note: This is from some old notes of mine, and it will probably need to be reviewed to be sure it's within best practices)

   * sudo mkdir /mnt/*FolderNameonyourUbuntuSystem*
   * sudo chown -R nobody:nogroup /mnt/*FolderNameonyourUbuntuSystem*
   * sudo chmod -R 0755 /mnt/*FolderNameonyourUbuntuSystem*
   * sudo mount.cifs //*IPAddressofNetworkShare*/*ShareName* /mnt/*FolderNameonyourUbuntuSystem* -o user=*Username*,uid=1000
      * Enter Applicable Passwords  

   ### Further Ubuntu Setup items to be Added at a Later Time:

   1. Adding a public SSH Key to your Server 

   2. Remapping a Share at Server Boot

   3. Securing your Servers

   4. Quick access list of general Linux/Ubuntu Commands

## Portainer: In the Browser Setup

  You Should now be able to navigate to the IP of the VM or Ubuntu Machine, going to the portainer port 9000  http://IPADress:9000

  Do initial Portainer registration 

  Configure Endpoint Setting so that the IP is set to that of the Host (basically, set the IP to the same thing you used to connect) 
      - Click Endpoints, then click the name of your VM/Server, and adjust the IP in the noted space


<img width="592" alt="5" src="https://user-images.githubusercontent.com/84437811/150960304-414ff5dd-c586-4837-a689-c462807435b1.png">


  Adjust your app template list to: https://raw.githubusercontent.com/mycroftwilde/portainer_templates/master/Template/template.json
      - Click Settings, then adjust the App Template URL, and Apply the Changes. Afterword, navigate back to the app templates and the list should refesh to be pulling from this repository


<img width="725" alt="4" src="https://user-images.githubusercontent.com/84437811/150959906-96752d7c-f49f-4d45-88e0-cfe9e99c8269.png">

 ## Portainer: Updating Docker Containers 

For updating Containers you can see [wundertech's instructions here](https://www.wundertech.net/how-to-update-a-docker-container-using-portainer)

 ## Portainer and Docker-Compose: Stacks 

To use Docker-Compose within Portainer you will use the Stack Feature. Instructions can be found here: [Portainers Blog Post](https://www.portainer.io/blog/stacks-docker-compose-the-portainer-way)

 ## Using Proxmox with Thin Clients
 
 The YouTube Channel [apalrd's adventures](https://www.youtube.com/channel/UCIgNWXsJcFwvFptmUic6wSw) has a geat playlist of videos regarding using Promxmox with Thin Clients. 
 
 [The YouTube Playlist](https://www.youtube.com/watch?v=TuDrmq4RQzU&list=PLZcFwaChdgSqPfgWh-EftX7OcoB7G8PiU)
 
 Access to this information can also be found on his Blog: [The apalrd's adventures Blog - Thin Client Section](https://www.apalrd.net/projects/2022/thin_client/)
 
 You can also check out his website [Here](https://www.apalrd.net/)

 ## Helpful Links and URLs for Self-Hosting
 
  * [LinuxServer.io](https://www.linuxserver.io/)
 
  * [Dockerholics Github Page](https://github.com/petersem/dockerholics)

  * [Porkbun](https://porkbun.com)

  * [Cloudflare](https://www.cloudflare.com/)

  * [SiteGrounds](https://www.siteground.com/)

  * [Hotio.Dev](https://hotio.dev/)

  * [PfSense](https://www.pfsense.org/download/)
     * Note - to help with multicast traffic accross vlans for IoT devices and servers like Home Assistant the following package can be installed, and then configured: avahi

  * [Awesome Self-Hosted's Git Page](https://github.com/awesome-selfhosted/awesome-selfhosted)
  
  * [New Proxmox Host and Home Assistant Setup, Document and Video Guide - By JaunMTech](https://www.juanmtech.com/install-proxmox-and-virtualize-home-assistant/)

  * [Open Source Media Center](https://github.com/osmc/osmc) (An Open Source Media Center OS for a Raspberry Pi, etc)

  * [OpenMediaVault](https://www.openmediavault.org/)
  
  * [TrueNAS Core](https://www.truenas.com/)
  
  * [Raspberry Pi OS/Imager](https://www.raspberrypi.com/software/)

  * [Local Habitica Docker Sever Setup Instructions](https://habitica.fandom.com/wiki/Setting_up_Habitica_Locally_on_Docker)

  * [Proxmox Helper Scripts from TTech](https://tteck.github.io/Proxmox/)
  
  * [Self-Hosting Weekly Roundup by: NAS HOSTED](https://noted.lol/tag/weekly-roundup/)


 ## A Quick Note about Home Signage Servers

Often you can create a server version of something you'd like to display on a wall display at home, and then use a raspberry pi to connect to that webpage on boot automatically. You can use this set of instructions, and just substitute out the dakboard specific elements, and use it to setup a raspberry pi to connect automatically to one of your running dashboard/signage containers' URLs. 

[Instructions](https://blog.dakboard.com/diy-wall-display/)

 ## A Quick Idea Regarding Personal Dashboards
 
 I've found, when it comes to building a main personal web dashboard, that none of the options did everything I wanted it to. So, I started nesting dashboards together. 
 
 For the below setup example, I've nested both Organizr and Flame, inside of Muximux. 
 
 I've set the default page to the Flame Dashboard, and to bypass the splash screen, so that when I load the Muximux Dashboard the Flame Dashboard is naturally nested.  The Flame dashboard has all of the links that will open in a new window. This way, I never close my dashboard. Items that I want accessable for the whole family, or easy access for myself, are located at the top bar of Muximux, and will open in an iFrame. 
 
 <img width="760" alt="1" src="https://user-images.githubusercontent.com/84437811/150927161-57b22f78-0139-4c43-a805-b643f20385c3.png">
 
 One of the cool things about nesting dashboards this way is that you can have a menu at both the top and left hand side of the browser. I've used Muxmix for the top, and Organizr for the side bar that is specifically within the usenet server menu. (You can also add authentication to this submenu, if you wanted to have an administration section to your dashboard.)
 
 <img width="173" alt="2" src="https://user-images.githubusercontent.com/84437811/150927172-b9306459-48d0-49c0-a06c-3144fe03be85.png">

Here is an example of one of the other menu items open within the Dashboard. 

 <img width="940" alt="3" src="https://user-images.githubusercontent.com/84437811/150927181-d4403a26-b626-4f16-b029-ec7dd38983a3.png">


 ## Adding Further Containers: What I'm currently looking for
 
 I'm currently wanting to add the following containers 

 * Habitica

  If you'd like to assist with the above, please get into contact and I'll see about adding the applicable code to expand the list 
  
  Note: any supplimental setup notes can be placed in the description within portainer. 

# ** From the Forked Authors Notes ** 

Previous Authors
* **NASHosted** - *Current Work* - [NASHOSTED](https://github.com/nashosted)
* **SelfhostedPro** - *Current Work* - [SelfhostedPro](https://github.com/SelfhostedPro)
* **Jos Visser** - *Initial work* - [Qballjos](https://github.com/Qballjos)
* **xe-nvdk** - *template conversion to portainer V2* - [xe-nvdk](https://github.com/xe-nvdk)
* **tbiering** - *Termplate cleanup and typo fixes* - [tbiering](https://github.com/tbiering)

See also the list of [contributors](https://github.com/Qballjos/portainer_templates/graphs/contributors) who participated in this project.

#
![BannerLogoMid](/branding/images/Banner.png?raw=true "BannerMid")


# My Notes

Other Templates that items were discovered/pulled from will be added when time allows. A various list of other templates have been noted below where some items have been sourced. 

[technorabilia](https://raw.githubusercontent.com/technorabilia/portainer-templates/main/lsio/templates/templates-2.0.json)

[mikestraney](https://raw.githubusercontent.com/mikestraney/portainer-templates/master/templates.json)

[donPabloNow](https://raw.githubusercontent.com/donPabloNow/selfhosted-saas/master/Template/portainer-v2.json)

[xneo1](https://raw.githubusercontent.com/xneo1/portainer_templates/master/Template/template.json)

#

<img width="780" alt="4" src="https://raw.githubusercontent.com/mycroftwilde/portainer_templates/master/branding/images/LogoBanner2.png">

# Mental Health

 As a side note, not related, I'm a large advocate of Mental Health. If you are having a rough time right now, please see my Mental Health Youtube Playlist:
 
 [Mental Health Youtube Playlist](https://youtube.com/playlist?list=PLGk2on7ccZONCobYxwGdvwMcF43gIKmqk)
 
 Healthy Gamer GG is also a good channel for Mental Health related topics. 
 
 You can find the channel via the link [here](https://www.youtube.com/c/HealthyGamerGG)
 
 #### Always Remember - You Matter! 
