# Design For Scalability

Included in a basic network design strategy are the following recommendations:

* Use expandable, modular equipment, or clustered devices that can be easily upgraded to increase capabilities. Device modules can be added to the existing equipment to support new features and devices without requiring major equipment upgrades. Some devices can be integrated in a cluster to act as one device to simplify management and configuration.
* Design a hierarchical network to include modules that can be added, upgraded, and modified, as necessary, without affecting the design of the other functional areas of the network. For example, creating a separate access layer that can be expanded without affecting the distribution and core layers of the campus network.
* Create an IPv4 and IPv6 address strategy that is hierarchical. Careful address planning eliminates the need to re-address the network to support additional users and services.
* Choose routers or multilayer switches to limit broadcasts and filter other undesirable traffic from the network. Use Layer 3 devices to filter and reduce traffic to the network core.

#### **Redundant Links**

Implement redundant links in the network between critical devices and between access layer and core layer devices

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-18 at 09.45.25.png" alt=""><figcaption><p>Redundant Links</p></figcaption></figure>

#### Multiple Links

Implement multiple links between equipment, with either link aggregation (EtherChannel) or equal cost load balancing, to increase bandwidth.

Combining multiple Ethernet links into a single, load-balanced EtherChannel configuration increases available bandwidth. EtherChannel implementations can be used when budget restrictions prohibit purchasing high-speed interfaces and fiber runs.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-18 at 09.48.27.png" alt=""><figcaption><p>EtherChannel</p></figcaption></figure>

#### Scalable Routing Protocol

Use a scalable routing protocol and implement features within that routing protocol to isolate routing updates and minimise the size of the routing table.

#### Wireless Connectivity

Implement wireless connectivity to allow for mobility and expansion.



