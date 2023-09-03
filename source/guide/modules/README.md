# [modules](https://sass-lang.com/guide/#modules)

## How to preprocess SAAS files?
* `sass main.scss mainSCSS.css`
* `sass main.sass mainSASS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
* Need to pass the namespace to get access to module's variables
* `@use`
  * replacement of `@import` rule
