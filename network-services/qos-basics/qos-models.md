# QoS Models

> <mark style="color:green;">**QoS models**</mark> are frameworks that define how Quality of Service policies are applied across a network to prioritise traffic and allocate resources, commonly categorised as Best Effort, Integrated Services (IntServ), and Differentiated Services (DiffServ)

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 13.57.20.png" alt=""><figcaption><p>Models for Implementing QoS</p></figcaption></figure>

## Best-Effort Model

> <mark style="color:blue;">**Best-Effort**</mark> is a network service model where all traffic is treated equally, with no guarantees for delivery, bandwidth, latency, or quality.

* Treats all network packets in the same way, so an emergency voice message is treated the same way that a digital photograph attached to an email is treated

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 14.02.31.png" alt=""><figcaption><p>Benefits &#x26; Drawbacks of Best-Effort Model</p></figcaption></figure>



## Integrated Services (IntServ)

> <mark style="color:blue;">**Integrated Services (IntServ)**</mark> is a QoS model that provides end-to-end resource reservation for specific data flows, ensuring guaranteed bandwidth and low latency for critical applications.

* IntServ architecture model (RFC 1633, 2211, and 2212)
* Multiple-service model that can accommodate many QoS requirements
* Delivers the end-to-end QoS that real-time applications require
* Explicitly manages network resources to provide QoS to individual flows or streams, sometimes called microflows
* Uses resource reservation and admission-control mechanisms as building blocks to establish and maintain QoS
* Uses a connection-oriented approach inherited from telephony network design
* Each individual communication must explicitly specify its traffic descriptor and requested resources to the network
* Uses the Resource Reservation Protocol (RSVP) to signal the QoS needs of an application’s traffic along devices in the end-to-end path through the network

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 14.08.28.png" alt=""><figcaption><p>Benefits &#x26; Drawbacks of IntServ Model</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 14.06.13.png" alt=""><figcaption><p>Example IntServ Model</p></figcaption></figure>



## Differentiated Services (DiffServ)

> <mark style="color:blue;">**Differentiated Services (DiffServ)**</mark> is a scalable QoS model that classifies and marks packets into different classes, enabling routers and switches to apply specific traffic management policies based on the assigned class.

* Can provide low-latency guaranteed service to critical network traffic such as voice or video, while providing simple best-effort traffic guarantees to non-critical services such as web traffic or file transfers
* Overcomes the limitations of both the best-effort and IntServ models
* Described in RFCs 2474, 2597, 2598, 3246, 4594
* Can provide an “almost guaranteed” QoS while still being cost-effective and scalable
* As a host forwards traffic to a router, the router classifies the flows into aggregates (classes) and provides the appropriate QoS policy for the classes.
* DiffServ enforces and applies QoS mechanisms on a hop-by-hop basis

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 16.12.29.png" alt=""><figcaption><p>Benefits &#x26; Drawbacks of DiffServ Model</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 16.09.20.png" alt=""><figcaption><p>DiffServ Example</p></figcaption></figure>

