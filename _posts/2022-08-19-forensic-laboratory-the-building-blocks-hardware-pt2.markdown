---
title:  "Forensics Laboratory - The Building Blocks - Hardware Pt. 2"
author: Turb0Yoda
date:   2022-08-22 21:20:00 -0700
tags: [laboratory,infrastructure,hardware]
comments: true
---

## Introduction
This is the [second part](https://turb0yoda.com/posts/forensic-laboratory-the-building-blocks-hardware/) of the blog post about the hardware needed in a forensics lab. This will all be about the smaller gear and adapters and other miscellaneous stuff you might need. By no means is this comprehensive, partially because my memory is garbage, partially because you will need different gear for different things. A lab specializing in or providing vehicle forensic services will need special gear that I won't be putting down in this article.

## Write Blockers
Write Blockers(AKA Forensic Bridges) are exactly what they say on the tin - they prevent a computer from writing to the media being imaged or analyzed. This is primarily to ensure the evidence is not altered. There are both software and hardware write blockers, although the latter is always preferred.

NIST is lovely enough to have done testing on both [hardware write blockers](https://www.nist.gov/itl/ssd/software-quality-group/computer-forensics-tool-testing-program-cftt/cftt-technical/hardware) and [software write blockers](https://www.nist.gov/itl/ssd/software-quality-group/computer-forensics-tool-testing-program-cftt/cftt-technical/software). This is by no means comprehensive, especially the software list, but it's always good to stick to something on that list in case your methodology is questioned by someone like legal counsel, or if you have to give testimony in court and that is brought up.

I won't touch on software write-blockers as much as they are not nearly as popular/used. Cellebrite offers [softblock](https://cellebrite.com/en/softblock/), [CAINE](https://www.caine-live.net/index.html) and [SIFT](https://www.sans.org/tools/sift-workstation/) both offer similar functionality in included tools, as well as stuff like [ForensicSoft](https://www.forensicsoft.com/). Realistically though, the chances of having to use these are minuscule.

### Portable/Stand-alone 

As far as hardware write-blockers, there are only two options that I've seen ever used or offered widely- Tableau and Wiebetech(CRU). They are identical in functionality and serve the same purpose. Both also offer variants of the docks(coloured bright yellow so you don't miss it) that can be used to write as well if the physical dipswitches or software is adjusted. 

Primarily the only device types you will be imaging in this age are either SATA or PCIe. Form factors will vary, but I will cover that in the Adapters section. Tableau and Wiebetech both offer options for this:

|           | **Tableau T35u** | **Tableau TK7u** | **Wiebetech FUDv6** | **Wiebetech NVMe WriteBlocker** |
|:---------:|:----------------:|:----------------:|:-------------------:|:-------------------------------:|
|  **Type** |     SATA/IDE     |    PCIe(NVMe)    |       SATA/IDE      |            PCIe(NVMe)           |
| **Price** |     [389$ USD](https://www.forensiccomputers.com/tableau-t35u-bridge-kit.html)     |     [475$ USD](https://www.forensiccomputers.com/tableau-t7u-forensic-pcie-bridge.html)     |       [400$ USD](https://wiebetech.com/products/forensic-ultradock-fudv6-0/)      |             [499$ USD](https://wiebetech.com/products/nvme-writeblocker/)            |

<center> Prices sourced from either FCI or Wiebetech Direct </center>

&nbsp;
My recommendation is to spring for Tableau gear if you can do it, as it's way more widely used, otherwise, Wiebetech will work just fine, unless you're cursed like me with stuff breaking randomly - the Wiebetech gear has been finicky for me, whereas the Tableau gear has simply "just worked". 

As far as the PCIe gear, you *may* need additional adapters, but I'll address that in the Adapters section.


### 5.25" Bay

Both companies offer the same product, but one that mounts in a 5.25" bay. Tableau's is the [T356789iu](https://www.forensiccomputers.com/tableau-t356789iu.html) at a nice 1,099$ USD.

Wiebetech has the [Forensic LabDock U5](https://wiebetech.com/products/forensic-labdock-u5/) at a much nicer 399$ USD. 

The Tableau unit is much more versatile, and that wins hands-down due to that, but it also comes at ~2x the cost of the Wiebetech. Again, I highly recommend springing for the Tableau gear.

### Imaging Stations

I covered this in the previous article about forensic hardware, but they merit a duplicate section here. Companies such as [Tableau](https://www.forensiccomputers.com/tableau-tx1-forensic-imager.html) and [Logicube](https://www.logicube.com/shop/forensic-falcon-neo/) make these little devices that are solely built for imaging drives. They take up a lot less space than full-on workstations, and can quickly output to either staging drives or network shares. However, I would consider these devices more of a splurge or non-essential if you are fine with having a separate write-blocker as mentioned above. They make great sense if you are a high throughput shop and need to be imaging items constantly without having to mess with a physical system and kicking users off/messing with mounted drives. Once again, I like the Logicube because of the dual 10GB NICs. Spinning rust won't saturate it but PCIe/NVMe drives will surpass 1GBit *I believe*.

## Mobile Analysis

Mobile Analysis is unique in that you cannot use a write blocker due to how the collection tools operate. If you do need hardware outside of your chosen tool (Cellebrite, Paraben, Oxygen, etc) and the required cables for the device, Cellebrite offers the [Touch2](https://www.teeltech.com/mobile-device-forensic-tools/cellebrite/ufed-touch-ultimate/) which is essentially just a ruggedized tablet preloaded with UFED. Paraben also has a [similar solution](https://www.oxygen-forensic.com/en/products/oxygen-forensic-kit).

However, you will need a faraday bag or box to prevent signals from reaching the phone. Airplane mode/similar alone should not be trusted. Bags/boxes should be used for both transport and storage of the evidence. I like this [kit](https://siliconforensics.com/products/accessories/faraday-bags/faraday-bag-sampler-bundle.html) from Silicon Forensics since it has multiple bags as well as a battery bank if the device must remain on.

I cannot stress how important it is to have at least one of every possible cable or adapter you think you might need. There may be a day where you have to imagine some old external that runs off of firewire or some IDE/PATA hard drive, and not everyone is lucky enough to have a lab next to both a Microcenter, Best Buy, and (when it was still alive anyways) Fry's. Both Cellebrite and Tableau make kits that are essentially just bags/cases full of neatly organized cables. They do come at a premium but are nice if you just want "everything" from a reputable source. 

You can also just go to Amazon and buy a load of adapters or cables that you think you might need. I will stress that it is extremely important to stay with a good brand **and** test them with test media before using it on evidence. I once had a drive go up in smoke due to a dodgy adapter- the only thing that saved me was using test media before going to the evidence itself.

I won't make a list of "essentials" here, since not only will that vary from shop to shop, depending on what you offer, but also since the write blockers will come with their own set of cables, and that very well may be exactly what you need/require and nothing more. But again, it's better to be safe than sorry and on a time crunch ordering a load of items from Amazon and hoping they arrive in time and undamaged.

As the last item, I really, *really** like this [IODD multiple ISO drive cage](https://smile.amazon.com/Iodd-Iodd2531-Black-Virtual-Enclosures/dp/B00TDJ4BJU/). It may be more of a lab manager/tech item, but it's extremely useful to be able to boot off a plethora of ISOs from one drive. They have a few different variants, I simply linked the one I have. Do note that you need to supply a drive, I've tossed in a spare 128GB SSD laying around and filled it with various Windows, Linux, and troubleshooting/testing ISOs. It's saved me more than one time and frees one up from carrying 20 unlabeled random USBs around.

## Outro

I think that mostly covers it for this section. I may make edits/additions to the articles which will be reflected in a little changelog below. As of right now, nothing else comes to mind :).