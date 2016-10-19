
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






