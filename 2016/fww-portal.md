# Development guide

## Checkpoint 1: We meet needs using HTML

### General HTML principles
There are a few principles which we follow for all HTML we produce. The peer review will check that:

1. HTML5 Document type is used and the ```<html>``` tag includes an appropriate ```'lang'``` attribute (typically ```en-gb```)
2. HTML validates (W3C validation tool options include http://validator.w3.org/ or the newer, but still experimental http://validator.w3.org/nu/)
3. The ```<title>``` tag is present and follows pattern ```{h1} | The National Archives```
4. HTML is indented to illustrate its structure

#### Reviewer comments

1. Fine.
2. Validation errors for some meta data but these are global and necessary. Warnings on aria-roles but these should be kept in. The only possible change could possibly be around using <section> with no headings. (worth changing to <div>?)
3. Fine (note: peer review needs to be updated as we now use hyphen instead of pipe symbol)
4. All indented ok.

#### Developer(s) actions in response

---

### HTML5 syntax style

HTML5 has considerably relaxed the syntax rules for HTML. To ensure consistency across projects we have agreed upon a house syntax style. The peer review will check that:

1. [Optional tags](http://www.w3.org/TR/html5/syntax.html#optional-tags) are used
2. All tags are closed, even where HTML5 might allow them not to be
3. Full attribute syntax is used and all attributes are quoted
4. All tag names and attributes are in lower case

#### Reviewer comments

1. Optional tags used.
2. Tags are closed.
3. Attribute syntax is ok.
4. Tags and attributes in lower case.

#### Developer(s) actions in response

---

### There is an appropriate HTML outline

HTML outlines are an important means for navigating pages with assistive technologies. All digital services we produce should have a logical document outline with one ```<h1>``` tag, and each subsequent ```<h*>``` 'sectioning' the content below it. Because the HTML5 outlining algorithm is not yet implemented in any browsers, we do not rely on HTML5 sectioning elements for outlines.

The peer review will check that:

1. The HTML outline is logical and based on an appropriate heading structure
2. All content appears in the correct part of the outline

#### Reviewer comments

1. With the exception of the global header and footer, the document outline is ok.

#### Developer(s) actions in response

---

### Appropriate semantics are used

We use HTML elements for their intended purpose, ensuring valid semantics wherever possible. We do use HTML5 sectioning element semantics (```<section>```, ```<article>```, ```<nav>```, ```<aside>```), but do so with care and avoid using them for document outlining (the HTML5 outline algorithm is not yet implemented in any user agents).

We use WAI-ARIA landmark roles (```application, banner, complementary, contentinfo, form, main, navigation, search```) and a traditional document outline for structuring documents. The peer review will check that:

1. There should be one ```<main>``` element 
2. HTML5 sectioning elements are used for semantics not structure
3. HTML5 sectioning elements are not over used in place of ```<div>``` elements
4. All relevant WAI-ARIA landmarks have been applied

#### Reviewer comments

1. Only one main tag is used.
2. Section used well to group content.
3. No over-use of section element.
5. WAI landmarks used.

#### Developer(s) actions in response

---

### HTML is ordered to support user needs

Navigation will typically be before primary content, and secondary content after primary. The peer review will check that:

1. The tab order fits the user goals
2. In-page navigation is facilitated with 'skip to content' and 'back to top' links where appropriate

#### Reviewer comments

1. You can't tab through the page in Firefox. Works fine in Chrome though.
2. Skip to content and back to top working ok.

#### Developer(s) actions in response

---

### Forms

We ensure our forms are accessible6, usable and make best use of HTML5 and ARIA semantics. The peer review will check that:

1. Forms are fully accessible via keyboard alone
2. Forms are logically organised
3. Instructions (such as 'required' fields) and cues are clearly identified to users
4. Where appropriate, ```<fieldset>``` is used to group related inputs and ```<legend>``` is used to describe these groupings
5. Form elements are appropriately labelled, with labels having a ```'for'``` attribute linking them to the corresponding input (we do not nest inputs in label elements)
6. Appropriate use is made of HTML5 form semantics (i.e. ```<input type="tel" />```) so that user agents can assist users with an appropriate input mechanism
7. Good use is made of appropriate ARIA landmark roles (i.e. ```<form role="search"><input type="search" /></form>```)
8. HTML5 form validation is used, supported by JavaScript validation for older browsers. This is covered in the JavaScript section of this document
9. Error messages are clearly visible and associated (both visually and within the DOM) to the corresponding input

#### Reviewer comments

1. Email newsletter and select a subject are accessible via keyboard alone.
2. Email newsletter and select a subject are organised.
3. Required field is applied to input.
4. Fieldsets and legends not needed.
5. Need to add a label for the email input box and select a subject menu. It can be hidden with CSS.
6. No extra form semantics needed.
7. Do we need <form role="form"> on both forms?
8. HTML5 form validation used on email form.
9. Error message works ok.

#### Developer(s) actions in response

---

### Tables

All tabular data is placed in HTML ```<table>``` elements. We do not use tables for layout and do not re-purpose other elements to recreate table-like representations of data. WebAIM provide guidance on ensuring tables are accessible7

The peer review will check that:	

1. All tabular data is in ```<table>``` elements
2. A brief descriptive ```<caption>``` is provided for tables
3. Table headings are provided in ```<th>``` elements with an appropriate scope attribute

#### Reviewer comments

No tables used

#### Developer(s) actions in response

---

### SVGs are accessible
Where appropriate images should be delivered in SVG format since this offers two significant accessibility benefits: the scalability of the image allows users with less than 20/20 vision to enjoy crisp images when zoomed, and; the inclusion of links within the SVG will allow for keyboard navigation by default. 

Guidance for using SVG includes: 

1. Use inline SVG where possible
2. Provide a title for the SVG in ```<title>``` tags and a description within ```<desc>``` tags
3. Use the ```<text>``` tag for any text to appear in the SVG
4. Use ```<a>``` tags for links within the SVG
5. Provide an ARIA role for the SVG
6. Provide a non-SVG alternative. If the SVG is purely graphical, the ```<title>``` and ```<desc>``` tags may suffice. If the SVG is interactive, an HTML alternative should be considered

Related resources are:

1. [Tips for creating accessible](http://www.sitepoint.com/tips-accessible-svg/) SVG, by Leonie Watson  

Where SVGs are used, they are used accessibly

#### Reviewer comments

No SVGs used

#### Developer(s) actions in response

---

### There is good use of appropriate ARIA roles to support native semantics

While HTML5 provides a range of new semantic elements which are recognised by newer browsers, there is poor support (even in newer browsers) when it comes to reporting these elements to the Accessibility API. This, and the lack of semantics when these elements are polyfilled with JavaScript, makes ARIA an important tool. The HTML5 spec was updated in mid-2014 to indicate compatibility between elements and ARIA roles.

Related resources are: 

1. [W3C introduction to ARIA](http://www.w3.org/WAI/intro/aria) 
2. [ARIA authoring guidance](http://www.w3.org/TR/wai-aria-practices/)
3. [WCAG 2.0 Principle 4](http://www.w3.org/TR/WCAG20/#robust)

The peer review will check that ARIA roles are provided to support native semantics

#### Reviewer comments

1. Might be worth adding 'aria-required=true' to as well as 'required' to the email input box?

#### Developer(s) actions in response

---

## Checkpoint 2: Enhance with CSS

### General CSS principles

There are a number of principles which we adopt for all CSS. The peer review will check that:

1. CSS is valid
2. All CSS is placed in external stylesheets
3. Relative units are used where possible
4. ID and class names reflect the purpose of the element in question
5. !important is avoided unless absolutely necessary (which is almost never)
6. Styles targeting older IE are placed in IE specific stylesheets that are included using conditional comments
7. Hacks for other browsers are placed in the 'shame.css' file

#### Reviewer comments

1. CSS doesn't return any errors. Only warnings.
2. No inline styles present
3. No absolute units used on text. Pixels used on some padding, margins, text-shadows but that's fine.
4. IDs and classes are fine.
5. One !important override used at 768px media query.
6. No browser specific CSS in the main stylesheet.
7. No hacks in main stylesheet.

####  Developer(s) comments

---

### User focus is clearly visible

It is important to ensure interactive elements have a distinct visual appearance when activated. The peer review will check that all interactive elements have a clearly differentiated visual appearance when they have focus (this can typically be achieved using ```:focus```)

#### Reviewer comments

When tabbing in Chrome, user focus is visible for every element.

#### Developer(s) actions in response

---

### Mobile first responsive design

We adopt a mobile-first approach which includes:

* Beginning from the premise that all content will be available to all users regardless of their screen size, unless there is a clear justification for doing otherwise
* Seeking to avoid duplicating HTML for display at different resolutions
* Recognising that there is no correlation between a user's screen resolution, network speed, device capability or processing power
* Fixing the viewport in older IE, rather than polyfilling media queries

The peer review will check that:

1. The principles of our mobile-first approach have been adopted
2. We have developed in a way that accommodates devices which have low processing power and/or a slow network
3. The viewport is fixed in older IE

#### Reviewer comments

1. Responsiveness is fine.
2. Page load is fine. (146KB inc images)
3. Works ok in IE9. Also looks fine in IE8.

#### Developer(s) actions in response

---

### CSS formatting standards

To ensure consistency across developers and assist with the maintainability of our code base we adopt a number of general CSS code formatting standards. The peer review will check that:

1. Code blocks have consistent indentation to reflect their hierarchy
2. Rules are separated with new lines
3. All rules are closed with a semicolon

#### Reviewer comments

1. Indentation is fine.
2. All separated with new lines.
3. All end with semicolon.

#### Developer(s) actions in response

---

### CSS structure

CSS is structured to reflect a mobile-first approach. Each stylesheet begins with universal rules outside of a media query block. The peer review will check that:

1. ```@media``` rules are introduced sequentially, from smallest to largest
2. Overly specific queries that are difficult to test are avoided - i.e. ```@media tv and (min-width: 700px) and (max-width: 960px) and (orientation: landscape) { ... }```

#### Reviewer comments

1. Media queries are introduced correctly.
2. Only the standard 768px media query is used.

#### Developer(s) actions in response

---

### Print CSS

We need to ensure we have accounted for users printing our content. While modern browsers provide a facility to emulate and debug print from within Developer Tools, we have encountered issues where IE prints differently to other browsers. The peer review will check that:

1. The printed page is well formatted, with legible content
2. The printed page does not include unnecessary components like decorative images and form elements.
3. The printed page includes full hyperlink destinations (appending our domain where they are relative)
4. Print specific styles are contained within in a ```@media = print``` block

#### Reviewer comments

#### Developer(s) actions in response

---

## Checkpoint 3: Enhance with JavaScript

### General JavaScript principles
There are a few principles which we follow for all JavaScript development. The peer review will check that:

1. JavaScript is well commented to aid maintainability
2. JavaScript is well formatted with consistent indentation
3. JavaScript does not cause any errors (including tests across older IE which do not support ECMAScript 5)
4. JavaScript is externalised into .js files. We do not place JavaScript in ```<script>``` tags or use native8 inline event handling (i.e. ```<a href="#" onclick="triggerAlert('Bad practice!'); return false;">Joe</a>```)
5. JavaScript is minified and concatenated where possible
6. JavaScript dependent elements are created with JavaScript. For example, if a ```<button>``` is used to perform a JavaScript action only, that button should be created with JavaScript
7. Server-side processing is used to ensure JavaScript is loaded only where needed

Please speak to the Lead Front-end Developer if you need guidance on meeting any of these requirements.

#### Reviewer comments

1. Possibly could do with a little more commenting in JS to explain what it's doing?
2. JS is well formatted.
3. No JS errors caused.
4. FWW javascript is in a separate file.
5. FWW JS is not concatenated or minified.
6. No JS dependent elements present.
7. Select a subject dropdown needs a fallback submit button. Currently doesn't work without JS.

#### Developer(s) actions in response

---

### jQuery or AngularJS are used for DOM abstraction

* jQuery provides an excellent means of managing the complexity of DOM manipulation across browsers and devices. Attempting to manipulate the DOM without jQuery needlessly exposes us to a large number of cross-browser bugs and inconsistencies.

We therefore use only jQuery or similarly 'battle tested' framework (such as AngularJS) for managing interaction with the DOM.

#### Reviewer comments

JQuery used.

#### Developer(s) actions in response

---

### jQueryUI is the primary source for custom widgets
It is essential that we consider the implications for users of assistive technologies when reviewing third-party plugins that provide non-standard user interface elements. This will include:

* Ensuring that suitable ARIA role and state management is provided
* Ensuring the plug-in does not make the DOM inaccessible (the overwhelming majority of assistive technology users are likely to have JavaScript enabled)
* We should not use plug-ins that do not provide suitable ARIA role and state management, unless they are available for open source contribution and we have the skills and resources to extend them in line with the WAI-ARIA authoring practices9.

For this reason, jQueryUI presents a good tool as its authors have worked hard to include the necessary ARIA role and state management in the library components. Nonetheless, we should test the accessibility of custom widgets before they are used.

#### Reviewer comments

JQueryUI not used. No custom widgets used.

#### Developer(s) actions in response

---

### JavaScript form validation

We provide JavaScript validation for user agents that do not support HTML5.

When working outside of .NET MVC:

* jQuery validate or AngularJS is used to provide client-side validation
* When using jQuery validate, feature detection is used to determine the need for JavaScript validation and it is applied only when necessary
* In all cases there is appropriate server-side validation in place

When working with .NET MVC: the MVC framework provides mechanisms to manage client- and server-side validation in tandem. When working with .NET MVC it is important that we rely upon these since it will be substantially easier to implement and maintain. A Systems Architect or a Senior Developer can advise on a suitable approach when working with .NET.

#### Reviewer comments

Client-side validation is handled by the browser as HTML5 input types have been specified and required attributes have been used.

#### Developer(s) actions in response

---

### Our JavaScript library is used for common patterns
We have a library of common utilities that cover a range of common UI patterns used across our digital services. The peer review will check that:

* Where possible, we have made use of tna-definitions.js, tna-bindings.js, and tna-run-on-page-load.js rather than reinventing code that already exists.
* Where appropriate, we have packaged any new patterns into reusable components that are included in tna-definitions.js

#### Reviewer comments

Custom JS has been written for eventbrite interactions. This is handled in a separate JS file.

#### Developer(s) actions in response

---

## Checkpoint 5: pre-release checks

### Release version is WCAG 2.0 compliant at AA

The peer reviewer will:

1. Check compliance with the Web Content Accessibility Guidelines (WCAG 2.0) using the W3C Quick Reference
2. Ensure the site remains accessible in the event that JavaScript and CSS are not available
3. Review [An Alphabet of Accessibility Issues](https://the-pastry-box-project.net/anne-gibson/2014-july-31) to consider how the implementation will meet the needs described.

<mark>Before any code is merged into Develop it should be:</mark>

1. WCAG compliant at AA, including appropriate use and management of ARIA roles and states
2. Accessible and usable without JavaScript and/or CSS

#### Reviewer comments

#### Developer(s) actions in response

---

### Testing user goals across browsers, devices and contexts

The site/service should be tested on:

1. all supported desktop browsers (the current list is available from Webmaster) 
2. a representative range of touch screen devices. 
3. a slow network connection (there are developer tools to assist with this)
4. [Where appropriate] in the Reading Rooms and on IE within the IN domain

While issues remain, iterate.

#### Reviewer comments

#### Developer(s) actions in response

---

## Lessons learned

Everything we build provides opportunities to for improvement to our processes and approach. By documenting the lessons learned and considering their implications for this development guide, we can understand the root cause of any problems as well as any opportunities for improvement.
Questions to consider

* What worked well either for this project or for the team?
* What didn't work well?
* What surprises did the team have to deal with?
* What would you do differently if given the chance to begin this project again

### Having considered these questions, what are the key lessons to take forward for future projects?





