---
title: Extract files from ISOs using a script
layout: default
nav_order: 2
parent: Optical Media
---
# Extract files from ISOs using a script  
This document outlines the procedure to extract files from ISOs using a  script running ISObuster.  
Currently, the script is available on the T1 Thinkpad.  

### Open PowerShell  
* Select PowerShell from Search  

### Navigate to script location  
* cd into amip-to-da  

## Batch Processing  
This script will extract files from all ISOs in a folder when called with ```uv run amip-to-da batch```  

### Prepare CSV  
* Create a CSV with header rows  “ami_id” and “acq_id”  


| ami_id | acq_id |
|:------:|:--------:|
|    123456 |  ACQ_1234_9876543  |  

* List the AMI IDs of the ISOs to extract in the ami_id column  
* List the corresponding ACQ_IDs in the acq_id column  
* Save the CSV  

### Run the script  
The batch script takes 3 arguments: mapping_csv ami_packages_dir output_root  
A batch report will be created in the output folder
* Enter ```uv run amip-to-da batch C:\Users\foren\amip-to-da\src\amip_to_da\mapping_csv.csv \\Volume_path\4_experiments\Coll_ID[ISO folder]\ 
\\Volume_path\4_experiments\ACQ_ID[output folder]\```  

## Processing Single ISOs  
This script will extract files from a single ISO when called with ```uv run amip-to-da convert```  
* Enter ```uv run amip-to-da convert --log-file [logfile] --acq-id [ACQ_ID] ..\[AMI_ID folder]\ ..\```  