---
title:  "Forensics Laboratory - Frameworks, Attestations and Accreditations"
author: Turb0Yoda
date:   2023-02-15 21:45:00 -0800
tags: [laboratory,audit,attestation,accreditation, Framework]
comments: true
---

# Introduction

Happy New Years! To kick the New Year off, we're gonna talk about probably the worst part, in my opinion, of running one of these bad boys- AUDITS. I will try to fake as much enthusiasm as I can, but I know all too well how boring this part is. This is not intended to be any sort of replacement or guide to set up your environment to the standards mentioned within, but to show you the different setups and overlaps that occur in this mire.


# Why do we have to deal with this crap?

Outside of the general goodness of keeping up secure and sanitary measures within your environment, and having a large document detailing everything, is that some of your customers may actually have a requirement for all their vendors to have a certain accreditation. Alongside this, it serves as a good badge of faith for customers since anyone looking from the outside-in will know that a _minimum_ level of items happens in order to make sure all data/information remains safe. It absolutely will be a key if they compare your services with another firm that is not accredited. If you deal with GDPR or HIPAA, it is doubly more-so important to be compliant.

# Frameworks

Frameworks are, once boiled down, a long bloody list of checkboxes that you have to tick in order to get compliance/Accreditations. In order to get Accreditations, all of the controls listed in the framework(s) have to be met. Just because you meet the requirements of the framework do not automagically get you the accreditation either - an external firm or agency must audit you to ensure they are met.

The one upside is that a lot of the framework's specifications are similar or interrelated such that you can set your standards to whichever is stricter, and then remain compliant for all frameworks you observe.

## ISO 27001

 Accompanying the granddaddy of them all is also ISO 17025, which is aimed specifically at forensic laboratories. Unfortunately, it is the forgotten cousin, so it often does not get mentioned. Any organization can follow this framework and get its respective Accreditation.

 ISO 27002 also tends to fall hand-in-hand with 27001. Whereas ISO 27001 is focused on managing and protecting sensitive information, ISO 27002 is a set of practices for Information Security Management. ISO 27001 comes with accreditation, but ISO 27002 does not.

## NIST 800-53

For Government Agencies, Contractors and... Acquaintances, NIST 800-53 exists. It's essentially a superset of the aforementioned ISO standards. It also comes with its own accreditation, and much more stress.

## FBI CJIS

And for the MacDaddy of stress, we have the FBI CJIS framework and attestation. It's essentially all of the above wrapped up, with even more controls, and one lovely consequence for failure. Being CJIS Accredited means you, and vetted individuals, are able to handle criminal evidence. This is primarily for Government Agencies, but private firms can get this attestation and audit done over a 3-year cycle if they want to work with agencies and local LEOs. The consequence of mishandling evidence, however, results in a nice trip to Federal Prison.

# Attestations and Accreditations

These are the nice shiny badges you get for successfully remaining in compliance with a framework! ISO, NIST, and CJIS all have these bundled with the framework if the organization wishes to pursue it, however there are two Accreditations I have not mentioned yet.

## FEDRAMP

AWS called, and along with the seven-figure bill you've racked up with totally legitimate mining programs, it also came with its own Attestation. It is essentially a NIST-type deal, but aimed towards anything that resides or touches the cloud. If you are looking to work with Agencies and leverage the cloud, then FEDRAMP is a must.

## CMMC

CMMC is a new program on the scene, kicked off in 2020 by the DoD. As expected, it is also for Federal Agencies and contractors, and there are different levels of compliance requirements based on the type of data you handle. It's primarily to safeguard Controlled Unclassified Information, or CUI. CUI was also originally called For Official Use Only, or FOUO, to further add to the confusion. I suppose it also makes more sense grammatically...


# Outro

This is painful to write. INAL or an auditor, so please take the above with a grain of salt. There may be some nuances in phrasing that I may have missed.