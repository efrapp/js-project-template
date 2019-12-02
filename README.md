## Eslint

### Create a `package.json` file
This file is needed to install all the packages needed in the project.
To create the `package.json` file, run:
```
npm init
```
This will ask some question to set up the file like the author, package name, etc. You can accept the default parameters or add custome ones.
When you complete those steps, you will see the `package.json` file in the root of your project.

### Install ESlint
You can install Eslint using `npm` or `yarn`:
```
npm install eslint --save-dev
```
```
yarn add eslint --dev
```
This will create the `node-modules` folder and `package-lock.json` file.


Now create the `.eslintrc.json` configuration file with:
```
npx eslint --init
```
This will prompt a dialog with some question to configure the file. A sample configuration could be:
```
? How would you like to use ESLint?
  To check syntax only
  To check syntax and find problems
❯ To check syntax, find problems, and enforce code style
```
```
? What type of modules does your project use? (Use arrow keys)
❯ JavaScript modules (import/export)
  CommonJS (require/exports)
  None of these
```
```
? Which framework does your project use?
  React
  Vue.js
❯ None of these
```
```
? Does your project use TypeScript? (y/N) N
```
```
? Where does your code run?
❯◉ Browser
 ◯ Node
```
```
? How would you like to define a style for your project?
❯ Use a popular style guide
  Answer questions about your style
  Inspect your JavaScript file(s)
```
```
? Which style guide do you want to follow? (Use arrow keys)
❯ Airbnb: https://github.com/airbnb/javascript
  Standard: https://github.com/standard/standard
  Google: https://github.com/google/eslint-config-google
```
```
? What format do you want your config file to be in?
  JavaScript
  YAML
❯ JSON
```

Depending if you followed the options above, ESlint will install some additional packages like `eslint-plugin-import` and `eslint-config-airbnb-base`.

### Set up `.eslintrc` file

When Eslint is installed, you will get a `.eslintrc` like this:
```
{
    "env": {
        "browser": true,
        "es6": true
    },
    "extends": [
        "airbnb-base"
    ],
    "globals": {
        "Atomics": "readonly",
        "SharedArrayBuffer": "readonly"
    },
    "parserOptions": {
        "ecmaVersion": 2018,
        "sourceType": "module"
    },
    "rules": {
    }
}
```
In this file we need add the `eslint:recommended` option in the `extends` parameter to get ESlint check our project.


## Stickler
Stickler set up involves 4 main actions:
* Enable Stickler app on GitHub
* Turn on GitHub repository on Stickler
* Add `.stickler.yml` file to the project root
* Add `.eslint.config` file to the project root

You can find the step by step set up [here](https://github.com/microverseinc/linters-config/tree/master/javascript#set-up-stickler-github-app---it-will-show-that-your-app-is-free-from-style-errors)

As additional note if you want Stickler to use the `.eslintrc` ESlint created to check your project locally, you can change the `config` attribute in the `.stickler.yml` file from `./eslint.config` to `./.eslintrc`:
```
linters:
  eslint:
    # replace
    config: './eslint.config'
    # with
    config: './.eslintrc'
```
