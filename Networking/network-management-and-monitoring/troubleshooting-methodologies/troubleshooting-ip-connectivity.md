---
description: Example
---

# Troubleshooting IP Connectivity

Throughout this topic, the following scenario is used. The client host PC1 is unable to access applications on Server SRV1 or Server SRV2.&#x20;

The figure shows the topology of this network. PC1 uses SLAAC with EUI-64 to create its IPv6 global unicast address. EUI-64 creates the Interface ID using the Ethernet MAC address, inserting FFFE in the middle, and flipping the seventh bit.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-22 at 17.02.51.png" alt=""><figcaption></figcaption></figure>

When there is no end-to-end connectivity, and the administrator chooses to troubleshoot with a bottom-up approach, the following are common steps the administrator can take:

**Step 1.** Check physical connectivity at the point where network communication stops. This includes cables and hardware. The problem might be with a faulty cable or interface, or involve misconfigured or faulty hardware.\
\
**Step 2.** Check for duplex mismatches.\
\
**Step 3.** Check data link and network layer addressing on the local network. This includes IPv4 ARP tables, IPv6 neighbour tables, MAC address tables, and VLAN assignments.\
\
**Step 4.** Verify that the default gateway is correct.\
\
**Step 5.** Ensure that devices are determining the correct path from the source to the destination. Manipulate the routing information if necessary.\
\
**Step 6.** Verify the transport layer is functioning properly. Telnet can also be used to test transport layer connections from the command line.\
\
**Step 7.** Verify that there are no ACLs blocking traffic.\
\
**Step 8.** Ensure that DNS settings are correct. There should be a DNS server that is accessible.

The outcome of this process is operational, end-to-end connectivity. If all the steps have been performed without any resolution, the network administrator may either want to repeat the previous steps or escalate the problem to a senior administrator.



## Step 1 - Verify the Physical Layer

* Check generic hardware components (CPU, RAM, storage)
  * The most commonly used Cisco IOS commands for this purpose are **`show processes cpu`**, **`show memory`**, and **`show interfaces`**
  * From the **`show interfaces`** command:
    * **Input queue drops -** if this number is consistently high, it is worth trying to spot at which moments these counters are increasing and how this relates to CPU usage.
    * **Output queue drops -** Consistently seeing output queue drops can be an indicator that you need to implement an advanced queuing mechanism to implement or modify QoS
    * **Input errors -** Input errors indicate errors that are experienced during the reception of the frame, such as CRC errors. High numbers of CRC errors could indicate cabling problems, interface hardware problems, or, in an Ethernet-based network, duplex mismatches.
    * **Output errors -** Output errors indicate errors, such as collisions, during the transmission of a frame

## Step 2 - Check for Duplex Mismatches

Duplex configuration guidelines include the following:

* Autonegotiation of speed and duplex is recommended.
* If autonegotiation fails, manually set the speed and duplex on interconnecting ends.
* Point-to-point Ethernet links should always run in full-duplex mode.
* Half-duplex is uncommon and typically encountered only when legacy hubs are used.

## Step 3 - Verify Addressing on the Local Network

When troubleshooting end-to-end connectivity, it is useful to verify mappings between destination IP addresses and Layer 2 Ethernet addresses on individual segments.

In IPv4, this functionality is provided by ARP. In IPv6, the ARP functionality is replaced by the neighbour discovery process and ICMPv6.&#x20;

The neighbour table caches IPv6 addresses and their resolved Ethernet physical (MAC) addresses.

## Step 4 - Verify Default Gateway

* If there is no detailed route on the router, or if the host is configured with the wrong default gateway, then communication between two endpoints in different networks does not work.
* DHCP configuration may need to be also checked

## Step 5 - Verify Correct Path

When troubleshooting, it is often necessary to verify the path to the destination network.

Use commands such as **`show ip route | begin Gateway`** and **`show ipv6 route`** to verify routing information is correct.

The IPv4 and IPv6 routing tables can be populated by the following methods:

* Directly connected networks
* Local host or local routes
* Static routes
* Dynamic routes
* Default routes

The process of forwarding IPv4 and IPv6 packets is based on the longest bit match or longest prefix match.&#x20;

The routing table process will attempt to forward the packet using an entry in the routing table with the greatest number of leftmost matching bits.&#x20;

The number of matching bits is indicated by the prefix length of the route.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-22 at 17.54.42.png" alt=""><figcaption></figcaption></figure>

## Step 6 - Verify the Transport Layer

