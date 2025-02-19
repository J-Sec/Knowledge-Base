# TMA02 Q2

<table><thead><tr><th width="114">Device</th><th width="113">Interface</th><th width="95">Device Type</th><th width="139">IP</th><th width="158">Subnet Mask</th><th>Default Gateway</th></tr></thead><tbody><tr><td>PC1</td><td>Fa/0</td><td>Host</td><td>192.168.1.153</td><td>255.255.255.0</td><td>192.168.1.1</td></tr><tr><td>PC2</td><td>Fa/0</td><td>Host</td><td>192.168.3.50</td><td>255.255.255.0</td><td>192.168.3.1</td></tr><tr><td>PC3</td><td>Fa/0</td><td>Host</td><td>192.168.4.115</td><td>255.255.255.0</td><td>192.168.4.1</td></tr><tr><td>PC4</td><td>Fa/0</td><td>Host</td><td>192.168.5.83</td><td>255.255.255.128</td><td>192.168.5.1</td></tr><tr><td>PC5</td><td>Fa/0</td><td>Host</td><td>192.168.5.227</td><td>255.255.255.128</td><td><mark style="color:green;">192.168.5.129</mark></td></tr><tr><td>PC6</td><td>Fa/0</td><td>Host</td><td>192.168.2.48</td><td>255.255.255.224</td><td>192.168.2.33</td></tr><tr><td>PC7</td><td>Fa/0</td><td>Host</td><td>192.168.2.67</td><td>255.255.255.224</td><td>192.168.2.65</td></tr><tr><td>Server</td><td></td><td>Server</td><td>203.0.113.27</td><td></td><td></td></tr><tr><td>ISP</td><td>-----------</td><td>Router</td><td>-----------</td><td>-----------</td><td>-----------</td></tr><tr><td></td><td>G0/0/0</td><td></td><td>192.0.2.2</td><td>255.255.255.252</td><td></td></tr><tr><td></td><td>G0/0/1</td><td></td><td>203.0.113.1</td><td>255.2555.255.0</td><td></td></tr><tr><td>HUB</td><td>-----------</td><td>Router</td><td>----------------</td><td>-------------------</td><td>-------------</td></tr><tr><td></td><td>G0/0/0</td><td></td><td>192.0.2.1</td><td>255.255.255.252</td><td></td></tr><tr><td></td><td>S0/1/0</td><td></td><td>192.168.0.1</td><td>255.255.255.252</td><td></td></tr><tr><td></td><td>S0/1/1</td><td></td><td>192.168.0.5</td><td>255.255.255.252</td><td></td></tr><tr><td></td><td>S0/2/0</td><td></td><td>192.168.0.9</td><td>255.255.255.252</td><td></td></tr><tr><td></td><td>S0/2/1</td><td></td><td>192.168.0.13</td><td>255.255.255.252</td><td></td></tr><tr><td>Branch 1</td><td>-----------</td><td>Router</td><td>-------------</td><td>-------------</td><td>-------------</td></tr><tr><td></td><td>G0/0/0</td><td></td><td>192.168.1.1</td><td>255.255.255.0</td><td></td></tr><tr><td></td><td>S0/1/0</td><td></td><td>192.168.0.2</td><td>255.255.255.252</td><td></td></tr><tr><td>Branch 2</td><td> -----------</td><td>Router</td><td>-------------</td><td>-------------</td><td>-------------</td></tr><tr><td></td><td>G0/0/0</td><td></td><td>NONE</td><td></td><td></td></tr><tr><td></td><td>G0/0/0.1</td><td></td><td>192.168.2.1</td><td>255.255.255.224</td><td></td></tr><tr><td></td><td>G0/0/0.32</td><td></td><td>192.168.2.33</td><td>255.255.255.224</td><td></td></tr><tr><td></td><td>G0/0/0.64</td><td></td><td>192.168.2.65</td><td>255.255.255.224</td><td></td></tr><tr><td></td><td>S0/1/0</td><td></td><td><mark style="color:green;">192.168.0.6</mark></td><td>255.255.255.252</td><td></td></tr><tr><td>HQ</td><td>-----------</td><td>Router</td><td>-------------</td><td>-------------</td><td>-------------</td></tr><tr><td></td><td>G0/0/0</td><td></td><td><mark style="color:red;">NONE</mark></td><td></td><td></td></tr><tr><td></td><td>G0/0/0.1</td><td></td><td>192.168.6.1</td><td>255.255.255.0</td><td></td></tr><tr><td></td><td>G0/0/0.5</td><td></td><td>192.168.5.1</td><td>255.255.255.128</td><td></td></tr><tr><td></td><td>G0/0/0.10</td><td></td><td>192.168.5.129</td><td>255.255.255.128</td><td></td></tr><tr><td></td><td>S0/1/0</td><td></td><td>192.168.0.10</td><td>255.255.255.252</td><td></td></tr><tr><td>Factory</td><td>-----------</td><td>Router</td><td>-------------</td><td>-------------</td><td>-------------</td></tr><tr><td></td><td>G0/0/0</td><td></td><td>192.168.3.1</td><td>255.255.255.0</td><td></td></tr><tr><td></td><td>G0/0/1</td><td></td><td>192.168.4.1</td><td>255.255.255.0</td><td></td></tr><tr><td></td><td>S0/1/0</td><td></td><td>192.168.0.14</td><td>255.255.255.252</td><td></td></tr><tr><td>SW-B1</td><td>-----------</td><td>Switch</td><td>-----------</td><td>-----------</td><td>-----------</td></tr><tr><td></td><td>Vlan1</td><td></td><td>192.168.1.252</td><td></td><td></td></tr><tr><td>SW-B2</td><td>------------</td><td>Switch</td><td>-----------</td><td>-----------</td><td>-----------</td></tr><tr><td></td><td>Vlan1</td><td></td><td>192.168.2.17</td><td>255.255.255.224</td><td>192.168.2.1</td></tr><tr><td>SW-F1</td><td>-----------</td><td>Switch</td><td>-----------</td><td>-----------</td><td>-----------</td></tr><tr><td></td><td>Vlan1</td><td></td><td>192.168.3.252</td><td></td><td></td></tr><tr><td>SW-F2</td><td>-----------</td><td>Switch</td><td>-----------</td><td>-----------</td><td>-----------</td></tr><tr><td></td><td>Vlan1</td><td></td><td>192.168.4.252</td><td></td><td></td></tr><tr><td>SW-HQ1</td><td>-----------</td><td>Switch</td><td>-----------</td><td>-------------------</td><td>-----------</td></tr><tr><td></td><td>Vlan1</td><td></td><td>192.168.6.252</td><td>255.255.255.0</td><td>192.168.6.1</td></tr><tr><td>SW-HQ2</td><td></td><td>Switch</td><td></td><td></td><td></td></tr><tr><td></td><td>Vlan1</td><td></td><td>192.168.6.253</td><td>255.255.255.0</td><td>192.168.6.1</td></tr><tr><td>SW-HQ3</td><td></td><td>Switch</td><td></td><td></td><td></td></tr><tr><td></td><td>Vlan1</td><td></td><td>192.168.6.254</td><td>255.255.255.0</td><td>192.168.6.1</td></tr></tbody></table>





