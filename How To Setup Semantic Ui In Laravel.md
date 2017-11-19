# How to setup Laravel 5.5 + Vue.js + Semantic UI in project

Create a **new Laravel project** with _composer_:

	$ composer create-project Laravel/Laravel myproject

Install Laravel Elixir, Vue.js, Gulp, etc.:

	$ npm install
	
Install Laravel Elixir, Vue.js, Gulp, etc.:

	$ npm install -g gulp
	

Install **Semantic UI**:

	$ npm install semantic-ui --save
	...
	> Automatic
	> Yes
	? semantic/


To build Semantic UI:

	$ cd semantic
	$ gulp build
	
Edit in Asset/app.scss

	@import "node_modules/semantic-ui/dist/semantic";


Modify the `gulpfile.js` to include the Semantic UI's files:

	elixir(mix => {
	    mix.sass('app.scss')
    	   .webpack('app.js')
       	   .copy('semantic/dist/semantic.min.css', 'public/css/semantic.min.css')
       	   .copy('semantic/dist/semantic.min.js', 'public/js/semantic.min.js');
	});
