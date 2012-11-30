# denkwerk TYPO3 standard

## Structure

### Project structure

*Description of the most important folders:*

- BASE
	- htdocs
		- **public**: public web root (see chapter TYPO3 structure)
		- **configuration**: environment configuration (see chapter Configuration)
			- **global.ini**: all configuration except database
			- **localconf.php**: database configuration
		- sources
			- **typo3_src-(...)**: TYPO3 sources
			- **Zend**: Zend Framework sources
		- sql
			- **project.sql**: complete project database
			- **templavoila.sql**: only Templavoila tables

### TYPO3 structure

*Description of the most important folders in TYPO3:*

- fileadmin
	- templates
		- **config.rb**: Compass configuration file
		- **css**: stylesheet files, auto-compiled by Compass
		- **font**: webfonts
		- **html**: HTML templates
			- **fce**: Templavoila content element templates (FLUID)
			- **page**: Templavoila page templates
			- **plugins**: TYPO3 plugin templates
			- **viewhelpers**: FLUID helpers
		- **img**: non-editior-maintainable images
		- **js**: Javascript files
		- **scss**: SCSS stylesheets (see chapter SCSS)
		- **test**: templates for test approval
		- **ts**: TypoScript templates
			- **constants**: manual set constant variables
			- **setup**: TypoScript setup templates
				- **_lib**: TypoScript libaries
					- **fce**: Templavoila content elements
					- **global**: global TypoScript libraries used by fce and page
					- **page**: Templavoila page templates
				- **_main**: main TypoScript templates
					- **config.ts**: TypoScript config object
					- **includeLibs.ts**: TypoScript includeLibs object
					- **lib.ts**: TypoScript lib object
					- **page.ts**: TypoScript page object
					- **tt_content.ts**: TypoScript tt_content object
			- **tsconfig**: TSConfig TYPO3 backend configuration
	- **upload**: cms editor upload folder
	- **userfunc**: TYPO3 userfunc php classes
- typo3conf
	- **ext**: TYPO3 extensions

## Configuration

The reason of the configuration is a central place where all developers can maintain their local as well as the server configuration. It is splitted into two parts - **global.ini** for everything except database and server hacks. Therefore the **localconf.php** is used.

The global.ini is rendered as a PHP array and TypoScript Constants. For that the TYPO3 extension dw_config is used. Because TYPO3 indexes the database configuration before any extension code is rendered, the database configuration has to be done in the localconf.php for local systems.