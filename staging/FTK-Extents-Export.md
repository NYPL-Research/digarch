---
title: FTK Extents Export
layout: default
nav_order: 8
has_children: false
parent: Post-processing
---
# Exporting Extents from FTK

{: .no_toc }
&nbsp;
{: .no_toc .text*delta }

When Digital Archives staff have completed review of the bookmarks created by a Processing Archivist, the extents of the collection are exported from FTK and delivered to Archival Processing Unit as a json file for import into ArchivesSpace. This page describes instructions for preparing and exporting extents JSON files using the [report_ftk_extents script](https://nypl.github.io/digarch/tools/software.html#report-ftk-extents-script). <!-- will need to add this to the software page -->

## Export XML Report from FTK

FTK does not generate reports in the the JSON file format, however it does generate XML.

* Prepare a destination directory
  * Navigate to the FTKsettings directory in the Storage (F:) drive on FRED 2.
  * Open the extents_reports directory
  * Create a destination directory for the XML report using the naming convention 'CollectionIDreport'.
    * As an example the XML report destination directory for the Morris Dickstein Collection is named M18867report

* Export XML report
  * Open collection to be exported in FTK.
  * Navigate to Bookmarks tab.
  * Navigate to the "File" menu
  * Select Report
  * Select the checkbox for "Bookmarks" in the "Report Options" dialog box. (Bookmarks is the only option that needs to be checked.
  * Click on the "Bookmarks" option to open the bookmarks hierarchy. Make sure that "Shared" and all subsequent bookmarks are actually checked by expanding the Bookmarks hierarchy.
  * Select "OK" after verifying that all bookmarks have been checked.
  * Select the report destination folder you created earlier by selecting the ellipses "..." and navigating to the destination folder or entering the destination path.
  * Select the checkbox for "XML" in the "Report Output" dialog box
  * Select "OK" in the "Report Output" dialog box.
  * After export is complete, return to the collection report destination folder to verify report export took place. The destination folder.
    * The report destination directory will now contain a folder called "Report_Files" and two files: "Report.fo" and "Report.xml".

## Transform XML Report to JSON using report_ftk_extents.py
The report_ftk_extents.py script transforms an XML report output from FTK into JSON for import into ASpace. The script takes two arguments: ```-f / --file``` for the path to the xml report being transformed and ```-o / --output``` for the path to the destination directory for the JSON file. For more information see [the section on report_ftk_extents.py in the Software section of Digital Archives documentation](https://nypl.github.io/digarch/tools/software.html#report-ftk-extents-script).  

* Open WSL on Fred 2.  
* Run report_ftk_extents.py script using the following the following syntax:
```python3 path/to/report_ftk_extents.py -f /path/to/xml/report -o /path/to/json/destination/directory```
  * The destination directory for the JSON file should be the ASpace directory in /mnt/f/FTKSettings.

## Deliver extents JSON to Archival Processing Unit

Digital archives staff should deliver the extents JSON file to the Processing Archvist(s) for the associated collection. The Manager of Archival Metadata should be included in any correspondence for assistance with and troubleshooting for JSON import into ArchivesSpace.