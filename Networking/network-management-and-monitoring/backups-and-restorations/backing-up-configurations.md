# Backing Up Configurations

## Using a Text File

Configuration files can be saved to a text file by using Tera Term:

* **Step 1**. On the File menu, click **Log**.
* **Step 2**. Choose the folder location and filename to save the file and click **Save**. Tera Term will open **Tera Term: Log** window and will now capture all commands and output generated in the terminal window.
* **Step 3**. To capture the current configuration, enter the **show running-config** or **show startup-config** command privileged EXEC command. The text displayed in the terminal window will also be directed to the chosen file.
* **Step 4**. When the capture is complete, select **Close** in the Tera Term: Log window.
* **Step 5**. Open the file to verify that the configuration was captured properly and not corrupt.



## Using TFTP

Configuration files can be stored on a Trivial File Transfer Protocol (TFTP) server, or a USB drive. A configuration file should also be included in the network documentation.

To save the running configuration or the startup configuration to a TFTP server, use either the **`copy running-config tftp`** or **`copy startup-config tftp`** command:

```bash
R1# copy running-config tftp
Remote host []?192.168.10.254
Name of the configuration file to write[R1-config]? R1-Jan-2019
Write file R1-Jan-2019 to 192.168.10.254? [confirm]
Writing R1-Jan-2019 !!!!!! [OK]
```

Follow these steps to back up the running configuration to a TFTP server:

* **Step 1**. Enter the **`copy running-config tftp`** command.
* **Step 2**. Enter the IP address of the host where the configuration file will be stored.
* **Step 3**. Enter the name to assign to the configuration file.
* **Step 4**. Press Enter to confirm each choice.



## Using a USB

When backing up to a USB port, it is a good idea to issue the **`show file systems`** command to verify that the USB drive is there and confirm the name



Use the **`copy run usbflash0:`**_`/`_ command to copy the configuration file to the USB flash drive.

Be sure to use the name of the flash drive, as indicated in the file system.



Use the **`dir`** command to see the file on the USB drive and use the **`more`** command to see the contents.
