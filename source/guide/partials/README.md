# [partials](https://sass-lang.com/guide/#partials)

# := Little snippets of CSS to be included in other Sass files
* Check '_partialsass.sass' / '_partialsass.scss'
* === no .css file is generated
  * `sass _partial.scss partialSCSS.css` / `sass _partial.sass partialSAAS.css`
    * generate empties '.css' 
* can be loaded in others stylesheets with
  * `@use` or
  * `@import`

## How to preprocess SAAS files?
* no partials
  * `sass main.scss mainSCSS.css`
  * `sass main.sass mainSASS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
* You can refer directly to the variable defined in the partial file
