---
title: Iomega Disk Imaging
layout: default
nav_order: 6
parent: Transfers
---

## Iomega Disks
This page covers Iomega disk imaging with the FTK Imager software. Iomega disks are usually imaged with FTK Imager. Use FTK Imager when creating a disk image of a hard drive or removable media.

### Before Imaging
* Before any media can be imaged **it first must have an object record in SPEC**.  on verifying record creation in SPEC.
* Verify a tracking card exists on Trello for the associated acquisition being imaged, create a card if it does not already exist
* See our [Preparing for Transfer](https://nypl.github.io/digarch/transfers/preparing-for-transfer.html) page for detailed pre-imaging and transfer instructions.

### Using Digital Archives scripts
Make sure the setup instructions for Digital Archives [scripts](https://github.com/NYPL/digarch_scripts){:target="_blank"} have been completed before running the scripts in the next section.  

### Create destination directories

**These instructions show you how to create destination directories for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers.**  

On Mac:

* Open Terminal.

* Navigate to DigArchDiskStation.  

* Change into diskImages directory.  
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/diskImages```

* Create a directory for your collection if it does not exist.  
```$ mkdir ACQ_acqID```  

* Change into your collection directory.  
```$ cd ACQ_acqID```  

* Run [makesips script](https://nypl.github.io/digarch/tools/working-scripts.html#makesips-sipdirsh){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to diskImages directory.  

```$ cd /Volumes/DigArchDiskStation/Staging/ingest/diskImages```  
  * Enter ```mkdir``` command.  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID/{metadata,objects}``` 

On Windows via WSL:

* Open WSL.
* If you do not see the Y:\ drive in /mnt or /mnt/y appears to be empty then it must be re-mounted by:
  * Changing to the top level directory by entering ```cd ../```
  * Entering the command ```sudo mount drvfs Y: /mnt/y```
* Change into diskImages directory.  
```$ cd /mnt/y/Staging/ingest/diskImages```

* Create a directory for the acquisition if it does not exist.  
```$ mkdir ACQ_acqID```  

* Change into the acquisition directory.  
```$ cd ACQ_acqID```  

* Run [makesips script](https://nypl.github.io/digarch/tools/working-scripts.html#makesips-sipdirsh){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to diskImages directory.  

```$ cd /mnt/y/Staging/ingest/diskImages```  
  * Enter ```mkdir``` command.  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID/{metadata,objects}```

#### Directory structure

* /M2319-0021
  * /metadata
    * 
  * /objects


<!-- ![](media/media/image29.png){width="6.069444444444445in"
height="2.3472222222222223in"} -->

### Image disks

* Connect the Iomega drive to the FRED's Tableau Ultrabay. See [Using Tableau Write Blockers](/digarch/transfers/using-tableaus.html){:target="_blank"} for instructions.  

* Start FTK Imager from the FRED's launch bar and select
Create New Image from the application's file menu.

<!-- ![](media/media/image9.png){width="0.7395833333333334in"
height="0.5104166666666666in"} -->

* Select Physical Image and click next.

<!-- ![](media/media/image21.png){width="5.0in"
height="3.6666666666666665in"} -->

* Select the drive to be imaged from the drop down menu and
click finish.

<!-- ![](media/media/image23.png){width="4.946247812773404in"
height="3.5879155730533685in"} -->

* Select E01 form the image type menu and click next.

<!-- ![](media/media/image20.png){width="5.008970909886264in"
height="3.433333333333333in"} -->

* Type the acquisition ID in the Case number field, the
media ID in the Evidence number field, and your name in the
Examiner field. Click next.

<!-- ![](media/media/image12.png){width="5.130208880139983in"
height="3.5120352143482063in"} -->

* Using the browse button, select the objects folder in the
correct acquisition directory (e.g.
Staging/ingest/diskImages/ACQ_1234/ACQ_1234_123456/objects). Enter the SPEC Object ID
into the Image Filename field. Ensure that the image fragment
size is set to 0 and the compression field is set to 9. Click finish.

<!-- ![](media/media/image14.png){width="5.094400699912511in"
height="3.493303805774278in"} -->

* Ensure all check boxes are checked and click Start to
begin the imaging process.

<!-- ![](media/media/image16.png){width="5.590798337707787in"
height="4.778125546806649in"} -->

**FTK Imager will approximate the time needed to image the media.**

<!-- ![](media/media/image8.png){width="5.989583333333333in"
height="3.84375in"} -->

* Make sure that the checksums match on the complete screen, if not imaging was not successful.

<!-- ![](media/media/image19.png){width="4.950121391076116in"
height="4.55in"} -->

### Tracking
* Navigate to the [Tracking](https://drive.google.com/drive/folders/1tv4nr9Nq_c8wkqPpz_eQX7NKRRrlEisp?usp=share_link){:target="_blank"} folder in Google Drive.  
* Find the spreadsheet for the acquisition that you will be working with.  
* Copy [Tracking_TEMPLATE](https://docs.google.com/spreadsheets/d/1TwWMsrCf2hf5LzdtA6EG-2wcgFW_Uz750x-PZtFop90/edit?usp=sharing) to create a spreadsheet if one doesn't exist.  
* Name the spreadsheet the acquisition ID of the acquisition that you will be working with.  
* Check the media ID for the disk you are working with (for example, ACQ_1234_123456).  
* Media IDs follow the naming convention ACQ_acqID_specObjectID.  
* Enter acqID in the ref_acq_id field.  
* Enter specObjectID in the object_id field.  

| ref_acq_id | object_id |  
| -- | -- |  
| 1234 | 123456 |  

* Enter item in the type field.  
* Enter digital carrier in the format_1 field.  
* Enter Zip disk in the format_2 field.  
* Enter Zip disk size in the format_3 field.  (for example, 100 MB)

| type | format_1 | format_2 | format_3 |  
| ------- | -------- |-------- | -------- |   
| item | digital carrier | Zip disk | 100 MB |  

* Enter failed in the notes.transfer field if imaging fails.  

| notes.transfer |  
| -- |  
| failed |  

* Enter the filesystem format in the notes.transfer field if that format isn't recognized by FTK.  
* Amiga, ProDOS, CPM are formats not recognized in FTK. (Unrecognized formats less likely for Zip)  

| notes.transfer |  
| -- |  
| Amiga |  

* Enter a note in the notes.transfer field if there were problems with the transfer.  

| notes.transfer |  
| -- |  
| Imaging repeatedly stopped at 75%. |  

* Enter Y in the removed field if the disk is removed from the collection.  

| removed |  
| -- |  
| Y | 

### Completing the imaging process

* Put the media back in the collection’s box and move or remove the pink “To image” flag as necessary if you are working on a large collection.  
* Move the media to the “Small collections complete” box if you are working on a small collection without a box.  

### Metadata
Deprecated
{: .label .label-red }
* Open Cygwin and enter the following commands:
* Connect to ARCHV Mac.  
```$ ssh archv```
* Change to the diskImages directory and change directory to the objects folder for the media object.  
`$ diskimages`  
`$cd ACQ_acqID/ACQ_acqID_specObjectID/objects`
* Run disktype on the disk image to get the file system metadata.  
`$ disktype ACQ_acqID_specObjectID.E01`
* Copy the file system information data into the media objects CMS record.
* Run program to move metadata files to metadata directory.  
`$ movemetadata`
