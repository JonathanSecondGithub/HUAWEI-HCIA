# HUAWEI-HCIA

## 1. VRP and Configuration Basics
# Basic Configurations
We will be using the following configuration to practice:

** Config Image
![alt text](http://url/to/img.png)

Double clicking on the router will open a terminal like shown below
** Terminal Image
![alt text](http://url/to/img.png)

The following are the basic commands: 
- The `system-view` command enables you to enter the system view from the user view.

- The `sysname` command sets the device host name.

- The `interface GigabitEthernet 0/0/1` command specifies the type and number of the interface from which the current interface is isolated unidirectionally for example in this case the interface type is *GigabitEthernet* and its number is *0/0/1*.

- `?`
Enter a question mark (?) in any command view to obtain all the commands and their simple descriptions.
Enter some keywords of a command and a question mark (?) separated by a space. All keywords associated with this command, as well as simple descriptions, are displayed.
an output of *<cr>* indicates that there is no keyword or parameter in this position. You can press Enter to run this command.

- The `display this` command displays the running configuration in the current view.
- The `display current-configuration` displays the currently running configuration.
This command does not display parameters that use default settings.
- quit
- undo
- save
- dir
- save test.cfg
- startup saved-configuration test.cfg
- display startup
- reboot 
- display interface
- display clock
- display users
- display ip interface
- display version
- ip address 192.168.1.2 255.255.255.0
- include
## 2. Ethernet Switching Basics
## 3. VLAN

### a. Create VLANs 2 and 3 on S1 and S2.
    The `vlan vlan-id` command creates a VLAN and displays the VLAN view. If the VLAN to be created exists, the VLAN view is displayed directly.
    
    The `vlan batch { vlan-id1 [ to vlan-id2 ] }` command creates VLANs in batches.`
    
    The `port link-type { access | hybrid | trunk }` command specifies the link type of an interface, which can be access, trunk, or hybrid.
    
    The `port default vlan vlan-id` command configures the default VLAN of an interface and assigns the interface to the VLAN.
    
    The `port trunk allow-pass vlan` command assigns a trunk port to the specified VLANs.
    
    The `undo port trunk allow-pass vlan` command deletes a trunk port from the specified VLANs.

### b. Configure MAC address-based VLANs.
    The ==mac-vlan mac-address== command associates a MAC address with a VLAN.


## 4. STP
## 5. Eth-Trunk iStack and CSS
## 6. IP Routing
## 7. OSPF
## 8. ipv6
## 9. Inter-Vlan
## 10. WLAN
## 11. ACL
## 12. AAA
## 13. NAT
## 14. Network Services and Applications
## 15. WAN
## 16. Network Management and OM
## 17. Campus Network
## Objectives
    1. Complete basic configurations, such as device name and router interface IP address.
    2. Save the configurations.
    3. Restart the device.




