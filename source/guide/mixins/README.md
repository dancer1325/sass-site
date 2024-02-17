# [Mixins](https://sass-lang.com/guide/#mixins)

# := Directive which
* allows grouping CSS declarations
  * reusable
  * arguments can be passed
* `@mixin mixinName(VariablesToPass) {
    …
    }`
  * way to declare a mixin
  * by itself, once it's compiled -> nothing is generated in css
* `@include mixinName(VariablesToPass)`
  * way to use a mixin

## How to preprocess SAAS files?
* `sass mixin.scss mixinSCSS.css`
* `sass mixin.sass mixinSAAS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher

