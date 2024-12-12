# QoS Implementation Techniques

## QoS Tools

There are three categories of QoS tools, as described in the table:

* Classification and marking tools
* Congestion avoidance tools
* Congestion management tools

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 10.21.40.png" alt=""><figcaption><p>QoS Tools</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 10.23.03.png" alt=""><figcaption><p>QoS Sequence</p></figcaption></figure>

* Ingress packets (grey squares) are classified and their respective IP header is marked (coloured squares)
* To avoid congestion, packets are then allocated resources based on defined policies
* Packets are then queued and forwarded out the egress interface based on their defined QoS shaping and policing policy

{% hint style="info" %}
<mark style="color:blue;">**Note**</mark>**:** Classification and marking can be done on ingress or egress, whereas other QoS actions such queuing and shaping are usually done on egress.
{% endhint %}



## Classification and Marking

### Classification

* Before a packet can have a QoS policy applied to it, the packet has to be classified
* Classification determines the class of traffic to which packets or frames belong
* How a packet is classified depends on the QoS implementation
  * Methods of classifying traffic flows at Layer 2 and 3 include using interfaces, ACLs, and class maps
  * Traffic can also be classified at Layers 4 to 7 using Network Based Application Recognition (NBAR)

### Marking

* Marking means that we are adding a value to the packet header
* Devices receiving the packet look at the marked field to see if it matches a defined policy
* Marking should be done as close to the source device as possible
* How traffic is marked usually depends on the technology
* The decision of whether to mark traffic at Layers 2 or 3 (or both) is not trivial and should be made after consideration of the following points:
  * Layer 2 marking of frames can be performed for non-IP traffic.
  * Layer 2 marking of frames is the only QoS option available for switches that are not “IP aware”.
  * Layer 3 marking will carry the QoS information end-to-end.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 10.40.36.png" alt=""><figcaption><p>Traffic Marking for QoS</p></figcaption></figure>

#### Marking at Layer 2

* 802.1Q is the IEEE standard that supports VLAN tagging at Layer 2 on Ethernet networks
* When 802.1Q is implemented, two fields are added to the Ethernet Frame (TPID & <mark style="color:orange;">TCI</mark>)
  * These two fields are inserted into the Ethernet frame following the source MAC address field:

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 10.44.46.png" alt=""><figcaption><p>Ethernet Class of Service (CoS) Values</p></figcaption></figure>

* The 802.1Q standard also includes the QoS prioritisation scheme known as IEEE 802.1p
  * 802.1p standard uses the first three bits in the <mark style="color:orange;">Tag Control Information (TCI)</mark> field
    * Known as the Priority (PRI) field, this 3-bit field identifies the Class of Service (CoS) markings
    * Three bits means that a Layer 2 Ethernet frame can be marked with one of eight levels of priority (values 0-7)

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 10.48.12.png" alt=""><figcaption><p>Ethernet Class of Service (CoS) Values</p></figcaption></figure>

#### Marking at Layer 3

* IPv4 and IPv6 specify an 8-bit field in their packet headers to mark packets
  * Type of Service (ToS) field for IPv4
  * Traffic Class field for IPv6

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 10.53.41.png" alt=""><figcaption><p>IPv4 &#x26; IPv6 Marked Packet Headers</p></figcaption></figure>

* The Type of Service (IPv4) and Traffic Class (IPv6) carry the packet marking as assigned by the QoS classification tools
  * Field is then referred to by receiving devices which forward the packets based on the appropriate assigned QoS policy
* The original IP standard specified the IP Precedence (IPP) field to be used for QoS markings. However, in practice, these three bits did not provide enough granularity to implement QoS
* IPP has been renamed and extended to Differentiated Services Code Point (DSCP) and 6 bits
  * These six bits offer a maximum of 64 possible classes of service
  * The over field is 8 bits with the last two bits saved for Explicit Congestion Notification (ECN) bits used by ECN-aware routers to mark packets instead of dropping them

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.06.18.png" alt=""><figcaption><p>IPP vs the Newer DSPC &#x26; ECN</p></figcaption></figure>

**DSCP Values**

The 64 DSCP values are organised into three categories:

* <mark style="color:green;">**Best-Effort (BE)**</mark> - This is the default for all IP packets. The DSCP value is 0. The per-hop behavior is normal routing. When a router experiences congestion, these packets will be dropped. No QoS plan is implemented.
* <mark style="color:green;">**Expedited Forwarding (EF)**</mark> - RFC 3246 defines EF as the DSCP decimal value 46 (binary 101110). The first 3 bits (101) map directly to the Layer 2 CoS value 5 used for voice traffic. At Layer 3, Cisco recommends that EF only be used to mark voice packets.
* <mark style="color:green;">**Assured Forwarding (AF)**</mark> - RFC 2597 defines AF to use the 5 most significant DSCP bits to indicate queues and drop preference.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.14.02.png" alt=""><figcaption><p>Assured Forwarding Values</p></figcaption></figure>

