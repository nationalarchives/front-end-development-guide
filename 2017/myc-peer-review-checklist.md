# Peer review checklist

This checklist represents all the checks necessary to ensure that all steps contained in the accompanying [development guide](development-guide.md) have been followed. Each section corresponds to a Checkpoint in the Development Guide and there are sections for comments from both the developer(s) and peer reviewer.

If for any reason it has not been possible to meet any individual standard set out in the development guide the reason and justification should be recorded here.

## Checkpoint 1: We meet needs using HTML

* General HTML principles
* HTML5 syntax style
* There is an appropriate HTML outline
* Appropriate semantics are used
* HTML is ordered to support user needs
* Forms
* Tables
* SVGs are accessible
* There is good use of appropriate ARIA static roles (see ARIA section of development guide) to support native semantics

### Comments from peer reviewer and developer(s)

* all: li missing for `<a href="/sign-in" id="bookmarkLink">Bookmark</a>`
* preview.php: li missing for `<a href="/browse">All departments</a>`

## Checkpoint 2: Enhance with CSS

* General CSS principles
* User focus is clearly visible
* SASS guidelines
* SASS/CSS formatting standards
* Print CSS

### Comments from peer reviewer and devloper(s)

* CSS passes validation with warnings
* No focus on select form element
* Text input form element focuses blue not yellow
* history.php: Print view bg icons not showing. Not really necessary. 

## Checkpoint 3: Enhance with JavaScript

* General JavaScript principles
* jQuery or AngularJS are used for DOM abstraction
* jQueryUI is the primary source for custom widgets
* JavaScript form validation
* ARIA pseudo-interactive and interactive widget roles (see ARIA section of development guide) are correctly applied and managed with JavaScript

### Comments from peer reviewer and devloper(s)

* jQuery looks fine and well commented
* Uplaod form appears to have no validation

## Checkpoint 4: Implementation reflects key architectural considerations

See related section in the Development Guide

* All application logic resides on the server
* Users can link to specific application states (i.e. a specific tab or step within a process)
* Browser 'back' and 'forward' buttons behave as expected

## Checkpoint 5: pre-release checks

* Release version is WCAG 2.0 compliant at AA
* Testing user goals across browsers, devices and contexts

### Comments from peer reviewer and developer(s)

* A `menu` should have at least one instance of a `menuitem`, `menuitemcheckbox`, or `menuitemradio`.

## Lessons learned

What are the key lessons to take forward for future projects?





