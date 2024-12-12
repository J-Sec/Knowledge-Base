# Cisco Discovery Protocol (CDP)

{% hint style="info" %}
<mark style="color:blue;">**Cisco Discovery Protocol (CDP)**</mark> is a proprietary Layer 2 network protocol used by Cisco devices to discover and share information about directly connected devices in a network.
{% endhint %}

* Media and protocol independent and runs on all Cisco devices, such as routers, switches, and access servers
* The device sends periodic CDP advertisements to connected devices
* These advertisements share information about the type of device that is discovered, the name of the devices, and the number and type of the interfaces
* Can assist in network design decisions, troubleshooting, and making changes to equipment
* Can help build a logical topology of a network when documentation is missing or lacking in detail



## Configure & Verify CPD

> <mark style="color:blue;">**Note**</mark>**:** For Cisco devices, CDP is enabled by default. For security reasons, it may be desirable to disable CDP on a network device globally, or per interface.
>
>
>
> An attacker can gather valuable insight about the network layout, such as IP addresses, IOS versions, and types of devices.



To verify the status of CDP and display information about CDP, enter the **`show cdp`** command:

```shell
Router# show cdp
Global CDP information:
      Sending CDP packets every 60 seconds
      Sending a holdtime value of 180 seconds
      Sending CDPv2 advertisements is enabled
```



To enable CDP globally for all the supported interfaces on the device, enter **`cdp run`** in the global configuration mode. CDP can be disabled for all the interfaces on the device with the **`no cdp` run** command in the global configuration mode:

```shell
Router(config)# no cdp run
Router(config)# exit
Router# show cdp
CDP is not enabled
Router# configure terminal
Router(config)# cdp run
```



To disable CDP on a specific interface, such as the interface facing an ISP, enter **`no cdp enable`** in the interface configuration mode and **`cdp enable`** to reenable it:

```sh
Switch(config)# interface gigabitethernet 0/0/1
Switch(config-if)# no cdp enable
Switch(config-if)# cdp enable
```



To verify the status of CDP and display a list of neighbors, use the **`show cdp neighbors`** command in the privileged EXEC mode:

```sh
Router# show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone,
                  D - Remote, C - CVTA, M - Two-port Mac Relay
Device ID        Local Intrfce     Holdtme    Capability  Platform  Port ID
Total cdp entries displayed : 0
```



Use the **`show cdp interface`** command to display the interfaces that are CDP-enabled on a device:

```sh
Router# show cdp interface
GigabitEthernet0/0/0 is administratively down, line protocol is down
  Encapsulation ARPA
  Sending CDP packets every 60 seconds
  Holdtime is 180 seconds
GigabitEthernet0/0/1 is up, line protocol is up
  Encapsulation ARPA
  Sending CDP packets every 60 seconds
  Holdtime is 180 seconds
  ...<snip>...
```



Use **`show cdp neighbors detail`** to discover more information about device neighbours:

```bash
R1# show cdp neighbors detail
-------------------------
Device ID: S1
Entry address(es):
  IP address: 192.168.1.2
Platform: cisco WS-C3560-24TS,  Capabilities: Switch IGMP
Interface: GigabitEthernet0/0/1,  Port ID (outgoing port): FastEthernet0/5
Holdtime : 136 sec
...<snip>...
```
