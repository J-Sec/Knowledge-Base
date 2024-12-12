# Link Layer Discovery Protocol (LLDP)

{% hint style="info" %}
<mark style="color:blue;">**Link Layer Discovery Protocol (LLDP)**</mark> is an open-standard Layer 2 protocol used by network devices to advertise their identity, capabilities, and neighbours on a local network.
{% endhint %}

> <mark style="color:green;">**RFC**</mark>: 8945

## Configure & Verify LLDP

Depending on the device, LLDP may be enabled by default.&#x20;

To enable LLDP globally on a Cisco network device, enter the **`lldp run`** command in the global configuration mode.

To disable LLDP, enter the **`no lldp run`** command in the global configuration mode.

LLDP can be configured on specific interfaces. However, LLDP must be configured separately to transmit and receive LLDP packets

1. To disable the sending of LLDP messages on an interface enter **`no lldp transmit`**
2. To disable the receiving of LLDP messages on the interface enter **`no lldp receive`**

To verify LLDP has been enabled on the device, enter the **`show lldp`** command in privileged EXEC mode:

```bash
Switch(config)# lldp run
Switch(config)# interface gigabitethernet 0/1
Switch(config-if)# lldp transmit
Switch(config-if)# lldp receive
Switch(config-if)# end
Switch# show lldp
Global LLDP Information:
    Status: ACTIVE
    LLDP advertisements are sent every 30 seconds
    LLDP hold time advertised is 120 seconds
    LLDP interface reinitialisation delay is 2 seconds
```



With LLDP enabled, device neighbours can be discovered by using the **`show lldp neighbors`** command, as displayed in the output:

```bash
S1# show lldp neighbors
Capability codes:
    (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
    (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
Device ID           Local Intf     Hold-time  Capability      Port ID
R1                  Fa0/5          117        R               Gi0/0/1
S2                  Fa0/1          112        B               Fa0/1
Total entries displayed: 2
```

When more details about the neighbours are needed, the **`show lldp neighbors detail`** command can provide information, such as the neighbour IOS version, IP address, and device capability.