## Issue 1 - Wrong IP address on Branch-2 Router S0/1/0 Interface

* PC7 and PC6 can ping each other and their default gateways
* Can't ping other host or webserver (destination host unavailable)
* telnet into default gateway (branch 2)
* routing table shows that ip address of interface S0/1/0 is 192.168.0.17 in the 192.168.0.16/30 network
* cdp neighbors detail command shows that the HUB router is connected via the S0/1/0 interface but with an IP address of 192.168.0.5 which is not in the network of 192.168.0.16/30
* change ip address of interface to 192.168.0.6
* can now ping some hosts and the web server from both PC6 and PC7



## Issue 2 - OSPF network command not set on factory router

* couldn't ping PC3 from PC7
* tracert from PC7 showed packet was being redirected to gateway of last resort (192.0.2.2)
* telnet into HUB router, check routing table notice 192.168.4.0/24 network not on there
* telnet into factory router and check OSPF settings notice network command not used
* used correct network command `network 192.168.4.0 0.0.0.255 area 0`



## Issue 3 - Interface G0/0/1 shutdown on factory router

* while on factory router checked running config and noticed interface was set to shutdown
* changed it with the no shutdown command



## Issue 4 - Default gateway not set on PC5

* couldn't ping PC5 from PC7
* tracert packet to the HQ router
* check running config, couldn't see anything of likely cause
* checked PC5 configurations noticed default gateway not set
* changed default gateway to 192.168.5.129 which is the IP address of the G0/0/0.10 sub interface on the HQ router
* can now ping PC5



## Issue 5 - NAT not set correctly on S0/1/0 on HUB router

* Noticed PC1 couldn't ping web server
* tracert shows the packet at HUB router
* Also noticed can access the website on the web server from PC1 which indicates it could be a NAT or ACL problem.
  * TCP uses port numbers anyway so will work even if PAT is not set correctly
* telnet into HUB router and check configurations
* notice NAT not set correctly on S0/1/0 interface
* changed it with the `ip nat inside` command

