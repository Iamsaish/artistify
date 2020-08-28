Initializing npm (package.json): 
	npm init
Add git: 
	git init 
	git add .
	git commit -m ""
	git remote add origin url
	git push -u origin master

add the following to package.json:
	in script{
		"start": "npm run lite",
		"lite": "lite-server",
    		"scss": "node-sass -o css/ css/"
		}
add bootstrap contents to folder: 
	npm install bootstrap@4.0.0 --save
	npm install jquery@3.3.1 popper.js@1.12.9 --save

add font-awesome: 
	npm install font-awesome@4.7.0 --save
	npm install bootstrap-social@5.1.1 --save

	    <link rel="stylesheet" href="node_modules/font-awesome/css/font-awesome.min.css">
    	    <link rel="stylesheet" href="node_modules/bootstrap-social/bootstrap-social.css">

To init onchange and parallel shell:
	npm install --save-dev onchange@3.3.0 parallelshell@3.0.2

	in package.json: 
	in scripts:
		    "watch:scss": "onchange \"css/*.scss\" -- npm run scss",
    		    "watch:all": "parallelshell \"npm run watch:scss\" \"npm run lite\""

	    "start": "npm run watch:all"

To init rimraff to clean the distribution folder:
	npm install --save-dev rimraf@2.6.2

	in package.json scripts:
		    "clean": "rimraf dist",

To install copy files:
	npm -g install copyfiles@2.0.0

	in package:
		"copyfonts": "copyfiles -f node_modules/font-awesome/fonts/* dist/fonts"

To install imagemin:
	npm -g install imagemin-cli@3.0.0

	in package:
	
 install the usemin-cli, cssmin, uglifyjs and htmlmin NPM packages as follows:
	npm install --save-dev usemin-cli@0.5.1 cssmin@0.4.3 uglifyjs@2.4.11 htmlmin@0.0.7

	in .html file add:
	to css files above meta:
	    <!-- build:css css/main.css -->
	end of css files:
	    <!-- endbuild-->

	do the same for js files: 
	    <!--build:js js/main.js-->

	in package:
	"usemin": "usemin contactus.html -d dist --htmlmin -o dist/contactus.html && usemin aboutus.html -d dist --htmlmin -o dist/aboutus.html && usemin index.html -d dist --htmlmin -o dist/index.html",
	 "build": "npm run clean && npm run imagemin && npm run copyfonts && npm run usemin"