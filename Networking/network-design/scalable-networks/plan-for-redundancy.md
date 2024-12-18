# Plan For Redundancy

> Redundancy is an important part of network design. It can prevent disruption of network services by minimising the possibility of a single point of failure.



One method of implementing redundancy is by installing duplicate equipment and providing failover services for critical devices.



Another method of implementing redundancy is redundant paths. Redundant paths offer alternate physical paths for data to traverse the network. Redundant paths in a switched network support high availability. However, due to the operation of switches, redundant paths in a switched Ethernet network may cause logical Layer 2 loops. For this reason, [Spanning Tree Protocol (STP)](#user-content-fn-1)[^1] is required.



Using Layer 3 in the backbone is another way to implement redundancy without the need for STP at Layer 2. Layer 3 also provides best path selection and faster convergence during failover.

[^1]: Link
