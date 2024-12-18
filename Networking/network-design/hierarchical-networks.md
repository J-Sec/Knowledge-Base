# Hierarchical Networks

{% hint style="info" %}
<mark style="color:blue;">**Hierarchical networks**</mark> are structured designs that organise devices into layers—core, distribution, and access—to improve scalability, manageability, and performance in a network.
{% endhint %}



## Borderless Switched Networks

{% hint style="info" %}
<mark style="color:blue;">**Borderless switched networks**</mark> are scalable and secure architectures that enable seamless connectivity and access to resources across wired, wireless, and remote networks without location-based restrictions.
{% endhint %}

A borderless switched network builds on the hierarchical network design by leveraging its structured layers (core, distribution, and access) to provide seamless connectivity, scalability, and secure access across diverse and geographically dispersed environments.

<figure><img src="../.gitbook/assets/Screenshot 2024-12-18 at 08.27.24.png" alt=""><figcaption><p>Example Borderless Switched Network</p></figcaption></figure>

Borderless switched network design guidelines are built upon the following principles:

* **Hierarchical** - The design facilitates understanding the role of each device at every tier, simplifies deployment, operation, and management, and reduces fault domains at every tier.
* **Modularity** - The design allows seamless network expansion and integrated service enablement on an on-demand basis.
* **Resiliency** - The design satisfies user expectations for keeping the network always on.
* **Flexibility** - The design allows intelligent traffic load sharing by using all network resources.

These are not independent principles. Understanding how each principle fits in the context of the others is critical.



## Two & Three Tiered Hierarchal Design Frameworks

The three critical layers within these tiered designs are the access, distribution, and core layers.

<figure><img src="../.gitbook/assets/Screenshot 2024-12-18 at 08.34.03.png" alt=""><figcaption><p>Three-Tier Model Example</p></figcaption></figure>

### Access Layer

* Represents the network edge, where traffic enters or exits the campus network
* The primary function of an access layer switch is to provide network access to the user
* Access layer switches connect to distribution layer switches, which implement network foundation technologies such as routing, quality of service, and security

### Distribution Layer

The distribution layer interfaces between the access layer and the core layer to provide many important functions, including the following:

* Aggregating large-scale wiring closet networks
* Aggregating Layer 2 broadcast domains and Layer 3 routing boundaries
* Providing intelligent switching, routing, and network access policy functions to access the rest of the network
* Providing high availability through redundant distribution layer switches to the end user, and equal cost paths to the core
* Providing differentiated services to various classes of service applications at the edge of the network

### Core Layer

* The core layer is the network backbone
* Serves as the aggregator for all of the distribution layer devices and ties the campus together with the rest of the network
* Primary purpose of the core layer is to provide fault isolation and high-speed backbone connectivity

