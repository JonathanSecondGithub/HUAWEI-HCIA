# HUAWEI-HCIA

## 1. VRP and Configuration Basics
## Objectives
    1. Complete basic configurations, such as device name and router interface IP address.
    2. Save the configurations.
    3. Restart the device.

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

- The `dis this`
-display current-configuration
-quit
-undo
-save
-dir
-save test.cfg
-startup saved-configuration test.cfg
-display startup
-reboot 
-display interface
-display clock
-display users
-display ip interface
-display version
-ip address 192.168.1.2 255.255.255.0


