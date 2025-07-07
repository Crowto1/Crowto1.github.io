---
layout: post
title: Digital Forensics - USB drive investigation
description: >
  The importance of contemptuous notes in digital forensics. A USB drive investigation answering questions from a Line Manager. 
sitemap: false
hide_last_modified: true
---

##### Overview
This investigation focuses on the forensic analysis of a USB stick image, validated against its provided MD5 hash to ensure integrity. All actions taken during the investigation will be thoroughly documented, including accurate timestamps and the specific forensic tools used, along with their version numbers.

Contemporaneous notes will be maintained and digitally signed by the end of each day to preserve the chain of custody and support evidence admissibility. The investigation will address the questions provided by the line manager and will strictly remain within the defined scope of the case.

##### The investigation

| Exhibit        | Description|
|:---------------|:-----------|
| #DFT-USB-A-218 |Forensic image of a USB stick |
| #DFT-MD5-A-218 |Exhibit contains the MD5 hash value of the USB stick provided by the line manager.|

| Tools / Operating system used | Version|
|:---------------|:-----------|
|Tsurugi Linux VM|6.9.3|
|Autopsy|4.21.0|
|John the Ripper|1.9.0 |

|Python|3.9.0 |

Questions: 
1.	Is there evidence on the USB stick #DFT-USB-A-218 that suggests that it contains or contained weapon images? - If so, how many unique images are there? 
-	Since I’m tasked to find the number of unique images, I obtain the MD5 digest of each individual image (MD5 suffices for the investigation, although SHA-256 is more collision resistant).
2.	Is there evidence of how any images that are present have been obtained? 
-	Most likely images would be obtained via communication (email, IM platforms, etc) or downloaded from external sources, further investigation on browser history required.
3.	Are there indicators whether the suspect acted alone or is a member of an organised group? 
-	Keep track of identities such as group names or individuals and decide on the relevancy. 

4.	As weapon images are not illegal outside of England, is there evidence of potential illegal imports of such images? If so, for how long? 
-	Make it clear on the definition of illegal imports with the line manager, does it mean external downloads, location of the images etc... Send an email to clear this up.
5.	Is there evidence of another party having accessed the USB stick?
-	Examine the metadata of the files to find other owners. Create a python script to automate this.

<src img="/assets/img/blog/df-cn-proof.png"></src>
