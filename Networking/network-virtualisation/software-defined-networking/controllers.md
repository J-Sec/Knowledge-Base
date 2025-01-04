# Controllers

* The SDN controller defines the data flows between the centralised control plane and the data planes on individual routers and switches.
* Each flow traveling through the network must first get permission from the SDN controller, which verifies that the communication is permissible according to the network policy.
* If the controller allows a flow, it computes a route for the flow to take and adds an entry for that flow in each of the switches along the path
* All complex functions are performed by the controller. The controller populates flow tables. Switches manage the flow tables.

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-03 at 09.38.11.png" alt=""><figcaption></figcaption></figure>

In the figure, an SDN controller communicates with OpenFlow-compatible switches using the OpenFlow protocol. This protocol uses Transport Layer Security (TLS) to securely send control plane communications over the network. Each OpenFlow switch connects to other OpenFlow switches. They can also connect to end-user devices that are part of a packet flow.

Within each switch, a series of tables implemented in hardware or firmware are used to manage the flows of packets through the switch. To the switch, a flow is a sequence of packets that matches a specific entry in a flow table.

The three tables types shown in the previous figure are as follows:

* **Flow Table** - This table matches incoming packets to a particular flow and specifies the functions that are to be performed on the packets. There may be multiple flow tables that operate in a pipeline fashion.
* **Group Table** - A flow table may direct a flow to a Group Table, which may trigger a variety of actions that affect one or more flows
* **Meter Table** - This table triggers a variety of performance-related actions on a flow including the ability to rate-limit the traffic.
