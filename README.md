
<strong>Installing Bower</strong>

Assuming you already have node.js and npm installed, first init our project by creating an npm package.json using:

$ npm init 

name: (project-name)

version: (0.0.0) 0.0.1

description:

entry point: (index.js) public/index.php

test command:

git repository:

keywords:

author: Reginald Bossman <reginald.bossman@hellogroup.co.za>

license: (ISC)

About to write to <path>/project-name/package.json:

{

  "name": "project-name",

  "version": "0.0.1",

  "description": "",

  "main": "public/index.php",

  "dependencies": {

    "bower": "~1.3.5"

  },

  "devDependencies": {},

  "scripts": {

    "test": "echo \"Error: no test specified\" && exit 1"

  },

  "author": "Reginald Bossman <reginald.bossman@hellogroup.co.za>",

  "license": "(ISC)"

}

Is this ok? (yes)

All of the necessary prompts should be self-explanatory, you can skip the rest.

Next you can install Bower:

$ npm install -g bower

This will make the bower command available globally.

To make it install locally, and automatically, with npm install, additionally run:

$ npm install --save-dev bower

This installs it to ./node_modules/bower, with the bower command available at ./node_modules/.bin/bower. To add this directory to your path automatically, npm includes a bin sub-command that will return the path to this directory no matter where you are in the project, so simply add $(npm bin) to your path, or you can use an alias like so:

alias npm-exec='PATH=$(npm bin):$PATH'

Now you can run either bower and it will pick up the correct one (local if it exists, or global otherwise) or if you used the alias, you can use npm-exec bower.

<strong>Using Bower</strong>

Similar to other package managers, Bower uses the bower.json file to setup dependencies.

Like both Composer and NPM, Bower will treat every project as an installable library in its own right. This means whether you just want to use Bower to manage your dependencies, or are writing your own libraries, the setup is very much the same.

$ bower init

[?] name: project-name

[?] version: 0.0.1

[?] description:

[?] main file: public/index.php

[?] what types of modules does this package expose?

[?] keywords:

[?] authors: Reginald Bossman <reginald.bossman@hellogroup.co.za>

[?] license: (ISC)

[?] homepage:

[?] set currently installed components as dependencies? Yes

[?] add commonly ignored files to ignore list? Yes

[?] would you like to mark this package as private which prevents it from being accidentally published to the registry? Yes

{

  name: 'gulp-bower-example',

  version: '0.0.1',

  authors: [

    'Reginald Bossman <reginald.bossman@hellogroup.co.za>'

  ],

  main: 'public/index.php',

  license: '(ISC)',

  private: true,

  ignore: [

    '**/.*',

    'node_modules',

    'bower_components',

    'test',

    'tests'

  ]

}

[?] Looks good? Yes

This will walk you through numerous questions to generate a new bower.json file. Some of the questions are pretty obvious, while others may be a little confusing:
    
<ul>
    <li>main file — this would be the entry point for the application, in the case of PHP that's likely something like public/index.php </li>    
    <li>what types of modules does this package expose? — as we're not building our own libraries, we can skip this</li>
    <li>set currently installed components as dependencies? — if you install packages by hand using bower install, this will add them as dependencies to your new bower.json</li>
    <li>add commonly ignored files to ignore list? — this will ignore files and folders that are commonly ignored, such as node_modules, bowers own bower_components, or a tests directory.</li>
    <li>would you like to mark this package as private which prevents it from being accidentally published to the registry? — answering yes will stop you from being able to accidentally publish your "package" to the bower registry.</li>
</ul>

At this point, you can easily now install packages, updating the bower.json along the way:

$ bower install --save jquery bootstrap

This will install the latest jquery and bootstrap into the bower_components directory. If you check your bower.json, it will have been updated with:

"dependencies": {

    "jquery": "~2.1.1",

    "bootstrap": "~3.1.1"

  }

Now, if we wanted to install these dependencies in a fresh checkout, we can simply run:

<p>$ bower install</p>

If webroot isn't the root of your project (which it likely isn't), you can easily change the install directory by creating a new file .bowerrc with the following:

{

  "directory": "public/bower_components"

}

Once you've done this, delete the original install, and install again:

$ rm -Rf bower_components

$ bower install

You can then reference the files as /bower_components/<package>/dist/<files> for example to include Bootstrap you would add the following two lines in their appropriate places:

<link href="/bower_components/bootstrap/dist/css/bootstrap.min.css" rel="stylesheet">

<link href="/bower_components/bootstrap/dist/css/bootstrap-theme.min.css" rel="stylesheet">

<script type="text/javascript" src="/bower_components/bootstrap/dist/js/bootstrap.min.js">

To keep your libraries up-to-date simply use bower update:

$ bower update bootstrap






