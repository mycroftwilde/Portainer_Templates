### Preface:

After installing Open-Wrt, These are the rough steps to follow in order to configure the wireless router as an AP for your PfSense Network (With Vlan)

Please be aware these instructions pressuppose that you have already setup: 

   - A PfSense Network 
   
   - With vlans 
   
   - And, have things connected to a smart switch with the applicable VLAN port configuration already in place
    
#

### Rough Instructions:



Set Lan Network to: IPAddress/24

Management Interface: http://SameIPAddress

Admin password set.

Wireless Setup

Settings for Bridged mode with Vlans:

1. Go to Network - Interfaces - Devices 
  
  - Create a Vlan Device, using the Wan as the base, so it's wan.*VLANID*
  
    If I was usig 43, then it would be wan.43
    
2. While still in the devices section, Create a Bridge and add the VLAN. IF you want more than one SSID/have a 2.4Ghz and 5Ghz, etc, you will need to create a second bridge. One bridge Per SSID. 

3. Go to the Wireless Section to create SSIDs
  
  - Basically Click add, where applicable, and fill out ESSID field in the General Setup with your desired SSID. Under the network dropdown, on the same page, specify the bridge you created for the SSID.
  
  <img width="592" alt="5" src="https://github.com/mycroftwilde/portainer_templates/blob/8e2dc4237e17eba91e6a81238eedf9fb450f9b39/Images/Openwrt.png">
  
  - After this, go to the wireless security section and set a password
  
    Click Save
    
4. Go back to Interfaces and Click "Add New interface"    
   
   - Create an Unmanaged interface for each bridge you created previously 

(I can't remember if you need to do 4 before it will allow 3, just an FYI - this is all from my notes ;) ) 

You Should now be able to connect to your network via the SSIDs that you setup, with the applicable password you set when you setup the security tab. 

#

I'll probably clean these instructions up at a later time, but they should provide a good base as written. 

#### [Main Repository Page](https://github.com/mycroftwilde/portainer_templates)    
