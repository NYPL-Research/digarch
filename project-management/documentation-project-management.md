---
title: Documentation Project Management
layout: default
nav_order: 2
parent: Project Management
---
# Documentation Project Management
This page outlines the workflow for staff creating documentation on 
* [NYPL Digital Archives](https://nypl.github.io/digarch/){:target="_blank"}
* [Born Digital Documentation](https://nypl.github.io/born-digital-docs/){:target="_blank"}
* [NYPL Digital Preservation](https://nypl.github.io/digpres/){:target="_blank"}
<!-- Add note about repos and structure? -->

## Github Pages
Digital Preservation uses Github Pages to publish documentation. Documentation repositories are under the NYPL organization. Repository permissions are managed by team. Membership in DigPres, DigArch, and DigRepo control access to repositories. 
* [NYPL Digital Archives](https://github.com/NYPL/digarch){:target="_blank"}  
* [Born Digital Documentation](https://github.com/NYPL/born-digital-docs){:target="_blank"}
* [NYPL Digital Preservation](https://github.com/NYPL/digpres/){:target="_blank"}  

Digital Preservation uses Visual Studio Code to build Github Pages sites, edit markdown pages, and publish to Github Pages. Staff use rbenv to manage instances of Ruby when building a Github Pages site using Jekyll. All Digital Preservation Github Pages sites use just-the-docs theme. 

### Creating Documentation
Instructions for Digital Preservation staff publishing documentation to Github Pages sites.
* Create a new branch from gh-pages branch to update the site.  
* Edit or create the markdown pages to update the site.  
* Create a Pull Request from the edited branch.  
* Continue to commit edits to the branch until your Pull request is approved.  
* Merge Pull Request into the gh-pages branch once it is approved.  

## Meetings
The Documentation project holds weekly meeting up to an hour long. Meetings divide upcoming work into quarterly themes or epics. Epics are related work that move toward an overall goal for the quarter. At the first meeting of a quarter, staff decide on 3 or 4 epics for the quarter. During the quarter, staff propose and self-assign tasks within an epic that can be completed in 1 or 2 weeks. 

Each week staff present significant updates to their work for others to review. When a task has been completed and reviewed during a meeting any associated Pull Requests can be merged. 

## Trello
Each epic is represented as a list on [Documentation Projects](https://trello.com/b/va8CctGX/documentation-projects){:target="_blank"} Trello board. Tasks are represented by cards. Cards can have a Github Pages site label, a due date, a status field, assigned members, and Github Pull Request attachments.