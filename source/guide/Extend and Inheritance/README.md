# [Extend and inheritance](https://sass-lang.com/guide/#inheritance)

## How to preprocess SAAS files?
* `sass extendAndInheritance.scss extendAndInheritance.css`
* `sass extendAndInheritance.sass extendAndInheritance.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
* Placeholder class
  * `%placeHolderClassName {
    …
    }`
  * used with extended / inheritance
    * once the placeholder class is extended -> it's generated
    * if the placeholder class is not extended → not generated in the .css
* Extend / Inheritance
  * `@extend placeHolderClassName`
