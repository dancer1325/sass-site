# [Mixins](https://sass-lang.com/guide/#mixins)

# := Directive which
* allows grouping CSS declarations
  * -> 
    * reusable
    * avoid using non-semantic classes
  * arguments can be passed
  * they can be nested
* `@mixin mixinName(VariablesToPass) {
    …
    }`
  * way to declare a mixin
  * by itself, once it's compiled -> nothing is generated in css
  * body can contain any statement, except to top-level statements
  * `mixinName`
    * non-sensitive to  `-` or `_`
* `@include mixinName(VariablesToPass)`
  * way to use a mixin

## How to preprocess SAAS files?
* `sass mixin.scss mixinSCSS.css`
* `sass mixin.sass mixinSAAS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher

