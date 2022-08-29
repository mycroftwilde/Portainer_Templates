## New Ubuntu Server/VM Setup Instructions (With Portainer Install)

### Where to get the OS image:

* [Ubuntu Desktop](https://ubuntu.com/download/desktop)

* [Ubuntu Server](https://ubuntu.com/download/server)


### Commands to prep your system, after Install:

  Update the system:

    sudo apt update
    
  Ugrade the system:
    
    sudo apt upgrade

  If you want to Install Glances: 

    sudo glances -w

  If you want to Install CFIS Utilities to Map Network Shares: 

    sudo apt-get install cifs-utils

  If you want to Install GIT: 

    sudo apt install git-all

  Install Docker:

    sudo apt install docker.io

  Enable Docker:

    sudo systemctl enable docker
 
 Start Docker: 

    sudo systemctl start docker
  
  Check Docker Status: 
  
    sudo systemctl status docker

  Create Portainer Volume:

    sudo docker volume create portainer_data

  Install Portainer: 
  
    sudo docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce

** How to Update Portainer, for when needed: **

  Stop Portainer:

    sudo docker stop portainer
  
  Remove the Current Container Image (not your Data)
  
    sudo docker rm portainer
  
  Pull a New Container Image for Portainer:
  
    sudo docker pull portainer/portainer-ce
    
  Install/Update Portainer:
  
    sudo docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce

** How to install the Portainer Agent, for when needed: **

    docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:2.6.3 
  
  [Reference for the above](https://docs.portainer.io/v/ce-2.6/start/install/agent/docker/linux)



   ## Supplemental steps for a PiHole Container, Ubtuntu Server
   
   After pulling the container image, and it failing to start, make the following adjustments: 

  Stop Command: 
  
    sudo systemctl stop systemd-resolved.service

Disable Command: 

    sudo systemctl disable systemd-resolved.service

   Next, run the below and edit the name server:

    sudo nano /etc/resolv.conf

   You can change the name server to OpenDNS normally

    208.67.222.222, 208.67.220.220

   ## Supplimental Setup Notes
   
   Commands for Mapping a Network Share, after installing the CFIS Utilities
   
   (Please note: This is from some old notes of mine, and it will probably need to be reviewed to be sure it's within best practices)

  Make Required Directory

    sudo mkdir /mnt/*FolderNameonyourUbuntuSystem*
    
  Change
    
    sudo chown -R nobody:nogroup /mnt/*FolderNameonyourUbuntuSystem*
    
  Adjust
  
    sudo chmod -R 0755 /mnt/*FolderNameonyourUbuntuSystem*
    
  Mount 
    
    sudo mount.cifs //*IPAddressofNetworkShare*/*ShareName* /mnt/*FolderNameonyourUbuntuSystem* -o user=*Username*,uid=1000
      
      * Enter Applicable Passwords
      
 Another version of this has been noted by Matthew Peterson from Dockerholics: 

  * sudo apt install cifs-utils
  * sudo mkdir /mnt/media
  * sudo touch /etc/win-credentials
  * sudo nano /etc/win-credentials

username=shareusername

password=sharepassword

domain=domain

* sudo nano /etc/fstab
  * //192.168.1.135/Multimedia /mnt/media cifs credentials=/etc/win-credentials,file_mode=0755,dir_mode=0755 0 0
  * sudo mount -a
  
##
[Portainer: In the Browser Setup](https://github.com/mycroftwilde/portainer_templates/tree/master/TableOfContents/Portainer)
##
   ### Further Ubuntu Setup items to be Added at a Later Time:

1. Adding a public SSH Key to your Server 
   
   a. Install OpenSSH Server, if you don't install it during the initial setup
    
        sudo apt-get install openssh-server

2. Remapping a Share at Server Boot

3. Securing your Servers

4. Quick access list of general Linux/Ubuntu Commands


#
#### [Main Repository Page](https://github.com/mycroftwilde/portainer_templates)
