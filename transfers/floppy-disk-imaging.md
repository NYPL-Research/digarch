---
title: Floppy Disk Imaging
layout: default
nav_order: 5
parent: Transfers
---

# Floppy Disks 
This page describes instructions for imaging floppy disks using the KryoFlux microcontroller and software. For more detailed installation and use information see the [Kryoflux documentation](https://nypl.github.io/digarch/tools/kryoflux) in our Tools section.

### Before Imaging
* Before any media can be imaged **it first must have an object record in SPEC**.
* Verify a tracking card exists on Trello for the associated acquisition being imaged, create a card if it does not already exist.
* See our [Preparing for Transfer](https://nypl.github.io/digarch/transfers/preparing-for-transfer.html) page for detailed pre-imaging and transfer instructions.

### Connect the KryoFlux
* Ensure the floppy drive is correctly connected to the Kryoflux. 
* Attach the KryoFlux USB cable from the forensic workstation to the Kryoflux board.  
* See a green power light glow on the Kryoflux board.  
* Attach the AC power cable to the power supply. 
*  See the green LED on the power supply light up.  
*  Listen for a faint click from the disk drive.

 
### Calibrate the KryoFlux
* Open the KryoFlux software from the desktop "kryoflux-ui.jar".
* Click on the drive menu and ensure that ‘Drive 0’ is selected.
* Select ‘calibrate’ from the drive menu, then ‘yes’ from the pop-up window.  
* When the calibration is complete you should see the message  
  `calibration is successful, the maximum number of tracks available is: 83`
* Calibrate only once when you begin a session, unless calibration fails.  

### Resolve communication with the drive.
Follow these steps if the KryoFlux is unable to communicate with the drive.  
* Close the application.  
* Disconnect the power source from the drive.  
* Disconnect the USB cable from the KryoFlux board.  
* Reconnect the USB cable to the KryoFlux board.  
* Reconnect the power source to the drive.  
* Try connecting a different drive if there is still no communication after the the previous steps.  

### Imaging

* Insert the floppy disk into the drive.
* Enter the media object ID (for example, ACQ_11111_4444) in the "Enter name ..." text field in the Kryoflux imaging software.  
* Determine the filesystem format of the disk.
  * “MFM sector image” is usually the correct format for PC disks  
  * “Apple DOS 400/800k” is usually the correct format for Apple Macintosh disks.
  *  Test the disk if you're unsure about the format.  
  *  Select a format in the dropdown underneath the name field and select "start" to begin imaging the disk.  
  *  The sector grid displays color as the disk is imaged.  
  * Grey indicates the format is likely incorrect. Try another format.  
  * Green, orange, or yellow indicates the correct sector format has been determined.  
  * Red sectors indicate either the disk or the drive is damaged.

* Select “Multiple” from the drop-down below the "Enter name ..." text field when you have determined the correct sector format.  
* Select “KryoFlux stream image” and, while holding down the control key, select the correct sector format from the dropdown.  
* Select ‘ok’ to close the popup.  
* Click the start button to begin the imaging process. 

The KryoFlux will now create a folder with the name of the id of the media that contains the stream image files and a sector image (again with the name of the media plus an “.001” file extension). Both the stream directory and the sector image file will be written to the kryofluxOutput directory on Staging.  

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
* Enter floppy disk in the format_2 field.  
* Enter floppy disk size in the format_3 field.  (for example, 3.5 inch floppy)

| type | format_1 | format_2 | format_3 |  
| ------- | -------- |-------- | -------- |   
| item | digital carrier | floppy disk | 3.5 inch floppy |  

* Enter failed in the notes.transfer field if imaging fails.  

| notes.transfer |  
| -- |  
| failed |  

* Enter the filesystem format in the notes.transfer field if that format isn't recognized by FTK.  
* Amiga, ProDOS, CPM are formats not recognized in FTK.  

| notes.transfer |  
| -- |  
| Amiga |  

* Enter bad sectors in the notes.transfer field if a third or more of the sector blocks are red.  

| notes.transfer |  
| -- |  
| bad sectors |  

* Enter Y in the removed field if the disk is removed from the collection.  

| removed |  
| -- |  
| Y |  

### Package Images with package_images.py
The python script package_images.py identifies digital carrier images in an input directory and creates a archival information package and moves image files into the package. This section describes packaging with package_images.py for floppy and Iomega disks. For detailed information on installation and use see the [package_image.py]() listing in the Working Scripts section of our documentation.

* Open Terminal
* Enter the following command with the appropriate paths: ```python3 package_images.py –images path/to/images –stream path/to/streams –log path/to/logs –dest path/diskImages/folder –id (M#### or ACQ_####)```
* Navigate to destination directory, diskImages, on DigArchDiskStation to verify packages have been created and image files have been moved

### Completing the imaging process

* Return media to the collection’s box or move media to the "Small Collections Transferred" box if you are working on a small collection without a box.  
* Update object record migration status in SPEC. See [Updating records in SPEC](https://nypl.github.io/digarch/transfers/Completing-transfer.html#updating-records-in-spec) section on Completing a Transfer page for detailed instructions


{: .deprecated }
**The following sections describe floppy disk imaging processes no longer regularly used, including the use of department developed bash scripts for the movement and packaging of imaged files. Consult these sections when working with legacy collections requires understanding previously done work.**

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
```$ cd ACQ_acqID```  

* Run [makesips script](https://nypl.github.io/digarch/tools/working-scripts.html#makesips-sipdirsh){:target="_blank"} to create a consecutive number of submission information packages for material from digital media.

Or

* Change to diskImages directory.  

```$ cd /mnt/y/Staging/ingest/diskImages```  
  * Enter ```mkdir``` command.  
```mkdir -p ACQ_acqID/ACQ_acqID_specObjectID/{metadata,objects}``` 
#### Directory structure

* /ACQ_1234_123456
  * /metadata
    * 
  * /objects

### Package images
On Mac:

* Open Terminal.

* Navigate to DigArchDiskStation.

* Change to the kryofluxOutput directory.  
```$ cd /Volumes/DigArchDiskStation/Staging/ingest/kryofluxoutput```  
* Run the command to tar the stream files.  
```$ compress```  
* Run the program to move files from kryofluxOutput to the appropriate subdirectory in diskImages.  
```$ movekflux```  
* Move s0 and s1 images separately.  

On Windows via WSL:

* Open WSL.
* Navigate to DigArchDiskStation.
* Change to the kryofluxOutput directory.  
```$ cd /mnt/y/Staging/ingest/kryofluxoutput```  
* Run the command to tar the stream files.  
```$ compress```  
* Run the program to move files from kryofluxOutput to the appropriate subdirectory in diskImages.  
```$ movekflux```  
* Move s0 and s1 images separately.  
