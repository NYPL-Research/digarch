---
title: Archivist Workstation Processing Instructions
layout: default
nav_order: 3
has_children: true
parent: Processing
---

# Archivist Workstation Processing Instructions

<iframe src="https://docs.google.com/presentation/d/1vn8s-UogFv4HMn4iifnEtRKGt8WYHwRI4Za1R2YVQI4/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

{: .no_toc }
&nbsp;
{: .no_toc .text-delta }
1. TOC
{:toc}

## Processing Electronic Records with Your Workstation Video Training

<div class="embed-container">
  <iframe
      src="https://www.youtube.com/embed/ytF8UsE3rJA"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="true">
  </iframe>
</div>

Archivists processing electronic records without using FTK or ePADD will receive an external hard drive or thumb drive with copies of files to be arranged. In some cases files might
be available on remote storage.   

## Using an External Hard Drive

* Attach the external hard drive or thumb drive to your workstation.  
<!--*Will need to add new language around SPEC updates*-->
* Navigate to the SPEC object inventory of the acquisition to view digital carrier information.  
* You may need to update fields in SPEC object records at various points during processing.   

### Navigating the Drive

* Select the drive icon to display the drive folders in Windows Explorer.
* The folders will have the following structure:  
  * 📁 ```M12345_workingfiles```  
      * 📁 ```ACQ_12345_54321```  
          * 📁 ```metadata```  
          * 📁 ```objects```  
              * 📁 ```data``` (optional)    
     
* Note the metadata folder may contain metadata created during the transfer of the files.  
* Note a file directory listing of the files in .csv format, if present.
* Navigate to the objects folder to view the files to be arranged.  

OR

* Navigate to the data folder in the objects folder to view the files to be arranged.  
<!--* Note manifest.txt files contain a directory listing. --> 

Go to [Navigating the Drive](navigating-the-drive) for more examples of folder structures.  

{: .important }
`data` folders are not collection folders. Move the contents within `data` folders only.  

## Surveying and Appraising

Using your workstation you will be able to survey and appraise a copy of  
the records with the same structure as contained on the original media.  
Surveying digital material relies on the same guidelines as other collection material.  
"The goal of the survey is to attain a more comprehensive understanding of the  
collection's scope, content, and purpose." [^1]

[^1]: New York Public Library. 2024. “Archival Processing Manual.” New York Public Library. [https://nypl.github.io/pres-docs/archivalProcessing/Survey.html#survey](https://nypl.github.io/pres-docs/archivalProcessing/Survey.html#survey).

Appraising digital material relies on the same guidelines as other collection material.  
“In archives, appraisal is the process of determining whether collection material has  
archival value and should be retained, preserved, and described.” [^2]

[^2]: New York Public Library. 2024. “Archival Processing Manual.” New York Public Library. [https://nypl.github.io/pres-docs/archivalProcessing/Appraisal.html#appraisal](https://nypl.github.io/pres-docs/archivalProcessing/Appraisal.html#appraisal)

Digital material that will be retained is [arranged](#arranging-and-describing-files-from-a-workstation).  

### Surveying
* Survey files as you would any other format.    
* Ascertain the arrangement of the files.
* Note file naming conventions, how the files relate to each other, and possible duplicates.  
  
When surveying digital material the content of some files might not be immediately
obvious when viewed. The following strategies can help identify files or provide a best
guess.  

#### Identifying Contents by Folder
* Compare unidentified content to other content in the folder  
* Check the folder's descriptive information for information on the files it contains  

#### Identifying Contents by Filename
* Use any descriptive information from the filename when file content is not apparent  

#### Identifying Contents by Modified Date
* Use the modified dates to compare the files to files from similar dates  
* Describe files by dates if that is the most information you can obtain  

#### Dealing with Unreadable Files
* Appraise unreadable files by identifying them with the methods just discussed
* Contact Digital Archives staff If you don’t feel you can make appraisal decisions
  * Digital Archives staff will assist in viewing files if possible
* Contact Digital Archives when you include unreadable files in Finding Aid Components 


## Arranging and Describing Files from a Workstation

Using their workstation the archivist will be able to create a set of intellectual   
components (arrangement), summarize the logical extents (size) and date ranges of  
the components, and enter them into ArchivesSpace.  

{: .warning }
Do not rename collection files.  


### Arrangement  
Once you have an understanding of the contents from identifying files during survey and making appraisal decisions, you can arrange the files you have decided to retain. Arrange electronic records by moving folders and files into ER folders. Refrain from renaming collection files and folders when moving. Try to avoid item level arrangement where possible.

{: .important }
Avoid creating an ER for a single file. 
* Create a new folder on the drive you received at the same folder level as ```M12345_workingfiles```.  
* Use the naming convention ```CollectionID_FAcomponents``` to create a collection folder.  
* Name the folder ```M12345_FAcomponents```, for example.  
* Create a folder for each series and subseries represented in the electronic records.        
  * 📁 ```Series 1```  
    * 📁 ```Subseries 1```  
    * 📁 ```Subseries 2```  
* Create a folder for each FA Component using ```ER # Title, dates```.  
* Create an ```objects``` folder within each ER_# folder.  
  * 📁 ```ER 1 Files, 2012``` 
    * 📁 ```objects```
* Move the files into the new FA Component ```objects``` folders as your process the files.  

Go to [Arranging and Describing Files](arranging-and-describing-files) for more examples of folder structures.

{: .important }
```objects``` must be lower case.  
 

### Finishing up
* Email [Digital Archives](mailto:digitalarchives@nypl.org) when you are finished processing.  
* Digital Archives will arrange to pick up the hard drive.  
* Digital Archives will email you a JSON file for import into ASpace.  
* Import the JSON file received from Digital Archives into ASpace.  
* Email [Digital Archives](mailto:digitalarchives@nypl.org) when your arrangement is approved.  

### Entering your collection in ArchivesSpace
After arrangement is complete Processing Archivists notify Digital Archives and deliver the external hard drive containing FA Components to Digital Archives for review.  Digital Archives staff then create a JSON file containing extents for import into ASpace. For detailed instruction on importing the extents JSON to ASpace review the [Importing FTK ERs in ArchiveSpace](https://docs.google.com/document/d/1BVMaDOzdcPFIht5yN5V16zmsnjMTwG_3e73HPTdVzSg/edit) guide.

* Note in some situations ERs may have to be manually created in ASpace instead of imported. Contact the Manager of Archival Metadata when deciding whether manual creation or JSON import is pertinent to your processing.  

----------------------------------------------------------------------------------------