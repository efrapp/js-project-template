## Webpack

### Installation
We need to install the `webpack` library, and if it is the version 4 or later, we need to install the `webpack-cli` also.
```
npm install --save-dev webpack
# Using an specific version:
npm install --save-dev webpack@<x.x.x>
```
```
npm install --save-dev webpack-cli
```
It is recommended to install these libraries locally (`--save-dev` flag) because it you install them globaly and there is breaking update all the projects using those globals will be affected.

### Basic set up
We are going to setup Webpack with a `webpack.config.js` file so the structure we will need is like this:
```
js-project-template
  |- package.json
  |- webpack.config.js
  |- /dist
    |- index.html
    |- main.js
  |- /src
    |- index.js
```
- The **`/src`** folder will contain all our work, the files we need to develop the application
- The **`/dist`** folder is where Webpack will place all the processed files from the /src folder

We can use a basic `webpack.config.js` like this:
```
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

The first step is to set up our `package.json` file to make our package private to prevent it to be published accidentally. The file will look like this:
```
{
    "name": "js-project-template",
    "version": "1.0.0",
    "description": "",
    "private": true,
    "main": "index.js", // remove this line
    ...
}
```
Now we need to add an html file in the root of our `dist` folder, we can call it `index.html` or the name you prefer, and in this file we are going to add a reference to a js file Webpack will create after build the code in the `src` folder. The `index.html` file will look like this:
```
<!doctype html>
<html>
 <head>
   <title>Getting Started</title>
 </head>
 <body>
  <!-- main.js file is create by Webpack after build the src folder -->
   <script src="main.js"></script>
 </body>
</html>
```
When we have ready our project with this structure the next step is to generate our `main.js` file. For this we need to create an **entry point** this will be a file in the root of the `src` folder that Webpack will build to generate the `main.js` file. To tell Webpack what is the entry point we will add it in the `webpack.config.js` file like this:
```
const path = require('path');

module.exports = {
  entry: './src/index.js', //this will be the entry point
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```
Now we can build the project using: `npx webpack` to let Webpack makes its magic. When it is done we will see the `main.js` file inside the `dist` folder.
You will get a warning after run the command:
```
WARNING in configuration
The 'mode' option has not been set, webpack will fallback to 'production' for this value. Set 'mode' option to 'development' or 'production' to enable defaults for each environment.
You can also set it to 'none' to disable any default behavior. Learn more: https://webpack.js.org/configuration/mode/
```
You can can add the key `mode: 'none'` to the `webpack.config.file` like this:
```
...
module.exports = {
  mode: 'none',
  entry: './src/index.js',
...
}
````

### NPM scripts set up
We can set up some shortcuts to useful Webpack commands. For this, we will modifiy the `scritps: {}` key in the `package.json` file.

To create an script to `build` the application, we can use:
```
{
....
  "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "build": "webpack"
    },
...
}
```
If we don't want to build the project each time we make modifications we can use the `--watch` option of `webpack` command. For this we need to add the following script in the `package.json` file.
```
{
....
  "scripts": {
      "watch": "webpack --watch"
  },
...
}
```
We also need a sever to run the application, we can install the `webpack-dev-server` npm packege to run our app in a development enviroment. To install it, we can run:
```
npm install webpack-dev-server --save-dev
```
And the, we can create an script in the `package.json` to run it using `npm run server`. The script looks like this:
```
{
....
  "scripts": {
      "server": "webpack-dev-server --open-page 'dist/'"
  },
...
}
```
The `--open-page` flag is to open the path supplied in string right away after the server runs.
