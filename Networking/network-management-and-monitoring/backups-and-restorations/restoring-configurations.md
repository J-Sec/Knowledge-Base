# Restoring Configurations

## Using a Text File

A configuration can be copied from a file and then directly pasted to a device. The IOS executes each line of the configuration text as a command.

The file will require editing to ensure that encrypted passwords are in plaintext, and that non-command text such as **`--More--`** and IOS messages are removed.&#x20;

In addition, you may want to add **`enable`** and **`configure terminal`** to the beginning of the file or enter global configuration mode before pasting the configuration.



Instead of copying and pasting, a configuration can be restored from a text file by using Tera Term:

* **Step 1**. On the File menu, click **Send** file.
* **Step 2**. Locate the file to be copied into the device and click **Open**.
* **Step 3**. Tera Term will paste the file into the device.

The text in the file will be applied as commands in the CLI and become the running configuration on the device.



## Using TFTP

To restore the running configuration or the startup configuration from a TFTP server, use either the **`copy tftp running-config`** or **`copy tftp startup-config`** command. Use the following steps to restore the running configuration from a TFTP server:

* **Step 1**. Enter the **`copy tftp running-config`** command.
* **Step 2**. Enter the IP address of the host where the configuration file is stored.
* **Step 3**. Enter the name to assign to the configuration file.
* **Step 4**. Press **Enter** to confirm each choice.



## Using a USB

To copy the file back, it will be necessary to edit the USB R1-Config file with a text editor. Assuming the file name is **`R1-Config`**, use the command **`copy usbflash0:/R1-Config`** _`running-config`_ to restore a running configuration.
