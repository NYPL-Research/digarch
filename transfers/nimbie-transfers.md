---
title: Mass Optical Disc Transfers with Nimbie
layout: default
nav_order: 1
parent: Optical Media
---

# Mass Optical Disc File Transfers with the Nimbie Auto-Loader

This document describes how to use the [Nimbie Disc Auto-Loader]({% link tools/nimbie.md %}) to transfer files from optical media in archival collections to staging storage for processing and arrangement. For information on the Nimbie and the software this process depends on, see the Nimbie page. 

This applies for the vast majority of CD's, DVD's. and BluRays with born-digital contents.  

**Before a media object can be transferred it first must be recorded SPEC.**

Before beginning to work with the Nimbie, confirm that you have all of the collection's optical media by comparing discs to the media log in CMS.
Using the Nimbie Robot consists of three steps.
1. Loading discs into the robot
2. Monitoring the transfer process
3. Completing the transfer batch

## Loading discs into the Nimbie Robot

1.  Follow these steps to setup up the workstation:
	- Turn on the [Thinkpad W520](../thinkpad(W520)tools) laptop
	- On the Thinkpad, login to the mssa-admin account.
	- Plug-in the USB cable from the Nimbie USB disc robot to the Thinkpad.
	- Turn on the Nimbie using the power switch at the back of the device.
    - On the Thinkpad, launch IROMLAB. Double-click the “iromlab.ps1” icon on the Desktop.
    
2.  Create a file transfer batch. Click on “New Batch”. Select “Bags” for Batch Type and select your name for “Staff Name”. Enter the Collection ID (e.g. M1234). Click on select Save Batch Info.
    -  If your name is not in the staff name drop-down, contact Nick Krabbenhoeft to have it added.

3.  Add discs to the batch. For each disc, follow these steps. Enter the media number from the Media ID that is written on the interior of the disc. Click on “Add Disc”. Place the disc in the robot hopper. Click on “OK”.
    - The Media ID automatically increments by 1. If the discs are in numerical order, select “Add Disc”, and continue.
    - The robot can hold about 15-20 discs by default. To hold up to 100 discs, insert the plastic guides that are held to the lid into the three holes around the hopper.
    - For large collections, it's often easier to first load discs in large sequential batches, and then add queue them in the IROMLAB software. 
    - If a collection has more than 100 discs, wait for discs to process before adding more.
    - If a disc is physically damaged, set it aside for further inspection.

4.  Finalize the batch. Once the final discs have been loaded, select “Finalize Batch”.
    

## Monitor the Transfer Process
Completed discs are ejected into the plastic cylinder to the front of the robot. Rejected discs are ejected into a second cylinder underneath the robot. Rejected discs are evaluated after the batch is completed. See [Problem Discs](#problem-discs) for steps.

It is useful to check the process every 1-2 hours to ensure it is running correctly.

### Discs taking a long time
Most disc transfers take less than 10 minutes to complete. If the Nimbie has not loaded a new disc in a while, the most likely reason is that the disc being processed is scratched. Depending on the extent of the scratches, it may take up to 24 hours for the Nimbie to complete the disc. You can confirm this is happening if you hear the motor inside the Nimbie repeatedly spinning up and cutting power. This is normal.

### Red Light
If the red light on the front of the Nimbie is on, the auto-loading mechanism has probably jammed. Follow the instructions for [Stopping a Batch](#stopping-a-batch) below.

### Discs and Queue Out of Sync
Accidents and mistakes while loading the Nimbie will cause the transferred files to be linked with the wrong discs. If this is happening:
1. Record what disc transfers are affected.
2. Finalize the batch if you have not done so already.
3. Allow the transfer to continue.
4. Contact Nick Krabbenhoeft to come up with a plan to relabel the transfers.

### Non-halting errors
If the terminal window named "iromlab.ps1" shows error messages, it means that files were transferred from the disc, but there may be errors. Take note of these discs for examination after the batch completes.

### Stopping a Batch
You may need to stop the Nimbie because one of the above solutions did not work or you're encountering a new error. To stop the Nimbie:

1. Close IROMLAB. If you cannot close the IROMLAB window, close the terminal window named "iromlab.ps1".
2. Remove the discs from the hopper.
3. Remove the disc from the drive if one is currently in the drive. To open the drive, press the button on the bottom right of the disc drive inside of the Nimbie, remove the disc from the tray, and then press the button to close the tray again.

### Restarting a Batch
If you had to stop a batch, it is possible to reload the queue by using the "Load Batch" button in IROMLAB. In the file dialog box, navigate to the collection-level folder, highlight the batch folder, and select open.

## Completing a batch

After the final disc has been processed, follow these steps:
1. Close IROMLAB.
2. Rehouse the successfully transferred discs from the plastic cylinder in front of the Nimbie into their original sleeves or cases by matching their ID labels. If you recorded any error messages during transfer, add these to the unsuccessful transfer instead of rehousing them.
3. Examine the unsuccessful transfers. Remove the discs from the second cylinder under the Nimbie. Open the failManifest file in Z:\ingest\fileTransfers\[collectionNumber]\[collectionNumber-batchID].
   * If the failManifest reports that the disc is audio or video, set these discs aside to send them to the AMI inventory workflow.
   * If the failManifest reports that the disc is blank, examine the back to see if that is accurate. If there is a distinct circle separating a dark and light region of the disc, the disc must be read using a different computer. 
   * If the failManifest reports that the disc is software, set aside for further examination to determine if it contains collection material.
   * If the disc was set aside because of error reports in Powershell, examine the back of the disc for scratches or lint. If visible, use an alcohol pad to clean the disc.
4. After examining the unsuccessful transfers, move the discs to the appropriate workflow:
	* Deaccessioning - See [Deaccessioning]()
	* Transferring via a different method - See [Transfer process]()
	* Inventorying as AMI - Deliver back to the Archives Unit
	* Accepted as a successful transfer - rehouse and include with other media
5. Update the CMS Media Log. [Forthcoming]()
