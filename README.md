# Development guide and peer review

## Introduction

This repository provides several resources to help developers at The National Archives:

* deliver **high quality**, **inclusive** and **maintainable** digital services, while;
* achieving a good **balance between innovation and effective use of our development capability**. 

It is a living, open tool to which all can contribute and is:

* regularly reviewed and refined to ensure it reflects emerging industry best practice; 
* comprehensively reviewed by developers in Digital Services each year (See details of the [2016 review](reviews/2016-review.md) here).

We welcome any and all feedback to be submitted either as a pull request or issue. 

## What's included

The two primary components of this guide are:

1. a high-level [peer review checklist](/templates/peer-review-checklist.md) describing key considerations for digital services. This has sections covering: 
    - **design** standards;
    - **development** and pull requests;
    - **testing** of accessibility and compatibility.
2. a detailed client-side [development guide](/development-guide.md) describing the **standards and client-side architectural considerations for our digital services**. This is intentionally focused on the code that is delivered to the user's browser and is intended to **apply to all products** - _regardless of the server-side technology used to generate and deliver the HTML, CSS and JavaScript_

### Supplemental material

Additional materials include:

* [Version control guidance](/version_control/) including the **branching methodologies** we use in Git and how to write useful commit messages;
* [Server-side](/server_side_coding_standards) coding standards _[Note: this is a new section (introduced in July 2017) but will be added to over time]_;
* an [introduction for new developers](supporting_material/development_standards_introduction_for_new_developers.pdf) explaining the broader context, purpose and components of this guide;
* a range of [templates](/templates/) including accessibility acceptance criteria;
* an [introduction to progressive enhancement](supporting_material/progressive_enhancement_introduction.ppt).
    
## How to conduct a peer review 

The process of conducting a peer review begins with the **developer** identifying a peer reviewer. This is followed by:

* The **peer reviewer** cloning this repository to their development machine and creating a copy of the [peer review checklist](/templates/peer-review-checklist.md) in the relevant year folder. For example, a peer review of a meeting minutes template conducted in 2017 would be saved as ```peer-review-meeting-minutes.md``` within the ```2017``` directory.
* The **peer reviewer** then populates the checklist and discusses these with the developer. 
* The **developer** acts on the comments and describes how they have addressed any issues raised.

### Use pull requests for detailed discussions about code

The peer review checklist is intended to ensure standards are met. It is not normally the correct place for detailed technical discussions about code. Such detailed technical discussions should instead be conducted as part of the **pull request**

## Key things for developers to keep in mind

### Involve others early

Perhaps the most important thing to bear in mind is the need to involve other specialists early since this can avoid significant problems later on. This includes:

* **Speaking to the User Experience and Editorial teams before beginning development**. Their perspective and expertise will help shape the approach taken and can avoid significant changes later on.
* **Server-side and front-end developers discussing the technical approach _together_ before development begins**. A short conversation to agree on a technical approach that works from both perspectives can bring significant benefits and avoid one or both having to do significant refactoring and re-work.
* Identifying a peer reviewer early.

### Try to anticipate what is relevant to the activity and plan for it

* Identify the **testing that is relevant to the specific development activity** and ensure development work meets all relevant standards in the development guide
* Ensure the **pull request takes place at a time that  allows for any necessary changes** before the product or service is made public. (Note: the progressive enhancement approach set out in this Development Guide is intentionally designed so that developers will have a good sense of the project 'health' at any given time, reducing the likelihood that substantial changes will be needed as development nears completion)

### Let us know how we can improve this guidance

The purpose of the development guide and peer review is to ensure we are delivering digital services that meet user needs in a way that is both efficient and effective. To achieve this it must work for product teams. While the current version has emerged over several iterations to reflect lessons we have learned, we are keen for it to continue to evolve. We therefore actively encourage to contribution to the guide via either a pull request, discussion at the Digital Service 10% meeting or by raising an issue in GitHub.
