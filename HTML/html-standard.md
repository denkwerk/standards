# denkwerk HTML Standards

## Coding Guidelines

Inspired by [Twitter Bootstrap](http://twitter.github.com/bootstrap/) and [Object Oriented CSS](https://github.com/stubbornella/oocss/wiki)

### Main Principles

**Patterns**  
Usage of well proven, self-explanatory patterns to align the development.

**Object Orientation**  
Separate structure and skin. Use classes to name objects and their components, rather than relying solely on the semantics of HTML.

**Code Flexiblility**

- Evident code modifiactons must be possible, e.g. adding sub elements, links, rich text formation
- CMS compatibility - the site content is not a fixed template 
- Fixed width and height should be avoided beyond the site container

## File System

- **root/css** for css documents
- **root/js** for javaScript files
- **root/js/libraries** for javaScript libraries
- **root/js/plugins** for javaScript plugins
- **root/images** for images and graphic elements 
- **root/images/content/size180x50** for content-images ordered in sub-files according to their dimensions
- **root/images/ico**/green**/size9x9** for icons in dimensional sub-files for css sprite-generation. When using GIF format for sprites additional color sub-files may be provided to enable a broader range of colors.
- **root/images/btn** as non-css3 fallback for editable button-graphics elements, constructed in sliding-doors technique
- **root/images/nav** for editable graphic menu-(navigation)-elements 
- **root/de/images/fr/images/nav** for non-editable language related elements containing graphic text.

## Formatting

- **Indenting** tabs (four spaces width)
- **HTML**
	- **block, table and table child-elements** new line, indented
	- **inline child-elements**	same line as parent element
- **CSS** 
	- **selectors (also multiple comma separated ones)** new line each
	- **property:value pairs** new line each, indented with terminating semicolon each

**CSS Comment examples:**

	/*
	 * Group comment block.
	 * Ideal for multi-line explanations and documentation.
	 */

	/* ==========================================================================
	   Section comment block
	   ========================================================================== */

	/* Sub-section comment block
	   ========================================================================== */

	/* Basic comment */

**SCSS Comment examples:**

	// ==========================================================================
	// Section comment block
	// ==========================================================================

	// Sub-section comment block
	// ==========================================================================

	//
	// Group comment block
	// Ideal for multi-line explanations and documentation.
	//

	// Basic comment

## Nomenclature

### File names

All file names must also be lowercase and words are divided by "-".

### Element- und Pseudo-Element Selectors

	h2
	:hover	

Lower case

### Class Attributes and Selectors

	.teaserpic-right 
	.subline

Lower case hyphenated

### ID-Attributes (only for JS, disapproved as CSS selectors!)

	#MainNav
	#MainContentCol

- Upper case with CamelCase 
- to address elements with javascript and for attributes in LABEL elements
- do not use as css selectors

### Recommended Nomenclature

	teaser-image, teaser-text

functionally motivated, generic

### Disapproved Nomenclature

- **customernameTeaser** too specific
- **float-left, text-bold** behavior and appearance motivated nomenclature only for differentiating purposes as addtl. classnames

## Stylesheets

- **Avoid** inline-style attributes
	<element style="property: value;">
- **Succession**
	1. **reset.css** fixed dw document for integration into all projects
	2. **grid.css** contains complete styles for area and grid divison of the page 
	3. **navigation.css** contains complete styles for all types of navigations; including main, sub (side), internal (tab) navigations
	4. **general.css** for all other modules 
	5. **print.css** embedding via LINK tag with *media="print"* attribute
- **Sibling Elements Margins and Paddings**
	- **Alignment** Except for H1 to the **top**: margin-top, preferably padding-top (due to different behavior of collapsing margins)
	- **Defining Exceptions to this**

		<pre><code>p:first-child,
		h1 + p,
		h1 + h2  {
    		padding-top:0;
		}
		</code></pre>

- **print.css begins with:**

	<pre><code>\* {
		overflow:visible !important;
		background:transparent !important; 
	}
	</code></pre>
	In addition: selectors for areas and elements which are to be hidden via *display:none;* or whose widths and font sizes are to be defined in *%* and *mm* or *pt* respectively instead of *px*.

### Colors

- **Recommended**
	- **#BD00FF, #A00, buttontext, scrollbar** as short as possible; hexadecimal or system-color names
- **Only to mark temporary status** 
	- **teal, white, etc.** for testing purposes during development

### Short Notation

- **Recommended**
	body {
  		font: normal 12px/1.25 "Courier New", Courier, monospace; 
	}
	.myBox { 
		border: solid 1px #F00;
		border-right-color: #A00;
		border-bottom: solid 2px #800;
	} 
- **Disapproved**
	body {
  		color: #333333;
  		font-size: 12px;
  		font-family: â€žCourier New";
  		line-height: 1.25em; 
	}
- **Only for overruling in combination with successor selector**
	.sidebar .myBox {
		border-top-style: solid; 
		border-top-width: 1px; 
		border-top-color: #F00;
		border-right-style: solid; 
		border-right-width: 1px; 
		border-right-color: #A00;
		border-bottom-style: solid; 
		border-bottom-width: 2px; 
		border-bottom-color: #800;
		border-left-style: solid; 
		border-left-width: 1px; 
		border-left-color: #F00;
	} 

### CSS Hacks

- **IE**
	.ie7 p {
    	padding-top: 1em;
	}
	.ie8 p,
	.ie9 p {
    	padding-top: 1.25em;
	}
- **Opera**
	@media all and (-webkit-min-device-pixel-ratio:10000), not all and (-webkit-min-device-pixel-ratio:0){ 
		head~body SELECTOR { 
			property: value; 
  		}
	}
- **safari, chrome, konqueror**
	@media screen and (-webkit-min-device-pixel-ratio:0) {
  		p { padding-top: 1.25em; }
	}

### SCSS

[SCSS](http://sass-lang.com/) is an extension of CSS3 which adds nested rules, variables, mixins, selector inheritance, and more. It makes your stylesheets easier to organize and maintain and generates well formatted CSS using the open-source CSS authoring framework [Compass](http://compass-style.org/).

#### Folder structure

- base
- config
- contents
- mixins
- partials
- patterns
- sprites
- widgets

**base** is the backbone of the stylesheet where well proven libraries like [Compass](http://compass-style.org/), [978 Grid System](http://978.gs/) are included. **config** contains all the project related configuration variables - definition of fonts, grid size, site dimensions and size levels for space, border, rounded corners and shadows. **contents** is used for content elements, each element has it's own scss file. The file names are identical to the HTML template and/or the template of a CMS like [TYPO3](http://www.typo3.org/) or [WordPress](http://wordpress.com/). **mixins** defines helper functions, which can be used in all scss files by *@include mixin-title(mixin-parameters);*. **partials** contains the site parts - global styles, header, footer and the main content area. **patterns** are bootstrap elements like headings, buttons and form elements that can either be integrated in the HTML template or selector inheritance in SCSS by *@extend .pattern-style;*. **sprites** definition see next paragraph. **widgets** contains the interactive elements of the project.

#### Sprites

[Compass Sprites](http://compass-style.org/reference/compass/utilities/sprites/) generate the sprite file and CSS classes automatically.  
Sprite images are integrated as :before or :after pseudo classes or if not possible - html elements (e.g. *span*). 

In SCSS, there is a **sprites** folder and a file for each sprite (e.g. *_icon.scss*) where images folder and configuration variables are defined. *$icon-sprite-dimensions: true;* is set to get the width and height dimensions in the CSS classes.

*Example:*

The sprite image folder *icon* contains a file *sample.png* (32x32px).  
Compass then generates the following style:

	.icon-sample {
		width: 32px;
		height: 32px;
		(...)
	}

#### StyleDocco

[StyleDocco](http://jacobrask.github.com/styledocco/) generates documentation and style guide documents from the stylesheets. 

Stylesheet comments will be parsed through Markdown and displayed in a generated HTML document. HTML code is written prefixed with 4 spaces or between code fences (```) in the comments, and StyleDocco shows a preview with the styles applied, and displays the example HTML code.

## Patterns

### Color pattern

Based on [Twitter Bootstrap Button colors](http://twitter.github.com/bootstrap/base-css.html#buttons)

- **default** (default value, e.g. white or gray color or background)
- **primary** (primary highlight color)
- **secondary** (secondary highligh color)
- **success** (success color, e.g. green)
- **warning** (warning color, e.g. orange)
- **danger** (danger color, e.g. red)
- **inverse** (alternate darken version of default)

### Size pattern

Based on font sizing

#### Main sizes

*Full written*

- **small** (small element size)
- **medium** (default element size)
- **large** (large element size)

#### Advanced sizes

*Shortened*

- **xs** (extra small)
- **xl** (extra large)
- **2xl** (double extra large)
- (...)

### Link pattern

- **default** (default link, e.g. text color)
- **primary** (primary link color)
- **go** (arrow to the right in front of the text)
- **back** (arrow to the left in front of the text)
- **close** (closing icon in front of the text)
- **info** (info icon in front of the text)
- **success** (success icon in front of the text)
- **warning** (warning icon in front of the text)
- **danger** (danger icon in front of the text)

*Examples:*

	<a href="link">Default link</a>
	<a href="link-primary">Primary link</a>
	<a href="link-go">Go link</a>
	<a href="link-back">Back link</a>
	<a href="link-close">Close link</a>

### Helper classes

#### Flip

Position inversion of child element(s)

- **flip-h** (horizontal)
- **flip-v** (vertical)

*Examples:*

	<div class="content-block flip-h">
		<h2>Content block heading with inverted position (e.g. right instead left)</h2>
		<p>Content block text with inverted position (e.g. right instead left)</p>
		<img src="(...)" title="Content block image with inverted position (e.g. left instead right)" alt="" />
	</div>

	<div class="content-bubble flip-v">
		<h3>Content message bubble with inverted position (e.g. edge top instead bottom) heading</h3>
		<p>Content message bubble text</p>
	</div>

## Responsive Web Development with Media Queries

### Media Query in a CSS file:
	@media only screen and (min-width: 600px) and (max-width: 799px) {...}
	
### Media Query in the head of a HTML file (preferred):
	<link rel="stylesheet" type="text/css" href="css/800.css" media="screen and (min-width: 600px) and (max-width: 799px)">

### For all browsers
	@media only screen and (min-width: 600px) and (max-width: 799px) {...}
	@media only screen and (min-width: 800px) {...}

### Device-specific (code example for all statements in ONE CSS file)
	/* iPhone 4 landscape */
	@media only screen and (max-device-width: 480px) and (-webkit-min-device-pixel-ratio: 2) and (orientation : landscape) {
	}
	/*iPhone 4 portrait*/
	@media only screen and (max-device-width: 320px) and (-webkit-min-device-pixel-ratio : 2) and (orientation : portrait) {
	}
	/*iPad 3 landscape*/
	@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio : 2) and (orientation : landscape) {
	}
	/*iPad 3 Hochfportraitormat*/
	@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio : 2) and (orientation : portrait) {
	}
	/*iPad 2 landscape*/
	@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) {
	}
	/*iPad 2 portrait*/
	@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) {
	}

### Further information about Medie Queries

#### SCSS files

It is recommended to create a separate (S)CSS file for every resolution. You can keep a much better overview of the project and allows you to make changes easier.
Code example for all statements in different CSS files:

	<link rel="stylesheet" type="text/css" href="css/screen.css" media="screen">
    <link rel="stylesheet" type="text/css" href="css/320.css" media="screen and (max-width: 479px)">
    <link rel="stylesheet" type="text/css" href="css/480.css" media="screen and (min-width: 480px) and (max-width: 767px)">
    <link rel="stylesheet" type="text/css" href="css/800.css" media="screen and (min-width: 768px) and (max-width: 999px)">
    <link rel="stylesheet" type="text/css" href="css/1024.css" media="screen and (min-width: 1000px) and (max-width: 1179px)">
	<link rel="stylesheet" type="text/css" href="css/1280.css" media="screen and (min-width: 1180px)">

#### Mobile first

The IE < 9 can represent media queries only using JavaScript. If JS is off, the default option (in this case, the mobile) is displayed. This can be optimized with Conditional Comments -> higher cost.

## Mandatory Document Information

### DTD

Except for HTML5 documents Otherwise write XHTML-compatible code independent of chosen DTD
Always close empty elements with slash

	<col />, <input />, <img />, <meta /> 

â€¦ such that document type can easily be changed to XHTML.

### Mandatory Tags

	<meta http-equiv="Content-Type" content="text/html; charset="myCharacterSet" />

preferably utf-8, unless requested otherwise by customer

	<title>Mirrors highest ranking Hx-Element within main content area of the page</title>
	<meta http-equiv="Content-Script-Type" content="text/javascript" />
	
### Conditional Comments Internet-Explorer

	<!--[if lt IE 7]><body class="ie6"><![endif]-->
	<!--[if IE 7]><body class="ie7"><![endif]-->
	<!--[if IE 8]><body class="ie8"><![endif]-->
	<!--[if IE 9]><body class="ie9"><![endif]-->
	<!--[if gt IE 9]><body class="ie9"><![endif]-->
	<!--[if !IE]><!--><body><!--<![endif]-->
	
### Mandatory Attributes

	<html lang="de>
	<html lang="en">
	<html lang="fr">

&hellip; according to top-level domain country codes

	<body class="langDE">
	<body class="langETC">

&hellip; in internationalized projects


## Site Structure

	<div class="site-container">
		<header class="site-header">(...)</header>
		<div class="site-main">(...)</div>
		<footer class="site-footer">(...)</footer>
	</div>

## Navigation Structure

### Primary Site Navigaton

	<nav class="nav-primary">
		(...)
	</nav>

### Secondary Site Navigation

	<nav class="nav-secondary">
		(...)
	</nav>

### Tertiary Site Navigation

	<nav class="nav-tertiary">
		(...)
	</nav>

### Meta Navigation

	<nav class="nav-meta">
		(...)
	</nav>

### Service Navigation

	<nav class="nav-service">
		(...)
	</nav>

### Breadcrumb Navigation

	<nav class="nav-breadcrumb">
		(...)
	</nav>

## Content Structure

	<div class="content-heading">
		<h1>Page heading</h1>
	</div>

	<div class="content-text">
		<p>Text</p>
	</div>

	<div class="content-image">
		<img src="(...)" title="Image title" alt="" />
	</div>

	<div class="content-block">
		<h2>Content block heading</h2>
		<p>Content block text</p>
		<img src="(...)" title="Content block image" alt="" />
	</div>

	<div class="content-block">
		<h2>Content block heading</h2>
		<p>Content block text</p>
		<img src="(...)" title="Content block image" alt="" />
	</div>

	<div class="content-box">
		<h3>Content box heading</h3>
		<p>Content box text</p>
		<p><a href="#" class="link-go">Content box link with arrow on the left</a>/p>
	</div>

	<div class="content-bubble">
		<h3>Content message bubble heading</h3>
		<p>Content message bubble text</p>
	</div>

	<div class="content-container cols-2">
		<div class="col">First col</div>
		<div class="col">Second col</div>
	</div>

## Accessibility

### Structurally meaningful "semantic" markup

- **Hx, P**	
	- As a principle, running text has to be organized in paragraph (P) and headline (Hx) elements. 
	- Do not fake paragraphs with BR elements! 
	- No more than one H1 per area (page header, main content, page footer, sub-navigation, sidebar) 
	- The highest-ranking headline of the main-contents area mirrors the TITLE-Element of the document. 
	- Mind the hierarchical succession within each document area: Do not jump from H1 to H3 without a preceding H2!
- **A**
	- Clad  in LI-, DT, DD, P, Hx, TH oder TD.
	- Do not abuse as buttons: Use BUTTON- and INPUT elements instead! Otherwise forms can not be submitted via enter or return key! 
	- Do not suppress *focus* marking via css or javaScript!
- **BUTTON, INPUT[type = image, submit, reset, button]** BUTTON elements to be preferred over INPUT [type=image, submit, reset, button] elements, as they can be styled more easily via css.
- **INPUT, SELECT, TEXTAREA** to be addressed with LABEL elements; preferably as their parent elements; separately, with *for* and *id* attributes only in tabular arrangement with DL or TABLE elements.
- **IMG**
	- Set *width* and *height* via HTML attributes or css properties to avoid jittering of a loading!
	- Use alt attribute in a meaningful way!
	- Block unwanted or redundant tooltips via empty title attribute!
- **Styled Tooltips**
	- Source code position immediately after or as child of the element to be commented on. 
	- If applicable:  unobstrusive  reference via *longdesc* attribute to an external document, which can either be integrated via Ajax or called independently on demand.
- **TABLE** 
	- For tabular data only: Usually these contain **exactly one** TH element in both, each row **and** column (except THEAD row). 
	- Set summary attribute!
- **CAPTION, THEAD, TFOOT, TBODY** use these elements where appropriate! 
- **TH, TD** Relation definition between both elements preferably via *scope* attribute, else via *axis* and *headers* attribute (dispensable when containing no other than input elements, with an established relation via *for* and *id* attributes, avoid redundancy!)

## Common HTML5 Tags for structuring

	<!DOCTYPE html>
HTML5 Doctype

	<article>
For articles, e.g. in a blog

	<nav>
For the main navigation. Therein an "ul"

	<aside>
For a sidebar

	<section>
Differentiates the document into sections

	<header>
Tags the head of an document or a "section"

	<footer>
Informs about Copyright or relevant links to other documents that bear a relation to the document or a "section".
	
For older browsers use [**Modernizr**](http://modernizr.com/) to get HTML5 tags and CSS3 features.
If only HTML5 Tags are necessary, use [**HTML5 Shiv**](http://code.google.com/p/html5shiv/).

## Performance:

- CSS: Maximum 4 selectors in a row. The fewer, the better / faster
- Use Sprites:  Multiple images together into one big. Really simple with Compass/SCSS
- Minimize CSS and JS at the end
- Use as few images as possible. Most elements can be displayed with CSS3 e.g. buttons, box shadows, gradients.