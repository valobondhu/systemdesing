# Vlan
Vlan allow to break up one pysical switch into multiple virtual switched. VLANs are usually configured on switches by placing some interfaces into one broadcast domain and some interfaces into another. Each VLAN acts as a subgroup of the switch ports in an Ethernet LAN.

#  Vxlan

## What is VXLAN?

VXLAN is an encapsulation protocol that provides data center  connectivity using tunneling to stretch Layer 2 connections over an  underlying Layer 3 network.

In data centers, VXLAN is the most commonly used protocol to create  overlay networks that sit on top of the physical network, enabling the  use of virtual networks. The VXLAN protocol supports the virtualization  of the data center network while addressing the needs of multi-tenant  data centers by providing the necessary segmentation on a large scale.

 

## What Problem Does VXLAN Solve?

Data centers have rapidly increased their server virtualization over  the past decade, resulting in dramatic increases in agility and  flexibility. Virtualization of the network and decoupling the virtual  network from the physical network makes it easier to manage, automate,  and orchestrate.

VXLAN is a technology that allows you to segment your networks (as  VLANs do) but also solves the scaling limitation of VLANs and provides  benefits that VLANs cannot. Some of the important benefits of using  VXLANs include:

- You can theoretically create as many as 16 million VXLANs in an administrative domain (as opposed to 4094 VLANs).
- VXLANs provide network segmentation at the scale required by cloud builders to support very large numbers of tenants.
- With traditional Layer 2 networks you are constrained by Layer 2  boundaries and forced to create large or geographically stretched Layer 2 domains. VXLAN's functionality allows you to dynamically allocate  resources within or between data centers and enables migration of  virtual machines between servers that exist in separate Layer 2 domains  by tunneling the traffic over Layer 3 networks.

 

## How Does VXLAN Work?

The VXLAN tunneling protocol that encapsulates Layer 2 Ethernet  frames in Layer 3 UDP packets, enables you to create virtualized Layer 2 subnets, or segments, that span physical Layer 3 networks. Each Layer 2 subnet is uniquely identified by a VXLAN network identifier (VNI) that  segments traffic.

The entity that performs the encapsulation and decapsulation of  packets is called a VXLAN tunnel endpoint (VTEP). To support devices  that can’t act as a VTEP on their own, like bare-metal servers, a  Juniper Networks device can encapsulate and de-encapsulate data packets. This type of VTEP is known as a hardware VTEP. VTEPs can also reside in hypervisor hosts, such as kernel-based virtual machine (KVM) hosts, to  directly support virtualized workloads. This type of VTEP is known as a  software VTEP.

Hardware and software VTEPs are shown below.

