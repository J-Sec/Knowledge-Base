# Reduce Failure Domain Size

{% hint style="info" %}
A <mark style="color:blue;">**failure domain**</mark> is the area of a network that is impacted when a critical device or network service experiences problems.
{% endhint %}

The use of redundant links and reliable enterprise-class equipment minimise the chance of disruption in a network.&#x20;

Smaller failure domains reduce the impact of a failure on company productivity. They also simplify the troubleshooting process, thereby, shortening the downtime for all users.



### Limiting the Size of Failure Domains

* In the hierarchical design model, it is easiest and usually least expensive to control the size of a failure domain in the distribution layer.
* In the distribution layer, network errors can be contained to a smaller area; thus, affecting fewer users.&#x20;
* When using Layer 3 devices at the distribution layer, every router functions as a gateway for a limited number of access layer users.

### Switch Block Deployment

* Routers, or multilayer switches, are usually deployed in pairs, with access layer switches evenly divided between them. This configuration is referred to as a building, or departmental, switch block.
* Each switch block acts independently of the others.
* The failure of a single device does not cause the network to go down. Even the failure of an entire switch block does not affect a significant number of end users.
