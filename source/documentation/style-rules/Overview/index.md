---
title: Style Rules
table_of_contents: true
introduction: >
  Style rules are the foundation of Sass, just like they are for CSS. And they
  work the same way: you choose which elements to style with a selector, and
  [declare properties](/documentation/style-rules/declarations) that affect how
  those elements look.
---

{% codeExample 'style-rules' %}
  .button {
    padding: 3px 10px;
    font-size: 12px;
    border-radius: 3px;
    border: 1px solid #e1e4e8;
  }
  ===
  .button
    padding: 3px 10px
    font-size: 12px
    border-radius: 3px
    border: 1px solid #e1e4e8
{% endcodeExample %}

## Nesting

But Sass wants to make your life easier. Rather than repeating the same
selectors over and over again, you can write one style rules inside another.
Sass will automatically combine the outer rule's selector with the inner rule's.

{% render 'code_snippets/example-nesting' %}

{% headsUp %}
  Nested rules are super helpful, but they can also make it hard to visualize
  how much CSS you're actually generating. The deeper you nest, the more
  bandwidth it takes to serve your CSS and the more work it takes the browser to
  render it. Keep those selectors shallow!
{% endheadsUp %}

### Selector Lists

Nested rules are clever about handling selector lists (that is, comma-separated
selectors). Each complex selector (the ones between the commas) is nested
separately, and then they're combined back into a selector list.

{% codeExample 'selector-lists' %}
  .alert, .warning {
    ul, p {
      margin-right: 0;
      margin-left: 0;
      padding-bottom: 0;
    }
  }
  ===
  .alert, .warning
    ul, p
      margin-right: 0
      margin-left: 0
      padding-bottom: 0
{% endcodeExample %}

### Selector Combinators

You can nest selectors that use [combinators][] as well. You can put the
combinator at the end of the outer selector, at the beginning of the inner
selector, or even all on its own in between the two.

[combinators]: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors#Combinators#Combinators

{% codeExample 'selector-combinators' %}
  ul > {
    li {
      list-style-type: none;
    }
  }

  h2 {
    + p {
      border-top: 1px solid gray;
    }
  }

  p {
    ~ {
      span {
        opacity: 0.8;
      }
    }
  }
  ===
  ul >
    li
      list-style-type: none



  h2
    + p
      border-top: 1px solid gray



  p
    ~
      span
        opacity: 0.8
{% endcodeExample %}

### Advanced Nesting

If you want to do more with your nested style rules than just combine them in
order with the descendant combinator (that is, a plain space) separating them,
Sass has your back. See the [parent selector documentation][] for more details.

[parent selector documentation]: /documentation/style-rules/parent-selector

## Interpolation

You can use [interpolation][] to inject values from [expressions][] like
variables and function calls into your selectors. This is particularly useful
when you're writing [mixins][], since it allows you to create selectors from
parameters your users pass in.

[interpolation]: /documentation/interpolation
[expressions]: /documentation/syntax/structure#expressions
[mixins]: /documentation/at-rules/mixin

{% codeExample 'interpolation' %}
  @mixin define-emoji($name, $glyph) {
    span.emoji-#{$name} {
      font-family: IconFont;
      font-variant: normal;
      font-weight: normal;
      content: $glyph;
    }
  }

  @include define-emoji("women-holding-hands", "👭");
  ===
  @mixin define-emoji($name, $glyph)
    span.emoji-#{$name}
      font-family: IconFont
      font-variant: normal
      font-weight: normal
      content: $glyph



  @include define-emoji("women-holding-hands", "👭")
{% endcodeExample %}

{% funFact %}
  Sass only parses selectors *after* interpolation is resolved. This means you
  can safely use interpolation to generate any part of the selector without
  worrying that it won't parse.
{% endfunFact %}

You can combine interpolation with the parent selector `&`, the [`@at-root`
rule][], and [selector functions][] to wield some serious power when dynamically
generating selectors. For more information, see the [parent selector
documentation][].

[`@at-root` rule]: /documentation/at-rules/at-root
[selector functions]: /documentation/modules/selector
[parent selector documentation]: /documentation/style-rules/parent-selector
