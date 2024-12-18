# IOS Image Management

As a network grows, Cisco IOS Software images and configuration files can be stored on a central TFTP server.

This helps to control the number of IOS images and the revisions to those IOS images, as well as the configuration files that must be maintained.

Production internetworks usually span wide areas and contain multiple routers. For any network, it is good practice to keep a backup copy of the Cisco IOS Software image in case the system image on the router becomes corrupted or accidentally erased.

Widely distributed routers need a source or backup location for Cisco IOS Software images. Using a network TFTP server allows image and configuration uploads and downloads over the network. The network TFTP server can be another router, a workstation, or a host system.



### Backup IOS Image to TFTP Server Example

**Step 1. Ping the TFTP server**

Ensure that there is access to the network TFTP server. Ping the TFTP server to test connectivity:

```bash
R1# ping 172.16.1.100
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.16.1.100, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5),
round-trip min/avg/max = 56/56/56 ms
```



**Step 2. Verify image size in flash**

Verify that the TFTP server has sufficient disk space to accommodate the Cisco IOS Software image.&#x20;

Use the **`show flash0:`** command on the router to determine the size of the Cisco IOS image file:

```bash
R1# show flash0: 
-# - --length-- -----date/time------ path
8   517153193   Apr 2 2019 21:29:58  +00:00 
                        isr4200-universalk9_ias.16.09.04.SPA.bin
(output omitted)
```



**Step 3. Copy the image to the TFTP server**

Copy the image to the TFTP server by using the **`copy`**` `_`source-url destination-url`_ command.  The user is prompted for the source file name, IP address of the remote host, and destination file name:

```bash
R1# copy flash: tftp: 
Source filename []? isr4200-universalk9_ias.16.09.04.SPA.bin
Address or name of remote host []? 172.16.1.100
Destination filename [isr4200-universalk9_ias.16.09.04.SPA.bin]? 
Writing isr4200-universalk9_ias.16.09.04.SPA.bin...
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
(output omitted)
517153193 bytes copied in 863.468 secs (269058 bytes/sec)
```



### Copy an IOS Image to a Device Example

**Step 1. Ping the TFTP server**

Ensure that there is access to the network TFTP server. Ping the TFTP server to test connectivity:

```bash
R1# ping 2001:db8:cafe:100::99
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 2001:DB8:CAFE:100::99,
timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), 
round-trip min/avg/max = 56/56/56 ms
```



**Step 2. Verify the amount of free flash**

Ensure that there is sufficient flash space on the router that is being upgraded.&#x20;

The amount of free flash can be verified by using the **`show flash`:** command.

```bash
R1# show flash: 
-# - --length-- -----date/time------ path
(output omitted)
6294806528 bytes available (537251840 bytes used) 
R1#
```



**Step 3. Copy the new IOS image to flash**

Copy the IOS image file from the TFTP server to the router by using the **`copy`** command.

The user will be prompted for the IP address of the remote host, source file name, and destination file name:

```bash
R1# copy tftp: flash: 
Address or name of remote host []?2001:DB8:CAFE:100::99
Source filename []?  isr4200-universalk9_ias.16.09.04.SPA.bin
Destination filename [isr4200-universalk9_ias.16.09.04.SPA.bin]? 
Accessing tftp://2001:DB8:CAFE:100::99/ isr4200-
universalk9_ias.16.09.04.SPA.bin...
Loading isr4200-universalk9_ias.16.09.04.SPA.bin
from 2001:DB8:CAFE:100::99 (via
GigabitEthernet0/0/0): !!!!!!!!!!!!!!!!!!!!
 
[OK - 517153193 bytes]
517153193 bytes copied in 868.128 secs (265652 bytes/sec)
```



To upgrade to the copied IOS image after that image is saved on the flash memory of the router, configure the router to load the new image during bootup by using the **`boot system`** command:

```bash
R1# configure terminal
R1(config)# boot system flash0:isr4200-universalk9_ias.16.09.04.SPA.bin
R1(config)# exit
R1#
R1# copy running-config startup-config
R1#
R1# reload
Proceed with reload? [confirm]
*Mar  1 12:46:23.808: %SYS-5-RELOAD: Reload requested by console. Reload Reason: Reload Command.
```

After the router has booted, to verify that the new image has loaded, use the **`show version`** command.
