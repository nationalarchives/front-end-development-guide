# Peer review checklist

This checklist represents all the checks necessary to ensure that all steps contained in the accompanying [development guide](development-guide.md) have been followed. Each section corresponds to a Checkpoint in the Development Guide and there are sections for comments from both the developer(s) and peer reviewer.

If for any reason it has not been possible to meet any individual standard set out in the development guide the reason and justification should be recorded here.

## Checkpoint 1: We meet needs using HTML - Comments from peer reviewer and developer(s)

The W3C validator identified 20 issues with the HTML. Of these:

* 8 related to `<meta>` tag and attribute usage (mostly to do with the DC items) and suggest the `scheme` attribute is obsolete. These are existing issues that go beyond the details page but need to be fixed.
* 2 relate to the inclusion of ARIA roles on HTML5 tag equivalents, but this is intentional to support older browsers
* **Priority** two relate to `<a>` elements being direct descendent of a `<ul>`
* **Priority** a closing `</p>` where no opening tag is seen
* **Priority** remove the `role="form"` attribute from the form with ID `signup`. This is unlike the other role based warnings since it provides no backward compatibility benefits
* a `<form>` element with an empty string passed as the `action` attribute

On series level details pages the form that allows users to "Search within or browse this series":

* **Priority** the search field is missing descriptive label text. Please replace the placeholder with a linked descriptive label. Please also check that any known variants have descriptive labels
* **Priority** the 'Search' button is mis-aligned  
* **Priority** the 'Search within or browse this series...' would be better suited to a heading element
* **Priority** the 'Date range (yyy)' is currently in a `<p>` tag but should be a `<legend>`. This will require a new fieldset

**Priority** There are a number of `<p class="section-heading">` that should be headings. These include: 

* 'You are in'
* 'Add a tag'
* 'Feedback'
* 'Catalogue description' - note this may need to be absolutely positioned because it is visually above the `<h1>`

Within the 'Suggest a correction' form: 

* **Priority** fields have no visual indicator of focus state. Please apply the normal yellow border.
* **Priority** fields currently use a '*' to indicate mandatory fields but the pattern for contact forms is to use '(optional)' to denote the optional fields. Please update this to reflect the contact forms pattern.
* **Priority** the 'email' field currently has a type of 'text' but it should be 'email'

* **Priority** the inclusion of Font Awesome is adding 75KB to the page weight (making it the largest item on the page). We should replace this with some lightweight PNGs.

Actions for future sprints: 
* Please raise an issue to fix the `<meta>` tags in the next sprint. Look into alternatives to passing an empty string to a `<form>` element `action=` attribute.

## Checkpoint 2: Enhance with CSS - Comments from peer reviewer and devloper(s)

**Priority** the delivery option link expander for 'More information about the Freedom of Information review process' wraps strangely and needs some attention. Perhaps making it block level would be an improvement.

Actions for future sprints: I found it really hard to:
 
* identify links on the page because the blue colour is so close to that of the standard body text
* see the focus state for elements on a grey background

Can we raise these as possible design issues that need to be looked into as soon as possible.

## Checkpoint 3: Enhance with JavaScript - Comments from peer reviewer and devloper(s)

While keyboard navigating through the page I noticed that global search remains expanded once it has lost focus, obscuring the links below it. **Priority** this is quite a simple fix that can be achieved by attaching a 'blur' handler to the submit field.

Within the 'Suggest a correction' form: **Priority** when the form is expanded, focus should shift to the first element in the form (following the same pattern as the 'Could this page be improved' form)

We need to ensure that appropriate ARIA attributes have been applied to those elements whose visibility is controlled with JavaScript. Consider applying and managing the `aria-controls`, `aria-expanded` and `aria-hidden` attributes with JavaScript. 

## Checkpoint 4: Implementation reflects key architectural considerations - Comments from peer reviewer and devloper(s)

All key architectural considerations are OK here.

## Checkpoint 5: pre-release checks

* Release version is WCAG 2.0 compliant at AA
* Testing user goals across browsers, devices and contexts

**To be done after the issues identified above have been addressed**

### Comments from peer reviewer and developer(s)

## Lessons learned

What are the key lessons to take forward for future projects?





