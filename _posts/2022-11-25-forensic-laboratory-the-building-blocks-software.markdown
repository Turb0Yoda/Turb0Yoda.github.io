---
title:  "Forensics Laboratory - Forensic Software"
author: Turb0Yoda
date:   2022-11-24 18:42:00 -0800
tags: [laboratory,infrastructure,software]
comments: true
---

## Introduction

If I've seen anything close to divisive in the industry, it's the software forensicators use in their day-to-day work. A lot of tools come and go, and a lot remain giants in the field. I don't intend this as an end-all-be-all list of tools you'll see in a lab, but maybe more of the more popular/often used tools, closed-source or open-source, extremely pricey or free-99. At the end of the day, I like to describe most of these tools as a different way to do the same thing. If you're trying to pull out the NTUSER.DAT file from an image or triage data, you can just as easily do that with X-WAYS or EnCase or FTKi or Autopsy. 

I'll do my best to keep this specific post updated with any more tools I find(primarily the specialized tooling section). Additionally, some of these tools can function well in multiple categories. I've put them in what I believe their main focus is, but I will note down if they're able to carry out other tasks- but without further ado...

## Traditional Dead Disk Tooling

- [Autopsy & The Sleuth Kit](https://www.sleuthkit.org/)
    - Autopsy, and by extension The Sleuth Kit, holds a very special place in my heart. This is the tool I used to teach workshops when I was in college, and instead of all of the tools in this section, which are paid, Autopsy(TSK) is free. I can't thank the people enough behind this project(first and foremost in my mind is Dr. Brian Carrier(Writing this post is the first time I learned he had a doctorate, I shouldn't be surprised yet I am) and the Basis Tech team) in keeping this software alive. If you are in a position where you do not have access to the paid tools, you **HAVE** to have Autopsy in your arsenal. Even with the paid tools, we still keep an updated copy of Autopsy ready to go.

        It also deserves mention that Autopsy is the sum of both itself(the GUI) and the underlying "The Sleuth Kit". Just about everyone that I know, including me, simply calls this tool Autopsy, but you can run TSK in just the terminal without the GUI should you wish.

