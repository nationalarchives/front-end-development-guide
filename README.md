# Development guide and peer review

## Introduction

This repository outlines a development approach that will support us in delivering high quality, inclusive and maintainable digital services while achieving a good balance between innovation and effective use of our development capability. It is a living, open tool to which we should all contribute and is also comprehensively reviewed each year (See details of the [2016 review](reviews/2016-review.md) here).

## How it works

The [development guide](/development-guide.md) is presented as sequential checkpoints and can be used as a companion to the development process. Each section includes related peer review checks. This is accompanied by a [peer review checklist](/peer-review-checklist.md) with corresponding sections including:

 * A section for comments from the peer reviewer. 
 * A section for developer(s) comments.
 
## Who does what

The nature of web projects and tasks will mean that some checks are not relevant to all projects or tasks. **It is therefore the responsibility of developers to**: 

1. Identify the checks relevant to the specific development activity and **ensure their development work meets all relevant checks**. 

2. Ensure all relevant **pre-release checks take place at a time that will allow for any necessary changes** before the product or service is made public. By following the progressive enhancement approach set out in this Development Guide, developers will have a good sense of the project 'health' at any given time, reducing the likelihood that substantial changes will be needed as development nears completion.

3. Initiate and assign a pull request

4. Address and/or respond to comments made by the peer reviewer

It is the **responsibility of the peer reviewer to**:

1. Review the code submitted in the peer request, make observations and - ultimately - to be responsible for it being merged into `develop`
2. Record comments and observations in the [peer review checklist](peer-review-checklist.md) for future reference


It is the **responsibility of both** to discuss any lessons learned during a Design Team 10% meeting with a view to capturing insights that might benefit our approach to future projects.

## The individual steps of a peer review

The process for conducting a peer review is separated into two distinct steps: 

### Step 1: Code review

* The developer should initiate a pull request on GitHub and identify a peer reviewer
* The peer reviewer should clone this repository to their development machine and create a copy of ```peer-review-checklist.md```. The copy should then be added to this repository in the relevant folder. For example, a peer review of a meeting minutes template conducted in 2017 would be saved as ```peer-review-meeting-minutes.md``` within the ```2017``` directory.
* The peer reviewer should then:
    * review the pull request, discussing the detail of code in GitHub
    * populate the checklist with comments based on standards set out in the development guide 
* The developer should then act on the comments (within the checklist and pull request) and, where necessary, describe how they have addressed any issues raised. 

Before migrating a prototype into a target environment **discuss the proposed approach with webmaster and the editorial team**. This is also an excellent knowledge sharing opportunity so please **discuss implementation and technical design decisions with others**

### Step 2: Pre-release checks

* Once the necessary changes have been made the code can be ported to the target platform (i.e. WordPress).
* Having ported the code to the target platform the peer reviewer should:
  * Perform all the **pre-release checks**
  * Check that porting the code to a target platform hasn't compromised the code. 

While this process has emerged from several discussions in the design team, it is open to change and improvement. **If any member of the team has concerns or suggestions about this process please raise them**. 
