# How to setup Laravel 5.5 + Semantic UI in project

Create a laravel project

	$ composer create-project Laravel/Laravel myproject

Install npm in your project

	$ npm install
	
Install gulp

	$ npm install -g gulp
	

First, with administrator privileges, run npm with the --ignore-scripts flag, otherwise semantic-ui will launch the installer automatically, which can cause problems if you cancel halfway through.

	$ npm install semantic-ui --save-dev --ignore-scripts

Once it’s downloaded navigate to 

	cd node_modules/semantic-ui

Then run the following to start the installer:

	$ gulp install

Now we just need to follow the installer:

	1) Select “Automatic” under the set up options.
	2) When asked if the given location is your project folder select “yes”.
	3) Type resources/assets/semantic when asked where to put semantic-ui
	to specify where our semantic folder will be. In Laravel
	the assets folder makes the most sense.

Navigate to resources/assets/semantic and run.

	$ gulp build
	
Everything will now be outputted to:

	resources/assets/semantic/dist/semantic.css:

Edit in Asset/app.scss

	@import "../semantic-ui/dist/semantic";

Modify the `gulpfile.js` to include the Semantic UI's files:

	elixir(mix => {
	    mix.sass('app.scss')
    	   .webpack('app.js')
       	   .copy('semantic/dist/semantic.min.css', 'public/css/semantic.min.css')
       	   .copy('semantic/dist/semantic.min.js', 'public/js/semantic.min.js');
	});
