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
We will be using 3 routers for this practical:

    Configure IP addresses for the 3 routers R1, R2, and R3.
    Configure OSPF on R1, R2, and R3 and assign them to area 0 to enable connectivity.
    Run the ping command on R3 to test network connectivity.
Configuration R3 as a server.

    The telnet server enable command enables the Telnet service.
    The user-interface command displays one or multiple user interface views.The Virtual Type Terminal (VTY) user interface manages and monitors users logging in using Telnet or SSH.
    
    [R3-ui-vty0-4]user privilege level 3
    [R3-ui-vty0-4] set authentication password cipher 

Configure an ACL to match desired traffic.
Method 1: Configure an ACL on the VTY interface of R3 to allow R1 to log in to R3 through Telnet using the IP address of loopback 1.

    - Configure an ACL on R3.
    An example of how to configure acl on a router
        system-view
        acl number 3000
        rule 5 deny icmp
        rule 10 permit ip
        interface GigabitEthernet0/0/1
        traffic-filter inbound acl 2000
        save
        display acl 3000
        
    - Filter traffic on the VTY interface of R3.
    - Display the ACL configuration on R3.
    The display acl command displays the ACL configuration.

Method 2: Configure an ACL on the physical interface of R2 to allow R1 to log in to R3 through Telnet from the IP address of the physical interface.

    - Configure an ACL on R2
    - Filter traffic on GE0/0/3 of R3.
    - Display the ACL configuration on R2.
    display acl 3001
Test the Telnet access and verify the ACL configuration.

    telnet -a 10.1.1.1 10.1.3.1
    The telnet command enables a user to use the Telnet protocol to log in to another device.
    -a source-ip-address: specifies the source IP address. Users can communicate with the server from the specified IP address.
    
## 12. AAA
We will be using 2 routers in this configuration:

    Name the routers R1 and R2.
    Configure IP addresses for R1 and R2.
    Commands:
        interface GigabitEthernet 0/0/3
        ip address 10.0.12.1 24
Configure authentication and authorization schemes.

    Enter the AAA view.
        aaa
    Create an authentication scheme named datacom.
        authentication-scheme datacom
    Set the authentication mode to local authentication.
        authentication-mode local
Create a domain and apply the AAA scheme to the domain.

    Create a domain named datacom.
Configure local users.

    Create a local user and password.
        local-user hcia@datacom password cipher HCIA-Datacom
Configure the parameters for the local user, such as access type and privilege level.

    The local-user service-type command configures the access type for a local user.
    
     Huawei devices support 16 levels of user privilege, numbered from 0 to 15. Level 0 represents the visit level, level 1 to 14 represent the user level, and level 15 represents the management level.
     
         local-user <username> privilege level <level_number>
         save
Enable the telnet function on R2.

    user-interface vty 0 4 

    The authentication-mode command configures an authentication mode for accessing the user interface.

Verify the configuration.

    Telnet R2 from R1
        telnet 10.0.12.2
    
    
## 13. NAT
## 14. Network Services and Applications
## 15. WAN
## 16. Network Management and OM
## 17. Campus Network





