# Development guide and peer review

## Introduction

This repository outlines an approach to enable us deliver high quality, inclusive and maintainable digital services while achieving a good balance between innovation and effective use of our development capability. It is a living, open tool to which we can all contribute and is comprehensively reviewed each year (See details of the [2016 review](reviews/2016-review.md) here).

## What's included

1. the high level [peer review checklist](/templates/peer-review-checklist.md) with sections covering: 
    - **design** considerations
    - **development** and pull requests
    - **testing** of accessibility and compatibility
2. a detailed client-side [development guide](/development-guide.md) covering development standards for our digital services. This applies to all products, regardless of the server-side technology used
3. [server-side](/server_side_coding_standards) coding standards [Note: this is a new section (as of July 2017) but will be added to over time]
4. Supporting materials including:
    * slides that provide an [introduction for new developers](supporting_material/development_standards_introduction_for_new_developers.pdf) explaining the broader context, purpose and components of this guide
    * a range of [templates](/templates/) including accessibility acceptance criteria
    * an [introduction to progressive enhancement](supporting_material/progressive_enhancement_introduction.ppt) 

## Developer responsibilities

It is the responsibility of developers to: 

1. Ensure The National Archives' design patterns are reflected

2. Identify the **testing that is relevant to the specific development activity** and ensure their development work meets all relevant standards in the development guide

3. Ensure the **pull request takes place at a time that  allows for any necessary changes** before the product or service is made public. (Note: the progressive enhancement approach set out in this Development Guide is intentionally designed so that developers will have a good sense of the project 'health' at any given time, reducing the likelihood that substantial changes will be needed as development nears completion).

4. Where appropriate, discuss any lessons learned during a Digital Services 'Ten Percent' meeting with a view to capturing insights that might benefit our approach to future projects

## Conducting a peer review

* The peer reviewer should clone this repository to their development machine and create a copy of ```peer-review-checklist.md```. The copy should then be added to this repository in the relevant year folder. For example, a peer review of a meeting minutes template conducted in 2017 would be saved as ```peer-review-meeting-minutes.md``` within the ```2017``` directory.
* The peer reviewer should then populate the created file with comments corresponding to sections within the [peer review checklist](/templates/peer-review-checklist.md) and discuss these with the developer when completed. 
* The developer should then act on the comments and, where necessary, describe how they have addressed any issues raised.
* The technical detail of discussions about code and merging of any code to `develop` is managed via a **pull request** process during which the reviewer will be confirming that all development standards are met.
