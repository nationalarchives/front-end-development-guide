# Development guide

## Introduction: 

### A progressive enhancement approach

In acknowledgement of the web's inherent variability this development guide describes an approach based on the principle of progressive enhancement. In practice this means building the interface of a website or application in layers:
 
* If the user’s browser only supports HTML they get content and the abilities to navigate and interact using forms. 
* If the user’s browser also supports CSS the application looks better. 
* If it can run JavaScript (and/or supports newer technologies colloquially known as _HTML5_ and _ESNext_) the experience will be enhanced by those capabilities. 

The important points are that:
* **only the core HTML is required to meet users’ basic needs**, and; 
* CSS, JavaScript and JavaScript APIs should be applied in such a way that they do not 'break' the experience for those clients that cannot support them.

Here are some resources to help new developers appreciate and communicate the value of progressive enhancement: 

* the [Progressive enhancement at The National Archives](supporting_material/progressive_enhancement_at_tna.pdf) slide deck
* [Why we use progressive enhancement to build GOV.UK](https://gdstechnology.blog.gov.uk/2016/09/19/why-we-use-progressive-enhancement-to-build-gov-uk/) by Government Digital Services
* the [Everyone has JavaScript, right?](https://kryogenix.org/code/browser/everyonehasjs.html) site which describes several scenarios that might result in your JavaScript not running
* Jeremy Keith's [Resilience: Building a Robust Web That Lasts](https://aneventapart.com/news/post/resilience-building-a-robust-web-that-lasts-jeremy-keith-an-event-apart) from An Event Apart 2018
* The book [Adaptive Web Design](https://adaptivewebdesign.info/2nd-edition/) by Aaron Gustafson


### An emphasis on accessibility

Developers will also notice an emphasis upon accessibility throughout this guide. This is intentional and reflects the central importance of ensuring our services are accessible to users. This position is also reflected in the [GDS Service Manual](https://www.gov.uk/service-manual/helping-people-to-use-your-service/making-your-service-accessible-an-introduction) and the [GDS Technology Code of Practice: Point 2](https://www.gov.uk/government/publications/technology-code-of-practice/technology-code-of-practice), which states departments **must**:

> Make sure your technology, infrastructure and systems are accessible for users.

You can read the detail of this requirement in the [guidance for Point 2](https://www.gov.uk/guidance/make-things-accessible)

### Moving towards a component mindset

On 12 September 2018, front end developers at The National Archives met to discuss ways we might be able to work more effectively across the broad range of applications we support. Primary concerns were: 

* Ensuring consistency of changes across multiple teams, applications and platforms
* Establishing a 'single source of truth' for functionality, design, shared content and implementation across services
* Avoiding duplication of effort when implementing a change

Having considered some options we have opted to start implementing new functionality that is shared across multiple services as components that will reside on - and be referenced directly from - our CDN. Where these are JavaScript components, develops must ensure that: 

* users' basic user needs are still met if the component is unavailable for any reason (See 'A progressive enhancement approach' section)
* the relevant product owner is aware of any implementation choices and how these relate to GDS guidance

Further detail about the approach and implementation can be found in [tna-components](https://github.com/nationalarchives/tna-components) which acts as **the sole repository** for components that are to be used across environments.

### Some key points about components

#### How to determine if a feature is an appropriate candidate for implementation as a component

There are a number of questions that developers should use to determine whether the component approach is suitable for a specific feature. These include: 

* Is it a feature that is - or is likely to be - implemented across multiple applications and stacks? If so, it may be a candidate for componentization. If not, it probably isn't.
* On balance, does the development of a component help us over the short- medium- and long-term.
* To what extent will the component be replicating functionality that will also exist in the server-rendered code? If it is essentially the same, it may be that the server-rendered code alone will suffice (subject to the impact on user experience, of course)

#### ⚠️ Speak to the Lead Front End Developer _before_ embarking on creating a component

This will help ensure we have a consistent approach and to allow developers to get a view on how best we might approach the feature as well as get a view on any potential pitfalls. 

#### ⚠️ Not all JavaScript should be written as a component

The move to a component mindset does not mean that all JavaScript features will be implements as React components, or that all new features should be implemented in React. There is a place for vanilla JavaScript and jQuery.

### Services for Government users 

Most of us will have experienced the frustration resulting from using software that offers poor accessibilty or usability. Despite this there can be a tendency for development teams across the industry to pay less attention to accessibility and usability when developing tools for 'internal' use. GDS have provided clear [guidance for building or buying services for government](https://www.gov.uk/service-manual/design/services-for-government-users):

> Hold internal services to the same standard you would a public-facing service. This guidance covers services for government users, whether you’re building them yourself or buying them.

This guidance also describes the need to ensure accessibility:

> As of 2017, 9.9% of civil servants who declared their disability status were disabled. It’s crucial that your service is fully accessible.

## Checkpoint 1: Coding standards

This guide has a focus on the HTML, CSS and JavaScript code that is delivered to a user's browser and related client-side architectural considerations. Broader development guidance includes:

* [Git workflows and branching strategies](version_control)
* [Server-side coding standards](server_side_coding_standards)

### Client-side architectural considerations

The [Resource Oriented Client Architecture](http://roca-style.org/) describes a number of recommendations that should be reflected in the applications we produce, as appropriate. Some key considerations which are not represented elsewhere in this guide are:

* All [application logic](http://roca-style.org/#application-logic) resides on the server
* A user must be able to [link to a specific piece of information](http://roca-style.org/#link)
* Browser ['back' and 'forward' buttons](http://roca-style.org/#browser-controls) should work as expected. There is a recommendation related to this regarding the [History API](http://roca-style.org/#historyapi)
* All [JavaScript and CSS code must be static](http://roca-style.org/#static-assets), and must not be dynamically generated by the server in a form specific to the resource requested. (Note that this does not prohibit the use of preprocessors like Babel or SASS, as the respective code is usually pre-compiled as part of the release process.)

### Security considerations for front-end development 

Development decisions can have significant reputational and financial implications for an organisation. Developers have a responsibility to ensure their code is sufficiently secure and provides adequate protection for assets. Developers should consider the security implications of all development choices and, where there is doubt, approach a senior or lead developer for advice. Concerns that are of particular importance for front-end development are: 

* The need to _sanitize_ and _validate_ input, and _escape_ output:
    * *Sanitize* refers to escaping or removing unsafe characters from input data before it reaches an application storage layer
    * *Validate* refers to ensuring the received data matches expectations
    * *Escape* refers to preventing malicious code from being rendered and inadvertently executed by application users
    
* Recognition that client-side technologies alone are insufficient to protect against malicious behaviour (for example, client-side form validation must be accompanied by server-side validation)
* Recognition that resources sent to a browser can be obtained by users (for example, relying on CSS or JavaScript to obfuscate an image is not sufficient).

## Checkpoint 2: We meet needs using HTML

### General HTML principles
There are a few principles which we follow for all HTML we produce. The peer review will check that:

1. HTML5 Document type is used and the ```<html>``` tag includes an appropriate ```'lang'``` attribute (typically ```en```)
2. HTML validates (W3C validation tool options include http://validator.w3.org/ or the newer, but still experimental - as of September 2018 - http://validator.w3.org/nu/)
3. The ```<title>``` tag is present and follows pattern ```{h1} - The National Archives```
4. Source code is properly indented to reflect its structure

---

### HTML5 syntax style

HTML5 has considerably relaxed the syntax rules for HTML. To ensure consistency across projects we have agreed upon a house syntax style. The peer review will check that:

1. [Optional tags](http://www.w3.org/TR/html5/syntax.html#optional-tags) are used
2. All tags are closed, even where HTML5 might allow them not to be (as is the case for ```<li>``` and ```<p>``` tags)
3. Full attribute syntax is used and all attributes are quoted. See the W3C description of [quoted attribute syntax](http://www.w3.org/TR/html-markup/syntax.html#syntax-attributes)
4. All tag names and attributes are in lower case

---

### There is an appropriate HTML outline

HTML outlines are an important means for navigating pages with assistive technologies. All digital services we produce should have a logical document outline with one ```<h1>``` tag, and each subsequent ```<h*>``` serving to 'section' the content below it. Because - as of December 2017 - the HTML5 outlining algorithm is not implemented in _any_ graphical browsers or assistive technology user agents, **we do not rely on HTML5 sectioning elements for outlines**.

The peer review will check that:

1. The HTML outline is logical and based on an appropriate heading structure
2. All content appears in the correct part of the outline

---

### Appropriate semantics are used

We use HTML elements for their intended purpose, ensuring valid semantics wherever possible. We do use HTML5 sectioning element semantics (```<section>```, ```<article>```, ```<nav>```, ```<aside>```), but do so with care and avoid using them for document outlining.

We use WAI-ARIA landmark roles (```application, banner, complementary, contentinfo, form, main, navigation, search```) and a traditional document outline for structuring documents. The peer review will check that:

1. There should be one `<main>` element and `role=main` should be applied for compatibility with older browsers.
2. HTML5 sectioning elements are used for semantics not structure
3. HTML5 sectioning elements are not over used in place of ```<div>``` elements
4. All relevant WAI-ARIA landmarks have been applied

Note: Developers should use `role="application"` with caution as it signals to screen reading software to turn off normal web navigation controls. Refer to [W3C guidance](https://www.w3.org/TR/aria-in-html/#using-application).

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
10. When forms are presenting one question at a time to the user, include the `<h1>` element inside of `<legend>` tag. If no `<legend>` exists, where appropriate, include the form field's `<label>` element inside of the `<h1>`. This prevents screen readers reading out the question multiple times.

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

Decorative images should be implemented using the CSS `background-image` property, so that assistive technologies can ignore the images. If a decorative image must be implemented using the HTML `<img>` element, you must ensure that:
 
 - The element's `title` attribute is either absent or empty. 
 - The element's `alt` attribute is empty (`alt=""`). 
 - The element's `role` attribute is set to presentation (`role="presentation"`).
 
For more information, see:

1. [W3C's decorative images tutorial.](https://www.w3.org/WAI/tutorials/images/decorative/)
2. [W3C's specification.](https://www.w3.org/TR/WCAG20-TECHS/H67.html)

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

As we more routinely incorporate CSS-preprocessing into our workflow we need to ensure our approach is maintainable (so that future developers understand the code we're writing today) and as simple as possible. Some useful insights are provided at [SASS guidelines](http://sass-guidelin.es) but developers will need to exercise judgement about what is most appropriate in the specific circumstances. A useful principle to bear in mind (from the SASS guidelines) is that: 

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

### Transpiling new versions of ECMAScript to natively supported JavaScript

New releases of the ECMAScript are expected to be released every year from now on with versions being referred to by their publication year (ES2017, for example). While Firefox, Chrome, Edge and Safari offer good (over 96%) compliance with the ECMAScript 6 (ES6) specification, the use of a transpiler - such as BabelJS - remains essential for developers seeking to use any language feature beyond those available to the browsers we support. At the time of writing this is ES3.
 
 Developers are encouraged to make use of the benefits provided by newer language features provided that usage is via a local build system (such as Webpack and Babel) which creates an output file that can be interpreted natively by supported browsers. Do not deliver unsupported code to the browser and rely upon including a script to transpile in the browser (these tools do exist but are intended for prototyping purposes only).

### General JavaScript principles

There are a few principles which we follow for all JavaScript development. The peer review will check that:

1. JavaScript is logically organised and, where necessary, well commented to aid understanding
2. JavaScript is well formatted with consistent indentation
3. JavaScript does not cause any errors (including tests across older IE which do not support ECMAScript 5)
4. JavaScript is externalised into .js files. We do not place JavaScript in ```<script>``` tags or use native inline event handling (i.e. ```<a href="#" onclick="triggerAlert('Bad practice!'); return false;">Joe</a>```)
5. JavaScript is minified and concatenated where possible
6. JavaScript dependent elements are created with JavaScript. For example, if a ```<button>``` is used to perform a JavaScript action only, that button should be created with JavaScript
7. Any DOM manipulation performed by JavaScript is accompanied by the application and management of relevant ARIA roles, states and properties. These should build upon the static and pseudo interactive roles applied during Checkpoint 2.
8. Server-side processing is used to ensure JavaScript is loaded only where needed

Relevant resources include: 

* [Writing JavaScript with accessibility in mind](https://medium.com/@matuzo/writing-javascript-with-accessibility-in-mind-a1f6a5f467b9)

Please speak to the Lead Front-end Developer if you need guidance on meeting any of these requirements.

---

### JavaScript Testing

JavaScript and jQuery code is tested using well established testing tools. Tools currently in use include [Jest](https://jestjs.io), [QUnit](https://qunitjs.com/), [Jasmine](https://jasmine.github.io) and [Mocha](https://mochajs.org). We are open to exploring other options but please discuss this with all team members so that we can be considered and surefooted in our adoption of new tools.

---

### We use established libraries for DOM abstraction

Established libraries such as jQuery, Angular and ReactJS provide an excellent means of managing the complexity of DOM manipulation across browsers and devices. Attempting all but the simplest DOM manipulation without a 'battle tested' framework needlessly exposes us to a large number of cross-browser bugs and inconsistencies.

In our experience many newer developers are unaware of this. To demonstrate, you can find out the number of cross browser bugs being addressed in the current version of jQuery (which has long since dropped support for older IE), for example, with 

```bash
curl -L https://code.jquery.com/jquery-git2.js | grep Support: | wc -l
```
At the time of writing this reveals **109** cross browser bugs being managed in the current version of jQuery .  While many of cross-browser bugs are traditionally related to older browsers there are many fixes in these libraries tackling inconsistencies where you might not expect them.

**We therefore use only established frameworks for managing complex interactions with the DOM**. If you are unsure about any of this please speak to the Lead Front End Developer.

---

### Accessibility is a primary concern when using JavaScript to introduce rich interactions

It is essential that we consider the implications for users of assistive technologies when:
 
* Writing JavaScript to provide rich interactions
* Reviewing third-party plugins that provide non-standard user interface elements.
 
This will include:

* Ensuring that suitable ARIA role and state management is provided
* Ensuring the plug-in does not make the DOM inaccessible (the overwhelming majority of assistive technology users are likely to have JavaScript enabled)

We should not use plug-ins that do not provide suitable ARIA role and state management, unless they are available for open source contribution and we have the skills and resources to extend them in line with the WAI-ARIA authoring practices9.

For this reason, jQueryUI presents a good tool as its authors have worked hard to include the necessary ARIA role and state management in the library components. Nonetheless, we should test the accessibility of custom widgets before they are used.

---

### JavaScript form validation

We provide JavaScript validation for user agents that do not support HTML5.

---

## Checkpoint 5: pre-release checks

### Release version is WCAG 2.0 compliant at AA

The peer reviewer will:

1. Check compliance with the Web Content Accessibility Guidelines (WCAG 2.0) using the [W3C Quick Reference](https://www.w3.org/WAI/WCAG20/quickref/)
2. Ensure the site remains accessible in the event that JavaScript and CSS are not available
3. Take a broad view of accessibility considerations that may be relevant, paying particular attention to ensuring we have done all that is possible to make things as accessible as possible. Resources to help with this judgement include:
    * the [Understanding disabilities and impairments: user profiles](https://www.gov.uk/government/publications/understanding-disabilities-and-impairments-user-profilesdis) by GDS
    * the (now archived) [BBC case studies](http://www.bbc.co.uk/accessibility/best_practice/case_studies) that illustrate how users with different abilities adapt the way they use the web
    * an [Alphabet of Accessibility Issues](https://the-pastry-box-project.net/anne-gibson/2014-july-31) to consider how the implementation will meet the needs described.

<mark>**Before** any code from a feature branch is merged the peer reviewer should be satisfied that:</mark>

1. Code is WCAG compliant at AA, including appropriate use and management of ARIA roles and states
2. We have considered a broad range of different abilities
3. The service is accessible and usable without JavaScript and/or CSS

#### Useful tools for accessibility testing:
In addition to the [W3C Quick Reference](https://www.w3.org/WAI/WCAG20/quickref/) tools that may be useful are the: 

* [aXe Chrome Extension ](https://chrome.google.com/webstore/detail/axe/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US) which provides a developer tools panel that allows you to run an in-browser audit against a page, including a colour and contrast check. The extension features are described on the [Google Chrome Developers channel on YouTube](https://youtu.be/cOmehxAU_4s?t=8m58s)
* [Chrome accessibility Developer Tools](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?utm_source=gmail). This does many of the same things as the aXe extension but also provides colour suggestions where contrast issues are found. This is also described on the [Google Chrome Developers channel on YouTube](https://youtu.be/cOmehxAU_4s?t=10m6s)

---

### Testing user goals across browsers, devices and contexts

The Service Manual provides clear guidance on cross Operating System and browser compatibility:
 
 > Your service must be universally accessible. This means building it to work on every browser or device that your users access it on ([GDS Service Manual](https://www.gov.uk/service-manual/technology/designing-for-different-browsers-and-devices#browsers-to-test-in))
 
 The Service Manual also describes a number of Operating Systems and browsers that service team developers are expected to test in to ensure their service is __'compliant'__. In this context, 'compliant' means a service **must look as good as it does in other modern browsers** (Note: this does not mean it should be visually identical). For all other browsers the service must be usable. 

At this point developers might ask how far back we are expected to support Internet Explorer on Windows. Check the most current information at the time of development but, in June 2018, [GDS announced](https://gdstechnology.blog.gov.uk/2018/06/26/changing-our-testing-requirements-for-internet-explorer-8-9-and-10/) that service team developers no longer needed to test on Internet Explorer 8, 9 and 10.

#### Government facing services

For government facing services the service manual states: 

> If you service is aimed at internal users rather than the general public you should use the browsers in the table [for public facing services] as a starting point then **use your own analytics data to decide an appropriate level of support**

#### Testing across contexts and conditions

The site/service should also be tested on:

1. a slow network connection (there are developer tools to assist with this)
2. [Where appropriate] in the Reading Rooms and on IE within the IN domain

While issues remain, iterate.

---
