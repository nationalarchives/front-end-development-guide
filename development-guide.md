![The National Archives logo](/images/tna.jpg "The National Archives logo")

# Development guide

## Introduction: 

### A progressive enhancement approach

In acknowledgement of the web's inherent variability this development guide describes an approach based on the principle of progressive enhancement. This approach is in line with [Service Manual guidance](https://www.gov.uk/service-manual/technology/using-progressive-enhancement). In practice this means building the interface of a website or application in layers:
 
* If the user’s browser only supports HTML they get content and the abilities to navigate and interact using forms. 
* If the user’s browser also supports CSS the application looks better. 
* If it can run JavaScript (and/or supports newer technologies colloquially known as _HTML5_ and _ESNext_) the experience will be enhanced by those capabilities. 

The important points for developers to recognise are that:
* **only the core HTML is required to meet users’ basic needs**, and; 
* CSS, JavaScript and HTML5 APIs should be applied in such a way that they do not 'break' the experience for those clients that cannot support them.

Progressive enhancement sometimes confuses developers who are unfamiliar with the approach: misconceptions like _"No users actually turn off JavaScript?"_ or _"So I can't use JavaScript?"_ are common responses. A full explanation of the benefits of progressive enhancement is beyond the scope of this guidance, but here are some resources to help new developers appreciate and communicate the value of progressive enhancement: 

