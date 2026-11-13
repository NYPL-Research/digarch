---
title: Memory Card File Transfers
layout: default
nav_order: 6.5
parent: Transfers
---
# Memory Card File Transfers  
{: .no_toc }
Memory Cards are small digital carriers used in devices from cameras to game consoles.  
NYPL usually receives Memory Cards that contain digital photographs.  

## Before Transfer  
Before any media can be transferred it first must have an object record in SPEC.  
* Verify a tracking card exists on Trello for the associated acquisition being transferred  
    * Create a card if it does not already exist  
* See our [Preparing for Transfer](https://nypl.github.io/digarch/transfers/preparing-for-transfer.html) page for detailed pre-imaging and transfer instructions.  

## Bulk Transfer  
This document outlines the procedure for transferring multiple memory cards at a time using a usb hub.  

### Device connection  

{: .important }
Only use this procedure in cases where you can risk mounting the devices as writable. 

This procedure uses software write protection rather than physical writeblockers. Memory cards may have read/write tabs that can be moved to read-only. Use caution if attempting to move a tab as older plastic media can break easily.

The software used for write protection in this procedure hasn’t been updated recently and can freeze without notice. When the software freezes media might be mounted read/write.

Linux devices might be more reliable when you want to prevent mounting.

#### Disk Arbitrator  
* Open Disk Arbitrator  
* Select Activated check box so it is checked  
* Select Read-only from Mode dropdown  
* Attached devices should appear as read-only in Disk Arbitrator and Disk Utility  

#### Memory Card Reader  
* Connect each Memory Card to a USB Memory Card Reader  

#### USB Hub  
* Connect a USB hub to the computer you are using for transfer  
* Connect each Memory Card Reader with a Memory Card to the USB hub  
* Connect Memory Cards in SPEC ID order or keep a list of SPEC IDs as devices appear  
* Disconnect unreadable cards and try connecting on a different Operating System  

{: .important }
If devices appear writable, unmount and repeat Disk Arbitrator steps.  

### Transfer  
* Open a terminal tab for each Memory Card connected to the USB hub  
* Use the following Rsync commands to transfer files from the Memory Cards  
```rsync -arPF --log-file=/[metadatapath]/rsync_log.csv --log-file-format=", %f, %l, %C" --exclude ".*" --exclude ".*." /path/to/source/drive /path/to/destination```  
* ```/path/to/source/drive``` should be the device as it appears in ```/Volumes```  
* ```/path/to/destination``` should be the SPEC ID objects folder  
