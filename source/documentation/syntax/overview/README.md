# [overview](https://sass-lang.com/documentation/syntax/)

## How to preprocess SAAS files?
* `sass syntaxOverview.scss mainSCSS.css`
* `sass syntaxOverview.sass mainSASS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
* `@mixin mixinName(VariablesToPass) {
  …
  }`
  * way to declare a mixin
  * by itself, once it's compiled -> nothing is generated in css
  * nexted mixins can be declared
* `@include mixinName(variable)`
  * way to use a mixin
* `&`
  * parent selector
* `:hover` and `:disabled`
  * are CSS's pseudo-element selector
