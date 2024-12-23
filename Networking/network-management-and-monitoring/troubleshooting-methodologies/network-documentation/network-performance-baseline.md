# Network Performance Baseline

{% hint style="info" %}
A <mark style="color:blue;">**network performance baseline**</mark> is a reference set of data that captures the normal operating conditions of a network, used to identify and diagnose deviations or issues.
{% endhint %}

A network baseline should answer the following questions:

* How does the network perform during a normal or average day?
* Where are the most errors occurring?
* What part of the network is most heavily used?
* What part of the network is least used?
* Which devices should be monitored and what alert thresholds should be set?
* Can the network meet the identified policies?

{% stepper %}
{% step %}
### Determine What Types of Data to Collect

* Start by selecting a few variables that represent the defined policies
* If too many data points are selected, the amount of data can be overwhelming, making analysis of the collected data difficult
* Start out simply and fine-tune along the way. Some good starting variables are interface utilisation and CPU utilisation
{% endstep %}

{% step %}
### Identify Devices and Ports of Interest

* Use the network topology to identify those devices and ports for which performance data should be measured
* Devices and ports of interest include the following:
  * Network device ports that connect to other network devices
  * Servers
  * Key users
  * Anything else considered critical to operations\\
* A logical network topology can be useful in identifying key devices and ports to monitor
* Remember that an interface on a router or switch can be a virtual interface, such as a switch virtual interface (SVI)
{% endstep %}

{% step %}
### Determine the Baseline Duration

* The length of time and the baseline information being gathered must be long enough to determine a “normal” picture of the network
* It is important that daily trends of network traffic are monitored
* It is also important to monitor for trends that occur over a longer period, such as weekly or monthly
* When capturing data for analysis, the period specified should be, at a minimum, **seven days** long
{% endstep %}
{% endstepper %}

