# Development guide

## Checkpoint 1: Coding standards

### Version control and code reviews

We follow the [Git Flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) branching methodology and routinely undertake code reviews using [pull requests](https://help.github.com/articles/about-pull-requests/) in GitHub to ensure all code has been reviewed before being merged into `develop`. The process is as follows: 

* A feature branch is made from `develop` on a local development machine and pushed to GitHub
* A pull request is made and assigned to one or more other developers
* When work is concluded the pull request is merged on GitHub
* Developers pull the `develop` branch from GitHub.

Key things to bear in mind are: 

* Merges to `develop` are done via a pull request to ensure there has been some review of code before it is merged to `develop`
* No development should be done on the `develop` or `master` branches. Urgent fixes can be managed via the 'Hotfix' process of in [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

### Architectural considerations

The [Resource Oriented Client Architecture](http://roca-style.org/) describes a number of recommendations that should be reflected in the applications we produce, as appropriate. Some key considerations which are not represented elsewhere in this guide are:

* All [application logic](http://roca-style.org/#application-logic) resides on the server
* A user must be able to [link to a specific piece of information](http://roca-style.org/#link).
* Browser ['back' and 'forward' buttons](http://roca-style.org/#browser-controls) should work as expected. There is a recommendation related to this regarding the [History API](http://roca-style.org/#historyapi)
* All [JavaScript and CSS code must be static](http://roca-style.org/#static-assets) 

### WordPress coding style for PHP

As part of our efforts to ensure clean, readable and consistent code across projects and developers we follow the [WordPress PHP Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/php/)

### Testing

* PHP code is tested using PHPUnit. There is a wealth of documentation and guidance on the [PHPUnit website](https://phpunit.de/) including: a [getting started guide](https://phpunit.de/), extensive [library documentation](https://phpunit.de/manual/current/en/index.html) and [presentations and videos](https://phpunit.de/presentations.html) 
* JavaScript and jQuery code is tested using QUnit. There is good documentation available on the [QUnit website] including [an introduction to unit testing](http://qunitjs.com/intro/), a [cookbook](http://qunitjs.com/cookbook/) and good [documentation](http://api.qunitjs.com/) of the API.
* Travis CI has been integrated into the repository to run PHPUnit and QUnit tests automatically when a branch is pushed to GitHub. This is very simple to achieve via a `.travis.yml` file in the project root. Travis also has good [documentation](https://docs.travis-ci.com).

## Checkpoint 2: We meet needs using HTML

### General HTML principles
There are a few principles which we follow for all HTML we produce. The peer review will check that:

1. HTML5 Document type is used and the ```<html>``` tag includes an appropriate ```'lang'``` attribute (typically ```en```)
2. HTML validates (W3C validation tool options include http://validator.w3.org/ or the newer, but still experimental - as of February 2017 - http://validator.w3.org/nu/)
3. The ```<title>``` tag is present and follows pattern ```{h1} - The National Archives```
4. Source code is correctly indented to illustrate its structure

---

### HTML5 syntax style

HTML5 has considerably relaxed the syntax rules for HTML. To ensure consistency across projects we have agreed upon a house syntax style. The peer review will check that:

1. [Optional tags](http://www.w3.org/TR/html5/syntax.html#optional-tags) are used
2. All tags are closed, even where HTML5 might allow them not to be (as is the case for ```<li>``` and ```<p>``` tags)
3. Full attribute syntax is used and all attributes are quoted. See the W3C description of [quoted attribute syntax](http://www.w3.org/TR/html-markup/syntax.html#syntax-attributes)
4. All tag names and attributes are in lower case

---

### There is an appropriate HTML outline

HTML outlines are an important means for navigating pages with assistive technologies. All digital services we produce should have a logical document outline with one ```<h1>``` tag, and each subsequent ```<h*>``` serving to 'section' the content below it. Because the HTML5 outlining algorithm is not yet implemented in any browsers, we do not rely on HTML5 sectioning elements for outlines.

The peer review will check that:

1. The HTML outline is logical and based on an appropriate heading structure
2. All content appears in the correct part of the outline

---

### Appropriate semantics are used

We use HTML elements for their intended purpose, ensuring valid semantics wherever possible. We do use HTML5 sectioning element semantics (```<section>```, ```<article>```, ```<nav>```, ```<aside>```), but do so with care and avoid using them for document outlining (the HTML5 outline algorithm is not yet implemented in any user agents).

We use WAI-ARIA landmark roles (```application, banner, complementary, contentinfo, form, main, navigation, search```) and a traditional document outline for structuring documents. The peer review will check that:

1. There should be one ```<main>``` element 
2. HTML5 sectioning elements are used for semantics not structure
3. HTML5 sectioning elements are not over used in place of ```<div>``` elements
4. All relevant WAI-ARIA landmarks have been applied

---

### HTML is ordered to support user needs

Navigation will typically be before primary content, and secondary content after primary. The peer review will check that:

1. The order in which elements receive focus when a user tabs through the document supports user goals.
2. In-page navigation is facilitated with 'skip to content' and 'back to top' links where appropriate

---

### Forms

We ensure our forms are **accessible**, **usable** and make best use of HTML5 and ARIA semantics. The peer review will check that:

1. Forms are fully accessible via keyboard alone
2. Forms are logically organised
3. Instructions (such as 'required' fields) and cues are clearly identified to users
4. Where appropriate, ```<fieldset>``` is used to group related inputs and ```<legend>``` is used to describe these groupings
5. Form elements are appropriately labelled, with labels having a ```'for'``` attribute linking them to the corresponding input (we do not nest inputs in label elements)
6. Appropriate use is made of HTML5 form semantics (i.e. ```<input type="tel" />```) so that user agents can assist users with an appropriate input mechanism
7. Good use is made of appropriate ARIA landmark roles (i.e. ```<form role="search"><input type="search" /></form>```)
8. HTML5 form validation is used, supported by JavaScript validation for older browsers. This is covered in the JavaScript section of this document
9. Error messages are clearly visible and associated (both visually and within the DOM) to the corresponding input. This includes appropriate use of ARIA attributes.

---

### Tables

Where appropriate, tabular data is placed in HTML ```<table>``` elements. We never use tables for layout and avoid re-purposing other elements to recreate table-like representations of data. WebAIM provide guidance on ensuring tables are accessible

The peer review will check that:	

1. All tabular data is in ```<table>``` elements
2. A brief descriptive ```<caption>``` is provided for tables
3. Table headings are provided in ```<th>``` elements with an appropriate scope attribute

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

---

### Images

Where appropriate and practical we do make use of the incoming `srcset` attribute on `<img>` elements.

### There is good use of appropriate ARIA roles to support native semantics

While HTML5 provides a range of new semantic elements which are recognised by newer browsers, there is poor support (even in newer browsers) when it comes to reporting these elements to the Accessibility API. This, and the lack of semantics when these elements are polyfilled with JavaScript, makes ARIA an important tool. Because the HTML5 spec was updated in mid-2014 to indicate compatibility between elements and ARIA roles, developers can see the compatibility of an element with ARIA roles, states and properties by looking up the tag within the [HTML5 specification](http://www.w3.org/TR/2014/REC-html5-20141028/).

Because we are focussed in Checkpoint 1 on the HTML delivered to the user's browser, developers should ensure that all relevant **static** ARIA roles have been applied (these being landmark, region, and speciality roles) as well as *any* relevant pseudo interactive roles (such as dialog). See ARIA role conformance matrices or ask a fellow developer for guidance if needed. At this stage it can be very helpful to think about the four 'rules of using ARIA in HTML' from [W3C notes on ARIA use in HTML](https://www.w3.org/TR/2015/WD-aria-in-html-20150521/#notes-on-aria-use-in-html): 

1. If you can use an HTML element with the required semantics and behaviour built in, then do so
2. Do not change native semantics, unless you really have to
3. All interactive ARIA controls must be usable with a keyboard
4. Do not use `role="presentation"` or `aria-hidden="true"` on a visible **focusable** element

Related resources are: 

1. [W3C introduction to ARIA](http://www.w3.org/WAI/intro/aria) 
2. [ARIA authoring guidance](http://www.w3.org/TR/wai-aria-practices/)
3. [WCAG 2.0 Principle 4](http://www.w3.org/TR/WCAG20/#robust)
4. [ARIA role matrices by Whatsock](http://whatsock.com/training/matrices/)
5. The [A11Y Project](http://a11yproject.com/)
6. [W3C Notes on ARIA use in HTML](https://www.w3.org/TR/2015/WD-aria-in-html-20150521/#notes-on-aria-use-in-html)

The peer review will check that ARIA roles are provided to support native semantics

---

## Checkpoint 3: Enhance with CSS

### General CSS principles

There are a number of principles which we adopt for all CSS. The peer review will check that:

1. CSS is valid
2. All CSS is placed in external stylesheets
3. Relative units are used where possible
4. ID and class names reflect the purpose of the element in question
5. `!important` is avoided unless absolutely necessary (which is almost never)
6. Styles targeting older IE are placed in IE specific stylesheets that are included using conditional comments
7. Hacks for other browsers are placed in the 'shame.css' file

---

### User focus is clearly visible

It is important to ensure interactive elements have a distinct visual appearance when activated. The peer review will check that all interactive elements have a clearly differentiated visual appearance when they have focus (this can typically be achieved using ```:focus```)

---

### SASS guidelines

As we more routinely incorporate CSS-preprocessing into our workflow we need to ensure our approach is maintainable (and that future developers understand the code we're writing today) and as simple as possible. Some useful insights are provided at [SASS guidelines](http://sass-guidelin.es) but developers will need to exercise judgement about what is most appropriate in the specific circumstances. A useful principle to bear in mind (from the SASS guidelines) is that: 

> ... CSS is a simple language. Sass, being intended to write CSS, should not get much more complex than regular CSS. The KISS principle (Keep It Simple Stupid) is key here and may even take precedence over the DRY principle (Don’t Repeat Yourself) in some circumstances.

> Sometimes, it’s better to repeat a little to keep the code maintainable, rather than building a top-heavy, unwieldy, unnecessarily complicated system that is completely unmaintainable because it is overly complex.

**Developers are strongly encouraged to contribute to this section of the development guide as we get more familiar with SASS**

### SASS/CSS formatting standards

To ensure consistency across developers and assist with the maintainability of our code base we adopt a number of general CSS code formatting standards. The peer review will check that:

1. Code blocks have consistent indentation to reflect their hierarchy
2. Rules are separated with new lines
3. All rules are closed with a semicolon

---

### Print CSS

We need to ensure we have accounted for users printing our content. While modern browsers provide a facility to emulate and debug print from within Developer Tools, we have encountered issues where IE prints differently to other browsers. The peer review will check that:

1. The printed page is well formatted, with legible content
2. The printed page does not include unnecessary components like decorative images and form elements.
3. The printed page includes full hyperlink destinations (appending our domain where they are relative)
4. Print specific styles are contained within in a ```@media = print``` block

---

## Checkpoint 4: Enhance with JavaScript

### General JavaScript principles
There are a few principles which we follow for all JavaScript development. The peer review will check that:

1. JavaScript is logically organised and, where necessary, well commented to aid understanding
2. JavaScript is well formatted with consistent indentation
3. JavaScript does not cause any errors (including tests across older IE which do not support ECMAScript 5)
4. JavaScript is externalised into .js files. We do not place JavaScript in ```<script>``` tags or use native8 inline event handling (i.e. ```<a href="#" onclick="triggerAlert('Bad practice!'); return false;">Joe</a>```)
5. JavaScript is minified and concatenated where possible
6. JavaScript dependent elements are created with JavaScript. For example, if a ```<button>``` is used to perform a JavaScript action only, that button should be created with JavaScript
7. Any DOM manipulation performed by JavaScript is accompanied by the application and management of relevant ARIA roles, states and properties. These should build upon the static and pseudo interactive roles applied during Checkpoint 2.
8. Server-side processing is used to ensure JavaScript is loaded only where needed

Relevant resources include: 

* [Writing JavaScript with accessibility in mind](https://medium.com/@matuzo/writing-javascript-with-accessibility-in-mind-a1f6a5f467b9)

Please speak to the Lead Front-end Developer if you need guidance on meeting any of these requirements.

---

### We use established libraries for DOM abstraction

Established libraries such as jQuery, Angular and ReactJS provide an excellent means of managing the complexity of DOM manipulation across browsers and devices. Attempting to manipulate the DOM without a 'battle tested' framework needlessly exposes us to a large number of cross-browser bugs and inconsistencies.

You can find out the number of cross browser bugs being addressed in the current version of jQuery, for example, with 

```bash
curl -L https://code.jquery.com/jquery-git2.js | grep Support: | wc -l
```
At the time of writing this reveals **104** cross browser bugs being managed in the current version of jQuery (which long since dropped support for IE6-8).  While many of cross-browser bugs are traditionally related to older browsers there are many fixes in these libraries tackling inconsistencies where you might not expect them.

**We therefore use only established frameworks for managing interactions with the DOM**. If you are unsure about any of this please speak to the Lead Front End Developer.

---

### jQueryUI is the primary source for custom widgets
It is essential that we consider the implications for users of assistive technologies when reviewing third-party plugins that provide non-standard user interface elements. This will include:

* Ensuring that suitable ARIA role and state management is provided
* Ensuring the plug-in does not make the DOM inaccessible (the overwhelming majority of assistive technology users are likely to have JavaScript enabled)
* We should not use plug-ins that do not provide suitable ARIA role and state management, unless they are available for open source contribution and we have the skills and resources to extend them in line with the WAI-ARIA authoring practices9.

For this reason, jQueryUI presents a good tool as its authors have worked hard to include the necessary ARIA role and state management in the library components. Nonetheless, we should test the accessibility of custom widgets before they are used.

---

### JavaScript form validation

We provide JavaScript validation for user agents that do not support HTML5.

When working outside of .NET MVC:

* jQuery validate or AngularJS is used to provide client-side validation
* When using jQuery validate, feature detection is used to determine the need for JavaScript validation and it is applied only when necessary
* In all cases there is appropriate server-side validation in place

When working with .NET MVC: the MVC framework provides mechanisms to manage client- and server-side validation in tandem. When working with .NET MVC it is important that we rely upon these since it will be substantially easier to implement and maintain. A Systems Architect or a Senior Developer can advise on a suitable approach when working with .NET.

---

## Checkpoint 5: pre-release checks

### Release version is WCAG 2.0 compliant at AA

The peer reviewer will:

1. Check compliance with the Web Content Accessibility Guidelines (WCAG 2.0) using the [W3C Quick Reference](https://www.w3.org/WAI/WCAG20/quickref/)
2. Ensure the site remains accessible in the event that JavaScript and CSS are not available
3. Review [An Alphabet of Accessibility Issues](https://the-pastry-box-project.net/anne-gibson/2014-july-31) to consider how the implementation will meet the needs described.

<mark>Before any code is merged into Develop it should be:</mark>

1. WCAG compliant at AA, including appropriate use and management of ARIA roles and states
2. Accessible and usable without JavaScript and/or CSS

#### Useful tools for accessibility testing:
In addition to the [W3C Quick Reference](https://www.w3.org/WAI/WCAG20/quickref/) tools that may be useful are the: 

* [aXe Chrome Extension ](https://chrome.google.com/webstore/detail/axe/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US) which provides a developer tools panel that allows you to run an in-browser audit against a page, including a colour and contrast check. The extension features are described on the [Google Chrome Developers channel on YouTube](https://youtu.be/cOmehxAU_4s?t=8m58s)
* [Chrome accessibility Developer Tools](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?utm_source=gmail). This does many of the same things as the aXe extension but also provides colour suggestions where contrast issues are found. This is also described on the [Google Chrome Developers channel on YouTube](https://youtu.be/cOmehxAU_4s?t=10m6s)

---

### Testing user goals across browsers, devices and contexts

#### Testing for compatibility

> Users must be able to access and use all the information and features they need, regardless of which browser they use ([GDS Service Manual](https://www.gov.uk/service-manual/technology/designing-for-different-browsers-and-devices#test-for-compatibility))

#### Operating systems and browsers to test in 

##### For public facing services

The ([Service Manual](https://www.gov.uk/service-manual/technology/designing-for-different-browsers-and-devices#browsers-to-test-in)) lists the Operating System and browser support levels that are expected for public facing services. The levels of support are __'compliant'__ and __'functional'__ and are described as:

* 'Compliant' means your service **must look as good as it does in other modern browsers** (Note: this does not mean it should be visually identical)
* 'Functional' means it might not look perfect **but must still be usable**

At this point developers might ask how far back we are expected to support Internet Explorer on Windows. Check the most current information at the time of development but, as of February 2017, it is:

* _functional_ support in IE8 on Windows
* _compliant_ support in IE9+ on Windows

##### For government facing services

For government facing services the service manual states: 

> If you service is aimed at internal users rather than the general public you should use the browsers in the table [for public facing services] as a starting point then **use your own analytics data to decide and appropriate level of support**

#### Testing across contexts and conditions

The site/service should also be tested on:

1. a slow network connection (there are developer tools to assist with this)
2. [Where appropriate] in the Reading Rooms and on IE within the IN domain

While issues remain, iterate.

---

## Lessons learned

Everything we build provides opportunities to for improvement to our processes and approach. By documenting the lessons learned and considering their implications for this development guide, we can understand the root cause of any problems as well as any opportunities for improvement.
Questions to consider

* What worked well either for this project or for the team?
* What didn't work well?
* What surprises did the team have to deal with?
* What would you do differently if given the chance to begin this project again

### Having considered these questions, what are the key lessons to take forward for future projects?