The **AFxy** formula is specified as follows:

* The first 3 most significant bits are used to designate the class. Class 4 is the best queue and Class 1 is the worst queue.
* The 4th and 5th most significant bits are used to designate the drop preference.
* The 6th most significant bit is set to zero.

For example, AF32 belongs to class 3 (binary 011) and has a medium drop preference (binary 10). The full DSCP value is 28 because you include the 6th 0 bit (binary 011100).



#### **Class Selector Bits**

First 3 most significant bits of the DSCP field indicate the class, these bits are also called the Class Selector (CS) bits

These 3 bits map directly to the 3 bits of the CoS field and the IPP field to maintain compatibility with 802.1p and RFC 791:

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.24.57.png" alt=""><figcaption><p>Layer 2 CoS and Layer 3 ToS</p></figcaption></figure>

The table in the figure shows how the CoS values map to the Class Selectors and the corresponding DSCP 6-bit value. This same table can be used to map IPP values to the Class Selectors:

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.27.06.png" alt=""><figcaption><p>Mapping CoS to Class Selectors in DSCP</p></figcaption></figure>



## Trust Boundaries

{% hint style="info" %}
Traffic should be classified and marked as close to its source as technically and administratively feasible. This defines the trust boundary.
{% endhint %}

Trust boundaries can occur:

1. Trusted endpoints have the capabilities and intelligence to mark application traffic to the appropriate Layer 2 CoS and/or Layer 3 DSCP values. Examples of trusted endpoints include IP phones, wireless access points, videoconferencing gateways and systems, IP conferencing stations, and more.
2. Secure endpoints can have traffic marked at the Layer 2 switch.
3. Traffic can also be marked at Layer 3 switches / routers.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.29.59.png" alt=""><figcaption><p>Various Trust Boundaries</p></figcaption></figure>



## Congestion Avoidance

Congestion avoidance tools:&#x20;

* Monitor network traffic loads in an effort to anticipate and avoid congestion at common network and internetwork bottlenecks before congestion becomes a problem
*   Monitor the average depth of the queue

    * When the queue is below the minimum threshold, there are no drops
    * As the queue fills up to the maximum threshold, a small percentage of packets are dropped
    * When the maximum threshold is passed, all packets are dropped



    <figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.35.28.png" alt=""><figcaption><p>Congestion Avoidance Mechanisms</p></figcaption></figure>


* Some congestion avoidance techniques provide preferential treatment for which packets will get dropped
  * Cisco IOS QoS includes weighted random early detection (WRED) as a possible congestion avoidance solution
    * WRED algorithm allows for congestion avoidance on network interfaces by providing buffer management and allowing TCP traffic to decrease, or throttle back, before buffers are exhausted
    * Using WRED helps avoid tail drops and maximises network use and TCP-based application performance
* There is no congestion avoidance for User Datagram Protocol (UDP)-based traffic
  * queuing and compression techniques help to reduce and even prevent UDP packet loss



### Shaping and Policing

Traffic shaping and traffic policing are two mechanisms provided by Cisco IOS QoS software to prevent congestion



#### Shaping

Traffic shaping retains excess packets in a queue and then schedules the excess for later transmission over increments of time. The result of traffic shaping is a smoothed packet output rate:

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.40.07.png" alt=""><figcaption><p>Shaping Traffic</p></figcaption></figure>

* Shaping implies the existence of a queue and of sufficient memory to buffer delayed packets, while policing does not
* Shaping requires a scheduling function for later transmission of any delayed packets
  * This scheduling function allows you to organise the shaping queue into different queues
  * Examples of scheduling functions are CBWFQ and LLQ
* Shaping is an outbound concept; packets going out an interface get queued and can be shaped



#### Policing

* When the traffic rate reaches the configured maximum rate, excess traffic is dropped (or remarked)
* Policing is applied to inbound traffic on an interface
* Commonly implemented by service providers to enforce a contracted customer information rate (CIR)

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-02 at 11.47.09.png" alt=""><figcaption><p>Policing Traffic</p></figcaption></figure>



## QoS Policy Guidelines

* Your QoS policy must consider the full path from source to destination
* If one device in the path is using a different policy than desired, then the entire QoS policy is impacted

A few guidelines that help ensure the best experience for end users includes the following:

* Enable queuing at every device in the path between source and destination.
* Classify and mark traffic as close the source as possible.
* Shape and police traffic flows as close to their sources as possible.
