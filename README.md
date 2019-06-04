# Javascript Tooling & Workflow

# Links

- [https://medium.com/the-node-js-collection/modern-javascript-explained-for-dinosaurs-f695e9747b70](https://medium.com/the-node-js-collection/modern-javascript-explained-for-dinosaurs-f695e9747b70)

# Learning Plan

---

- ES6 for Everyone
    - [https://es6.io/](https://es6.io/)
    - [https://courses.wesbos.com/account/access/5be5eab0c413951cd2b18b14](https://courses.wesbos.com/account/access/5be5eab0c413951cd2b18b14)
    - Master Package 21 Modules
- UDEMY:
    - [https://www.udemy.com/home/my-courses/learning/](https://www.udemy.com/home/my-courses/learning/)
    - Javascript-Understanding the Weird Parts
    - The Complete Javascript Course 2018: Build Real....
- FrontEnd Master
    - [https://frontendmasters.com/learn/javascript/](https://frontendmasters.com/learn/javascript/)
    - Master Writing Professional and Modern Javascript
    - 
- asdf

# To Do

## (as they relate to additional learning, picking up where I left off)

---

## Webpack

1. learn css, html, minification, image compression 
2. is dist/ —> production output ready? Can I publish this? via git or sftp?
3. 

---

# NPM is becoming the default Javascript Package Manager

Others that were popular: Bower, Yarn

    $ npm init -y

What does it do?

It automates the process of downloading and upgrading (dependencies) libraries from a central repository. It eliminates the need to manually download and manage libraries your app uses.

It will create a `package.json` file in your working directory. It is a configuration file that saves information on all your project dependencies

The -y flag says yes to all the default configs

To install packages

$ npm install moment 

$ npm install dompurify 

Import them into you JS file (instead of including these in HTML script tags in the HEAD of your HTML file, just load them in your Javascript files)

Webpack will bundle them all together for you replacing every require() or import statement with actual library code

// use ES2015 import statement
import moment from 'moment';

import dompurify from 'dompurify';

# Webpack is becoming the default Javascript Module Bundler

     

     Other that were popular: Browserify

    $ npm install webpack webpack-cli --save-dev

What does it do?

Allows you to use node-style **`require(libaryName)`** statements in your Javascript files and then automatically replaces each instance with actual file contents.

A JavaScript module bundler is a tool that replaces `require()` statements with a build step (which has access to the file system) to create a final output that is browser compatible (which doesn’t need access to the file system). In this case, we need a module bundler to find all require statements (which is invalid browser JavaScript syntax) and replace them with the actual contents of each required file. The final result is a single bundled JavaScript file (with no require statements)!

# Babel is becoming the default Javascript Transpiler

     

     Others that were popular: CoffeeScript, TypeScript

    `$ npm install @babel/core @babel/preset-env babel-loader --save-dev`

What does it do?

Babel is not a new language but a transpiler that transpiles next generation JavaScript with features not yet available to all browsers (ES2015 and beyond) — to older more compatible JavaScript (ES5).

# NPM (scripts) is becoming the default Javascript Task Runner

Others that were popular: Grunt, Gulp

One way to write NPM scripts is to edit the *"scripts"* section of the `package.json` file

    ...
    "scripts": {    
    	"test": "echo \"Error: no test specified\" && exit 1",    
    	"build": "webpack --progress --mode=production",    
    	"watch": "webpack --progress --watch"  
    },
    ...

What does it do?

A task runner is a tool that automates different parts of the build process. A build process generates the final code for your website that is used in production. For frontend development, tasks include: 

- minifying code,
- optimizing images, svgs
- running tests
- transpile ES2015
- copy, rename, and move files
- compile css via pre-processor
- add auto-prefixing
- generate sourcemaps
- run code linting
- run 'watch' for dev environment, live-reload, etc

Links About NPM Scripts

- [https://medium.freecodecamp.org/introduction-to-npm-scripts-1dbb2ae01633](https://medium.freecodecamp.org/introduction-to-npm-scripts-1dbb2ae01633)
- [https://medium.freecodecamp.org/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8](https://medium.freecodecamp.org/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8)
- [https://docs.npmjs.com/misc/scripts](https://docs.npmjs.com/misc/scripts)
- [https://docs.npmjs.com/files/package.json](https://docs.npmjs.com/files/package.json)
- Advanced Front End Automation with NPM scripts: [https://www.youtube.com/watch?v=0RYETb9YVrk](https://www.youtube.com/watch?v=0RYETb9YVrk)
- 

# Running a local Server

Webpack (popular javascript module bundler)

You can install regular webpack (to dev-dependencies in `package.json`)

`$ npm install webpack webpack-cli --save-dev`

You can also install a separate tool which provides a simple web server with live reloading. You can install it as a development dependency

`$ npm install webpack-dev-server --save-dev`

You can then add an NPM script to `package.json`

"server": "webpack-dev-server --open"

The run it from the command line: 

`$ npm run server`

## WHY?

This is nice, if you are already using Webpack for module bundling

BrowserSync 

To install (globally): 

`$ npm install -g browser-sync` 

USAGE:

If BrowserSync is installed globally

Run from the command line (inside your project directory):

`$ browser-sync start --server --files "css/*.css"`

If BrowserSync is installed locally (dev-dependencies)

Add a NPM script to your `package.json` 

"server": "browser-sync start --directory --server --files 'js/*.js, *.html, css/*.css' "

The run it from the command line: 

`$ npm run server`

## WHY?

You can use it across multiple devices and screens to test design and responsiveness for apps.

LiveServer

To install: 

`$ npm install -g live-server`

USAGE:

Issue the command `live-server` in your project's directory. 

This will automatically launch the default browser. When you make a change to any file, the browser will reload the page - unless it was a CSS file in which case the changes are applied without a reload.

## WHY?

No configuration is necessary; watches entire project directory by default

# How To Quickly Setup A Dev Environment using Node, Webpack, Babel

Use NPM as our Javascript package manager to automatically download and install all of your library needs.

## Create your project directory

`$ mkdir my-project && cd my-directory`

## Create index.html

`subl index.html ( OR code index.html if you use VSCode )`

Create this file inside your project directory and add a standard HTML container and `main.js` reference as provided below.

    <!DOCTYPE html>
    <html lang="en">
    	<head>
    	  <meta charset="utf-8">
    	  <title>JS Lab</title>
    	</head>
    	<body>
    
    	
    	<script src="dist/main.js"></script>
    	</body>
    </html>

## Create index.js

`subl index.js ( OR code index.js if you use VSCode )`

Create this blank file inside of your project directory. 

## Create package.json

`$ npm init -y`

The command above will create your project **`package.json`** file inside of your project directory. 

If you don't use the `-y` flag to accept the default configurations, you will be prompted to answer several questions, which you can ignore by pressing <Enter>.

     You can install packages like this (anytime you need them...):

`$ npm install moment --save`

This command does two things — first, it downloads all the code from the moment.js package into a folder called node_modules. Second, it automatically modifies the ***package.json*** file to keep track of moment.js as a project dependency.

This is useful later when sharing a project with others — instead of sharing the node_modules folder (which can get very large), you only need to share the ***package.json*** file and other developers can install the required packages automatically with the command:

`$ npm install`

## Install Webpack

`$ npm install webpack webpack-cli webpack-dev-server --save-dev`

- Webpack is a JavaScript module bundler (webpack) that automates the bundling of Javascript libraries and files.
- The --save-dev argument  saves it as a development dependency (in ***package.json***), which means it’s a package that you need in your development environment but not on your production server.
- We’re installing three packages as dev dependencies
    - webpack which is the base/core webpack package
    - webpack-cli which enables you to use webpack from the command line
    - webpack-dev-server which is a simple web server with live reloading

## Install Babel

`$ npm install @babel/core @babel/preset-env babel-loader --save-dev`

- Babel will transpile the modern Javascript you will be writing for cross-browser support
- We’re installing three packages as dev dependencies
    - @babel/core is the main part of babel
    - @babel/preset-env is a preset defining which new JavaScript features to transpile
    - babel-loader is a package to enable Babel to work with Webpack.

## Configure Webpack & Babel

`subl webpack.config.js ( OR code webpack.config.js if you use VSCode )`

Create a file called ***webpack.config.js*** with the following contents.

    // webpack.config.js
    module.exports = {
      mode: 'development',
      entry: './index.js',
      output: {
        filename: 'main.js',
        publicPath: 'dist'
      },
      module: {
        rules: [
          {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
              loader: 'babel-loader',
              options: {
                presets: ['@babel/preset-env']
              }
            }
          }
        ]
      }
    };

We will be writing code in ***index.js*** file and Webpack will bundle this and any require/import statements it finds in this file to create a single output file (which by default is ***dist/main.j***s).

Your ***index.html*** file already has a reference to the file generated by Webpack:

`<script src="dist/main.js"></script>`

We configure Webpack to use ***babel-loader*** by adding the loader property and options object to the list of modules. 

If you want to save `index.js` in a js/ directory simply update your webpack.config.js like so:
Change the entry property to `'./js/index.js'` instead of entry: `'./index.js'`

    // webpack.config.js
    module.exports = {
      mode: 'development',
      entry: './js/index.js',
      output: {
        filename: 'main.js',
        publicPath: 'dist'
      },
    ...

## Configure NPM Scripts

Open your `package.json` file and add the following contents to the SCRIPTS object.

TASK RUNNER NPM SCRIPTS via package.json

Add the following Webpack scripts (build, watch, server) to the SCRIPTS object of your ***package.json*** file.

    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "build": "webpack --progress --mode=production",
        "watch": "webpack --progress --watch",
        "server": "webpack-dev-server --open"
      },

### RUNNING SCRIPTS

To run the ***build*** script:

`$ npm run build`

This will run Webpack (using configuration from the ***webpack.config.js*** we made earlier) with the `--progress` option to show the percent progress and the `--mode=production` option to minimize the code for production. 

To run the ***watch*** script:

`$ npm run watch`

This uses the `--watch` option instead to automatically re-run Webpack each time any JavaScript file changes, which is great for development.

To start your dev server and begin writing code:

`$ npm run server`

This will automatically open the **`index.html`** website in your browser with an address of `localhost:8080` (by default). Any time you change your Javascript in **`index.js`**, webpack-dev-server will rebuild its own bundled Javascript and refresh the browser automatically.

# How To Quickly Setup A Dev Environment using Node, Webpack, Babel for ES6 & SCSS

Use NPM as our Javascript package manager to automatically download and install all of your library needs.

## Create your project directory

`$ mkdir my-project && cd my-project`

## Create index.html

`subl index.html if you use Sublime`

`OR code index.html if you use VSCode` 

`OR touch index.html from the command line`

Create this file inside your project directory and add a standard HTML container with `bundle.css and bundle.js` references as provided below.

    <!DOCTYPE html>
    <html lang="en">
    	<head>
    	  <meta charset="utf-8">
    	  <title>Hola Mundo</title>
    		<link rel="stylesheet" href="bundle.css">
    	</head>
    	<body>
    		<h1>Hola Mundo!</h1>
    
    		<script src="bundle.js" async></script>
    	</body>
    </html>

- Webpack will generate the CSS and JS files referenced in the index.html file.
- You will write and edit code within `app.js` and `app.scss` and Webpack will compile and transpile all of your files into `bundle.js` and `bundle.css`

## Create app.js

`subl app.js if you use Sublime`

`OR code app.js if you use VSCode` 

`OR touch app.js from the command line`

Create this blank file inside of your project directory. 

## Create app.scss

`subl app.scss if you use Sublime`

`OR code app.scss if you use VSCode` 

`OR touch app.scss from the command line`

Create this blank file inside of your project directory. 

## Create package.json

`$ npm init -y`

The command above will create your project **`package.json`** file inside of your project directory. 

If you don't use the `-y` flag to accept the default configurations, you will be prompted to answer several questions, which you can ignore by pressing <Enter>.

     You can install packages like this (anytime you need them...):

`$ npm install moment`

This command does two things — first, it downloads all the code from the moment.js package into a folder called node_modules. Second, it automatically modifies the ***package.json*** file to keep track of moment.js as a project dependency.

This is useful later when sharing a project with others — instead of sharing the node_modules folder (which can get very large), you only need to share the ***package.json*** file and other developers can install the required packages automatically with the command:

`$ npm install`

## Install Webpack

`$ npm install --save-dev webpack webpack-cli webpack-dev-server`

- Webpack is a JavaScript module bundler (webpack) that automates the bundling of Javascript libraries and files.
- The --save-dev argument  saves it as a development dependency (in **`package.json`**), which means it’s a package that you need in your development environment but not on your production server.
- We’re installing three packages as dev dependencies
    - webpack which is the base/core webpack package
    - webpack-cli which enables you to use webpack from the command line
    - webpack-dev-server which is a simple web server with live reloading

## Install SCSS Dependencies

`$ npm install --save-dev css-loader sass-loader node-sass extract-loader file-loader autoprefixer postcss-loader`

- The CSS is generated by sass-loader, which compiles Sass files into CSS. The CSS is extracted into a `bundle.css` file by extract-loader.
- In order to add vendor-specific styles to the Sass files, we need to configure autoprefixer through PostCSS (see `webpack.config.js` below).

## Install Babel

`$ npm install --save-dev @babel/core @babel/preset-env babel-loader`

- Babel will transpile the modern Javascript you will be writing for cross-browser support.
- The JS is extracted into a `bundle.js` file by babel-loader.
- We’re installing three packages as devDependencies
    - @babel/core is the main part of babel
    - @babel/preset-env is a preset defining which new JavaScript features to transpile
    - babel-loader is a package to enable Babel to work with Webpack.

## Create and Configure webpack.config.js

`subl webpack.config.js if you use Sublime`

`OR code webpack.config.js if you use VSCode` 

`OR touch webpack.config.js from the command line`

Create this file inside of your project directory ******with the following contents.

    // webpack.config.js
    const autoprefixer = require('autoprefixer');
    
    module.exports = {
      entry: ['./app.scss', './app.js'],
      output: {
        filename: 'bundle.js',
      },
      module: {
        rules: [
          {
            test: /\.scss$/,
            use: [
              {
                loader: 'file-loader',
                options: {
                  name: 'bundle.css',
                },
              },
              { loader: 'extract-loader' },
              { loader: 'css-loader' },
              { loader: 'postcss-loader',
                options: {
                  plugins: () => [autoprefixer()],
                },
              },
              {
                loader: 'sass-loader',
                options: {
                  includePaths: ['./node_modules'],
                },
              }
            ],
          },
          {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
              loader: 'babel-loader',
              options: {
                presets: ['@babel/preset-env']
              }
            }
          }
        ]
      }
    };

We will be writing code in ****`app.js` and Webpack will bundle this and any require/import statements it finds in this file to create a single output file `bundle.js`.

Your ***`index.html`*** file already has a reference to the file generated by Webpack:

`<script src="bundle.js" async></script>`

We configure Webpack to use ***babel-loader*** by adding the loader property and options object to the list of modules. 

If you want to save`app.js` in a js/ directory simply update your webpack.config.js like so:
Change the entry property to `'./js/app.js'` instead of entry: `'./app.js'`

    // webpack.config.js
    module.exports = {
      entry: ['./css/app.scss', './js/app.js'],
      output: {
        filename: 'bundle.js',
      },
    ...

## Configure NPM Scripts (task runners)

Open your `package.json` file and add the following contents to the SCRIPTS object.

    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "build": "webpack --progress --mode=production",
        "watch": "webpack --progress --watch",
        "server": "webpack-dev-server --open"
      },

### RUNNING SCRIPTS

To run the ***build*** script:

`$ npm run build`

This will run Webpack (using configuration from the ***webpack.config.js*** we made earlier) with the `--progress` option to show the percent progress and the `--mode=production` option to minimize the code for production. 

This will produce `bundle.js` and `bundle.css` in the project directory. These contain the compiled CSS and transpiled JS, which you can then copy into a directory served by any web server.

To run the ***watch*** script:

`$ npm run watch`

This uses the `--watch` option instead to automatically re-run Webpack each time any JavaScript file changes, which is great for development.

To start your dev server and begin writing code:

`$ npm run server`

This will automatically open the **`index.html`** website in your browser with an address of `localhost:8080` (by default). Any time you change your Javascript in **`index.js`**, webpack-dev-server will rebuild its own bundled Javascript and refresh the browser automatically.

# Yeoman and WebApp Generator + Material Design

    
    
    
    npm i @material/animation @material/typography @material/layout-grid @material/card @material/button @material/fab @material/icon-button @material/ripple @material/chips @material/dialog @material/list 
    @material/top-app-bar @material/drawer @material/menu @material/menu-surface @material/image-list @material/snackbar @material/tab-bar @material/form-field @material/textfield @material/select @material/checkbox @material/radio @material/slider @material/switch @material/linear-progress 
    
    
    
    

---

---

---

# Lessons Learned from using WebPack and Babel

[https://levelup.gitconnected.com/lessons-learned-from-a-year-of-fighting-with-webpack-and-babel-ce3b4b634c46](https://levelup.gitconnected.com/lessons-learned-from-a-year-of-fighting-with-webpack-and-babel-ce3b4b634c46)

# Configuring Airbnb Javascript setting for Babel and ESLint

It is recommended that these packages are installed locally.

 (your dev environment might require otherwise)

All of these are Node modules.

Make sure you install core babel, eslint, webpack, etc before installing the present, plugins, etc.

# BABEL

.babelrc should be installed local to your project directory

[https://www.npmjs.com/package/babel-preset-airbnb](https://www.npmjs.com/package/babel-preset-airbnb)

INSTALLATION

    $ npm install --save-dev babel-preset-airbnb

Configuration

    // babel.config.js
    module.exports = function () {
      const presets = ["airbnb"];
    //const plugins = [ ... ];
    
    // can return ,plugins reference if needed
      return {
        presets
      };
    }
    
    // ----------------------------------------
    // webpack.config.js
    // airbnb
    // OLD presets: ['@babel/preset-env']
    module.exports = {
      mode: 'development',
      entry: './index.js',
      output: {
        filename: 'main.js',
        publicPath: 'dist'
      },
      module: {
        rules: [
          {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
              loader: 'babel-loader',
              options: {
                presets: ['airbnb']
              }
            }
          }
        ]
      }
    };

# ESLINT

.eslintrc should be installed local to your project directory

[https://eslint.org/docs/user-guide/getting-started](https://eslint.org/docs/user-guide/getting-started)

webpack.config.js