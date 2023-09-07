---
title: Property Declarations
table_of_contents: true
introduction: >
  In Sass as in CSS, property declarations define how elements that match a
  selector are styled. But Sass adds extra features to make them easier to write
  and to automate. First and foremost, a declaration's value can be any
  [SassScript expression](/documentation/syntax/structure#expressions), which
  will be evaluated and included in the result.
---

{% codeExample 'declaration' %}
  .circle {
    $size: 100px;
    width: $size;
    height: $size;
    border-radius: $size * 0.5;
  }
  ===
  .circle
    $size: 100px
    width: $size
    height: $size
    border-radius: $size * 0.5
{% endcodeExample %}

## Interpolation

A property's name can include [interpolation][], which makes it possible to
dynamically generate properties as needed. You can even interpolate the entire
property name!

[interpolation]: /documentation/interpolation

{% codeExample 'interpolation' %}
  @mixin prefix($property, $value, $prefixes) {
    @each $prefix in $prefixes {
      -#{$prefix}-#{$property}: $value;
    }
    #{$property}: $value;
  }

  .gray {
    @include prefix(filter, grayscale(50%), moz webkit);
  }
  ===
  @mixin prefix($property, $value, $prefixes)
    @each $prefix in $prefixes
      -#{$prefix}-#{$property}: $value

    #{$property}: $value


  .gray
    @include prefix(filter, grayscale(50%), moz webkit)
{% endcodeExample %}

## Nesting

Many CSS properties start with the same prefix that acts as a kind of namespace.
For example, `font-family`, `font-size`, and `font-weight` all start with
`font-`. Sass makes this easier and less redundant by allowing property
declarations to be nested. The outer property names are added to the inner,
separated by a hyphen.

{% codeExample 'nesting' %}
  .enlarge {
    font-size: 14px;
    transition: {
      property: font-size;
      duration: 4s;
      delay: 2s;
    }

    &:hover { font-size: 36px; }
  }
  ===
  .enlarge
    font-size: 14px
    transition:
      property: font-size
      duration: 4s
      delay: 2s

    &:hover
      font-size: 36px
{% endcodeExample %}

Some of these CSS properties have shorthand versions that use the namespace as
the property name. For these, you can write both the shorthand value *and* the
more explicit nested versions.

{% codeExample 'nesting-shorthand' %}
  .info-page {
    margin: auto {
      bottom: 10px;
      top: 2px;
    }
  }
  ===
  .info-page
    margin: auto
      bottom: 10px
      top: 2px
{% endcodeExample %}

## Hidden Declarations

Sometimes you only want a property declaration to show up some of the time. If a
declaration's value is [`null`][] or an empty [unquoted string][], Sass won't
compile that declaration to CSS at all.

[`null`]: /documentation/values/null
[unquoted string]: /documentation/values/strings#unquoted

{% codeExample 'hidden-declarations' %}
  $rounded-corners: false;

  .button {
    border: 1px solid black;
    border-radius: if($rounded-corners, 5px, null);
  }
  ===
  $rounded-corners: false

  .button
    border: 1px solid black
    border-radius: if($rounded-corners, 5px, null)
{% endcodeExample %}

## Custom Properties

{% compatibility 'dart: true', 'libsass: "3.5.0"', 'ruby: "3.5.0"', 'feature: "SassScript Syntax"' %}
  Older versions of LibSass and Ruby Sass parsed custom property declarations
  just like any other property declaration, allowing the full range of
  SassScript expressions as values. Even when using these versions, it's
  recommended that you use interpolation to inject SassScript values for
  forwards-compatibility.

  See [the breaking change page][] for more details.

  [the breaking change page]: /documentation/breaking-changes/css-vars
{% endcompatibility %}

[CSS custom properties][], also known as CSS variables, have an unusual
declaration syntax: they allow almost any text at all in their declaration
values. What's more, those values are accessible to JavaScript, so any value
might potentially be relevant to the user. This includes values that would
normally be parsed as SassScript.

[CSS Custom Properties]: https://developer.mozilla.org/en-US/docs/Web/CSS/--*

Because of this, Sass parses custom property declarations differently than other
property declarations. All tokens, including those that look like SassScript,
are passed through to CSS as-is. The only exception is [interpolation][], which
is the only way to inject dynamic values into a custom property.

[interpolation]: /documentation/interpolation

{% codeExample 'custom-properties' %}
  $primary: #81899b;
  $accent: #302e24;
  $warn: #dfa612;

  :root {
    --primary: #{$primary};
    --accent: #{$accent};
    --warn: #{$warn};

    // Even though this looks like a Sass variable, it's valid CSS so it's not
    // evaluated.
    --consumed-by-js: $primary;
  }
  ===
  $primary: #81899b
  $accent: #302e24
  $warn: #dfa612

  :root
    --primary: #{$primary}
    --accent: #{$accent}
    --warn: #{$warn}

    // Even though this looks like a Sass variable, it's valid CSS so it's not
    // evaluated.
    --consumed-by-js: $primary
{% endcodeExample %}

{% headsUp %}
  Unfortunately, [interpolation][] removes quotes from strings, which makes it
  difficult to use quoted strings as values for custom properties when they come
  from Sass variables. As a workaround, you can use the [`meta.inspect()`
  function][] to preserve the quotes.

  [interpolation]: /documentation/interpolation
  [`meta.inspect()` function]: /documentation/modules/meta#inspect

  {% codeExample 'custom-properties-strings-meta' %}
    @use "sass:meta";

    $font-family-sans-serif: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto;
    $font-family-monospace: SFMono-Regular, Menlo, Monaco, Consolas;

    :root {
      --font-family-sans-serif: #{meta.inspect($font-family-sans-serif)};
      --font-family-monospace: #{meta.inspect($font-family-monospace)};
    }
    ===
    @use "sass:meta"

    $font-family-sans-serif: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto
    $font-family-monospace: SFMono-Regular, Menlo, Monaco, Consolas

    :root
      --font-family-sans-serif: #{meta.inspect($font-family-sans-serif)}
      --font-family-monospace: #{meta.inspect($font-family-monospace)}
  {% endcodeExample %}
{% endheadsUp %}
