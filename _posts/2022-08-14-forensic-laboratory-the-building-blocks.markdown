---
title:  "Forensics Laboratory - The Building Blocks"
author: Turb0Yoda
date:   2022-08-14 15:25:19 -0700
tags: [laboratory,infrastructure]
comments: true
---


Hiya!

This is the beginning of a series of posts detailing my <italicize>lovely<italicize> experience of building up a new Forensics Laboratory(Lab) for $lastjob. I was put in the unique position to (partially) design and manage construction of the new facility, and move all our infrastructure over while adding onto the backbone and other infrastructure we had previously. As some background, I was managing this facility due to the prior lab manager leaving, and me, while not terribly close to the facility, had spent the most time in forensic labs, including that one, to anyone local, and was thus delegated to managing that facility. The move was not something I had ever planned to take on, but corporate changes with the building required a new facility to be built. Most of what was in the old facility was all tribal knowledge, so alongside the planning/building/move, it was critical to actually document why things were done in such a way for anyone else who took over after me. Additionally, we also had the FBI CJIS audit and ISO 27001/27002 audit and attestation to content with. Both have extremely similar, if not identical compliancy requirements for most items, however, FBI CJIS is what let us work with local/state/federal governments on various cases if need be.

A lot of this information is based off this lovely book here: [Digital Forensics Processing and Procedures: Meeting the Requirements of ISO 17020, ISO 17025, ISO 27001 and Best Practice Requirements] (https://smile.amazon.com/gp/product/1597497428), which was reccomended to me by my former co-worker/mentor who has a hell of a lot more experience with this stuff, and who guided me through the finer points.

## Physical Location

I suppose the obvious comes first- the actual location and general access rules of the lab itself. Not anyone can walk into the lab willy nilly, let alone the building itself. A low-key area, one wholly owned and operated by the company tends to be ideal. All of the usual physical security steps apply to both the building and lab. Employees must have at bare minimum a badge to enter the building, and ideally some sort of '2FA' such as using a pin, fingerprint, retina scanner, etc. Additionally, a man-trap is ideal to have station at the entrance to the building itself. After that, the lab itself <italicize>must</italicize> have "2FA" for entry. Only allowed personnel are able to badge into the lab. Exceptions can be made, eg for maintenance/cleaning, if the lab manager or other authorized personnel are able to be on-site and monitor others in the room.

Cameras should also be monitoring the lab area as well as points of ingress and egress. We logged all motion activity and kept entrance/exit logs of both the card readers and motion for a period of time for compliance reasons - this includes all successful and failed attempts to badge in, and motion activity as detected by the cameras. The company's security team also had alerts for this room treated as a priority above all others to verify the person entering. Essentially, we did our best to turn this room into a SCIF.

For the new location, we were able to segregate the lab into two rooms:
1. Forensic Machines
2. Evidence and Infrastructure

The primary room housed our forensic machines and basic supplies, adapters, etc. Anyone on the ProServ team was allowed into this room. The second room housed evidence safes and servers. Only the Lab Manager and Data Custodians were allowed into this room. 

### Additional Considerations to Physical Location

Aside from the access requirements above, we also added several extras that aren't entirely required, but definitely helpful. 

Both rooms had anti-static flooring, which were linked to grounding straps throughout the room. This was a good addition to a room where sensitive electronics(evidence) would be handled. We also had security mesh installed throughout the walls/floors/ceilings of the room. This is essentially mesh made of <italicize>some</italicize> alloy that prevents people from bashing through the walls, or slows down access if someone attempts to cut through with an angle grinder or plasma cutter. This, in my mind, is the coolest thing by far done to the room, even if it's hard enough to get access to the building alone. If I had another go, I would have also requested mass loaded vinyl to be installed in the walls/ceiling/floor to prevent noise from escaping the room, eg if there is a client call with sensitive information going on. While we did add more insulation than normal, and voices are hard to make out, it definitely made sense to me after-the-fact, something I gathered from adding mass loaded vinyl inside my car to reduce road noise. The lighting in the room was also brighter than what was installed elsewhere, to allow for easier reading of the tiny serial numbers on hard drives or M.2 SSDS.


In my mind, that constitutes the absolute bare bones building block to start building a lab out. The next blog post should be about the actual equipment we used for day-to-day work.