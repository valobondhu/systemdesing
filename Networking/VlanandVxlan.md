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



একটা সুইচের মধ্যে অনেকগুলো পোর্ট থাকে, এর মধ্যে কিছু পোর্ট এক করে একটা নেটওয়ার্ক গ্রুপ, আর কিছু পোর্টকে এক করে কিছু গ্রুপ এভাবে অনেক গুলো নেটওয়ার্ক গ্রুপ বানানো যায়, প্রতিটি গ্রুগকে virtual local area network বা Vlan বলে।

যদি একটি কোম্পানিতে তিনটা গ্রুপ থাকে এবং তাদের ভিন্ন ভিন্ন নেটওর্য়াক দিতে চাই একটা সুইচ দিয়ে তখন vlan   

ব্যবহার করা হয়। যেকন একাউন্টসকে একটা নেটওয়ার্ক 192.168.3.2/24, ডিজাইনকে একটা নেটওয়ার্ক 192.168.4.2/24, অডিটকে একটা নেটওয়ার্ক 192.168.5.3/24 দিতে চাই তখন Vlan খুব কাজের কারণ এতে প্রত্যেক ডিপার্টমেন্টের আলাদা করে সুইচ কেনার খরচ বাচবে। এভাবে একটা সুইচ দিয়ে অনেক গুলো নেটওয়ার্ক করে তা রাউটারের মাধ্যমে একটা  নেটওয়ার্ক থেকে অন্যে নেটওয়ার্কে একসেস দেওয়া যায়। এটাই vlan। Vlan এর আরো অনেক গুলো সুবিধা আছে। 

তবে অসুবিধা  একটা Vlan 4096 টি ইন্টারনেট দিতে পারে তাই এ সমস্যা নমাধান করার জন্যে vxlan। vxlan ও vlan এর মত কাজ করে তবে একটু ভিন্নভাবে করে এটি layer 2 header কে layer 3 তে নিয়ে যাওয়ার সময় UDP তে রুপান্তর করে কাজ করে। vxlan এর মাধ্যমে ১৬ মিলিয়ন টি ইন্টারনেট দিতে পারে। 

এজন্যে বর্তমান cloud এ vxlan ব্যবহার করা হয়। 

আরো জানতে : 



https://www.juniper.net/us/en/research-topics/what-is-vxlan.html

https://www.pcwdld.com/vxlan#wbounce-modal