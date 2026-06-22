# Networking-Lab-RIP

RIP stands for Routing Information Protocol. It is a distance-vector routing protocol that helps routers share route information and choose paths based on hop count, with a maximum usable path length of 15 hops.

•	RIP is used in small to medium networks.

•	Routers send routing updates every 30 seconds / even there is no change.

•	It uses hop count as its metric, so fewer hops mean a better route.

•	A hop count of 16 means the destination is unreachable.

•	Shortest hop/ does not look at high bandwidth.

**RIP version detail:**

•	RIPv1 is the original version. It is classful, so it does not carry subnet mask information and does not support VLSM/CIDR.

•	RIPv2 is the improved version. It is classless, supports subnet masks, VLSM/CIDR, and adds authentication for better security.

•	RIPv1 sends updates by broadcast, while RIPv2 uses multicast to reduce unnecessary network traffic.

•	Both versions still use hop count as the metric, and RIP remains best suited to small networks.

**Why choose RIP v2**

•	It carries subnet mask information, so routers know the exact subnet size.

•	It supports VLSM and CIDR, which helps use IP addresses more efficiently.

•	It can authenticate routing updates, which improves security.

•	It uses multicast updates to reduce unnecessary traffic.

**No auto-summary**

“no auto-summary” is used in RIPv2 to stop routers from automatically summarizing routes at classful network boundaries. This is important when you have subnetted networks or disconnected subnets because automatic summarization can hide the real subnet information and cause routing problems.

•	RIP v1 always uses automatic summarization.

•	RIP v2 can be told not to summarize routes automatically with no auto-summary.

•	This lets subnets be advertised exactly as they are, which is better for VLSM and modern subnetted networks.

**LAB** 

This lab demonstrates RIP configuration on Routers.

Router

1.	Access Router:
• Enter privileged EXEC mode (to run advanced commands):

enable

• Enter global configuration mode (to make configuration changes):

configure terminal

2.	Configure Interface IP Address:

• Enter interface configuration mode :

interface Ethernet0/0

• Set IP address and subnet mask: 

ip address 10.0.0.1 255.255.255.252

• Enable the interface (if it’s administratively down):

No shutdown

Configure all the router interface in similar way.

3.	Save Configuration:

• Save the current configuration to startup-config (to retain changes after reboot):

write 

Or: copy running-config startup-config

4.	Exit Router Mode:

• Exit to previous mode:

exit 

Or: Cltr z

RIP routing command:

router rip
 
 version 2
 
 network 10.0.0.0
 
 network 11.0.0.0
 
 network 192.168.1.0
 
 no auto-summary 

All the directly connected network of each router should be configured.
(Include all the ip address that is not directly connected) Configure all the router interface in similar way.

Router

Configure PC IP address:

ip 192.168.1.2/24 192.168.1.1

save

• Check PC IP address:

Show ip

• Configure all the pc’s interface in similar way.

Ping test result:
 
Trace route result:




 



