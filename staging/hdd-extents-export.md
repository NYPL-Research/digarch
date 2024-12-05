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

* Review the finding aid components returned by Processing Archivist(s) for system files or other formats not retained by Digital Archives.

## Run report_hdd_extents.py

* Prepare a destination directory
  * Navigate to the FTKsettings directory in the Storage (F:) drive on FRED 2.
  * Open the /ASpace directory
  * Create a destination directory for the extents report using the naming convention 'CollectionIDreport'.
    * As an example the extents report destination directory for the Morris Dickstein Collection would be named M18867report

* Extract extents using report_hdd_extents.py
  * Open WSL on FRED 2
  * Navigate to the destination directory previously created.
  * Run [report_hdd_extents.py](https://nypl.github.io/digarch/tools/software.html#report-hdd-extents-script) script using the following the following syntax:
```python3 path/to/report_ftk_extents.py -d /path/to/collection/er/directory```

## Deliver extents JSON to Archival Processing Unit

Digital archives staff should deliver the extents JSON file to the Processing Archvist(s) for the associated collection. The Manager of Archival Metadata should be included in any correspondence for assistance with and troubleshooting for JSON import into ArchivesSpace.