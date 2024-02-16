# [parent selector](https://sass-lang.com/documentation/parent-selector/)

# := special CSS Selector
* allows
  * in nesting to refer to the outer selector
    * nesting behavior does NOT happen
    * replace the outer selector
* in compound selectors, just allowed at the beginning!!

# Uses
* pseudo-class to the outer selector
* adding extra suffixes to the outer selector
* within SassScript -- Check '../syntax/structureOfSytleSheet'
  * returns the current parent selector
    * if it’s used outside any CSS ruleset → null == falsey
  * + `@at-root` -> powerful nest selectors

## How to preprocess SAAS files?
* `sass parentSelector.scss mainSCSS.css`
* `sass parentSelector.sass mainSASS.css`

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
  * Sometimes it fails, although the syntax is correct -> you need to compile manually
* [dir](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/dir)
* [[]](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)
* [BEM](https://getbem.com/)
* [Interpolation](https://sass-lang.com/documentation/interpolation/)
* [mixins](https://sass-lang.com/guide/#mixins)
* [each](https://sass-lang.com/documentation/at-rules/control/each/)
* [&](https://sass-lang.com/documentation/style-rules/parent-selector/)
* [transition](https://developer.mozilla.org/en-US/docs/Web/CSS/transition)
* [:](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
  * [:root](https://developer.mozilla.org/en-US/docs/Web/CSS/:root)
* [if](https://sass-lang.com/documentation/at-rules/control/if/)
* [--*](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)

