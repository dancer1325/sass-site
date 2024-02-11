# [Extend and inheritance](https://sass-lang.com/guide/#inheritance)

# Extend / Inheritance
* allows
  * CSS selector1's properties -- can be shared with -- CSS selector2's  

# Placeholder class
* := special type of class which
  * once it’s extended → it’s generated
    * == if it’s not extended → not generated in the .css

## How to preprocess SAAS files?
* `sass extendAndInheritance.scss extendAndInheritance.css`
* `sass extendAndInheritance.sass extendAndInheritance.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
* Placeholder class
  * `%placeHolderClassName {
    …
    }`
* Extend / Inheritance
  * `@extend placeHolderClassName`