- [AXIOM](https://www.magnetforensics.com/products/magnet-axiom/)
    - I've often jokingly called MAGNET's AXIOM the iOS of forensics - simply click on your image, and the artifacts you want, and go grab a bite to eat. However belittling that sounds, it truly is still a testament to what MAGNET has brought to the table with its product. It may not be as granular as something like X-Ways, but makes up for it in the simpleness of UI and the "quick wins" I often find myself falling back to with it. Additionally, AXIOM supports MacOS, mobile, automotive, and some cloud platforms, making it an extremely unique swiss army knife.

- [EnCase](https://www.opentext.com/products/encase-forensic)
    - The giant in the field, EnCase has been around longer than I've known how to use a computer. I do think it seems to have fallen out of favor over the years, but it still remains a popular tool used by many. 

- [FTK(and it's younger brother FTK Imager)](https://www.exterro.com/forensic-toolkit)
    - FTK is also another giant in the field, but has also suffered a similar fate as EnCase. It is still seen in the field, and it's younger and free brother, [FTK Imager](https://www.exterro.com/ftk-imager), definitely deserves a shout-out. In it's own simplicity, FTKi is extremely useful not only for basic imaging of disks but for quickly pulling singular artifacts out or even _basic_ file recovery.

- [X-Ways Forensic](https://www.x-ways.net/forensics/gramm)
    - I had never heard of X-Ways until relatively recently, only a few years ago. Since then, it has become the one tool that seemingly every shop uses in my eyes. It is both my greatest nightmare and greatest asset. Brett Shavers offers a [great guide](https://smile.amazon.com/X-Ways-Forensics-Practitioners-Guide-Shavers/dp/0578399601) for XWF, I highly reccomend grabbing it if you find yourself working with XWF. XWF also handles MacOS filesystems, but I know little of that since MacOS scares me. 

## Mobile Forensics

- [Cellebrite](https://cellebrite.com/en/home/)
    - Infamous or famous, Cellebrite has carved its name into stone as far as mobile forensics goes. With the Acquisition of BlackBag Technologies, Cellebrite is also now a giant in the MacOS Forensics arena, and is the defacto name for both Mobile and MacOS forensics.

- [Belkasoft](https://belkasoft.com/)
    - Belkasoft is another firm that aims to be more of an AXIOM-like product, focusing on mobile, cloud, and computer forensics. 

- [Elcomsoft](https://www.elcomsoft.com/)
    - Elcomsoft is a Russian-based firm that produces forensic software... for many reasons, I also have no experience with this software.

- [MASB XRY](https://www.msab.com/product/xry-extract/)
    - XRY is also another large name in the industry, but from what I have seen, they primarily target Law Enforcement as their clientele. They have a suite of tools aimed for mobile crime-scene forensics.

- [Oxygen Forensics](https://www.oxygen-forensic.com/en/)
    - Oxygen is another firm that specializes in mobile forensics. I personally have 0 experience with their tooling, so I can't speak to anything about it other than it exists.

## Automotive Forensics
*Disclaimer: I haven't touched automotive forensics, so I will not be doing much other than listing names here.

- [Berla](https://berla.co/)

- [EnVista](https://www.envistaforensics.com/)

- [Teel Tech](https://teeltech.com/)

## Specialized Tooling

- [AccessData Registry Viewer](https://accessdata.com/product-download/registry-viewer-2-0-0)
    - Not updated anymore, but a useful tool for viewing Registry Hives quickly.

- [AnalyzeMFT](https://github.com/dkovar/analyzeMFT)
    - A Python tool for parsing out MFT entries.

- [Arsenal Recon](https://arsenalrecon.com/products)
    - Arsenal provides a range of tools, however, it's image mounting tool is extremely unique in that you can make a virtual machine based off of evidence without altering the original .e01/vmdk/mounted drive. This has absolutely saved our bacon at a past job when the physical domain controller fried and so too did our backup box. The other tools they offer, such as their registry parsing tools, are similarly great.

- [BMC-Tools](https://github.com/ANSSI-FR/bmc-tools)
    - RDP leaves behind a trail of bitmap images that an examiner can sometimes use to put together the RDP session of what was active at a time. While rarely used, sometimes one can get great results and solve an important piece of the puzzle with this tool.

- [CAINE](https://www.caine-live.net/page5/page5.html)
    - A similar tool to SIFT, although it does not get updated as nearly as much from my understanding. It can still be useful to keep around.

- [CyberChef](https://gchq.github.io/CyberChef/)
    - CyberChef, the google translate of the InfoSec world.

- [Digital Detective Dcode](https://www.digital-detective.net/dcode/)
    - A free tool for identifying and decoding different timestamp formats.

- [EZTools](https://ericzimmerman.github.io/#!index.md)
    - Yet another invaluable set of tools, Eric Zimmerman's toolset encompasses a wide gamut of artifacts, primarily/all for Windows forensics.

- [NirSoft Tools](https://launcher.nirsoft.net/)
    - Another set of tools that, while not immediately geared towards forensics, can easily be used for such.

- [OSFMount](https://www.osforensics.com/tools/mount-disk-images.html)
    - A tool for mounting images as well as making RAMDisks, should you casually have a few hundred extra gigabytes of RAM laying around.

- [RegRipper](https://github.com/keydet89/RegRipper3.0)
    - Registry Hives tremble in front of the Ripper.

- [SIFT](https://www.sans.org/tools/sift-workstation/)
    - A bootable ISO that has a load of forensic tools. SANS is an invaluable resource, and this is just one of the many they offer.

- [Volatility](https://www.volatilityfoundation.org/)
    - The memory forensics tool. Yes, _the_ tool. Notably, AXIOM uses Volatility as one of it's built in tools when doing it's automated analysis.


This low effort post brought to you by fear of Thanksgiving Dinner arguments. Happy Thanksgiving!