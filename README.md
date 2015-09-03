# Development guide and peer review

## Introduction

This repository outlines a development approach that will support us in delivering high quality, inclusive and maintainable digital services while achieving a good balance between innovation and effective use of our development capability. It is a living, open tool to which we should all contribute.

The [development guide and peer review](/peer-review-template.md) is presented as sequential checkpoints and can be used as a companion to the development process. Each section includes related peer review checks along with:

 * A section for comments from the peer reviewer. 
 * A section for developer(s) comments.

The nature of web projects and tasks will mean that some checks are not relevant to all projects or tasks. **It is therefore the responsibility of developers to**: 

1. Identify the checks relevant to the specific development activity and **ensure their development work meets all relevant checks**. 

2. Ensure all relevant **pre-release checks take place at a time that will allow for any necessary changes** before the product or service is made public. By following the progressive enhancement approach set out in this Development Guide, developers will have a good sense of the project 'health' at any given time, reducing the likelihood that substantial changes will be needed as development nears completion.

3. Where appropriate, discuss any lessons learned during a Design Team 10% meeting with a view to capturing insights that might benefit our approach to future projects.

## Conducting a peer review

The process for conducting a peer review is separated into two distinct steps: 

### Step 1: Before any code is migrated to a target platform (i.e. WordPress) 

* The peer reviewer should clone this repository to their development machine and create a copy of ```peer-review-template.md```. The copy should then be added to this repository in the relevant folder. For example, a peer review of a meeting minutes template conducted in 2015 would be saved as ```meeting-minutes.md``` within the ```2015``` directory.
* The peer reviewer should then populate the created file with the peer review comments and discuss these with the developer when completed. 
* The developer should then act on the comments and, where appropriate, provide further comments. 

### Step 2: Migrating the code into WordPress

* Once the necessary changes have been made the code can be ported to the target platform (i.e. WordPress). **Please bear in mind that this is an excellent knowledge sharing opportunity to discuss implementation and technical design decisions with others**
* Having ported the code to the target platform the peer reviewer should:
  * Perform all the **pre-release checks**
  * Check that porting the code to a target platform hasn't compromised the code. 

While this process has emerged from several discussions in the design team, it is open to change and improvement. **If any member of the team has concerns or suggestions about this process please raise them**. 
