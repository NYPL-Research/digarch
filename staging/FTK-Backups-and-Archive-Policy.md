---
title: FTK Backups and Archive Policy
layout: default
nav_order: 6
has_children: false
parent: Post-processing
---

# FTK Backups and Archive Policy
{: .no_toc }
&nbsp;
{: .no_toc .text*delta }

The Digital Archives program uses the software Forensic Toolkit (FTK) to
process the majority of the Library's born-digital acquisitions. For
each collection a case is created in FTK and information regarding this
case is stored in a PostGreSQL database. During processing, a backup of
the case can be created which contains case information and a copy of
the database files regarding that case. After processing, a case is
archived in FTK terminology. This means case information is moved from PostGreSQL
to the case directory. The case directory keeps the case information and the database 
files are then deleted from the PostGresSQL database.

## Archive of Case

*   A case will be archived when a collection has been processed. This
     means the archivist has finished the arrangement and description
     of the collection, the finding aid has been approved, and finding aid
     components have been exported.

*   After a case has been archived, all backups of that case will be
     deleted.

*   An archive will be retained for a two year retention period and
     disposition will occur in quarterly increments. Exceptions to this
     rule include:

    *   The collection contains media that could not be accessed,
         rendered, or otherwise fully arranged, described, and made
         accessible to researchers. An archive will be retained so that
         processing can be revisited at a later date.

    *  Collections with lots of executables. We have found
         that arrangement and description of these collections often
         are revisited.

    *   Exceptions will be stored in a separate directory and
         rationale provided in a README.txt file that will be stored
         with the archive.
