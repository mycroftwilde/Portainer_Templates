## New Ubuntu Server/VM Setup Instructions

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

## Portainer: In the Browser Setup: 

  You Should now be able to navigate to the IP of the VM or Ubuntu Machine, going to the portainer port 9000  http://IPADress:9000

  Do initial Portainer registration 

  Configure Endpoint Setting so that the IP is set to that of the Host (basically, set the IP to the same thing you used to connect) 
      - Click Endpoints, then click the name of your VM/Server, and adjust the IP in the noted space


<img width="592" alt="5" src="https://user-images.githubusercontent.com/84437811/150960304-414ff5dd-c586-4837-a689-c462807435b1.png">


  Adjust your app template list to: https://raw.githubusercontent.com/mycroftwilde/portainer_templates/master/Template/template.json
      - Click Settings, then adjust the App Template URL, and Apply the Changes. Afterword, navigate back to the app templates and the list should refesh to be pulling from this repository


<img width="725" alt="4" src="https://user-images.githubusercontent.com/84437811/150959906-96752d7c-f49f-4d45-88e0-cfe9e99c8269.png">

#
#### [Table of Contents](https://github.com/mycroftwilde/portainer_templates/blob/master/TableOfContents)
#### [Main Repository Page](https://github.com/mycroftwilde/portainer_templates)
