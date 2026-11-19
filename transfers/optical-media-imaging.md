---
title: Optical Media Imaging
layout: default
nav_order: 3
parent: Optical Media
---

## Optical Media - CD-R/DVD-R

**Before a media object can be imaged it first must be recorded in SPEC.**

### Using Digital Archives scripts
Make sure the setup instructions for Digital Archives [scripts](https://github.com/NYPL/digarch_scripts){:target="_blank"} have been completed before running the scripts in the next section.  

### Create destination directories

**These instructions show you how to create destination directories for a number of consecutive disks. Consider using a one-line command to create directories if the disks you are packaging do not have consecutive MediaID numbers.**  

On Mac:

* Open Terminal.

* Navigate to DigArchDiskStation.  

* Change into diskImages directory.  
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/diskImages```

* Create a directory for the acquisition if it does not exist.  
```$ mkdir ACQ_acqID```  

* Change into the acquisition directory.  
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
```$ cdA ACQ_acqID```  

* Run [makesips script](https://nypl.github.io/digarch/tools/working-scripts.html#makesips-sipdirsh){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to diskImages directory.  

```$ cd /mnt/y/Staging/ingest/diskImages```  
  * Enter ```mkdir``` command.  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID/{metadata,objects}``` 

#### Directory structure

* /ACQ_1234_123456
  * /metadata
  * /objects

### Image discs

* Place the optical media in the optical drive.
* Open a terminal window.
* Use the dd command to copy optical media in the drive to iso. ```if``` is the input file and ```of``` is the output file.  

On Mac:

```$ dd if=/dev/sr0 of=/Volumes/DigArchDiskStation/Staging/ingest/diskImages/ACQ_acqID/ACQ_acqID_specObjectID/objects/ACQ_acqID_specObjectID.iso```  

On Windows via WSL:

```$ dd if=/dev/sr0 of=/mnt/y/Staging/ingest/diskImages/ACQ_acqID/ACQ_acqID_specObjectID/objects/ACQ_acqID_specObjectID.iso```

* Once complete the terminal will display bytes copied and return to a blank prompt.
* Eject the disc from the drive.

### Metadata
Deprecated
{: .label .label-red }
* Open Cygwin and enter the following commands:
* Connect to ARCHV Mac.  
```$ ssh archv```  
* Change to the diskImages directory and change directory to the objects folder for the media object.  
```$ diskimages```  
```$cd ACQ_acqID/ACQ_acqID_specObjectID/objects```  
* Run disktype on the disk image to get the file system metadata.  
```$ disktype ACQ_acqID_specObjectID.iso```  
* Copy the file system information data from the output into the media objects CMS record.
* Get the size of the disk image using the du command if disktype outputs mb.  
```$ du -ck ACQ_acqID_specObjectID.iso```  
* Run the program to move metadata files to metadata directory.  
```$ movemetadata``` 

## Optical Media (CD-R, DVD-R) Export

Additionally, a single file system can be extracted from optical media for ease of processing in FTK. The multiple file systems usually available on optical media are redundant in this software.

* Select “Add Evidence Item” from File drop down menu. Select “Logical Image” and highlight F:\ or the source path of the CD drive if using a different drive letter. 
* FTK Imager will display the drive (F:), the session (1), the track (01) and 1-4 file systems (ISO, Joliet, UDF, HFS). (You may also see unpartitioned space and a partition for the CD builder/Disc Recorder but stick to the file systems 1-4 for now.)
* Click the + sign to the left of the F:\ if this information tree is not displayed. 
* Choose file system for export. Click on a folder or name to select it. In the example above the UDF file system has been selected.  
* Select Export Files… under the File menu to extract files from the highlighted file system.

Or

* Right-click on the file system and select Export Files.
* Create a folder in the Evidence directory if you have not already done so and save the extracted files to this location. Follow the path name convention  ```Z:\FTK\Evidence\ACQ_acqID\ACQ_acqID_specObjectID```
```(EX: Z:\FTK\Evidence\ACQ_1234\ACQ_1234_123456 ```

**Navigate to the folder using Windows Explorer, create the folder there, then click on the folder in the navigation bar to copy the path. Paste this path into FTK Imager Save as.**

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
* Enter optical disk in the format_2 field.  
* Enter optical disk type in the format_3 field.  (for example, CD-R)

| type | format_1 | format_2 | format_3 |  
| ------- | -------- |-------- | -------- |   
| item | digital carrier | optical disk | CD-R |  

* Enter failed in the notes.transfer field if imaging fails.  

| notes.transfer |  
| -- |  
| failed |  

* Enter the filesystem format in the notes.transfer field if that format isn't recognized by FTK.  
* Amiga, ProDOS, CPM are formats not recognized in FTK. (Unrecognized less likely for optical)  

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
