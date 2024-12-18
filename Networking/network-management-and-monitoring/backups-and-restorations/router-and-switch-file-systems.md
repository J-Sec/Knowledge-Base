# Router & Switch File Systems

## Commands

The **`show file systems`** command will list all the available file systems on the device:

```
Router# show file systems
File Systems:
       Size(b)       Free(b)      Type  Flags  Prefixes
             -             -    opaque     rw   system:
             -             -    opaque     rw   tmpsys:
*   7194652672    6294822912      disk     rw   bootflash: flash:#
     256589824     256573440      disk     rw   usb0:
    1804468224    1723789312      disk     ro   webui:
             -             -    opaque     rw   null:
             -             -    opaque     ro   tar:
             -             -   network     rw   tftp:
             -             -    opaque     wo   syslog:
      33554432      33539983     nvram     rw   nvram:
             -             -   network     rw   rcp:
             -             -   network     rw   ftp:
             -             -   network     rw   http:
             -             -   network     rw   scp:
             -             -   network     rw   sftp:
             -             -   network     rw   https:
             -             -    opaque     ro   cns:
Router#
```

This command provides useful information such as the amount of total and free memory, the type of file system, and its permissions. Permissions include read only (ro), write only (wo), and read and write (rw). The permissions are shown in the Flags column of the command output.



Notice that the flash file system also has an asterisk preceding it. This indicates that flash is the current default file system. The bootable IOS is located in flash; therefore, the pound symbol (#) is appended to the flash listing, indicating that it is a bootable disk.



To view other file systems you can use the **`cd`** command to change directory. The **`dir`** command will list the contents of the file system.
