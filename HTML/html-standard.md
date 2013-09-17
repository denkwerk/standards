# denkwerk HTML standard

## Coding guidelines

Inspired by [Twitter Bootstrap](http://twitter.github.com/bootstrap/) and [Object Oriented CSS](https://github.com/stubbornella/oocss/wiki)

### Main principles

**Patterns**  
Usage of well proven, self-explanatory patterns to align the development.

**Object orientation**  
Separate structure and skin. Use classes to name objects and their components, rather than relying solely on the semantics of HTML.

**Code flexiblility**

- Evident code modifiactons must be possible, e.g. adding sub elements, links, rich text formation
- CMS compatibility - the site content is not a fixed template 
- Fixed width and height should be avoided beyond the site container

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
- **block, table and table child-elements** new line, indented
- **inline child-elements**	same line as parent element

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

### Colors

- **Recommended**
	- **#bd00ff, #a00, buttontext, scrollbar** as short as possible; hexadecimal or system-color names
- **Only to mark temporary status** 
	- **teal, white, etc.** for testing purposes during development

### Short Notation

- **Recommended**
	body {
  		font: normal 12px/1.25 "Courier New", Courier, monospace; 
	}

	.sample-element { 
		border: solid 1px #F00;
		border-right-color: #A00;
		border-bottom: solid 2px #800;
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

## Mandatory Document Information

### DTD

Except for HTML5 documents Otherwise write XHTML-compatible code independent of chosen DTD
Always close empty elements with slash

	<col />, <input />, <img />, <meta /> 

so the document type can easily be changed to XHTML.

### Mandatory Tags

	<meta http-equiv="Content-Type" content="text/html; charset="myCharacterSet" />

preferably utf-8, unless requested otherwise

	<title>Mirrors highest ranking Hx-Element within main content area of the page</title>
	<meta http-equiv="Content-Script-Type" content="text/javascript" />
	
### Conditional Comments Internet-Explorer

	<!--[if lt IE 7]><body class="ie6"><![endif]-->
	<!--[if IE 7]><body class="ie7"><![endif]-->
	<!--[if IE 8]><body class="ie8"><![endif]-->
	<!--[if IE 9]><body class="ie9"><![endif]-->
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

### Navigation Structure

	<nav class="nav-primary">
		(...)
	</nav>

	<nav class="nav-secondary">
		(...)
	</nav>

	<nav class="nav-tertiary">
		(...)
	</nav>

	<nav class="nav-meta">
		(...)
	</nav>

	<nav class="nav-service">
		(...)
	</nav>

	<nav class="nav-breadcrumb">
		(...)
	</nav>

### Content Structure

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
