---
title: File Transfers
layout: default
nav_order: 2
parent: Transfers
---

# File Transfers
{: .no_toc }

This page describes instructions for acquiring born digital material via file transfer and packaging file transfers for processing. The file transfer workflow described on this page primarily applies to internal and external hard drives, thumb drives and sd cards.

### Before Transfer
{: .important }
Before any media can be transferred **it first must have an object record in SPEC**.
* Verify a tracking card exists on Trello for the associated acquisition being transferred 
    * Create a card if it does not already exist 
* See our [Preparing for Transfer](https://nypl.github.io/digarch/transfers/preparing-for-transfer.html) page for detailed pre-imaging and transfer instructions.

### Transfer files in office with transfer_rsync.py

{: .important}
Files that have been updated by the donor within the past 30 days should be quarantined for 30 days to ensure that all virus definitions are up to date.

Files are transferred from digital carriers in office using the [transfer_rsync script](https://nypl.github.io/digarch/tools/working-scripts.html#transfer_rsyncpy){:target="_blank"}. This script uses [rsync](https://nypl.github.io/digarch/tools/programs.html#rclone){:target="_blank"}, a command utility used for copying and syncing file locations, to initiate file transfer then packages the files in our digital archives package structure.

* Use a write-blocker to connect the drive to the computer. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.

* Open terminal on Mac or WSL on Windows

* Run transfer_rsync.py by entering the following command with the appropriate paths: ```python3 transfer_rsync.py –-carrierid (M#### or ACQ_####_######) -–payload path/to/files/directory -–dest path/to/destination/directory```

  * You may also add the optional ```--quiet``` flag to suppress rsync progress bar information.

### Package pre-transferred files with package_filetransfer.py
In some situations, files may be transferred but still require packaging in our digital archives package structure; such as with on site transfers. Digital Archives uses [package_filetransfer.py](https://nypl.github.io/digarch/tools/working-scripts.html#package_filetransferpy){:target="_blank"} to repackage already completed file transfers.

* Use a write-blocker to connect the drive to the computer. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.

* Open terminal on Mac or WSL on Windows

* Run package_filetransfer.py by entering the following command with the appropriate paths:
```python3 package_filetransfer.py –-carrierid (M#### or ACQ_####_######) -–payload path/to/files/directory --log path/to/rsync/transfer/log -–dest path/to/destination/directory```
