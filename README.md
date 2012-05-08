sass-vibe
=========

sass-vibe brings [SASS](http://sass-lang.com) to vibe.d applications. SASS creates a superset over
CSS to enable better stylesheet development, with features such as named variables and macros.

Installation
------------

 - Install SASS itself, either through RubyGems or your operating system's software management system.
 - Add "sass-vibe":">=0.1.2" to your applications dependencies.

Usage
-----

First you will need to add a call to compile your stylesheets using SASS. Import the 'sass' module,
then simply invoke compileSASS() with two arguments. The first is the directory where '.scss' files
will be found, and the second is the name of the file you want to compile into CSS. Finally, make
sure you are serving the files. For example, if you have a file "assets/styles/site.scss" you might
do this:

	module app;
	import vibe.d;
	import sass;
	static this () {
		// ...
		compileSASS( "./assets/styles/", "site" );
		// ...
		router.get( "*", serveStaticFiles( "./assets/" ) );
		// ...
	}

This will throw an exception on failure. The stylesheet is linked as normal in your view files.

	!!! 5
	html
		head
			title #{ title }
			link( href="/styles/site.css", rel="stylesheet", type="text/css" );
		body
			block body
