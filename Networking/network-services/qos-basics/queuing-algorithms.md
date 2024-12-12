# Queuing Algorithms

> <mark style="color:green;">**Queuing**</mark> is a congestion management tool that can buffer, prioritise, and, if required, reorder packets before being transmitted to the destination.



## First In First Out (FIFO)

> <mark style="color:blue;">**First In, First Out (FIFO)**</mark> queuing is a network traffic management method where packets are processed in the exact order they arrive, without prioritisation.

* First come first served queuing
* Buffers and orders packets as they arrive
* Happens when no QoS is implemented
* Important or time-sensitive packets can be dropped in the event of congestion
* Effective for large links that have little delay and minimal congestion

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 11.37.13.png" alt=""><figcaption><p>FIFO Example</p></figcaption></figure>



## Weighted Fair Queuing (WFQ)

> <mark style="color:blue;">**Weighted Fair Queuing (WFQ)**</mark> is a network scheduling algorithm that assigns bandwidth to traffic flows based on predefined weights, ensuring fair and prioritised treatment of multiple traffic types.

* Automated scheduling method that provides fair bandwidth allocation to all network traffic
* Is an implementation of QoS
* Default on E1 Serial interfaces and below
* Applies priority, or weights, to identified traffic and classifies it into conversations or flows
* The flow-based algorithm used by WFQ simultaneously schedules interactive traffic to the front of a queue to reduce response time
* Classifies traffic into different flows based on packet header addressing, including such characteristics as source and destination IP addresses, MAC addresses, port numbers, protocol, and Type of Service (ToS) value
* Not supported with tunnelling and encryption because these features modify the packet content information required by WFQ for classification

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 11.39.26.png" alt=""><figcaption><p>Weighted Fair Queuing Example</p></figcaption></figure>



## Class-Based Weighted Fair Queuing (CBWFQ)

> <mark style="color:blue;">**Class-Based Weighted Fair Queuing (CBWFQ)**</mark> is a traffic management method that organises packets into classes, assigns weights to each class, and allocates bandwidth proportionally to ensure fair and prioritised handling of different traffic types.

* Extends the standard WFQ functionality to provide support for user-defined traffic classes
* Define traffic classes based on match criteria including protocols, access control lists (ACLs), and input interfaces
* A FIFO queue is reserved for each class
* The bandwidth assigned to a class is the guaranteed bandwidth delivered to the class during congestion
* After a queue has reached its configured queue limit, adding more packets to the class causes tail drop or packet drop to take effect

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 11.57.05.png" alt=""><figcaption><p>CBWFQ Example</p></figcaption></figure>



## Low Latency Queuing (LLQ)

> <mark style="color:blue;">**Low Latency Queuing (LLQ)**</mark> is a queuing mechanism that combines Class-Based Weighted Fair Queuing (CBWFQ) with a strict priority queue to ensure low-delay handling of high-priority traffic, such as voice and video.

* Brings strict priority queuing (PQ) to CBWFQ
* Strict PQ allows delay-sensitive packets such as voice to be sent before packets in other queues
* Provides strict priority queuing for CBWFQ, reducing jitter in voice conversations
* Allows delay-sensitive packets such as voice to be sent first (before packets in other queues), giving delay-sensitive packets preferential treatment over other traffic
* It is possible to classify various types of real-time traffic to the strict priority queue, Cisco recommends that only voice traffic be directed to the priority queue

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-29 at 12.01.00.png" alt=""><figcaption><p>LLQ Example</p></figcaption></figure>

