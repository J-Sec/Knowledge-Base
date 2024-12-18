# Simple Network Management Protocol (SNMP)

{% hint style="info" %}
<mark style="color:blue;">**SNMP (Simple Network Management Protocol)**</mark> is a standard protocol used for monitoring, managing, and configuring network devices by exchanging management information between devices and network management systems.
{% endhint %}

> <mark style="color:green;">**Port Numbers**</mark>**:**&#x20;
>
> * UDP 161 (Manager to agents & MIB)
> * UDP 162 ( Agents sending traps to manager)
>
> <mark style="color:green;">**RFC**</mark>**:** [1157](https://datatracker.ietf.org/doc/html/rfc1157)



SNMP is an application layer protocol that provides a message format for communication between managers and agents.&#x20;

The SNMP system consists of three elements:

* SNMP manager
* SNMP agents (managed node)
* Management Information Base (MIB)

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-13 at 11.53.37.png" alt=""><figcaption><p>SNMP Overview</p></figcaption></figure>





## SNMP Operation

SNMP agents that reside on managed devices collect and store information about the device and its operation. This information is stored by the agent locally in the MIB. The SNMP manager then uses the SNMP agent to access information within the MIB.



There are two primary SNMP manager requests:

* _<mark style="color:purple;">get request</mark>_: used by the NMS to query the device for data
* _<mark style="color:purple;">set request</mark>_: is used by the NMS to change configuration variables in the agent device, as well as initiate actions with a device

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-13 at 11.57.04.png" alt=""><figcaption><p>get and set Actions</p></figcaption></figure>

The SNMP agent responds to SNMP manager requests as follows:

* **Get an MIB variable** - The SNMP agent performs this function in response to a GetRequest-PDU from the network manager. The agent retrieves the value of the requested MIB variable and responds to the network manager with that value.
* **Set an MIB variable** - The SNMP agent performs this function in response to a SetRequest-PDU from the network manager. The SNMP agent changes the value of the MIB variable to the value specified by the network manager. An SNMP agent reply to a set request includes the new settings in the device.



## SNMP Agent Traps

Data can be collected from the SNMP agents to create network baselines, reports, view real time information and trigger notification of events with SNMP polling.&#x20;



Periodic SNMP polling does have disadvantages. First, there is a delay between the time that an event occurs and the time that it is noticed (via polling) by the NMS. Second, there is a trade-off between polling frequency and bandwidth usage.



To mitigate these disadvantages, it is possible for SNMP agents to generate and send traps to inform the NMS immediately of certain events.



Traps are unsolicited messages alerting the SNMP manager to a condition or event on the network.



Examples of trap conditions include:

* improper user authentication
* restarts,
* ink status (up or down)
* MAC address tracking
* closing of a TCP connection
* loss of connection to a neighbour
* or other significant events

Trap-directed notifications reduce network and agent resources by eliminating the need for some of SNMP polling requests.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-13 at 12.11.29.png" alt=""><figcaption></figcaption></figure>



## SNMP Versions

There are several versions of SNMP:

* **SNMPv1** - This is the Simple Network Management Protocol, a Full Internet Standard, that is defined in RFC 1157.
* **SNMPv2c** - This is defined in RFCs 1901 to 1908. It uses a community-string-based Administrative Framework.
* **SNMPv3** - This is an interoperable standards-based protocol originally defined in RFCs 2273 to 2275. It provides secure access to devices by authenticating and encrypting packets over the network. It includes these security features: message integrity to ensure that a packet was not tampered with in transit, authentication to determine that the message is from a valid source, and encryption to prevent the contents of a message from being read by an unauthorised source.



## Community Strings

{% hint style="info" %}
<mark style="color:blue;">**Community strings**</mark> in SNMP are plaintext passwords that control access to a device's management information, acting as authentication keys for read-only or read-write operations.
{% endhint %}

* SNMPv1 and SNMPv2c use community strings that control access to the MIB.
* SNMP community strings authenticate access to MIB objects.
* There are two types of community strings:
  * <mark style="color:purple;">**Read-only (ro)**</mark> - This type provides access to the MIB variables, but does not allow these variables to be changed, only read. Because security is minimal in version 2c, many organizations use SNMPv2c in read-only mode.
  * <mark style="color:purple;">**Read-write (rw)**</mark> - This type provides read and write access to all objects in the MIB.



## MIB Object ID

{% hint style="info" %}
An <mark style="color:blue;">**MIB Object ID (OID)**</mark> in SNMP is a unique identifier that specifies a particular piece of management information within a device's Management Information Base (MIB).
{% endhint %}

* A Management Information Base (MIB) is a database used by SNMP to organise network management data.
* An Object ID (OID) is a unique numeric identifier assigned to each object in the MIB hierarchy.
* OIDs follow a tree-like structure, starting from a root and branching into specific object categories.
* Each node in the OID represents a level in the hierarchy, with dots separating numbers (e.g., `1.3.6.1.2.1`).
* The OID hierarchy is defined by standards, with some branches reserved for vendors to define custom objects.
* OIDs allow SNMP tools to query or set specific data points, such as CPU usage or interface status.
* A corresponding MIB file provides human-readable names and descriptions for OIDs.