* If the network layer appears to be functioning as expected, but users are still unable to access resources, then the network administrator must begin troubleshooting the upper layers.&#x20;
* Two of the most common issues that affect transport layer connectivity include ACL configurations and NAT configurations.&#x20;
* A common tool for testing transport layer functionality is the Telnet utility.

{% hint style="warning" %}
**Caution:** While Telnet can be used to test the transport layer, for security reasons, SSH should be used to remotely manage and configure devices.
{% endhint %}

#### Troubleshooting Example

A network administrator is troubleshooting a problem where they cannot connect to a router using HTTP. The administrator pings R2 as shown in the command output.

<pre class="language-bash"><code class="lang-bash"><strong>R1# ping 2001:db8:acad:2::2
</strong><strong>Type escape sequence to abort.
</strong><strong>Sending 5, 100-byte ICMP Echos to 2001:DB8:ACAD:2::2, timeout is 2 seconds:
</strong><strong>!!!!!
</strong><strong>Success rate is 100 percent (5/5), round-trip min/avg/max = 2/2/3 ms
</strong><strong>R1#
</strong></code></pre>

R2 responds and confirms that the network layer, and all layers below the network layer are operational. The administrator knows the issue is with Layer 4 or up and must start troubleshooting those layers.

Next, the administrator verifies that they can Telnet to R2 as shown in the command output.

<pre class="language-bash"><code class="lang-bash"><strong>R1# telnet 2001:db8:acad:2::2
</strong><strong>Trying 2001:DB8:ACAD:2::2 ... Open
</strong><strong>User Access Verification
</strong><strong>Password:
</strong><strong>R2> exit
</strong><strong>[Connection to 2001:db8:acad:2::2 closed by foreign host]
</strong><strong>R1#
</strong></code></pre>

The administrator has confirmed that Telnet services is running on R2. Although the Telnet server application runs on its own well-known port number 23 and Telnet clients connect to this port by default, a different port number can be specified on the client to connect to any TCP port that must be tested.

Using a different port other than TCP port 23 indicates whether the connection is accepted (as indicated by the word “Open” in the output), refused, or times out.

From any of those responses, further conclusions can be made concerning the connectivity.

```bash
R1# telnet 2001:db8:acad:2::2 80
Trying 2001:DB8:ACAD:2::2, 80 ... Open
^C
HTTP/1.1 400 Bad Request
Date: Mon, 04 Nov 2019 12:34:23 GMT
Server: cisco-IOS
Accept-Ranges: none
400 Bad Request
[Connection to 2001:db8:acad:2::2 closed by foreign host]
R1#
```

The output verifies a successful transport layer connection, but R2 is refusing the connection using port 80

## Step 7 - Verify ACLs

On routers, there may be ACLs that prohibit protocols from passing through the interface in the inbound or outbound direction.

Use the **`show ip access-lis`ts** command to display the contents of all IPv4 ACLs and the **`show ipv6 access-list`** command to display the contents of all IPv6 ACLs configured on a router.&#x20;

The specific ACL can be displayed by entering the ACL name or number as an option for this command.&#x20;

The **`show ip interfaces`** and **`show ipv6 interfaces`** commands display IPv4 and IPv6 interface information that indicates whether any IP ACLs are set on the interface.



The **show ip access-lists** command displays that the ACL is configured correctly:

```bash
R3# show ip access-lists
Extended IP access list 100
    10 deny ip 172.16.1.0 0.0.0.255 any (108 matches)
    20 permit ip any any (28 matches)
R3#
```



We can verify which interface has the ACL applied:

```bash
R3# show ip interface serial 0/1/1 | include access list
  Outgoing Common access list is not set
  Outgoing access list is not set
  Inbound Common access list is not set
  Inbound  access list is not set
R3#
R3# show ip interface gig 0/0/0 | include access list
  Outgoing Common access list is not set
  Outgoing access list is not set
  Inbound Common access list is not set
  Inbound  access list is 100
R3#
```

## Step 8 - Verify DNS

When you configure DNS on the device, you can substitute the hostname for the IP address with all IP commands, such as **`ping`** or **`telnet`**.

To display the DNS configuration information on the switch or router, use the **`show running-config`** command.

When there is no DNS server installed, it is possible to enter names to IP mappings directly into the switch or router configuration. Use the **ip host** command to enter a name to be used instead of the IPv4 address of the switch or router:

```bash
R1(config)# ip host ipv4-server 172.16.1.100
R1(config)# exit
R1#
```

Now the assigned name can be used instead of using the IP address:

```bash
R1# ping ipv4-server
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.16.1.100, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 4/5/7 ms
R1#
```

To display the name-to-IP-address mapping information on a Windows-based PC, use the **`nslookup`** command.
