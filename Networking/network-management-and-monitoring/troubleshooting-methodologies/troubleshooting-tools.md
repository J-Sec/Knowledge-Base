# Troubleshooting Tools

A wide variety of software and hardware tools are available to make troubleshooting easier. These tools may be used to gather and analyse symptoms of network problems. They often provide monitoring and reporting functions that can be used to establish the network baseline.

## Software Tools

#### Network Management System Tools

* Network management system (NMS) tools include device-level monitoring, configuration, and fault-management tools
* Network monitoring software graphically displays a physical view of network devices, allowing network managers to monitor remote devices continuously and automatically
* Device management software provides dynamic device status, statistics, and configuration information for key network devices

#### Knowledge Bases

* Online network device vendor knowledge bases have become indispensable sources of information
* **Cisco Tools & Resources** page can be found at [http://www.cisco.com](http://www.cisco.com/) under the **Support** menu. This page provides tools that can be used for Cisco hardware and software

#### Baselining Tools

* Baselining tools help with common documentation tasks
* They can draw network diagrams, help keep network software and hardware documentation up-to-date, and help to cost-effectively measure baseline network bandwidth use

## Protocol Analysers

* Protocol analysers can investigate packet content while flowing through the network
* A protocol analyser decodes the various protocol layers in a recorded frame and presents this information in a relatively easy to use format
* The information displayed by a protocol analyser includes the physical layer bit data, data link layer information, protocols, and descriptions for each frame
* Most protocol analysers can filter traffic that meets certain criteria so that all traffic to and from a device can be captured
* It is important to have both a good understanding of TCP/IP and how to use a protocol analyzer to inspect information at each TCP/IP layer.

## Hardware Troubleshooting Tools

#### Digital Multimeters

* Digital multimeters (DMMs) are test instruments that are used to directly measure electrical values of voltage, current, and resistance
* In network troubleshooting, most tests that would need a multimeter involve checking power supply voltage levels and verifying that network devices are receiving power

#### Cable Testers

* Cable testers are specialised, handheld devices designed for testing the various types of data communication cabling
* Cable testers can be used to detect broken wires, crossed-over wiring, shorted connections, and improperly paired connections
* These devices can be inexpensive continuity testers, moderately priced data cabling testers, or expensive time-domain reflectometers (TDRs)
  * TDRs are used to pinpoint the distance to a break in a cable
* TDRs used to test fibre-optic cables are known as optical time-domain reflectometers (OTDRs)

#### Cable Analysers

* Cable analysers are multifunctional handheld devices that are used to test and certify copper and fibre cables for different services and standards.
* The more sophisticated tools include advanced troubleshooting diagnostics that measure the distance to a performance defect such as near-end crosstalk (NEXT) or return loss (RL), identify corrective actions, and graphically display crosstalk and impedance behaviour
* Typically include PC-based software

#### Portable Network Analysers

* Portable devices are used for troubleshooting switched networks and VLANs
* By plugging the network analyser in anywhere on the network, a network engineer can see the switch port to which the device is connected, and the average and peak utilisation
* Can also be used to discover VLAN configuration, identify top network talkers (hosts generating the most traffic), analyse network traffic, and view interface details
* The device can typically output to a PC that has network monitoring software installed for further analysis and troubleshooting

#### **Cisco Prime Network Analysis Module**

* Includes hardware and software for performance analysis in switching and routing environments
* Includes an embedded browser-based interface that generates reports on the traffic that consumes critical network resources
* Can capture and decode packets and track response times to pinpoint an application problem to a network or server

## Syslog Server as a Troubleshooting Tool

* [Syslog](../logging-and-monitoring/syslog.md) is a simple protocol used by an IP device known as a syslog client, to send text-based log messages to another IP device, the syslog server.&#x20;
* Syslog is currently defined in RFC 5424.
* Cisco devices can log information regarding configuration changes, ACL violations, interface status, and many other types of events
* Event messages can be sent to one or more of the following:
  * **Console** - Console logging is on by default. Messages log to the console and can be viewed when modifying or testing the router or switch using terminal emulation software while connected to the console port of the network device.
  * **Terminal lines** - Enabled EXEC sessions can be configured to receive log messages on any terminal lines. Like console logging, this type of logging is not stored by the network device and, therefore, is only valuable to the user on that line.
  * **Buffered logging** - Buffered logging is a little more useful as a troubleshooting tool because log messages are stored in memory for a time. However, log messages are cleared when the device is rebooted.
  * **SNMP traps** - Certain thresholds can be preconfigured on routers and other devices. Router events, such as exceeding a threshold, can be processed by the router and forwarded as SNMP traps to an external SNMP network management station. SNMP traps are a viable security logging facility but require the configuration and maintenance of an SNMP system.
  * **Syslog** - Cisco routers and switches can be configured to forward log messages to an external syslog service. This service can reside on any number of servers or workstations, including Microsoft Windows and Linux-based systems. Syslog is the most popular message logging facility, because it provides long-term log storage capabilities and a central location for all router messages.
