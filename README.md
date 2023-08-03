# HUAWEI-HCIA

<details>
<summary>1. VRP and Configuration Basics</summary>
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
</details>

<details><summary>2. Ethernet Switching Basics</summary></details>

<details><summary>3. VLAN</summary>
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
</details>
<details><summary>4. STP</summary>
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
</details>

<details><summary>5. Eth-Trunk iStack and CSS</summary></details>

<details><summary>6. IP Routing</summary></details>

<details><summary>7. OSPF</summary>
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
</details>

<details><summary>8. ipv6</summary></details>

<details><summary>9. Inter-Vlan</summary>
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
</details>
<details><summary>10. WLAN</summary>
Name the devices

    Switch 3
    interface GigabitEthernet 0/0/4

    The poe enable command enables the PoE function on a port.

    Switch 4
    interface GigabitEthernet 0/0/4

    Configure VLANs.

    Configure interface IP addresses.

    Configure DHCP.
        system-view
        dhcp enable
        ip pool <pool_name> - Configure a DHCP IP pool:
        network <ip_address> mask <subnet_mask> - Configure the IP address range for the DHCP IP pool
        gateway-list <ip_address> - Configure the default gateway for the DHCP IP pool (optional)
        dns-list <primary_dns> <secondary_dns> - Configure the DNS server for the DHCP IP pool (optional)
        lease day <days> hour <hours> minute <minutes> - set a lease time (optional)
        
        Apply this DHCP IP pool to an interface
            interface Vlanif100
            dhcp select global
        save

    Create an AP group and name it ap-group1.
        system-view
        wlan
        ap-group name ap-group1 - Create the AP group
        description <description_text> - optional
        ap id <ap_id> type <ap_type> - add APs to the AP group
        save

    Create a regulatory domain profile, and set the AC country code in the profile.
        system-view
        wlan
        regulatory-domain-profile name <profile_name>
        country-code <country_code>
    A regulatory domain profile provides configurations of country code, calibration channel, and calibration bandwidth for an AP.
    The default regulatory domain profile is named default. Therefore, the default profile is displayed.
    A country code identifies the country in which the APs are deployed.

    Bind the regulatory domain profile to an AP group.
        ap-group name <ap_group_name>
        regulatory-domain-profile <profile_name>
        save

    The regulatory-domain-profile command in the AP group view binds a regulatory domain profile to an AP or AP group.

    Specify a source interface on the AC for establishing CAPWAP tunnels.
    The capwap source interface command configures the interface used by the AC to set up CAPWAP tunnels with APs.
    Import APs to the AC and add the APs to AP group ap-group1.

    APs can be added to an AC in the following ways:
    • Manual configuration: Specify the MAC addresses and serial numbers (SNs) of APs on the AC in advance. When APs are connected the AC, the AC finds that their MAC addresses and SNs match the preconfigured ones and establish connections with them.
    • Automatic discovery: When the AP authentication mode is set to no authentication, or the AP authentication mode is set to MAC or SN authentication and the MAC addresses or SNs are whitelisted, the AC automatically discovers connected APs and establish connections with them.
    • Manual confirmation: If the AP authentication mode is set to MAC or SN authentication and MAC address or SN of a connected AP is not included in the whitelist on the AC, the AC adds the AP to the list of unauthorized APs. You can manually confirm the identify of such an AP to bring it online.

    The ap auth-mode command configures the AP authentication mode.
    The ap-id command adds an AP or displays the AP view.
    The ap-mac argument specifies MAC address authentication, and the ap-sn argument specifies SN authentication.
    The ap-name command configures the name of an AP.
    The ap-group command configures the group for an AP.

    Display the information about the current AP.
    display ap all

    The display ap command displays AP information, including the IP address, model (AirEngine5760), status (normal), and online duration of the AP.
    In addition, you can add by-state state or by-ssid ssid to filter APs in a specified state or using a specified SSID.

    Configure WLAN service parameters.
    
        Create security profile HCIA-WLAN and configure a security policy.
            system-view
            wlan
            security-profile name <profile_name>
            wpa-psk pass-phrase <password> // Replace <password> with your desired passphrase
            security-policy wpa2-psk
            vap-profile name <vap_profile_name>
            security-profile <profile_name>
            save
            
        The security psk command configures WPA/WPA2 pre-shared key (PSK) authentication and encryption.
        Currently, both WPA and WPA2 are used. User terminals can be authenticated using either WPA or WPA2. The PSK is set to HCIA-Datacom. User data is encrypted using the AES encryption algorithm.
        [AC]
        # Create SSID profile HCIA-WLAN and set the SSID name to HCIA-WLAN.
        [AC]
        # Create VAP profile HCIA-WLAN, configure the data forwarding mode and service VLAN, and apply the security profile and SSID profile to the VAP profile. 
        [AC]
        The vap-profile command creates a VAP profile.
        You can configure the data forwarding mode in a VAP profile and bind the SSID profile, security profile, and traffic profile to the VAP profile.
        [AC] 
        The forward-mode command configures the data forwarding mode in a VAP profile. By default, the data forwarding mode is direct forwarding.
        [AC]
        The service-vlan command configures the service VLAN of a VAP. After a STA accesses a WLAN, the user data forwarded by the AP carries the service-VLAN tag.
        [AC]
        # Bind the VAP profile to the AP group and apply configurations in VAP profile HCIA-WLAN to radio 0 and radio 1 of the APs in the AP group.
        [AC]
        The vap-profile command binds a VAP profile to a radio. After this command is executed, all configurations in the VAP, including the configurations in the profiles bound to the VAP, are delivered to the radios of APs.
