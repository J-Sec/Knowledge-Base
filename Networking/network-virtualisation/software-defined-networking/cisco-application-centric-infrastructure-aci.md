# Cisco Application Centric Infrastructure (ACI)

{% hint style="info" %}
<mark style="color:blue;">**Cisco Application Centric Infrastructure (ACI)**</mark> is a software-defined networking solution that uses centralised policy-driven automation to simplify, secure, and optimise data centre and cloud network operations.
{% endhint %}

These are the three core components of the ACI architecture:

* **Application Network Profile (ANP)** - An ANP is a collection of end-point groups (EPG), their connections, and the policies that define those connections.
* **Application Policy Infrastructure Controller (APIC)** - The APIC is considered to be the brains of the ACI architecture. APIC is a centralised software controller that manages and operates a scalable ACI clustered fabric. It is designed for programmability and centralised management. It translates application policies into network programming.
* **Cisco Nexus 9000 Series switches** - These switches provide an application-aware switching fabric and work with an APIC to manage the virtual and physical network infrastructure.

The APIC is positioned between the APN and the ACI-enabled network infrastructure. The APIC translates the application requirements into a network configuration to meet those needs.

## Spine-Leaf Topology

* The Cisco ACI fabric is composed of the APIC and the Cisco Nexus 9000 series switches using two-tier spine-leaf topology
* The leaf switches always attach to the spines, but they never attach to each other
* Similarly, the spine switches only attach to the leaf and core switches
* In this two-tier topology, everything is one hop from everything else
* The Cisco APICs and all other devices in the network physically attach to leaf switches
* When compared to SDN, the APIC controller does not manipulate the data path directly. Instead, the APIC centralises the policy definition and programs the leaf switches to forward traffic based on the defined policies

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-04 at 20.47.35.png" alt=""><figcaption></figcaption></figure>