* the [Progressive enhancement at The National Archives](supporting_material/progressive_enhancement_at_tna.pdf) slide deck
* [Why we use progressive enhancement to build GOV.UK](https://gdstechnology.blog.gov.uk/2016/09/19/why-we-use-progressive-enhancement-to-build-gov-uk/) by Government Digital Services
* the [Everyone has JavaScript, right?](https://kryogenix.org/code/browser/everyonehasjs.html) site which describes several scenarios that might result in your JavaScript not running
* Jeremy Keith's [Resilience: Building a Robust Web That Lasts](https://aneventapart.com/news/post/resilience-building-a-robust-web-that-lasts-jeremy-keith-an-event-apart) from An Event Apart 2018
* the book [Adaptive Web Design](https://adaptivewebdesign.info/2nd-edition/) by Aaron Gustafson
* the talk [Inclusive forms](https://obyford.com/posts/inclusive-forms/) by Ollie Byford

## Frontend libraries and frameworks we use

![jQuery logo](/images/jquery-logo.jpg "jQuery logo") ![React logo](/images/react-logo.jpg "React logo") ![Sass logo](/images/sass-logo.jpg "Sass logo") ![D3 logo](/images/d3-logo.jpg "Sass logo")

In July 2020 front end developers met to review the front end technologies we use. This included: an honest discussion about how well our current front end approach meets our needs, and; reviewing industry trends to assess if there are new approaches we might benefit from.

At the time of this review we had been using:

* [jQuery](https://jquery.com) for simple DOM abstraction and progressive enhancements involving JavaScript
* [React](https://reactjs.org) where a more involved and/or stateful component is required
* [SASS](https://sass-lang.com) as a CSS extension language
* [D3](https://d3js.org) to build bespoke dynamic JavaScript visualisations 
 
These remain the leading frameworks in their space: Sass is by far the most mature, stable and popular CSS extension; D3 is the leading library for creating bespoke visualisations; and React and jQuery are the leading client-side JavaScript libraries:
 
<blockquote cite="https://insights.stackoverflow.com/survey/2020#technology-programming-scripting-and-markup-languages-all-respondents">
    <p>When focusing purely on web frameworks, we see that jQuery is still king, but is slowly losing ground to React.js and Angular year over year. We do see some consolidation, as more than 35% of respondents use jQuery, React, a version of Angular (combining Angular, which represents Angular 2+, and Angular.js) or a flavor of ASP.NET (ASP.NET or ASP.NET Core).
</p>
    <footer><a href="https://insights.stackoverflow.com/survey/2020#technology-programming-scripting-and-markup-languages-all-respondents"><cite>Stack Overflow - 2020 developer survey (Web Frameworks)</cite></a></footer>
</blockquote> 

There was broad consensus that these technologies are a good fit for the team and will help us meet challenges ahead. We have decided to continue using these technologies for The National Archives' new online platform.

### How we use these frameworks

During the review it was clear that there are varying levels of confidence with these frameworks. Some developers have less confidence with React, and the team as a whole has only recently started learning and working with D3. With this in mind developers have been asked to identify and undertake any additional learning they require to be comfortable working across these frameworks. 

As we move forward with these technologies we want to ensure there is a level playing field going forward and avoid the tendency for any one individual to become a single-point-of-failure. In support of this, developers have been asked to ensure:
 
* these frameworks are used with consideration for 'the next developer', avoiding unnecessary complexity
* they actively avoid esoteric and/or emerging features **without first securing the buy in of all other developers**.

### An emphasis on accessibility

Developers will also notice an emphasis upon accessibility throughout this guide. This reflects the [legal duty to ensure our services are accessible to users](https://www.gov.uk/guidance/accessibility-requirements-for-public-sector-websites-and-apps#who-has-to-meet-the-2018-accessibility-regulations) which all developers should be aware of.

This requirement is also reflected in the [GDS Service Manual](https://www.gov.uk/service-manual/helping-people-to-use-your-service/making-your-service-accessible-an-introduction) and the [GDS Technology Code of Practice: Point 2](https://www.gov.uk/government/publications/technology-code-of-practice/technology-code-of-practice), which states departments **must**:

> Make sure your technology, infrastructure and systems are accessible for users.

You can read the detail of this requirement in the [guidance for Point 2](https://www.gov.uk/guidance/make-things-accessible)

### Services for Government users 

Most of us will have experienced the frustration resulting from using software that offers poor accessibilty or usability. Despite this there can be a tendency for development teams across the industry to pay less attention to accessibility and usability when developing tools for 'internal' use. GDS have provided clear [guidance for building or buying services for government](https://www.gov.uk/service-manual/design/services-for-government-users):

> Hold internal services to the same standard you would a public-facing service. This guidance covers services for government users, whether you’re building them yourself or buying them.

This guidance also describes the need to ensure accessibility:

> As of 2017, 9.9% of civil servants who declared their disability status were disabled. It’s crucial that your service is fully accessible.

## Checkpoint 1: Coding standards

This guide has a focus on the HTML, CSS and JavaScript code that is delivered to a user's browser and related client-side architectural considerations.

### Client-side architectural considerations

The [Resource Oriented Client Architecture](http://roca-style.org/) describes a number of recommendations that should be reflected in the applications we produce, as appropriate. Some key considerations which are not represented elsewhere in this guide are:

* All [application logic](http://roca-style.org/#application-logic) resides on the server
* A user must be able to [link to a specific piece of information](http://roca-style.org/#link)
* Browser ['back' and 'forward' buttons](http://roca-style.org/#browser-controls) should work as expected. There is a recommendation related to this regarding the [History API](http://roca-style.org/#historyapi). GDS also recommend including 'back' links, as some users do not trust their browser's back buttons.
* All [JavaScript and CSS code must be static](http://roca-style.org/#static-assets), and must not be dynamically generated by the server in a form specific to the resource requested. (Note that this does not prohibit the use of preprocessors like Babel or SASS, as the respective code is usually pre-compiled as part of the deployment process).

### Security considerations for front-end development 

Development decisions can have significant reputational and financial implications for an organisation. Developers have a responsibility to ensure their code is sufficiently secure and provides adequate protection for assets. Developers should consider the security implications of all development choices and, where there is doubt, approach a senior or lead developer for advice. Concerns that are of particular importance for front-end development are: 

* The need to _sanitize_ and _validate_ input, and _escape_ output:
    * *Sanitize* refers to escaping or removing unsafe characters from input data before it reaches an application storage layer
    * *Validate* refers to ensuring the received data matches expectations
    * *Escape* refers to preventing malicious code from being rendered and inadvertently executed by application users
    
* Recognition that client-side technologies alone are insufficient to protect against malicious behaviour (for example, client-side form validation must be accompanied by server-side validation)
* Recognition that any resources sent to a browser can be saved by users. For example, relying on CSS or JavaScript to obfuscate an image or prevent 'Save as' behaviour is not sufficient.

## Checkpoint 2: We meet needs using HTML

### General HTML principles
There are a few principles which we follow for all HTML we produce. The code review will check that:

1. HTML5 Document type is used and the ```<html>``` tag includes an appropriate ```'lang'``` attribute (typically ```en```)
2. HTML validates (W3C validation tool options include http://validator.w3.org/ or the newer, but still experimental - as of July 2020 - http://validator.w3.org/nu/)
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

HTML outlines are an important means for navigating pages with assistive technologies. All digital services we produce should have a logical document outline with one ```<h1>``` tag, and each subsequent ```<h*>``` serving to 'section' the content below it.

**Please note: sectioning elements should not be relied upon for outlining** because the HTML5 outlining algorithm is not implemented in _any_ graphical browsers or assistive technology user agents. As MDN explains: 

> There are no implementations of the proposed outline algorithm in web browsers nor assistive technology; it was never part of a final W3C specification. Therefore the outline algorithm should not be used to convey document structure to users. Authors are advised to use heading rank (h1-h6) to convey document structure. [Using HTML sections and outlines, MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_HTML_sections_and_outlines) 




The peer review will check that:

1. The HTML outline is logical and based on an appropriate, sequentially descending heading structure
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

We ensure our forms are **accessible**, **usable** and make best use of HTML5 and ARIA semantics. The code review will check that:

1. Forms are fully accessible via keyboard alone
2. Forms are logically organised
3. Instructions (such as required fields) and other cues are clearly identified to users and expressed through semantics
4. Where appropriate, ```<fieldset>``` is used to group related inputs and ```<legend>``` is used to describe these groupings. Note: when forms use the pattern of presenting one question at a time to the user, include the `<h1>` element inside of `<legend>` tag. If no `<legend>` exists, where appropriate, include the form field's `<label>` element inside of the `<h1>`. This prevents screen readers reading out the question multiple times.
5. Form elements are appropriately labelled, with labels having a ```'for'``` attribute linking them to the corresponding input (we don't tend to nest inputs in label elements)
6. Appropriate use is made of HTML5 form semantics (i.e. ```<input type="tel" />```) so that user agents can assist users with an appropriate input mechanism
7. Good use is made of appropriate ARIA landmark roles in conjunction with form semantics (For example, ```<form role="search"><input type="search" />...</form>```)
8. HTML5 form validation is used, supported by JavaScript validation for older browsers. This is covered in the JavaScript section of this document
9. Error messages are clearly visible and associated (both visually and within the DOM) to the corresponding input. This includes: appropriate use of ARIA attributes; including `Error:` in the `<title>` tag; adding `Error:` `<span>` elements to labels of erroring inputs
10. Date fields are appropriately implemented. DD/MM/YYYY text inputs take precedence over datepickers. An example of a valid date should be provided (i.e. 01/12/2020) and the user's browser focus should not automatically move between the day, month, and year boxes.
12. Where appropriate, allow users to check their answers before submitting the form. Display clear confirmation once the form is submitted, and provide next steps. 

---

### Tables

Where appropriate, tabular data is placed in HTML ```<table>``` elements. Do not use tables for layout and avoid re-purposing other elements to recreate table-like representations of data. WebAIM provide guidance on ensuring tables are accessible

The code review should check that:	

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

A related resource is [tips for creating accessible SVG](http://www.sitepoint.com/tips-accessible-svg/), by Leonie Watson  

---

### Images

Decorative images should be implemented using the CSS `background-image` property, so that assistive technologies can ignore the images. If a decorative image must be implemented using the HTML `<img>` element, you should ensure that:
 
 - The element's `title` attribute is either absent or empty. 
 - The element's `alt` attribute is empty (`alt=""`). 
 - The element's `role` attribute is set to presentation (`role="presentation"`).
 
For more information, see:

1. [W3C's decorative images tutorial.](https://www.w3.org/WAI/tutorials/images/decorative/)
2. [W3C's specification.](https://www.w3.org/TR/WCAG20-TECHS/H67.html)

Where appropriate and practical we do make use of the incoming `srcset` attribute on `<img>` elements.

---

### `<a>` buttons

`<a>` tags can be styled to look like buttons. These are used to mimic the look of `<button>` and `<input type="submit">` elements when directing users to another page. When using these, it is important to:

- Ensure these elements have the `role="button"` attribute. This allows users of assisstive technologies to say for example "Click the _help_ button."
- Ensure these elements have the `draggable="false"` attribute. This prevents users with motor conditions from dragging the button by accident when they are trying to click on it.
- Use JavaScript to allow users to interact with `<a>` buttons using the spacebar. See the [GDS implementation](https://github.com/alphagov/govuk-frontend/blob/master/src/govuk/components/button/button.js) as an example.

---

### There is good use of appropriate ARIA roles to support native semantics

While HTML5 provides a range of new semantic elements which are recognised by newer browsers, there is poor support (even in newer browsers) when it comes to reporting these elements to the Accessibility API. This, and the lack of semantics when these elements are polyfilled with JavaScript, makes ARIA an important tool. Because the HTML5 spec was updated in mid-2014 to indicate compatibility between elements and ARIA roles, developers can see the compatibility of an element with ARIA roles, states and properties by looking up the tag within the [HTML5 specification](https://html.spec.whatwg.org).

Because we are focused in Checkpoint 1 on the HTML delivered to the user's browser, developers should ensure that **all relevant static ARIA roles have been applied (these being landmark, region, and speciality roles)** as well as *any* relevant pseudo interactive roles (such as dialog). See ARIA role conformance matrices or ask a fellow developer for guidance if needed. At this stage it can be very helpful to think about the four 'rules of using ARIA in HTML' from [W3C notes on ARIA use in HTML](https://www.w3.org/TR/2015/WD-aria-in-html-20150521/#notes-on-aria-use-in-html): 

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
7. Hacks for other browsers are placed in a 'shame.css' file

---

### User focus is clearly visible

It is important to ensure interactive elements have a distinct visual appearance when activated. The peer review will check that all interactive elements have a clearly differentiated visual appearance when they have focus (this can typically be achieved using ```:focus```)

---

### SASS guidelines

As we more routinely incorporate CSS-preprocessing into our workflow we need to ensure our approach is maintainable (so that future developers understand the code we're writing today) and as simple as possible. Some useful insights are provided at [SASS guidelines](http://sass-guidelin.es) but developers will need to exercise judgement about what is most appropriate in the specific circumstances. A useful principle to bear in mind (from the SASS guidelines) is that: 

> ... CSS is a simple language. Sass, being intended to write CSS, should not get much more complex than regular CSS. The KISS principle (Keep It Simple Stupid) is key here and may even take precedence over the DRY principle (Don’t Repeat Yourself) in some circumstances.

> Sometimes, it’s better to repeat a little to keep the code maintainable, rather than building a top-heavy, unwieldy, unnecessarily complicated system that is completely unmaintainable because it is overly complex.

### SASS/CSS formatting standards

To ensure consistency across developers and assist with the maintainability of our code base we adopt a number of general CSS code formatting standards. The code review will check that:

1. Code blocks have consistent indentation to reflect their hierarchy
2. Rules are separated with new lines
3. All rules are closed with a semicolon

---

### Print CSS

We need to ensure we have accounted for users printing our content. While modern browsers provide a facility to emulate and debug print from within Developer Tools, we have encountered issues where IE prints differently to other browsers. Where relevant and appropriate, the code review will check that:

1. The printed page is well formatted, with legible content
2. The printed page does not include unnecessary components like decorative images and form elements.
3. The printed page includes full hyperlink destinations (appending our domain where they are relative)
4. Print specific styles are contained within in a ```@media = print``` block

---

### CSS Colours & Shapes

We need to ensure that colour contrasts meet the [WCAG 2.1 AA Contrast (Minimum) criterion](https://www.w3.org/TR/WCAG21/#contrast-minimum). This means that colour contrasts between the background/foreground of elements must be a minimum of 4.5:1. 

It is also important to note that if a user changes the page colours using their browser, it will change border colours to the same colour as the page's text colour. In this scenario, transparent borders are also modified to match the page's text colour. Therefore relying on CSS to display shapes (i.e. triangles) may not be appropriate, and patching this with `clip-path` is not supported on IE11.

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

Please speak to the Lead Frontend Developer if you need guidance on meeting any of these requirements.

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
At the time of writing (July 2020) this reveals **61** cross browser bugs being managed in the current version of jQuery .  While many of cross-browser bugs are traditionally related to older browsers there are many fixes in these libraries tackling inconsistencies where you might not expect them.

**We therefore use only established frameworks for managing complex interactions with the DOM**. If you are unsure about any of this please speak to the Lead Front End Developer.

---

### Accessibility is a primary concern when using JavaScript to introduce rich interactions

It is essential that we consider the implications for users of assistive technologies when:
 
* Writing JavaScript to provide rich interactions
* Reviewing third-party code that provide non-standard user interface elements.
 
This will include:

* Ensuring that suitable ARIA role and state management is provided
* Ensuring the third-party code does not make the DOM inaccessible (the overwhelming majority of assistive technology users will have JavaScript enabled)

We should not use third-party code which does not provide suitable ARIA role and state management, unless they are available for open source contribution and we have the skills and resources to extend them in line with the WAI-ARIA authoring practices.

---

### JavaScript form validation

We provide JavaScript validation for user agents that do not support HTML5.

---

## Checkpoint 5: pre-release checks

### Release version is WCAG 2.1 compliant at AA

To ensure we meet our [legal duty to ensure our services are accessible to users](https://www.gov.uk/guidance/accessibility-requirements-for-public-sector-websites-and-apps#who-has-to-meet-the-2018-accessibility-regulations) the code reviewer will:

1. Check compliance with the Web Content Accessibility Guidelines (WCAG 2.1) using the [W3C Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/?currentsidebar=%23col_overview&levels=aaa&technologies=smil%2Cflash%2Csl) and an automated tool such as [Google Lighthouse](https://developers.google.com/web/tools/lighthouse) or [WAVE](https://wave.webaim.org)
2. Ensure the site remains accessible in the event that JavaScript and CSS are not available
3. Take a broad view of accessibility considerations that may be relevant, paying particular attention to ensuring we have done all that is possible to make things as accessible as possible. Resources to help with this judgement include:
    * the [Understanding disabilities and impairments: user profiles](https://www.gov.uk/government/publications/understanding-disabilities-and-impairments-user-profiles) by GDS
    * the (now archived) [BBC case studies](http://www.bbc.co.uk/accessibility/best_practice/case_studies) that illustrate how users with different abilities adapt the way they use the web
    * an [Alphabet of Accessibility Issues](https://the-pastry-box-project.net/anne-gibson/2014-july-31) to consider how the implementation will meet the needs described.

<mark>**Before** any code from a feature branch is merged the reviewer should be satisfied that:</mark>

1. Code is WCAG 2.1 compliant at AA, including appropriate use and management of ARIA roles and states
2. We have considered a broad range of different abilities
3. The service is accessible and usable without JavaScript and/or CSS

#### Useful tools for accessibility testing:
In addition to the [W3C Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/?currentsidebar=%23col_overview&levels=aaa&technologies=smil%2Cflash%2Csl) tools that may be useful are the: 

* [Google Lighthouse](https://developers.google.com/web/tools/lighthouse)
* The Web Accessibility Evaluation Tool [(WAVE)](https://wave.webaim.org)
* [aXe Chrome Extension ](https://chrome.google.com/webstore/detail/axe/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US) which provides a developer tools panel that allows you to run an in-browser audit against a page, including a colour and contrast check. The extension features are described on the [Google Chrome Developers channel on YouTube](https://youtu.be/cOmehxAU_4s?t=8m58s)

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
