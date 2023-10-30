![The National Archives logo](/images/tna.jpg "The National Archives logo")

# Front end development guide

> ⚠️ October 2023
> This handbook is no longer maintained.
> It has been replaced with the [National Archives Engineering Handbook](https://github.com/nationalarchives/engineering-handbook).

## Introduction

This guide has been produced to help developers at The National Archives:

* deliver **high quality**, **inclusive** and **maintainable** digital services, which 
* ensure their work is **compliant with the standards and regulations** that apply to public sector websites
* achieving a good **balance between innovation and effective use of our development capability**. 

It covers all aspects of modern front end development and is regularly reviewed and refined to ensure it reflects emerging industry best practice. Please let us know if you think anything is missing or unclear, and we'll look into it. **This a living, open tool and contributions are welcomed**.  

## What's included

The [development guide](/development-guide.md) describes **standards and client-side architectural considerations for our digital services**. 

All guidance is intentionally focused on the code that is delivered to the user's browser so it can **apply to all products** - _regardless of the server-side technology or client side frameworks_ being used for a particular application or site.

### What's not included

This guide is tightly focused on development practice and considerations related to implementation. It does not address visual and interaction design or user experience patterns.

### Supplemental material

Additional materials include:

* an [introduction to the front end development standards for new developers](supporting_material/front_end_development_standards_introduction_for_new_developers.pdf) explaining the broader context, purpose and components of this guide
* an [introduction to progressive enhancement](supporting_material/progressive_enhancement_at_tna.pdf)
* [Git guidance](/version_control/) including the **branching methodologies** we use in Git and how to write useful commit messages
    
## Use pull requests for peer review 

All code should be reviewed using the Pull Request process before it is merged or deployed. This review should ensure all relevant standards are met.

## Key things for developers to keep in mind

### Involve others early

Perhaps the most important thing to bear in mind is the need to involve other specialists early since this can avoid significant problems later on. This includes:

* **Speaking to the User Experience and Editorial teams before beginning development**. Their perspective and expertise will help shape the approach taken and can avoid significant changes later on.
* **Understanding analytics requirements to establish what is required and how we can best support/achieve it**
* **Server-side and front-end developers discussing the technical approach _together_ before development begins**. A short conversation to agree on a technical approach that works from both perspectives can bring significant benefits and avoid one or both having to do significant refactoring and re-work.
* Identifying a peer reviewer early, and discussing the technical approach with them as it evolves.

### Try to anticipate what is relevant to the activity and plan for it

* Identify the **testing that is relevant to the specific development activity** and ensure development work meets all relevant standards in the development guide
* Ensure the **pull request takes place at a time that  allows for any necessary changes** before the product or service is made public. (Note: the progressive enhancement approach set out in this Development Guide is intentionally designed so that developers will have a good sense of the project 'health' at any given time, reducing the likelihood that substantial changes will be needed as development nears completion)

### Let us know how we can improve this guidance

The purpose of the development guide and peer review is to ensure we are delivering digital services that meet user needs in a way that is both efficient and effective. To achieve this it must work for product teams. While the current version has emerged over several iterations to reflect lessons we have learned, we are keen for it to continue to evolve. We therefore actively encourage to contribution to the guide via either a pull request, discussion at Code Club or by raising an issue in GitHub.
