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
    The vlan vlan-id command creates a VLAN and displays the VLAN view. If the VLAN to be created exists, the VLAN view is displayed directly.
    
    The vlan batch { vlan-id1 [ to vlan-id2 ] } command creates VLANs in batches.`
    
    The port link-type { access | hybrid | trunk } command specifies the link type of an interface, which can be access, trunk, or hybrid.
    
    The port default vlan vlan-id command configures the default VLAN of an interface and assigns the interface to the VLAN.
    
    The port trunk allow-pass vlan command assigns a trunk port to the specified VLANs.
    
    The undo port trunk allow-pass vlan command deletes a trunk port from the specified VLANs.

### b. Configure MAC address-based VLANs.
    The mac-vlan mac-address command associates a MAC address with a VLAN.
    
    The port hybrid untagged vlan command assigns a hybrid port to the specified VLANs to allow untagged frames to pass through.

    To enable a port to forward packets based on associations between MAC addresses and VLANs, you must run the mac-vlan enable command.

    The display vlan command displays information about VLANs.

    The display vlan verbose command displays detailed information about a specified VLAN

    The display mac-vlan command displays the configuration of MAC address-based VLAN assignment.

## 4. STP
    The stp enable command enables STP, RSTP, or MSTP on a switching device or a port. By default, STP, RSTP, or MSTP is enabled on switches.

    The stp mode{mstp | rstp | stp} command sets the operation mode of the spanning tree protocol on a switching device.

    The display stp command displays the status of and statistics on a spanning tree instance.

    The display stp brief command displays the brief status.

    The stp root primary command specifies a switch as the root switching device.

    The stp root secondary command specifies a switch as the secondary root bridge.

    display stp 
    display stp brief 

Configure edge ports.

    The stp edged-port enable command sets the current port as an edge port.

## 5. Eth-Trunk iStack and CSS
## 6. IP Routing
## 7. OSPF
Complete basic device configuration.
ie:
-
    Create an OSPF process using ospf command
     
    The area command creates an OSPF area and displays the OSPF area view.

    The network network-address wildcard-mask command specifies the interfaces on which OSPF is to be enabled.

    The display ospf peer  command displays the OSPF neighbor information

    Display ip routing-table protocol ospf displays the routes learned from OSPF.

Configure OSPF authentication.
Commands on the Router:

    interface GigabitEthernet0/0/1
    ospf authentication-mode md5 1 cipher HCIA-Datacom
    interface GigabitEthernet0/0/3
    ospf authentication-mode md5 1 cipher HCIA-Datacom
    display this 

Advertisement

    The default-route-advertise command advertises the default route to a common OSPF area.
    If the always argument is not specified, the default route is advertised to other routers only when there are active non-OSPF default routes in the routing table of the local router.

    display ip routing-table 

    To verify results
    tracert –a 10.0.1.1 10.0.1.2
    
## 8. ipv6
## 9. Inter-Vlan
Complete basic device configuration.

    - Name the devices 
        Enter Syatem view and use sysname command
    - Configure IP addresses and gateways for routers
        Select the interface : interface GigabitEthernet 0/0/1
        Assign an IP address to the interface : ip address 192.168.1.1 255.255.255.0
        quit to leave the interface
        Configure the default gateway : ip route-static 0.0.0.0 0 192.168.1.254
    - Assign routers to VLANS
        port link-type access
        port default vlan 10
        quit
Configure Dot1q

    - Configure a trunk port on the switch.
    - Configure a dot1q termination sub-interface on R1.
    
    The dot1q termination vid vlan-id command configures the VLAN ID for Dot1q termination on a sub-interface.

    To allow such sub-interfaces to forward broadcast packets, the ARP broadcast function must be enabled using the arp broadcast enable command.
Configure VLANIF interfaces to enable inter-VLAN communication.

    The interface vlanif vlan-id command creates a VLANIF interface and displays the VLANIF interface view. You must create a VLAN before configuring a VLANIF interface.
    Test the connectivity between VLANs with ping
    

    
    

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




