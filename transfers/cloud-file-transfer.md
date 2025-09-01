---
title: Cloud File Transfers
layout: default
nav_order: 8
parent: Transfers
---

# Cloud File Transfers
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Introduction
Born-digital collection material can be acquired through file transfer from cloud based storage locations. This page describes Digital Archives workflow for preparing for a cloud based file transfer, creating a destination package using package_cloud.py and transferring material using rclone. The instructions detailed on this page are specific to transfers from google drive, but are adaptable to other cloud storage contexts.  

# Before File Transfer
Before beginning a file transfer confirmation with Donors and Collections Management about what material is being acquired is essential. Transfer from cloud storage will often require the sharing of permissions or access to the storage location for the duration of the transfer, this should be communicated with the Donor. Digital Archives does not acquire or retain system files, hidden files, deleted files or files containing personally identifiable information. See our [Acquiring Born Digital Material](/sitevisits/acquiring-born-digital.html) page for more information.

* Acquire link to cloud storage location from donor. Have google drive location shared with Digital Archives staff by donor.

# Workstation Preparation 
Born-digital material held in cloud storage is first transferred with rclone to a temporary working folder on a Digital Archives Lab workstation or a RAID connected to a Digital Archives Lab workstation.

* Connect RAID to Lab Workstation or Login to Lab Workstation
* Open Terminal 
* Create temporary working folder on RAID or on Lab Workstation by entering ```mkdir path/to/working/folder```
    * Note: Folder should be named following file transfer naming convention, ```ACQ_four-digit-acquisition-id_six-digit-spec-id```. Acquisiton, Collection and SPEC ID information can be found in the associated SPEC records.
* Navigate into temporary work folder by entering ```cd path/to/working/folder```


# File transfer with Rclone
Rclone is a command line program for managing files on cloud storage. Using rclone for filetransfers requires configuring storage locations as saved remote locations. For detailed rclone installation and configuration instructions visit the dedicated [rclone](https://nypl.github.io/digarch/tools/rclone.html) page.

* Confirm working folder created in the Workstation Preparation section is the current working directory in terminal.

* Confirm you have access to the intended folder
```rclone ls remote:path/to/source```
    * For Google Shared Folders, try ```remote: --drive-root-folder-id ###``` where ### is the string at the end of the Google Drive Folder URL.
For example, `1yOaxTcgPl5zNwYQP2_k7SOW59l4DgXgd` from `https://drive.google.com/drive/folders/1yOaxTcgPl5zNwYQP2_k7SOW59l4DgXgd`

* Transfer md5 checksum manifest for materials by entering
```rclone md5sum --exclude ".*" -P remote:path/to/source --output-file rclone-md5.txt```
    * `--exclude ".*"` excludes any files with a name beginning with ".", this is to exclude hidden system files
    * `-P` visually tracks progress
    * `--output-file rclone-md5.txt` saves checksums to a text file.

* Transfer the materials payload by entering
```rclone copyto --exclude ".*" -P --log-level INFO --log-file=path/to/working/folder/rclone.log remote:path/to/source payload```
    * `--log-level INFO --log-file=rclone.log` saves the logs to defined file path
    * `payload` is a directory that will be created by `rclone` to hold the files

# Create Cloud File Transfer Package with package_cloud.py
After born-digital material, transfer log, and checksum manifest have been transferred to a temporary working folder, Digital Archives Staff repackage the files to meet file transfer specifications using package_cloud.py. Digital Archives specifications for file transfers described below:

```
/ACQ_four-digit-acquisition-id
└── /ACQ_four-digit-acquisition-id_six-digit-spec-id
    ├── metadata
    └── objects

/ACQ_1234
└── /ACQ_1234_123456
    ├── metadata
    └── objects
```

The package_cloud.py script requires five inputs for repackaging:
* ```--payload```: The path to the payload folder created in the working directory, contains the actual born_digital material.
* ```md5```: The path to the rclone md5 text file generated during transfer.
* ```log```: The path to the rclone log generated during transfer.
* ```dest```: The path to the destination directory for package
* ```id```: The media id for the transferred material.

An example run of package_cloud.py:
```python3 package_cloud.py --payload /path/to/working/payload --log /path/to/working/rclone.log --md5 /path/to/working/rclone-md5.txt --dest /DigArchDiskStation/Staging/ingest/filetransfers --id ACQ_0000_000111```
