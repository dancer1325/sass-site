# [Preprocessing](https://sass-lang.com/guide/#preprocessing)

# Features no existing in CSS
* nesting
  * Check '../nesting'
* mixins
  * Check '../mixins'
* inheritance
  * Check '../Extend and inheritance'

# How does it work?
* '.sass' / '.scss' file — preprocessed to → '.css' file -- Check 'input.sass' & 'input.scss' --
  * `sass input.scss` / `sass input.sass` returns the generated .css
  * `sass input.scss outputFileToGenerate.css` / `sass input.sass outputFileToGenerate.css` generate a output .css file
  * `sass --watch stylesToWatch:./output` watch a folder of styles and also create the output folder if it does NOT exist

## Note
* If you use webstorm -> you can enable [some watcher plugin](https://www.jetbrains.com/help/webstorm/transpiling-sass-less-and-scss-to-css.html). _Example:_ File Watcher
