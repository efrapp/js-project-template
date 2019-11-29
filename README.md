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
