---
title: Site Visit File Transfers
layout: default
nav_order: 4
parent: Site Visits
---

# Site Visit File Transfers
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }
---
title: On-Site Transfers
layout: default
nav_order: 2
parent: Site Visits
---

## On-Site File Transfers

{: .no_toc }

When the Library acquires a copy of digital files, rather than the digital carriers themselves, Digital Archives prefers to make the copy on-site instead of bringing the carrier to the lab, copying, and returning.

The file transfer workflows are detailed in this document.
The workflow may need to be adapted based on the media types and file types encountered.
Transferring material during a site visit will differ from transferring material in the lab.

## Preparing the Transfer

* Use acquisition dossiers to understand the scale of the transfer.
* Contact the donor or organization for further details about:
  * the types of carriers (external drives, network storage, etc)
  * the available connections to the carriers (USB3, Thunderbolt, Ethernet, etc)
  * space available for a 2-3 week period
  * best times to complete the transfer
* Coordinate with LSC Collection Management about transport to and from the site.

## Equipment

* Check that you have the appropriate equipment for the transfer.
* Test that all equipment works before the site visit.

### Storage

* [ ] 8-16 TB USB External Hard Drive

Or

* [ ] 126TB RAID
* [ ] RAID power cord
* [ ] Thunderbolt 3 cord
* [ ] Thunderbolt 3 to Thunderbolt 2 adapter
* [ ] RAID Pelican case

### Laptop

* [ ] Laptop with Thunderbolt 2/3 ports and/or USB3-A/C ports
* [ ] Laptop power supply

### Potential Additional Supplies

* [ ] Pelican rollaway case
* [ ] USB A 10-receptacle hub
* [ ] USB hub power supply
* [ ] USB 3.1 A receptacle to USB-C plug adapter
* [ ] USB 3.1 B - USB 3.1 A cables
* [ ] USB 3.1 Micro B - USB 3.1 A cable
* [ ] Power strips
* [ ] USB3 write-blocker

## Transfer

* When you arrive, discuss the following with the site contact:
  * contact information and hours of site access
  * any documentation that might be useful for provenance
  * expectations for repeated on-site access (e.g. adding sets of hard drives)
  * whether any files have been updated in the past 30 days and will require additional quarantine
* Establish an expected completion date with LSC Collection Management and update as needed.

### Equipment Setup

Make sure all cables are run safely, such as around the back of a table.

* Find uninterrupted power source for extension cord.
* Connect the laptop, transfer storage, and and additional equipment to extension cord.
* Connect the transfer storage to the laptop.
* Connect any additional equipment to the laptop.
* Boot the laptop and check that all equipment works.
* Do not connect to network unless required for the transfer.

### Name the Transfers

At the time of a site visit no collection number will be assigned to the material.

* For the collection ID, use the name of the institution you are acquiring from or the personal name of the creator.  
  * The Foundry Theatre `foundryTheatre`
  * Lou Reed papers `louReed`
* Add additions to the transfer name when you are acquiring additions.
  * Bill T. Jones additions `billTJonesadditions`
* Create a text file for the collection in the root director of the transfer drive named `CollID.csv`.
* For each piece of source media, assign a sequential ID number `M0001`.
* In the text file, record the name or label of the drive and the ID number, separated by a comma.

### Preparing to Transfer from Hard Drives (if necessary)

Repeat this process until no additional ports are available.

* On the laptop, open the system disk manager or utility to check the status of drives.
* Connect the source drive to laptop or hub and turn on the power.
* Remount the source drive as read-only. Device numbers are available in the disk manager.

  ``` bash
  diskutil umount /dev/sda[]
  diskutil mount readOnly /dev/sda[]
  ```

* Make the transfer directories.

  ```bash
  mkdir -p /path/to/transfer/CollID/MediaID/{metadata,objects}
  ```

* Generate a file name and file size manifest of drive and save to the transfer drive

  ``` bash
  find /path/to/drive -type f -print0 | xargs -0r stat -f '%N, %z' | sort  > /path/to/transfer/CollID/MediaID/metadata/sourcedrive.csv
  ```

* In a text editor, create the command to transfer the source drive to its own folder on the transfer drive

  ``` bash
  rsync -rtP --exclude-from /path/to/transfer/exclude-list.txt --log-file=/path/to/transfer/CollID/MediaID/metadata/rsync_log.csv --log-file-format=", %f, %l, %C" /path/to/source /path/to/transfer/CollID/MediaID/objects/
  ```

### Preparing to Transfer from Network Locations (if necessary)

To be written{: .label .label-yellow }

### Starting Transfers

* Chain together the transfer commands with semi-colons to run them sequentially.
It is typically faster to copy from source drives sequentially, instead of simultaneously.

  ``` bash
  rsync -rtP ... ; rsync -rtP ... ; rsync -rtP ... ; ...
  ```

* Check transfer speed and determine when an additional visit will be necessary to add new drives or to complete the transfer.
For the number of expected days: `[total amount on drives in MB] / [transfer speed in MB] / 3600 / 24`

### Disconnecting Hard Drive Transfers

* Compare the size of the source drive to the folder on the transfer drive.

  ``` bash
  du -sh /path/to/source/
  du -sh /path/to/transfer/CollID/MediaID/objects/
  ```

* Generate a file name and file size manifest of folder on the transfer drive and save it to the transfer drive.

  ``` bash
  find /path/to/drive -type f -print0 | xargs -0r stat -f '%N, %z' | sort > /path/to/transfer/storage/CollID/MediaID/metadata/sourcedrive_transferred.csv
  ```

* Investigate any discrepancies between the manifests and retransfer if necessary.

  ``` bash
  comm -2 -3 /path/to/transfer/storage/CollID/MediaID/metadata/sourcedrive.csv /path/to/transfer/storage/CollID/MediaID/metadata/sourcedrive_transferred.csv
  ```

* Unmount the source drive.
* Disconnect completed drive from hub

### Equipment Tear Down

* Unmount the transfer drive and any additional equipment.
* Power down the transfer drive.
* Power down the laptop.
* Disconnect all power.
* Place equipment back into Pelican cases.
* Return to LSC with equipment using Library provided transportation.
