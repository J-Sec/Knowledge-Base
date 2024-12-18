# Password Recovery

For encrypted passwords, such as the enable secret passwords, the passwords must be replaced after recovery.&#x20;

Depending on the device, the detailed procedure for password recovery varies. However, all the password recovery procedures follow the same principle:

* **Step 1**. Enter the ROMMON mode.
* **Step 2**. Change the configuration register.
* **Step 3**. Copy the startup-config to the running-config.
* **Step 4**. Change the password.
* **Step 5**. Save the running-config as the new startup-config.
* **Step 6**. Reload the device.



Console access to the device through a terminal or terminal emulator software on a PC is required for password recovery. The terminal settings to access the device are:

* 9600 baud rate
* No parity
* 8 data bits
* 1 stop bit
* No flow control



### Example Recovery

**Step 1. Enter the ROMMON mode**

With console access, a user can access the ROMMON mode by using a break sequence during the boot up process or removing the external flash memory when the device is powered off. When successful, the **rommon 1 >** prompt displays:

```
Readonly ROMMON initialized
 
monitor: command "boot" aborted due to user interrupt
rommon 1 > 
```

**Note:** The break sequence for PuTTY is Ctrl+Break. A list of standard break key sequences for other terminal emulators and operating systems can be found by searching the internet.



**Step 2. Change the configuration register**

The ROMMON software supports some basic commands, such as **`confreg`**

The **`confreg 0x2142`** command allows the user to set the configuration register to 0x2142. With the configuration register at 0x2142, the device will ignore the startup config file during startup.&#x20;

After setting the configuration register to 0x2142, type **reset** at the prompt to restart the device. Enter the break sequence while the device is rebooting and decompressing the IOS.

```
rommon 1 > confreg 0x2142
rommon 2 > reset
 
System Bootstrap, Version 15.0(1r)M9, RELEASE SOFTWARE (fc1)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 2010 by cisco Systems, Inc.
(output omitted)
```



**Step 3. Copy the startup-config to the running-config**

After the device has finished reloading, copy the startup config to the running config by using the **`copy startup-config running-config`** command:

```bash
Router# copy startup-config running-config
Destination filename [running-config]?
 
1450 bytes copied in 0.156 secs (9295 bytes/sec)
R1#
```

Notice that the router prompt changed to **R1#** because the hostname is set to R1 in the startup-config.

{% hint style="danger" %}
**CAUTION**: Do not enter **`copy running-config startup-config`**. This command erases your original startup configuration.
{% endhint %}



**Step 4. Change the password**

Because you are in privileged EXEC mode, you can now configure all the necessary passwords:

```bash
R1# configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)# enable secret cisco
```



**Step 5. Save the running-config as the new startup-config**

After the new passwords are configured, change the configuration register back to 0x2102 by using the **`config-register 0x2102`** command in the global configuration mode. Save the running-config to startup-config:

```bash
R1(config)# config-register 0x2102
R1(config)# end
R1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
R1#
```



**Step 6. Reload the device**

```bash
R1# reload
Proceed with reload? [confirm]

*Mar  1 13:04:53.009: %SYS-5-RELOAD: Reload requested by console. Reload Reason: Reload Command.
```

The device now uses the newly configured passwords for authentication. Be sure to use **show** commands to verify that all the configurations are still in place. For example, verify that the appropriate interfaces are not shut down after password recovery.

To find detailed instructions for password recovery procedures for a specific device, search the internet.
