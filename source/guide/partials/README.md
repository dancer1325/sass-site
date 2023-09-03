# [partials](https://sass-lang.com/guide/#partials)

## How to preprocess SAAS files?
* partials
  * `sass _partial.scss partialSCSS.css`
    * no .css file is generated, since it's partial
  * `sass _partial.sass partialSAAS.css`
    * no .css file is generated, since it's partial
* no partials
  * `sass main.scss mainSCSS.css`
  * `sass main.sass mainSASS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
