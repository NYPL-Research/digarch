---
title: Hard Drive Extents Export
layout: default
nav_order: 9
has_children: false
parent: Post-processing
---
# Exporting Extents from a Hard Drive

{: .no_toc }
&nbsp;
{: .no_toc .text*delta }

When Processing Archivists have completed processing a collection at the their workstations and have returned a hard drive with completed finding aid components to Digital Archives, Digital Archives staff prepare extents for import to ArchivesSpace using the report_hdd_extents script. This page describes instructions for preparing and exporting extents JSON files from a hard drive. See the [report_hdd_extents section of our Software documentation page](https://nypl.github.io/digarch/tools/software.html#report-hdd-extents-script) for installation instructions.

## Review Finding Aid Components

* Attach the hard drive containing finding aid components
* Check that the FAC directory uses the naming convention ```CollectionID_FAcomponents```
  * ```M18867_FAcomponents```, for example
* Review the finding aid components returned by Processing Archivist(s) for system files or other formats not retained by Digital Archives.

## Run report_hdd_extents.py

{: .note }
These instruction assume you are using FRED 2.  
On computers with Google Drive you can store JSON files using the shared drive location  
```Digital Preservation/Stream - Digital Archives/Digital Archives Program/ASpace JSON```  

### Prepare a destination directory
  * Navigate to the FTKsettings directory in the Storage (F:) drive on FRED 2.
  * Open the ```ASpace``` directory
  * Create a report destination directory using the naming convention ```CollectionIDreport```.  
    * For example, the Morris Dickstein Collection directory would be ```M18867report```

### Extract extents using report_hdd_extents.py
  * Open WSL on FRED 2
  * Note the location of the FAcompnents directory.  
    * This location will be used after the -d flag in the command.  
  * Note the location of the destination directory previously created.  
    * This location will be used after the -o flag in the command.  
  * Run [report_hdd_extents.py](https://nypl.github.io/digarch/tools/software.html#report-hdd-extents-script) script using the following command:  
```python3 path/to/report_hdd_extents.py -d /path/to/CollectionID_FAcomponents -o /path/to/CollectionIDreport```
  * For example:  
```python3 digarch_scripts/report/report_hdd_extents.py -d /Volumes/DigArch11/M18867_FAcomponents -o /M18867report```  

## Deliver extents JSON to Archival Processing Unit

Digital archives staff should deliver the extents JSON file to the Processing Archvist(s) for the associated collection. 