---
title:  "Forensics Laboratory - The Building Blocks - Hardware Pt. 1"
author: Turb0Yoda
date:   2022-08-17 21:00:00 -0700
tags: [laboratory,infrastructure,hardware]
comments: true
---

## Introduction 

Hiya! 

This is part two in my little series about building a forensics lab from the ground up... literally. This post will be going over the basic hardware needed to run a lab, covering all aspects from machines to write blockers to the network. In another post, I hope to explore Hyper-Converged Infrastructure for Forensic Analysis, so this will be focused on a lab that does not have a relatively high volume of incoming evidence or work in general. I broke this post up into two parts, the second part should be coming out sometime soon. 

## Physical Machines 

### Forensic Towers 
The first step is to have a bank account with a large amount of money. I wish this was a joke, but unfortunately, tailor-built forensic workstations are extremely pricey. Not only should the hardware be top of the line and beefy, but items like drive cages, DVD/Blu-Ray/CD drives, and even write blockers are often shoved into these chassis. For example, a base configuration [SiForce Lightning X](https://siliconforensics.com/products/forensic-workstations/tower-workstations/siforce-lightning-x-hardware-defined-forensics.html) comes out to a lovely 10,695.00 USD before tax, which isn't an easy pill to swallow. 
<!---
<figure>
    <img src="/assets/post_images/sciforce_lightning_x.png"
         alt="SciForce Lightning X">
    <figcaption>Remember what I said about shoved chock-full of gear? This is how SciForce rolls.</figcaption>
</figure>
-->

For Reference, that system does have 40 threads, 192GB of RAM, and several storage areas for casework (examples in parentheses): 
* 500GB NVMe Boot 
* 1TB NVMe Temp Drive (used for e01s) 
* 8 1TB SSDs in a RAID config (used for software to do processing on) 
* 6TB Spinning rust 

The main benefit of buying from a company like SiForce, aside from these machines only needing a copy of your choice of forensic software(s), is the warranty with the machines. Downtime in an environment like this is unwanted, to say the least. There is little hassle for the lab manager or person handling the hardware while the warranty is active, versus building a system yourself and screaming in pain when a motherboard dies. 

Jokes aside, that system is extremely beefy but is most likely absolute overkill for most outfits. When building these systems, there is a finite number of resources available per user running process/analysis on an image. Tools like MAGNET AXIOM will chew up all your RAM with no regard to anything else, and while this can be limited in the AXIOM profile setup, you still are limited to say, 2-3 AXIOM PROCESS tasks running, at least in my experience. SiForce, alongside an extensive range of other boutique builders such as Sumuri and Digital Intelligence offers comparable/competing workstations. A large portion of deciding what system specifications and the number of systems depends both on the volume of evidence and the number of analysts actively working on disk images. 

In my experience, limiting say, AXIOM to 32GB of RAM and 12-20 threads seems to be the best balance of performance and system usage - you may find other balances with other tools such as X-Ways or EnCase.  
If you do take the DIY route, or go with a non-forensic workstation boutique builder, I do think there should be some strict requirements in mind: 

* A good amount of processor cores and RAM 
  * Make no mistake, your analysis software will chew through everything it's given and then some. It's always better to oversize than to have *just* enough. 
  * Keep in mind that Windows also needs RAM and CPU and running too many tasks (or *cough* AXIOM *cough*) will lock your system up.   
  * You don't need Xeon Platinum's or the top tier Threadripper CPUs and 1TB of RAM per system, but I baseline ~20C/40T and 128GB of RAM to allow multiple analysts to work on one system if necessary. 
* ECC RAM 
  * Every step to prevent data contamination must be taken, ECC is just one step in the process  
* Server/Workstation boards with features such as IPMI 
  * This will save you a lot of time if a machine needs to be remotely rebooted/troubleshot. It also allows even more information to be sent to a remote logging setup such as Zabbix, which will help alert the lab manager/caretakers if any critical issues arise. 
  * Additionally, not only do these boards can house large core count processors and a large amount of RAM, but they also come with many PCI-E slots, meaning adding in items such as extra graphics cards, more LAN controllers, or more RAID cards are extremely easy.  
  * This is, of course, a bit of a generalization in terms of features, but it does tend to be the norm in this class of motherboards. 
  * I highly recommend ensuring your systems have room for any possible expansion. 
* Multiple RAID controllers 
  * This is more about being able to have separate areas for data, but also to ensure there are some redundancies if a drive does go out. I would only recommend using RAID 10, RAID 50, or a similar setup to ensure data isn't lost if a drive dies. 
  * I can imagine seeing people set up a RAID 0 array for temporary files, however, the only way I could plausibly recommend this is if the only data stored on this drive are image files, and there are no less than three copies of the data elsewhere in case there was an incident with a drive dying. 
  * Again, do not recommend running RAID 0 for that level of production. 
* Loads of spare 5.25" Bays 
  * 5.25" bays, while uncommon in this age, are extremely useful for built-in write blockers, docking bays, etc. I wouldn't build a system without at least a few of these. 
* 10GB LAN 
  * This is more of a future-proofing step and can also be added in with an add-on card, but 10GB LAN to transfer case files is a godsend. 

### MacOS 

If you thought you were done spending the big bucks, you were wrong. While tools such as AXIOM and X-Ways *can* parse out MacOS systems, sometimes it is just best to have a dedicated Mac system for processing and analysis, especially with the advent of the new M1/M2 chips from Apple. Unfortunately, I have had no experience with forensically imaging/analyzing the M1/M2 gear, and only a small amount with normal MacOS. 

So, this section is pretty short and sweet. Offhand, I am not entirely sure if software such as Sumuri or Cellebrite will run on M1/M2 gear, but it will run on Intel-based Macs, and will still be able to analyze M1/M2 gear. My current recommendation is to buy either a decently specced Mac Pro (~9,000USD for a system with a 16c/32t processor and 96GB of RAM), or then a decently specced Mac Mini (much cheaper!). In all honesty, unless you happen to have a lot of analysis that needs native MacOS, I would stick with the Mac Mini and a 10GB NIC to host your data elsewhere, as the largest amount of storage on a Mac Mini is 2TB (from this old link on Apple's website). 
 

### Mobile Workstations and Jump kits 

Now let's say you get a call from your boss, and suddenly, you find yourself with a plane ticket for a flight that leaves in 4 hours, and you need to somehow pack all your gear into a neat little case for on-site imaging and analysis. Well fear not, but there are a few options for this! 

For on-the-go imaging/processing/analysis, Silicon Forensics offers the cute little [Nano](https://siliconforensics.com/products/forensic-workstations/forensic-laptops/siforce-nano-ii-hardware-defined-forensics.html), and Digital Intelligence offers the also cute little [μFRED](https://digitalintelligence.com/store/products/microfred?taxon_id=42). These little suckers are a full forensic workstation with a built-in write blocker. You have the choice to have them come with a pelican case and other extra goodies. We bundled ours with a portable monitor and mouse/keyboard setup - all that is needed is a power source and you have a ready-to-go workstation. The main downside to this solution is that it's extremely bulky and won't really fit in a carry-on section. 
<!---
 <table>
  <tr>
    <td><img src="/assets/post_images/sciforce_nano_w_monitor.png" width=270 height=270></td>
    <td><img src="/assets/post_images/ufred_front.png" width=270 height=270></td>
  </tr>
  <tr>
    <td>Nano</td>
    <td>μFRED</td>
  </tr>
 </table>
-->
So, for those of you who are like me and can't carry anything without breaking it, or simply don't have more luggage space, both companies offer "forensic laptops". These are nothing more than extremely beefy gaming laptops/workstation laptops(SiForce's looks eerily like an Alienware to me). The main benefit of these (other than having RGB for better performance :)) is that they're *much* smaller but can pack up to a desktop processor depending on the specific laptop, such as this [Sager](https://www.sagernotebook.com/Notebook-NP9672M-G1.html), which packs up to a desktop Intel i9 and 128GB of RAM. I would really hesitate to call this a laptop, more of a small desktop with a built in UPS since that battery won't last if it must process items. This, combined with a stand-alone write-blocker (I'll get to these in a later section), will be able to do what those specialized little boxes can do. 

But wait, there's more! In the off chance that you only need to image a device or three, you can also use a portable imager. This is an alternative to the aforementioned solutions- much more compact, but also a uni-tasker, something I'm sure Alton Brown won't approve of. These devices can also have their own place in the lab as a dedicated imaging station that does not take up valuable seat space on forensic workstations. Companies such as [Tableau](https://www.forensiccomputers.com/tableau-tx1-forensic-imager.html) and [Logicube](https://www.logicube.com/shop/forensic-falcon-neo/) make such devices. The Logicube unit is especially nice to have as a dedicated in-lab imaging station as it has dual 10GB NICs, which, while may not get close to saturated with spinning rust, will help if you are imaging NVMe devices. 

Regardless of what choice you choose, it's always good to keep evidence bags, chains of custody, stickies, etc. to correctly store evidence. Another good practice is to have a dedicated phone and/or camera just to take photos of evidence - this should all be well-known general practice regardless. 

## Outro 

That will conclude it for this section of the post. I tried to keep this section focused on the physical, expensive compute gear needed. The next section will be focused more on "odds and ends" such as dedicated write blockers, mobile gear, and various adapters and accessories that might come in handy. 

 
 
 

*Disclaimer: I'm not sponsored by any of the companies mentioned above, nor do they know (well I don't think they know) that I've written this. 

 