</details>

<details><summary>11. ACL</summary>
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
    -a source-ip-address: specifies the source IP address. Users can communicate with the server from the specified IP address
</details>

<details><summary>12. AAA</summary>
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
</details>

<details><summary>13. NAT</summary>
Configure IP addresses and routes.

    Router 1
    interface GigabitEthernet 0/0/3
    ip address 192.168.1.1 24
    quit
    ip route-static 0.0.0.0 0 192.168.1.254

    Router 2
    interface GigabitEthernet 0/0/3
    ip address 192.168.1.254 24
    quit
    
    interface GigabitEthernet 0/0/4
    ip address 1.2.3.4 24
    quit
    ip route-static 0.0.0.0 0 1.2.3.254

    Router 3
    interface GigabitEthernet 0/0/3
    ip address 1.2.3.254 24

    Configure the Telnet function on R1 and R3 for subsequent verification.
    Router 1
        user-interface vty 0 4
        authentication-mode aaa 
        quit
        aaa
        local-user test password irreversible-cipher Huawei@123 
    
    Add a new user.
        local-user test service-type telnet 
        local-user test privilege level 15

    Router 3
        user-interface vty 0 4
        authentication-mode aaa 
        quit
        aaa
        local-user test password irreversible-cipher Huawei@123

    Add a new user.
        local-user test service-type telnet 
        local-user test privilege level 15
        quit

    Test connectivity.
    ping 1.2.3.254
    ping 1.2.3.254

    Configure a NAT address pool.
    The nat address-group command configures a NAT address pool.

    Configure an ACL.
    acl 2000 
    rule 5 permit source any

    Configure dynamic NAT on GigabitEthernet0/0/4 of R2.
    interface GigabitEthernet 0/0/4
    The nat outbound command associates an ACL with an NAT address pool.
    If the address pool has sufficient addresses, you can add the no-pat argument to enable one-to-one address translation.

    Test connectivity.
    ping
    telnet
    display nat session all

    If the IP address of GigabitEthernet0/0/4 on R2 is dynamically assigned (e.g. through DHCP or PPPoE dialup), you need to configure Easy IP.
        Router 2
        interface GigabitEthernet 0/0/4
        
        Configure Easy IP.
        Test connectivity.
        Telnet R3 from R1 to simulate TCP traffic.

    R3 needs to provide network services (telnet in this example) for users on the public network. Because R3 does not have a public IP address, you need to configure NAT server on the outbound interface of R2.
        Configure NAT server on R2.
        interface GigabitEthernet 0/0/4
        The nat server command defines a mapping table of internal servers so that external users can access internal servers through address and port translation.
</details>

<details><summary>14. Network Services and Applications</summary></details>
<details><summary>15. WAN</summary></details>
<details><summary>16. Network Management and OM</summary></details>
<details><summary>17. Campus Network</summary></details>
