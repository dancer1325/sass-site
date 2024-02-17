# [@mixin and @include](https://sass-lang.com/documentation/at-rules/mixin/)

# Arguments
* Check 'arguments.scss' / 'arguments.sass'
* allows
  * trailing `,`
  * default values → optionals to be passed afterwards
* positional arguments
  * if you rename a mixin’s arguments → it might break
* keyword arguments
  * can NOT be passed before position arguments
* arbitrary number of arguments
  * `$ArgumentName…`
  * valid for
    * `@mixin`
    * `@include`
  * valid to pass
    * positional arguments 
    * keyword arguments
    

## How to preprocess SAAS files?
* `sass arguments.scss argumentsSCSS.css`
* `sass arguments.sass argumentsSAAS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
* Check '../guide/mixin'

