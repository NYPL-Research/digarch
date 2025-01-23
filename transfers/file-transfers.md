---
title: File Transfers
layout: default
nav_order: 2
parent: Transfers
---

# File Transfers
{: .no_toc }

<!--## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}-->

<!--# Introduction

Born digital collection material can be acquired through file transfer or forensic imaging. Most material will be transferred using a Bagit script through command line.

The file transfer workflows are detailed in this document. The workflows may vary based on media types and file types-->

This page describes instructions for acquiring born digital material via file transfer and packaging file transfers for processing. The file transfer workflow described on this page primarily applies to internal and external hard drives, thumb drives and sd cards.

### Before Imaging
{: .important }
Before any media can be transferred **it first must have an object record in SPEC**.
* Verify a tracking card exists on Trello for the associated acquisition being imaged  
    * Create a card if it does not already exist 
* See our [Preparing for Transfer](https://nypl.github.io/digarch/transfers/preparing-for-transfer.html) page for detailed pre-imaging and transfer instructions.

<!--**Before a media object can be transferred it first must be recorded SPEC.**-->

<!--## Prepare destination folders for files

**These instructions show you how to prepare destination folders for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive ID numbers or you are only transferring one media object.**  

<!--Windows instructions should go here-->

<!--May actually need to move the descriptive information on cygwin and wsl up here cause this can be done via terminal-->
<!--On Windows via WSL:

Working with WSL 

* Start WSL (Windows Subsystem for Linux) by searching for Ubuntu or selecting the Ubuntu icon on the Windows task bar.

Note: If you search for WSL you may come across the WSL app with a penguin icon, this is an older version of WSL and NOT the version currently used by Digital Archives

* On opening the WSL terminal navigate to the mount point directory by entering ```cd /mnt```

* Any mounted drives, such as those you are transferring between, should be accessible from the mount point directory. Drives you'll see in /mnt include:
  * d - Sata Drive Bay
  * f - Storage for FTK
  * h - Open FTK cases
  * i - Codemeter access key
  * y - DigArchDiskStation

* If you do not see the Y:\ drive in /mnt or /mnt/y appears to be empty then it must be re-mounted by:
  * Changing to the top level directory by entering ```cd /```
  * Entering the command ```sudo mount -t drvfs Y: /mnt/y```

* Note: For a visual example of mounting a drive in WSL reference the following recording:
<script async id="asciicast-bqEfvxCtzxiPXjfr2S8zEimov" src="https://asciinema.org/a/bqEfvxCtzxiPXjfr2S8zEimov.js" data-speed="3.5" data-theme="dracula"></script>

* Note: For a visual example of mounting a drive in WSL reference the following recording:
<script async id="asciicast-bqEfvxCtzxiPXjfr2S8zEimov" src="https://asciinema.org/a/bqEfvxCtzxiPXjfr2S8zEimov.js" data-speed="3.5" data-theme="dracula"></script>

* Change to fileTransfers directory by entering ```cd /mnt/y/Staging/ingest/fileTransfers```

* Run [makesips script](https://nypl.github.io/digarch/tools/working-scripts.html#makesips-sipdirsh){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

or

* Use ``mkdir`` command to create directories when media aren't consecutively numbered:

  * Enter ```mkdir``` command.  

```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID/{metadata,objects}``` 

* Note: For a visual example of using mkdir to make multiple directories reference the following recording: 
<script async id="asciicast-Qa9HoimUXpvyGDYzxe63QOXhf" src="https://asciinema.org/a/Qa9HoimUXpvyGDYzxe63QOXhf.js" data-speed="3.5" data-theme="dracula"></script>


On Mac:

* Open Terminal.

* Navigate to DigArchDiskStation  

* Change into fileTransfers directory.  
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/fileTransfers```

* Create a directory for the acquisition if it does not exist.  
```$ mkdir ACQ_acqID```  

* Change into the acquisition directory.  
```$ cd ACQ_acqID```  

* Run [makesips script](https://nypl.github.io/digarch/tools/working-scripts.html#makesips-sipdirsh){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to fileTransfers directory.
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/fileTransfers```
  * Enter ```mkdir``` command.  

```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID/{metadata,objects}```

### Directory structure

* /ACQ_1234_123456
  * /metadata
  * /objects-->

### Transfer files in office with transfer_rsync.py

{: .important}
Files that have been updated by the donor within the past 30 days should be quarantined for 30 days to ensure that all virus definitions are up to date.

Files are transferred from digital carriers in office using the [transfer_rsync script](https://nypl.github.io/digarch/tools/working-scripts.html#transfer_rsyncpy){:target="_blank"}. This script uses rsync, a command utility used for copying and syncing file locations, to initiate file transfer then packages the files in our digital archives package structure. 

More information about rsync can be found on the [rsync documentation page](https://linux.die.net/man/1/rsync) and [installation instructions](../software#rsync) can be found in our software section. More information about [transfer_rsync.py](https://nypl.github.io/digarch/tools/working-scripts.html#transfer_rsyncpy){:target="_blank"} can be found in the [working scripts](https://nypl.github.io/digarch/tools/working-scripts){:target="_blank"} section of our documentation.

* Use a write-blocker to connect the drive to the computer. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.

* Open terminal on Mac or WSL on Windows

* Run transfer_rsync.py by entering the following command with the appropriate paths: ```python3 transfer_rsync.py –-carrierid (M#### or ACQ_####_######) -–payload path/to/files/directory -–dest path/to/destination/directory```

  * You may also add the optional ```--quiet``` flag to suppress rsync progress bar information.

### Package pre-transferred files with package_rsync.py
In some situations, files may be transferred but still require packaging in our digital archives package structure; such as with on site transfers. Digital Archives uses [package_rsync.py](https://nypl.github.io/digarch/tools/working-scripts.html#package_filetransferpy){:target="_blank"} to repackage already completed file transfers.

* Use a write-blocker to connect the drive to the computer. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.

* Open terminal on Mac or WSL on Windows

* Run package_filetransfer.py by entering the following command with the appropriate paths: ```python3 package_filetransfer.py –-carrierid (M#### or ACQ_####_######) -–payload path/to/files/directory -–dest path/to/destination/directory```

<!--### Rsync

Rsync is a command utility used for copying and syncing file locations, both locally and remotely. More information about rsync can be found on the [rsync documentation page](https://linux.die.net/man/1/rsync) and [installation instructions](../software#rsync) can be found in our software section.

On Windows via WSL:

* Open WSL terminal

Note: rsync will require a source path (the path to the disk of associated media carrier) and destination path (path to the fileTransfers directory in DigArchDiskStation ). Both paths should meet requirements for the terminal being used.

* Enter ```rsync -arP sourcepath destinationpath```

* An example rsync command may look like: ```rsync -arP /mnt/g/ /mnt/y/Staging/ingest/fileTransfers/acquisition-folder/carrier-folder/objects```


On Mac:

* Open Terminal.

* Enter ```rsync -arP sourcepath destinationpath```

* An example rsync command may look like: ```rsync -arP /Volumes/path/to/media/carrier /Volumes/DigArchDiskStation/Staging/ingest/fileTransfers/acquisition-folder/media-folder/objects```-->

<!--{: .deprecated}
The following sections describe processes no longer regularly used. Consult these sections when working with legacy collections requires understanding previously done work.

### FT.sh

Deprecated
{: .label .label-red }
On Mac:

* Open Terminal.
* Enter the alias ```FT``` and hit return.

Or

* Enter ```/usr/local/bin/ft.sh``` and hit return if the alias is not set.
* Drag the destination directory from the media object to the window and hit return as prompted.
* Enter the MediaID for the file transfer and hit return.

* Copy the number of files in payload and the size of payload in kb when displayed in the window.
* Paste the number of files and the size in the File Transfers section of the media log in CMS.
  
<script id="asciicast-mKpfPqUl74R3t30B0tvpfPBQV" src="https://asciinema.org/a/mKpfPqUl74R3t30B0tvpfPBQV.js?" async></script>-->
