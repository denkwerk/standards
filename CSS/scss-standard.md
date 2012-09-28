# denkwerk (S)CSS standard
 
## Performance: 

- CSS: Maximum 4 selectors in a row. The fewer, the better / faster
- Use Sprites:  Multiple images together into one big. Really simple with Compass/SCSS
- Minimize CSS and JS at the end
- Use as few images as possible. Most elements can be displayed with CSS3 e.g. buttons, box shadows, gradients.

## SCSS

[SCSS](http://sass-lang.com/) is an extension of CSS3 which adds nested rules, variables, mixins, selector inheritance, and more. It makes your stylesheets easier to organize and maintain and generates well formatted CSS using the open-source CSS authoring framework [Compass](http://compass-style.org/).

### Folder structure

- base
- config
- contents
- mixins
- partials
- patterns
- sprites
- widgets

**base** is the backbone of the stylesheet where well proven libraries like [Compass](http://compass-style.org/), [978 Grid System](http://978.gs/) are included. **config** contains all the project related configuration variables - definition of fonts, grid size, site dimensions and size levels for space, border, rounded corners and shadows. **contents** is used for content elements, each element has it's own scss file. The file names are identical to the HTML template and/or the template of a CMS like [TYPO3](http://www.typo3.org/) or [WordPress](http://wordpress.com/). **mixins** defines helper functions, which can be used in all scss files by *@include mixin-title(mixin-parameters);*. **partials** contains the site parts - global styles, header, footer and the main content area. **patterns** are bootstrap elements like headings, buttons and form elements that can either be integrated in the HTML template or selector inheritance in SCSS by *@extend .pattern-style;*. **sprites** definition see next paragraph. **widgets** contains the interactive elements of the project.

### Sprites

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

### StyleDocco

[StyleDocco](http://jacobrask.github.com/styledocco/) generates documentation and style guide documents from the stylesheets. 

Stylesheet comments will be parsed through Markdown and displayed in a generated HTML document. HTML code is written prefixed with 4 spaces or between code fences (```) in the comments, and StyleDocco shows a preview with the styles applied, and displays the example HTML code.

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

## Nomenclature

### Element- und Pseudo-Element Selectors

	h2
	:hover	
Lower case

### Class Attributes and Selectors

	.teaserpic-right
	.subline
Lower case hyphenated

### ID-Attributes

	id=“MainNav“
	id=“MainContentCol“
- Upper case with CamelCase 
- to address elements with javascript and for attributes in LABEL elements
- do not use as css selectors

### Recommended Nomenclature

	teaser-image, teaser-text
functionally motivated, generic

### Disapproved Nomenclature

- **customernameTeaser** too specific
- **float-left, text-bold** behavior and appearance motivated nomenclature only for differentiating purposes as addtl. classnames

## Mandatory Document Information

### DTD

Except for HTML5 documents Otherwise write XHTML-compatible code independent of chosen DTD
Always close empty elements with slash

	<col />, <input />, <img />, <meta /> 

… such that document type can easily be changed to XHTML.

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

	<html lang=“de“>,
	<html lang=“en“>,
	<html lang=“etc…“>
… according to top-level domain country codes

	<body class=“langDE“>,
	<body class=“langETC…“>
… in internationalized projects

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
	p:first-child,
	h1 + p,
	h1 + h2  {
    	padding-top:0;
	}
- **print.css begins with:**
	* {
		overflow:visible !important;
		background:transparent !important; 
	}
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
  		font-family: „Courier New“;
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

## CSS Hacks

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