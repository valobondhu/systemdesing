# What Is VXLAN? The Difference Between Overlay And Underlay

This data is copying from saifudheen blog

Written by [Saifudheen Sidheeq](https://getlabsdone.com/author/admin/)in [Networking](https://getlabsdone.com/category/networking/),[SDN](https://getlabsdone.com/category/sdn/)Last Updated August 4, 2021





When I first heard about VXLAN I asked my colleague, what is VXLAN?



And his answer was it is the same as VLAN but with X in the middle :).
It is such a protocol that is difficult to comprehend for many.

Table of content:

- [What is Vxlan used for?](https://getlabsdone.com/what-is-vxlan-overlay-and-underlay-networks/#anchor1)
- [What is the difference between VLAN and VXLAN?](https://getlabsdone.com/what-is-vxlan-overlay-and-underlay-networks/#anchor2)
- [What is a Vtep in Vxlan?](https://getlabsdone.com/what-is-vxlan-overlay-and-underlay-networks/#anchor3)
- [Differences between the overlay and underlay network.](https://getlabsdone.com/what-is-vxlan-overlay-and-underlay-networks/#anchor4)
- What is VXLAN over IPsec?
  - [Overlay and underlay in plain English.](https://getlabsdone.com/what-is-vxlan-overlay-and-underlay-networks/#anchor8)
- [What happens when the underlay goes down?](https://getlabsdone.com/what-is-vxlan-overlay-and-underlay-networks/#anchor9)
- [What happens when the overlay goes down?](https://getlabsdone.com/what-is-vxlan-overlay-and-underlay-networks/#anchor10)

## What is Vxlan used for?



**VXLAN is a modern network protocol widely deployed in data center clouds, and the Sofware defined networking nowadays.**

If you wanted to understand the VXLAN protocol and how it works, you need  to know why we need a new protocol in the first place and what problem  it is trying to resolve. And the difference between the VLAN and VXLAN.

**Many people get confused that they think that the VXLAN and the VLAN’s are the same, but it is really not.**

So let’s take a look at the **differences between the VLAN and VXLAN.**

## What is the difference between VLAN and VXLAN?

**VLAN is a mechanism of segmenting the layer2 network, separating the single  broadcast domains into multiple ones. Because the VLAN has a 12bit tag,  the maximum allowed VLAN is 4094, which is more than enough for a  traditional network, but not so much for a modern network where  everything is in the cloud with multi-tenants.**

**Since VLAN uses STP and you have multiple redundancy links between the  switches, only one among them will be in a forwarding state. This  creates another problem that it cannot use half of the link efficiently, so you need to work a way around to use the links effectively.**

**In contrast, the VXLAN is a tunneling encapsulation protocol that uses mac in UDP encapsulation.**

**VXLAN maps VLAN ID into the VXLAN VNID. Instead of just carrying the VLANs  within the same layer2 domain, you can stretch the VLAN from one  location to another over layer3 or underlay network. You can have VLAN  100 in location A and VLAN 100 in Location B. With the help of VXLAN,  you can talk to the geographically separated VLAN via layer3. As if it  is the same L2 domain.**

**Basically, there will be a VXLAN tunnel created between the VTEP’s.** And the VXLAN virtual tunnel act as a Overlay network and actual  network act as underlay network. Now you might be wondering what is  underlay and overlay network, we will talk about that as well.

There are some limitations if you think about VLAN’s today. Only 4094 VLANs  are available to use, with many customers moving into the cloud and  physical servers are replaced with VM’s. The availability of just 4094  VLAN’s is not so sufficient.

Especially if you are a cloud company or any network service provider giving services to multiple customers,  you will, for sure, run out of those VLANs pretty quickly. So we need  something that can help us to have the same VLANs across multiple  customers. So we can use VLAN 100 with customer A as well as with  customer B while the VXLAN logically separates both.

Since the VXLAN header is 24bit, you can carry up to 16million VNID’s, and it provides great flexibility for the service provider when it comes to  multi-tenant environments in the cloud.

**Now you know that the VXLAN and VLAN’s are not the same.**

We still use VLAN today in the network, but the VXLAN provides more encapsulation options while using VLAN’s.

## What is a Vtep in Vxlan?

**The traditional network devices cannot read the VXLAN packet, to use VXLAN  you need to use VTEP known as vxlan tunnel endpoint device. VTEP’s can  encapsulate and decapsulate the VXLAN packets; there are two types of  VTEPs. Hardware-based and software-based. VTEP’s are usually configured  with IP addresses.**

When you talk about VXLAN, you will find people talk about underlay and overlay IP network, so **What is overlay and underlay network?**

## Differences between the overlay and underlay network

- [What is the Underlay network?](https://getlabsdone.com/wp-admin/post.php?post=4415&action=edit#anchor5)
- [What is the Overlay network?](https://getlabsdone.com/wp-admin/post.php?post=4415&action=edit#anchor6)

### What is the Underlay network?

**Remember that we spoke about VXALN that carries the VLAN over the Layer3  network, which is nothing but the underlay network. An underlay network  is a physical network that lets you connect between the networking  devices, such as routers, switches, or even firewalls. It also uses the  traditional networking protocol to route the traffic between the hosts.**

**Different vendors have implemented this overlay and underlay with VXLAN on their  products. One such example is the Cisco ACI for the datacenter.**

**There is one product that I worked known as Nuage SD-WAN, which uses this  overlay and underlay mechanism on their VNS SD-WAN platform.**

To learn about it, you can check out the Nuage SD-WAN lab here.

For example, below are the two network Services gateway’s or ( Routers if  you are looking from a traditional network perspective ), and it’s  connected via an **internet link, internet-1.** You can  consider this as an underlay network. Each link has its public IP  network. So ISP here is providing the underlay connectivity.

![img](https://getlabsdone.com/wp-content/uploads/2020/10/image-269.png?ezimgfmt=rs:602x131/rscb17/ng:webp/ngcb17)

These NSG’s could be anywhere geographically separated.

### What is the Overlay network?

**An overlay network is a virtual network routed on top of the underlay  network infrastructure. Routing decisions would take place with the help of software.**

**In both Cisco ACI and Nuage VNS, both use VXLAN as their overlay protocol.**

## What is VXLAN over IPsec?

**Does VXLAN provide security out of the box ? it doesn’t.**

**You usually don’t need any encryption in the data center as it is a trusted zone, but if you start sending the VXLAN traffic out to the internet  similar to how Nuage sd-wan implemented, you need to use IPsec on top of it to encrypt the VXLAN tunnel.**

The example below shows  the two overlay private IP address spaces, 10.1.1.0/24 and 10.2.2.0/24  routed via public underlay (Internet-1**.** From an end-user perspective, they are unaware of the changes.

<iframe id="google_ads_iframe_/1254144/getlabsdone_com-large-mobile-banner-2_0" title="3rd party ad content" name="google_ads_iframe_/1254144/getlabsdone_com-large-mobile-banner-2_0" scrolling="no" marginwidth="0" marginheight="0" style="border: 0px none; vertical-align: bottom; min-width: 100%;" sandbox="allow-forms allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts allow-top-navigation-by-user-activation" srcdoc="" data-google-container-id="a" data-load-complete="true" width="785" height="159" frameborder="0"></iframe>



![img](https://getlabsdone.com/wp-content/uploads/2020/10/image-270.png?ezimgfmt=rs:624x261/rscb17/ng:webp/ngcb17)

The Greenline represents an overlay network

### Overlay and underlay in plain English.

**To make it simpler, let me put it this way,**

**Have you ever worked in virtualization such as VMware or KVM?**

In virtualization, the host where you have the **VM’s resides is called the Host machine (the hypervisor)**, and the **VM’s are called Guest VM’s**. 

**Similarly, The physical networks are called the Underlay network, and the network that runs on top of the physical networks is** called **the overlay network.**

## What happens when the underlay goes down?

![img](https://getlabsdone.com/wp-content/uploads/2020/10/image-272.png?ezimgfmt=rs:785x377/rscb17/ng:webp/ngcb17)

**When the Underlay (Internet-1) network goes down, the overlay network would  also go down because there is no layer3 IP reachability to the remote  hosts.**

## What happens when the overlay goes down?

![img](https://getlabsdone.com/wp-content/uploads/2020/10/image-273.png?ezimgfmt=rs:785x315/rscb17/ng:webp/ngcb17)

**When the overlay network goes down, the Underlay network continues to work,  However, your production traffic will be down, and underlay is unaware  of any of these network outages. As the overlay is independent of the  underlay network.**

So if the underlay is the core network, how do we avoid network outages on **the underlay?**

**In a data center environment, you can have multiple links between the  switches, since there is no STP in place and VXLAN uses ECMP to load  balance between the links. When any of the link goes down you still have redundancy via other links.**


In the case of SD-WAN, you can have a secondary ISP (internet-2) link as an underlay.

![img](https://getlabsdone.com/wp-content/uploads/2020/10/image-271.png?ezimgfmt=rs:562x244/rscb17/ng:webp/ngcb17)

Now you can make both the internet links active, active, which means it can load balance the traffic or do **Active standby, meaning in the even of the internet-1 goes down the internet two would take over** underlay traffic and provide redundancy for overlay.

The overlay network is not aware of any of these changes on the underlay  network. It keeps forwarding traffic as long as the Underlay network is  available.

This concept is also useful during the troubleshooting  of the SDN network. You can also narrow down the issue based on which  layer (underlay or overlay) has the issue.