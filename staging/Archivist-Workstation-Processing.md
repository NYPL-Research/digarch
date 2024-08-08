---
title: Archivist Workstation Processing Instructions
layout: default
nav_order: 7
has_children: false
parent: Processing
---

# Archivist Workstation Processing Instructions
{: .no_toc }
&nbsp;
{: .no_toc .text-delta }
1. TOC
{:toc}

Archivists processing electronic records without using FTK or ePADD will receive an external hard drive or thumb drive with copies of files to be arranged. In some cases files might
be available on remote storage.   

## Using an External Hard Drive

* Attach the external hard drive or thumb drive to your workstation.  
<!--*Will need to add new language around SPEC updates*-->
* Navigate to the SPEC object inventory of the acquisition to view digital carrier information.  
* You may need to update fields in SPEC object records at various points during processing.   

### Navigating the Drive

* Double-click the drive icon to display the drive folders in Windows Explorer.
* The folders will have the following structure:  
    * \M12345_workingfiles
        * \ACQ_12345_54321
            * \metadata
            * \objects  
                * \data (optional)    
        
* Note the metadata folder may contain metadata created during the transfer of the files.  
* Note a file directory listing of the files in .csv format, if present.
* Navigate to the objects folder to view the files to be arranged.  

OR

* Navigate to the data folder in the objects folder to view the files to be arranged.
<!--* Note manifest.txt files contain a directory listing. --> 

{: .important }
`data` folders are not collection folders. Move the contents within `data` folders only.  

## Surveying and Appraisal

The goal of the survey and appraisal phase is to approximate the process in which an archivist works with a physical collection. By using their workstation the archivist will be able to appraise a copy of records with the same structure as contained on their original media. 

* Appraise the files.  
* Ascertain the arrangement of the files.
* Note file naming conventions, how the files relate to each other, and  possible duplicates.  
  

## Arranging and Describing Files from a Workstation

The goal of the arrangement and description phase is to approximate the
process in which an archivist works with a physical collection. By using
their workstation the archivist will be able to appraise a copy of records with the same 
structure as contained on their original media, create a set of intellectual components
(arrangement), summarize the logical extents (size) and date ranges of
the components, and enter them into ArchivesSpace.

{: .warning }
Do not rename collection files.  
Avoid creating an ER for a single file. 

### Arrangement  

* Create a new folder on the drive you received at the same folder level as \M12345_workingfiles.  
* Use the naming convention ```CollectionID_FAcomponents``` to create a collection folder.  
* Name the folder \M12345_FAcomponents, for example.  
* Create a folder for each heading represented in the electronic records.  ```Correspondence```
* Create a folder for each FA Component using ```ER # Title, dates```.  
* Create an objects folder within each ER_# folder. ```ER 1 Files, 2012\objects```
* Move the files into the new FA Component objects folders as your process the files.  

### Finishing up
* Email [Digital Archives](mailto:digitalarchives@nypl.org) when you are finished processing.  
* Digital Archives will arrange to pick up the hard drive.  
* Digital Archives will email you a JSON file for import into ASpace.  
* Import the JSON file received from Digital Archives into ASpace.  
* Email [Digital Archives](mailto:digitalarchives@nypl.org) when your arrangement is approved.  

### Entering your collection in ArchivesSpace
After arrangement is complete Processing Archivists notify Digital Archives and deliver the external hard drive containing FA Components to Digital Archives for review.  Digital Archives staff then create a JSON file containing extents for import into ASpace. For detailed instruction on importing the extents JSON to ASpace review the [Importing FTK ERs in ArchiveSpace](https://docs.google.com/document/d/1BVMaDOzdcPFIht5yN5V16zmsnjMTwG_3e73HPTdVzSg/edit) guide.

* Note in some situations ERs may have to be manually created in ASpace instead of imported. Contact the Manager of Archival Metadata when deciding whether manual creation or JSON import is pertinent to your processing.
