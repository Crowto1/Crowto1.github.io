---
layout: post
title: Digital Forensics - USB drive investigation
description: >
  The importance of contemporaneous notes in digital forensics. A simulation where I act as a digital forensics expert to find malicious images from a USB drive taken as evidence.
sitemap: false
hide_last_modified: true
---
![800x400](/assets/img/blog/autopsy-logo.png "Autopsy")

This investigation focuses on the forensic analysis of a USB stick image, validated against its provided MD5 hash to ensure integrity. All actions taken during the investigation will be thoroughly documented, including accurate timestamps and the specific forensic tools used, along with their version numbers.

Contemporaneous notes will be maintained and digitally signed by the end of each day to preserve the chain of custody and support evidence admissibility. The investigation will address the questions provided by the line manager and will strictly remain within the defined scope of the case.

## The investigation

| Exhibit        | Description|
|:---------------|:-----------|
| #DFT-USB-A-218 |Forensic image of a USB stick |
| #DFT-MD5-A-218 |Exhibit contains the MD5 hash value of the USB stick provided by the line manager.|

| Tools / Operating system used | Version| Purpose |
|:---------------|:-----------|:--------------------|
|Tsurugi Linux VM|6.9.3|Operating system |
|Autopsy|4.21.0|GUI Digital forensics platform |
|John the Ripper|1.9.0 | Password cracking tool for recovered password protected zip files |
|Python|3.9.0 | Create scripts to automate extracting hidden plaintext from stego images (steganography) |

### Questions: 
1.	**Evidence of weapon images: Does the USB stick (#DFT-USB-A-218) contain or appear to have previously contained weapon-related images? If so, how many unique images are present?** 
-	To determine uniqueness, I calculated the MD5 hash of each image (sufficient for this case, though SHA-256 would provide stronger collision resistance).
2.	**Source of images: Is there evidence indicating how the images were obtained?** 
-	Possible acquisition methods include communication channels (e.g., email, instant messaging) or downloads from external sources. Further analysis of browser history is required.
3.	**Individual vs group involvement: Are there signs that the suspect acted independently or as part of an organized group?** 
-	This requires tracking references to group names, aliases, or other individuals, then assessing their relevance to the case.

4.	**Legality of imports: As possession of weapon images is not inherently illegal outside of England, is there evidence suggesting unlawful imports? If so, for what duration?** 
-	Clarification from the line manager is needed on the definition of "illegal imports" (e.g., whether it refers to foreign downloads, specific file origins, or geolocation). I will send an email to confirm this.
5.	**Third-party access: Is there evidence that another individual accessed the USB stick?**
-	File metadata will be examined for signs of different owners or users. A Python script can be written to automate this analysis.

## Contemporaneous notes (digitally signed)
![800x400](/assets/img/blog/df-cn-proof.png "CN-proof")

The screenshot above displays the contemporaneous notes (CN) recorded during my investigation. Each entry includes a Timestamp Query (TSQ) and a corresponding Timestamp Response (TSR) for every day changes were made. This process verifies the existence and authenticity of the CN at specific points in time.

**This is important as it provides the following:**

- **Verifies authenticity:** Timestamping proves the contemporaneous notes were created at specific times and haven’t been altered, ensuring their integrity.

- **Supports legal admissibility:** Time-stamped documentation strengthens credibility in legal or disciplinary proceedings by showing the notes were made during the actual investigation.

- **Maintains investigative transparency:** It demonstrates a clear, verifiable timeline of actions taken, aligning with forensic best practices and chain of custody standards.


## Outcome of my investigation
I’ve collected evidence from exhibit #DFT-USB-A-218 and ensure integrity of the notes by digitally signing at the end of each day. I ensured to timestamp anytime I use a tool such as Autopsy, Python, JtR and more. Any action made is timestamped with a statement to describe the choices I made in the investigation. In addition, I provided repeatable steps so further investigators can reproduce the same results. I was able to answer the following questions after doing my investigation (doesn’t include contemptuous notes):

1.	**Evidence of weapon images: Does the USB stick (#DFT-USB-A-218) contain or appear to have previously contained weapon-related images? If so, how many unique images are present?**

Yes, there is sufficient evidence that exhibit #DFT-USB-A-218 contains weapon-related images. A total of 16 unique weapon images were recovered from the USB stick:

-	5 images were found in the deleted _ILES folder.
-	11 images were located inside zip archives within the _ILES folder.

Additionally, two more unique weapon images were identified through the suspect's web history database; however, these two were not found on the USB stick itself. In total, 18 unique weapon images were identified during the investigation, with 16 of them residing on exhibit #DFT-USB-A-218.

2.	**Source of images: Is there evidence indicating how the images were obtained?**

Yes. The 16 weapon images stored on the USB stick were sourced from the website operated by individuals named James and Dan. To access these images, the suspect downloaded publicly available images from the site and used a Least Significant Bit (LSB) steganography tool to extract passphrases, which were then used to unlock the weapon images.

The two additional images (not present on the USB stick) were accessed by visiting weapongrove.com and wikipedia.org, as confirmed through the suspect’s browser history database.

3.	**Individual vs group involvement: Are there signs that the suspect acted independently or as part of an organized group?**

Yes. Evidence indicates that the suspect, Ben, is a member of an organised group. The leadership of this group appears to include James and Dan, as supported by:

-	A hidden message found in Crime.pdf.
-	A secret email from Dan referencing collaboration between him and James.

These findings suggest coordinated efforts and hierarchical structure within the group.

4.	**As weapon images are not illegal outside of England, is there evidence of potential illegal imports of such images? If so, for how long?** 

No conclusive evidence was found to support the occurrence of illegal imports. The available data shows downloads from open sources such as Wikipedia and Google, but these do not provide a reliable indication of geographic origin or illegality.

5.	**Is there evidence of another party having accessed the USB stick?**

No. Forensic analysis revealed no evidence of any user other than Ben accessing the USB stick.
