---
description: Explain how networking devices implement QoS.
---

# QoS Basics

> <mark style="color:green;">**Quality of Service (QoS)**</mark> is a set of techniques to manage and prioritise network traffic to ensure optimal performance, reduce latency, and guarantee specific service levels for critical applications.



When congestion occurs on a device (router) will implement some form of QoS technique.



> <mark style="color:blue;">**Bandwidth**</mark> is the maximum amount of data that can be transmitted over a network connection in a given amount of time, typically measured in bits per second (bps).

> <mark style="color:blue;">**Congestion**</mark> in a network occurs when the demand for bandwidth exceeds the available capacity, leading to packet delays, loss, and reduced overall network performance.

> <mark style="color:blue;">**Delay**</mark> (aka. latency)  in a network is the time it takes for data to travel from the source to the destination, including transmission, propagation, processing, and queuing times.

> <mark style="color:blue;">**Jitter**</mark> is the variation in packet arrival times in a network, which can cause uneven data flow and impact the quality of real-time applications like voice and video.



### Examples of Congestion Points

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-28 at 14.18.19.png" alt=""><figcaption><p>Congestion Points</p></figcaption></figure>

Network congestion points are ideal candidates for QoS mechanisms.



### Sources of Delay

Two types of delays are fixed and variable.&#x20;

<mark style="color:orange;">**Fixed delay**</mark>**:** a specific amount of time a specific process takes, such as how long it takes to place a bit on the transmission media.&#x20;

<mark style="color:orange;">**Variable delay**</mark>**:** an unspecified amount of time and is affected by factors such as how much traffic is being processed.

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-28 at 14.20.15.png" alt=""><figcaption><p>Sources of Delay</p></figcaption></figure>