​                                                ![img](https://www.juniper.net/content/dam/www/assets/images/us/en/research-topics/what-is/diagram-what-is-vx-wan-1.png/_jcr_content/renditions/cq5dam.web.1280.1280.png)            

Hardware and software VTEPs are shown above.

 

​                                                ![img](https://www.juniper.net/content/dam/www/assets/images/us/en/research-topics/what-is/diagram-what-is-vx-wan-2.png/_jcr_content/renditions/cq5dam.web.1280.1280.png)            

...

--------------------------

---------------------------------



# VXLan – What Is it & Quick Tutorial



![VxLAN](https://www.pcwdld.com/wp-content/uploads/VxLAN.jpg)

Your network is growing up and getting out of control.

You might have physical hosts and Virtual Machines distributed across the entire network, which you might want to get into the same network  segment.

Stretching your VLANs could be a solution, as it can help you span your layer 2 across the physical network.

But the problem is that the number of VLANs runs out quickly and the solution is VxLAN.

With this technology, you can layer 2 networks on top of your existing layer 3 network.

All those distributed hosts can be kept together using VxLAN.

In this article, we'll provide an overview of VXLAN and you'll learn what it is, how it works, and where to use it.

You'll also learn about its benefits and deployment method.

Let's dive in!

## 1. What is VxLAN?

VxLAN (**Virtual extensible Local Area Network**) is an industry-standard overlay network virtualization technology.

It was initially designed to address the issues related to  scalability in large-scale network deployments such as ISPs or cloud  providers.

As the name implies, VxLAN virtually extends a layer 2 segment across the layer 3 network infrastructure. VxLAN encapsulates the layer 2  Ethernet frames inside a VXLAN packet that includes an IP address.

VxLAN segments are identified by a 24-bit VNID (VxLAN IDentification) field which can scale to 16 million segments.

The VxLAN is a standardized specification created by the  collaboration of VMware, Cisco, and Arista Network vendors. VxLAN is  defined in the [RFC 7348](https://tools.ietf.org/html/rfc7348)

### a. VxLAN vs. VLAN

VxLAN is very similar to VLAN, which also encapsulates layer 2 frames and segments networks.

The main difference is that VLAN uses the tag on the layer 2 frame for encapsulation and can scale up to 4000 VLANs.

VXLAN, on the other hand, encapsulates the MAC in UDP and is capable of scaling up to 16 million VxLAN segments.

### b. What are VxLAN major advantages?

It is a fact that one of the significant benefits of VxLAN is  scalability. But when you can span layer 2 networks across IP network  infrastructure, there are also many more benefits.

1. **Scalability and flexibility**: VxLAN improves the scalability  in a network or virtualized data center, and it also makes its fabric  more flexible. The number of VLAN layer 2 identifiers are drastically  increased from 4,000 to 16 million.
2. **Segmentation and Multi-tenancy:** VxLAN provides a high level  of security by segmenting the network. The VxLAN traffic is limited to  VNI, so it is isolated. This segmentation can also help in multi-tenant  architectures, where a single infrastructure must be shared.
3. **Layer 2 Simplification.** Simplify the network and reduce the need for layer 2 Spanning Trees, Trunking, and VLAN stretching.
4. **Allow IP Mobility:** VMs can be migrated from a host in a subnet to another host in another subnet without having to change the IP address.
5. **Layer 2 and layer 3 Connectivity.** A virtual layer 2 running  VNIs is built upon a layer 3 infrastructure running IP. VxLAN switches  encapsulate layer 2 frames into layer 3 packets.
6. **It is a Software-Defined Network (SDN)**. VxLAN decouples the  central network controller (virtual network) from the data plane  (physical network). Having a centralized controller simplifies network  management, deployment, and monitoring. An example of a software-based  virtual network switch that supports VxLAN overlays is [Open vSwitch](https://www.openvswitch.org/).
7. **Hardware Support:** Although it is more common to run VxLAN in  software, some platforms implement it in hardware through ASICs. An  example is Cisco’s [Nexus 9000-EX](https://www.cisco.com/c/en/us/products/switches/nexus-9000-series-switches/index.html) platform switches.
8. **It is a standard:** VXLAN is a technical standard. When you implement it, you are not locked by any vendor.

## 2. VxLAN Overlay Network Design

VxLAN is an overlay encapsulation technology. It creates a virtual  network overlaid on top of the existing physical network infrastructure.

It uses the underlay IP network and builds a flexible layer 2 overlay logical network on it.

With the overlay, any layer 2 connection can span across layer 3 network.



![VxLan Overlay](https://www.pcwdld.com/wp-content/uploads/VxLan-Overlay-1024x507.jpg)

There are many advantages to using an overlay network.

The most obvious one is its segmentation.

The overlay and the underlay networks are totally independent, so if  there is a change in the underlay network topology, the overlay network  will not be affected (design-wise).

The overlay network can be re-designed without needing to add, remove, or update network devices.

Of course, physical problems that affect performance or uptime of the underlay will be reflected on the overlay.

For example, if there are not enough devices to provide enough bandwidth, the overlay will also be affected.

How does the overlay VxLAN avoid being affected by underlay changes?

Using a switching fabric, referred to as the Spine-and-Leaf.

### a. Spine-and-Leaf (Underlay) + VxLAN (Overlay)

The best way to guarantee performance, scalability, reliability, and  flexibility on a VxLAN overlay while allowing the underlay to change, is to make good use of a switching fabric topology.

The best example of a switching fabric topology is the Spine-and-Leaf, which is commonly used as an underlay network.

Spine-and-leaf is an independent architecture. It is not exclusive to VxLAN, but it is often associated with it.

Usually the spine-and-leaf is the underlay of the VxLAN is the overlay.



![Spine-and-Leaf (Underlay) + VxLAN (Overlay)](https://www.pcwdld.com/wp-content/uploads/Spine-and-Leaf-Underlay-VxLAN-Overlay-1024x576.jpg)

**Spine-and-Leaf uses two layers:**

- **Spine:** The spine layer switches are only used to pass traffic through leaf switches. They are not aware of VxLAN.
- **Leaf:** The Leaf layer of switches interconnect the spine and  the end points. The leaf layer switches create the VxLAN tunnels,  encapsulation, and maps VLANs to VNI. The leaf switches that perform  VxLAN functions are known as VTPEs (VxLAN Tunnel Endpoints

All the leaf switches have a link to every spine switch. Every link  between leaf and switch is routed through an IP address by an IGP  routing protocol such as BGP or OSPF.

This topology makes every destination only two hops away.

Leaf-and-switch may also use ECMP (Equal Cost Multi-Pathing) to  recover when a spine switch or link fails or to balance the traffic  loads.

The spine-and-leaf fabric topology is highly relevant to VxLAN  because, as the overlay network scales, the supporting underlay can  physically grow or decrease the size without affecting the design of the overlay.

Adding VxLAN on top of the spine-and-leaf underlay allows IP mobility of east-west traffic patterns, full scalability, and fault tolerance.

As your network scales, your design doesn’t need to change.

You just need to add more switches, IP addresses, and links to the underlay.

## 3. VXLAN Encapsulation

We know so far that VxLAN stretches the layer 2 subnets across the  layer 3 network limits. It builds a logical overlay network on top of a  switching fabric like the Spine-and-Leaf.

To make this work, **VxLAN encapsulates layer 2 Ethernet frames in a VxLAN packet that is also encapsulated in an IP UDP header.** 

The following picture shows the VxLAN packet format.

![VXLAN Encapsulation](https://www.pcwdld.com/wp-content/uploads/VXLAN-Encapsulation-1024x458.jpg)



VxLAN adds the following fields to the original Layer 2 frame.

- **Outer MAC header:** This is the header that contains  information for next-hop transport. It includes the destination and the  source MAC address of the VxLAN endpoints, a VLAN ID (16 bits), and  Type. The size of the outer MAC header is 14 bytes.
- **Outer IP header:** This header allows transport across the IP  network. It includes the destination and the source IP address of the  VxLAN endpoints. The size of the outer IP header is 20 bytes.
- **Outer UDP header:** This header identifies the packet as VxLAN. It contains the UDP source port, VxLAN port, and UDP length. The size  of the UDP header is 8 bytes.
- **A VxLAN header.** This header is also referred to as the VxLAN  Network Identifier (VNI). The VNID is used to identify the VxLAN  segment. It is similar to the VLAN ID tag (16 bits) found on the MAC  header but with a size of 24 bits, which allows up to 16 million  different segments.

## 4. VxLAN Tunnel Endpoints (VTEPs)

Any endpoint like a host, switch, or router that supports VxLAN can be referred to as a VTPE (VxLAN Tunnel Endpoint).

As the name implies, the job of VTEPs is to create and terminate  tunnels between each other. In other words, they encapsulate and  decapsulate VxLAN traffic.

### a. How does a VTEP work?

The VTPE is connected to the underlay network using a layer 3 IP address. VTPEs may have one or more VNIs associated with it.

When a layer 2 frame with the same VNI arrives at the ingress VTEP, it encapsulates the frame with a VxLAN and UDP/IP headers.

Then sends it over using the underlay IP network transport towards the egress VTPE for decapsulation.

The egress VTPE removes the IP and UDP headers and delivers the original layer 2 frame.



![VXLAN Tunnel Endpoints](https://www.pcwdld.com/wp-content/uploads/VXLAN-Tunnel-Endpoints-1024x399.jpg)

A VTEP can be either a virtual or a physical switch port and is usually configured on leaf switches.

VTEPs communicate using traditional underlay IP routing and forwarding mechanisms such as OSPF and EIGRP.

### b. VTEP + IP Transport: The Bud Node

In some cases, you might need a device to forward IP traffic and perform VxLAN encapsulation/decapsulation.

A bud node is a switching device with two roles, a VTEP to perform  VxLAN related tasks and an IP transit device to forward VxLAN traffic.

In order to deliver traffic to other VTEPs, the bud node should be in the same multicast group used by the VxLAN VNIs.

The below screenshot shows an example of the bud node. Let’s say that host 1 wants to communicate with host 3.

The VTEP-2 and VTEP-3 belong to a multicast group used for VXLAN  VNIs. The VTEP-2 checks the VxLAN ID from the packet and forwards it  based on IP.

But if Host-1 wants to communicate with host-2, VTEP-2 can also decapsulate the VxLAN packet.



![Bud Node](https://www.pcwdld.com/wp-content/uploads/Bud-Node-1024x432.jpg)

Not all platforms can be a bud node. Running two roles at the same time requires powerful processing power.

Platforms that run VxLAN on ASIC, such as the Cisco Nexus 9000 series, are adequate for this type of topology.

### c. VTEP Redundancy with vPC

VTEPs may fail, so you would need to consider a way to provide redundancy and load sharing.

Although the design of the spine-and-leaf topology is already  redundant and leaves are not supposed to connect to each other, you can  still introduce peering between them to provide host-level redundancy.

Two leaf VTEPs gateways can act as one through peer-link and  keep-alive links. You can accomplish this with a Cisco-based feature,  called the vPC (Virtual Port-Channel).

vPC is a layer 2 feature found on the Cisco Nexus switches, which allows you to connect a host to two switches at the same time.

The pair of virtual vPC switches can provide redundancy to the attached hosts.

These vPCs work as logical VTEP devices sharing an anycast address.

## 5. Deploying VxLAN

VxLAN is a standard-based technology, so it is not limited to a specific vendor and can be supported by hardware or software.

You can deploy the technology through a VxLAN host or VxLAN gateway.  You can limit the deployment to one method or use a combination of both.

### a. Host-based VxLAN

VxLAN doesn’t need to be deployed on a switch; it can also run on any host, as long as it natively supports VxLAN.

An example is a hypervisor, which can be configured to run VxLAN on all of its virtual machines.

The vSwitch running the functions of the VTEP, encapsulates traffic coming from the VMs before they go out to physical switches.

Since the VxLAN encapsulation is happening at the host, the rest of the network infrastructure only sees IP traffic.

The advantage of a host-based deployment is that the entire physical network can be simplified.

Other examples of hosts that may support VxLAN are servers, firewalls, load balancers, etc.

### b. Gateway-based VxLAN

When hosts do not support VxLAN, the best way to deploy it is directly on a switch or router.

When a switch performs the VTEP functions, it is referred to as a VxLAN Gateway.

The switches can perform VxLAN encapsulation/decapsulation and can also translate the VLAN ID to VNI.

The VxLAN gateway creates the tunnel to the destination VTEP (either  host or gateway), so the hosts and IP infrastructure are not aware of  the existence of VxLAN.

A benefit of gateway-based deployments is that some platforms such as the [Cisco Nexus 9000-EX](https://www.cisco.com/c/en/us/products/collateral/switches/nexus-9000-series-switches/white-paper-c11-732453.html#_Toc401870675) are capable of implementing VxLAN on hardware.

Running VxLAN right from the ASIC, rather than from software, can increase performance dramatically.

### c. Hybrid Deployment

You can also use a combination of both. A hybrid deployment is when  you are using VxLAN with some devices behind a VxLAN Gateway and also  have some hosts running native VxLAN.

## 6. Putting it all Together

Now that you know about Spine-and-leaf overlay topology, VxLAN  encapsulation, and VTEPs, let’s go through the process of how VxLAN  traffic flows from host to host in a simple VxLAN network.

![Putting it All Together](https://www.pcwdld.com/wp-content/uploads/Putting-it-All-Together-1024x336.jpg)



1. Host A wants to communicate with Host Z on the other side of the  network. Host A (unaware of VxLAN) creates a regular layer 2 frame and  sends it over to the switch port. The receiving access switch port is  configured with a specific VLAN. So the switch assigns the VLAN ID to  the frame coming from Host A.
2. The Switch A (VxLAN Gateway) with the role of VTEP, maps the  (source) VLAN ID with the (destination) VxLAN ID. The VTEP adds the  VxLAN header, and encapsulates the layer 2 frame into a layer 3 packet,  and forwards it across the layer 3 infrastructure.
3. Now, the in-between layer 3 infrastructure only sees IP traffic and  is unaware of any VxLAN information. The VxLAN traffic is tunneled. All  routers on the underlay network, only see an IP header, so they just  forward it accordingly.
4. The receiving end (VxLAN Gateway), Switch B which is also a VTEP,  opens up the packet and finds the VxLAN information. Switch B also  understands VxLAN and knows the VxLAN ID to VLAN ID map. So it takes the packet, uncovers the VLAN ID, and uses the destination MAC address to  switch it to the respective access switch port.
5. Host Z, also unaware of VxLAN, receives the regular layer 2 frame sent from Host A.



---------------------



একটা সুইচের মধ্যে অনেকগুলো পোর্ট থাকে, এর মধ্যে কিছু পোর্ট এক করে একটা নেটওয়ার্ক গ্রুপ, আর কিছু পোর্টকে এক করে কিছু গ্রুপ এভাবে অনেক গুলো নেটওয়ার্ক গ্রুপ বানানো যায়, প্রতিটি গ্রুগকে virtual local area network বা Vlan বলে।

যদি একটি কোম্পানিতে তিনটা গ্রুপ থাকে এবং তাদের ভিন্ন ভিন্ন নেটওর্য়াক দিতে চাই একটা সুইচ দিয়ে তখন vlan   

ব্যবহার করা হয়। যেকন একাউন্টসকে একটা নেটওয়ার্ক 192.168.3.2/24, ডিজাইনকে একটা নেটওয়ার্ক 192.168.4.2/24, অডিটকে একটা নেটওয়ার্ক 192.168.5.3/24 দিতে চাই তখন Vlan খুব কাজের কারণ এতে প্রত্যেক ডিপার্টমেন্টের আলাদা করে সুইচ কেনার খরচ বাচবে। এভাবে একটা সুইচ দিয়ে অনেক গুলো নেটওয়ার্ক করে তা রাউটারের মাধ্যমে একটা  নেটওয়ার্ক থেকে অন্যে নেটওয়ার্কে একসেস দেওয়া যায়। এটাই vlan। Vlan এর আরো অনেক গুলো সুবিধা আছে। 

তবে অসুবিধা  একটা Vlan 4096 টি ইন্টারনেট দিতে পারে তাই এ সমস্যা নমাধান করার জন্যে vxlan। vxlan ও vlan এর মত কাজ করে তবে একটু ভিন্নভাবে করে এটি layer 2 header কে layer 3 তে নিয়ে যাওয়ার সময় UDP তে রুপান্তর করে কাজ করে। vxlan এর মাধ্যমে ১৬ মিলিয়ন টি ইন্টারনেট দিতে পারে। 

এজন্যে বর্তমান cloud এ vxlan ব্যবহার করা হয়। 

আরো জানতে : 



https://www.juniper.net/us/en/research-topics/what-is-vxlan.html

https://www.pcwdld.com/vxlan#wbounce-modal