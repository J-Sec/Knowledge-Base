# Software-Defined Networking

{% hint style="info" %}
<mark style="color:blue;">**Software-Defined Networking (SDN)**</mark> is a networking approach that centralises control through software-based controllers, enabling dynamic, programmable network management and improved flexibility.&#x20;
{% endhint %}

## Control Plane and Data Plane

#### Control Plane

* typically regarded as the brains of a device
* used to make forwarding decisions
* contains Layer 2 and Layer 3 route forwarding mechanisms, such as routing protocol neighbour tables and topology tables, IPv4 and IPv6 routing tables, STP, and the ARP table
* Information sent to the control plane is processed by the CPU

#### Data Plane

* Also called the forwarding plane, this plane is typically the switch fabric connecting the various network ports on a device
* data plane of each device is used to forward traffic flows
* Routers and switches use information from the control plane to forward incoming traffic out the appropriate egress interface.&#x20;
* Information in the data plane is typically processed by a special data plane processor without the CPU getting involved.

In **Software-Defined Networking (SDN)**:

* The **Control Plane** is responsible for making decisions about how data packets are forwarded, such as determining routing paths and network policies. This logic resides in a centralized SDN controller, separate from the network devices.
* The **Data Plane** is responsible for forwarding data packets based on the instructions received from the control plane, handling the actual movement of data through switches, routers, or other network devices.

By decoupling the control plane from the data plane, SDN enables centralised management, programmability, and dynamic configuration of the network.

<figure><img src="../.gitbook/assets/Screenshot 2025-01-02 at 21.24.21.png" alt=""><figcaption><p>Traditional Architecture vs SDN Architecture</p></figcaption></figure>
