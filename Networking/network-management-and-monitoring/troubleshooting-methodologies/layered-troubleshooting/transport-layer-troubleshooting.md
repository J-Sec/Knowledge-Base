# Transport Layer Troubleshooting

## ACLs

Problems with ACLs may cause otherwise working systems to fail.

Areas where misconfigurations commonly occur:

<figure><img src="../../../.gitbook/assets/Screenshot 2024-12-22 at 16.36.01.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot 2024-12-22 at 16.39.54.png" alt=""><figcaption></figcaption></figure>

## NAT for IPv4

There are several problems with NAT, such as not interacting with services like DHCP and tunnelling.&#x20;

These can include misconfigured NAT inside, NAT outside, or ACLs.&#x20;

Other issues include interoperability with other network technologies, especially those that contain or derive information from host network addressing in the packet.



Common interoperability areas with NAT:

<figure><img src="../../../.gitbook/assets/Screenshot 2024-12-22 at 16.44.37.png" alt=""><figcaption></figcaption></figure>
