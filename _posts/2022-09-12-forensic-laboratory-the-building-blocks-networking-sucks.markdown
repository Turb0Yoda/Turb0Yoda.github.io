---
title:  "Forensics Laboratory - Networking Sucks"
author: Turb0Yoda
date:   2022-10-28 19:27:00 -0700
tags: [laboratory,infrastructure,networking]
comments: true
---

# Introduction

I _despise_ networking with a passion. Not because it's overtly complicated.. which it is. It's because I have the absolute worst luck with hardware and making simple configurations work, like when I bricked a Juniper switch by setting a port to trunk. I don't know _how_ it happened or why, but I do know it's what led to that being tossed in the bin. 

Nevertheless, this cursed subject is indeed a requirement to build out a proper laboratory. This post has a list of assumptions about _your_ network, in that your organization already has authentication, VPNs/ZeroTrust, Access Management, AD/DNS, etc all set up. I'll leave covering all that up to the people who know and love networking and will focus primarily on the little nugget that is the lab. Additionally, I won't go too far into configurations of different aspects of networking, primarily due to how different these items can vary from vendor to vendor at all levels of this realm... and because my knowledge doesn't extend that deeply into said realm.


# Hardware Considerations

This section isn't a hardware buying guide insomuch as what you may want to consider when purchasing equipment. The number one thing that comes to mind outside of vendor preferences is throughput and longevity/upgradeability.

I strongly suggest that someone who is building out a forensics lab in this day push their organization to, at a minimum, get hardware that is capable of 10Gbps for data transfer. The time it takes to transfer images between machines and hot/cold storage will be drastically shortened assuming that the destination and/or source are not a single spinning drive. Additionally, if one is getting into a HCI setup, then greater than 10Gbps is ideal. Offhand companies like iXSystems push to have a 40GB connection to the core network for larger SAN devices. This doesn't mean you shouldn't get a standard 1Gbit switch for management or other items that may only be limited to 1GBit, eg a dongle server. Additionally, some switches, such as Cisco Nexus gear, come with empty/filled slots for expansion ports. If you can't get the buy-in now for a full-fat 10GB or greater switch, these may be worth looking into.

# Isolation, Authentication, and Access

As per the tradition of a secure location, only authorized people can get in. As such, the lab network should also be similarly locked down with VPNs, captive portals, etc. Generally speaking, each step of authentication will have 2FA from what I have seen, be it through Duo, a RSA token, or another method. Unfortunately, my lack of knowledge in this specific tooling is pretty lackluster outside of product names. I will say that from what I have seen, initial authentication can be done via the corporate SSO, and then inside-lab-network authentication can be handled with either a separate domain or the corporate domain depending on what is wanted.

## Multiple VLANs

If you're extremely lazy like me, the idea of a flat network for this area sounds amazing. However, it's not the most "secure", and it does get annoying when you have different categories of devices to manage. At bare minimum, there should be at least two VLANs, one for normal workstations, and one for management. If we take a trip down memory lane real fast and look at my previous post on [hardware](https://turb0yoda.com/posts/forensic-laboratory-the-building-blocks-hardware/#forensic-towers), I mentioned making sure that each machine has IPMI/equivalent. Speaking from personal experience, having IPMI is a lifesaver, and keeping it separate from normal workstation addresses helps to not only make sure no one accesses it accidentally/maliciously but to make your network diagrams nicer :). In all seriousness, it also is nice to ensure that only lab administrators/managers have access to this VLAN. 

If you are lucky enough to have a hypervisor/HCI environment in your lab, you will also most likely want a network just for the storage layer. Making a VLAN for the VMs/Containers that will run on that infrastructure will bring up the total count to a nice even number of four. At the end of the day though, you can get by with two if you are careful about what goes where. A quick and dirty reference list is below.

Example Network Structure:
    - 172.16.16.x/24 - Management VLAN
    - 172.16.32.x/24 - Forensic Workstation VLAN
    ---------------------------------------------
    - 172.16.64.x/24 - HCI Storage Layer VLAN
    - 172.16.96.x/24 - HCI VM VLAN

## Conclusion

This post is really short since the networking side of the house is something I avoid, and don't have enough knowledge to flesh this out. I haven't figured out what the next post will be on yet, probably the particulars of handling evidence and such... we'll see.