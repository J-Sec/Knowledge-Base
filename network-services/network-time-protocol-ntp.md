# Network Time Protocol (NTP)

{% hint style="info" %}
<mark style="color:blue;">**Network Time Protocol (NTP)**</mark> is a protocol used to synchronise the clocks of devices across a network to a precise and accurate time source.
{% endhint %}

> <mark style="color:green;">**Port Number**</mark>: UDP 123
>
> <mark style="color:green;">**RFC**</mark>: 1305

* It is important to synchronise the time across all devices on the network because all aspects of managing, securing, troubleshooting, and planning networks require accurate timestamping
* When the time is not synchronised between devices, it will be impossible to determine the order of the events and the cause of an event.
* The date and time settings on a router or switch can be set by using one of two methods You can manually configure the date and time or configure the Network Time Protocol (NTP).
* When NTP is implemented in the network, it can be set up to synchronise to a private master clock, or it can synchronise to a publicly available NTP server on the internet.



## NTP Operation

* NTP networks use a hierarchical system of time sources with each level called a stratum
* The stratum level is defined as the number of hop counts from the authoritative source
* NTP servers are arranged in three levels showing the three strata

<figure><img src="../.gitbook/assets/Screenshot 2024-12-05 at 11.19.08.png" alt=""><figcaption><p>Stratum Levels</p></figcaption></figure>

### Stratum 0

* Stratum 0 devices such as atomic and GPS clocks are the most accurate authoritative time sources
* Stratum 0 devices are non-network high-precision timekeeping devices assumed to be accurate and with little or no delay associated with them

### Stratum 1

* Stratum 1 devices are network devices that are directly connected to the authoritative time sources
* Function as the primary network time standard to stratum 2 devices using NTP

### Stratum 2 and Lower

* Stratum 2 servers are connected to stratum 1 devices through network connections
* Stratum 2 devices, such as NTP clients, synchronise their time by using the NTP packets from stratum 1 servers
* Stratum 2 devices can also act as servers for stratum 3 devices
* Stratum 16, the lowest stratum level, indicates that a device is unsynchronised
* Time servers on the same stratum level can be configured to act as a peer with other time servers on the same stratum level for backup or verification of time



## Configure and Verify NTP

The **`show clock`** command displays the current time on the software clock:

```bash
R1# show clock detail
20:55:10.207 UTC Fri Nov 15 2019
Time source is user configuration
```



The **`ntp server`** _`ip-address`_ command is issued in global configuration mode. To verify the time source is set to NTP, use the **`show clock detail`** command. Notice that now the time source is NTP:

```sh
R1(config)# ntp server 209.165.200.225
R1(config)# end
R1# show clock detail
21:01:34.563 UTC Fri Nov 15 2019
Time source is NTP
```



The **`show ntp associations`** and **`show ntp status`** commands are used to verify that R1 is synchronised with the NTP server:

```bash
R1# show ntp associations  
  address         ref clock       st   when   poll reach  delay  offset   disp
*~209.165.200.225 .GPS.           1     61     64   377  0.481   7.480  4.261
* sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
R1# show ntp status
Clock is synchronized, stratum 2, reference is 209.165.200.225
nominal freq is 250.0000 Hz, actual freq is 249.9995 Hz, precision is 2**19
ntp uptime is 589900 (1/100 of seconds), resolution is 4016
reference time is DA088DD3.C4E659D3 (13:21:23.769 PST Fri Nov 15 2019)
clock offset is 7.0883 msec, root delay is 99.77 msec
root dispersion is 13.43 msec, peer dispersion is 2.48 msec
loopfilter state is 'CTRL' (Normal Controlled Loop), drift is 0.000001803 s/s
system poll interval is 64, last update was 169 sec ago.
```

