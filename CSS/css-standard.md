# denkwerk CSS standard

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

## Formatting

- **Indenting** tabs (four spaces width)
- **selectors (also multiple comma separated ones)** new line each
- **property: value pairs** new line each, indented with terminating semicolon each

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

## Helper classes

### Cols

Defines the column amount of one row

*Examples:*

	<div class="content-container cols-3">
		<div class="col">Row 1 - Column 1</div>
		<div class="col">Row 1 - Column 2</div>
		<div class="col">Row 1 - Column 3</div>
		<div class="col">Row 2 - Column 1</div>
		<div class="col">Row 2 - Column 2</div>
		(...)
	</div>

### Flip

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


## StyleDocco

[StyleDocco](http://jacobrask.github.com/styledocco/) generates documentation and style guide documents from the stylesheets. 

Stylesheet comments will be parsed through Markdown and displayed in a generated HTML document. HTML code is written prefixed with 4 spaces or between code fences (```) in the comments, and StyleDocco shows a preview with the styles applied, and displays the example HTML code.