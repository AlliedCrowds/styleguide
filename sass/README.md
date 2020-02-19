# SASS Style Guide

<p align="center"><img src="https://2.bp.blogspot.com/-41v6n3Vaf5s/UeRN_XJ0keI/AAAAAAAAN2Y/YxIHhddGiaw/s1600/css.gif" /></p>

## Preliminary

All CSS code written for AlliedCrowds should be using SASS for consistentcy inter-project. Never use `.scss`. Avoid inline CSS whenever style is used more than once.

## General Rules - Formatting

All indentation should be 2 spaces.

There should **always** be a space after a colon. Never before.

One selector per line, one rule per line.

```
.selector
  rule: value
```

Group related properties together, seperated by a line break.

```
font-size: 2em
color: red

width: 10px
height: 10px
```

Prefer dashes over camelCasing when naming classes.

Use hex colour codes `#000`. SASS’s `rgba()` function is overloaded to accept hex colours as a param, e.g., `rgba(#000, .5)`.

Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin: 0px;`.

Limit use of shorthand declarations to instances where you must explicitly set all the available values. This greatly improves readability of code.

Always use double quotes. Always wrap strings. Including font names. Do not wrap CSS identifiers in quotes (such as `initial` or `sans-serif`). URLs should also be quoted.

```scss
$direction: "left"
font-family: "Verdana", "Tahoma", sans-serif
```

Wrap lines to 80 characters. Lines should wrap to under their first parameter.

```css
.weather
  @include background("this is some test",
                      "really long test",
                      "really really long",
                      linear-test("really-long",
                                  "really-really-long"))
```

## List @extends First

```scss
.weather
  @extend .other-class
```

Knowing which classes a class inherits from always helps readability of code and also reduces bugs in code. Aim to stray away from @extends, however, if multiple classes and extending the same class, consider mixins.

## List @includes Next

```scss
.weather
  @extend .other-class
  @include transition(all 0.3s ease-out)
```

Next up is your @includes for mixins and other functions. Again, this is nice to have near the top for reference, but also allows for overrides. You might also want to make the call on separating user-authored @includes and vendor-provided @includes.

## After that is your normal rules

```scss
.weather@extend .other-class
  @include transition(all 0.3 ease-out)
  background: blue;
```

This allows us to override anything from the extends or the includes above.

## Nested Psuedo Classes and Elements Next

```scss
.weather
  @extends .other-class
  @include transition(all 0.3 ease-out)
  background: blue

  &:hover
    background: red

  &::before
    content: ""
    display: block
```

Seperate these rules with a single line break. These line breaks should be empty lines, there should be no spaces on these lines.

## Nested Selectors Last

```scss
.weather
  @extends .other-class
  @include transition(all 0.3 ease-out)
  background: blue

  &:hover
    background: red

  &::before
    content: ""
    display: block

  > div
    @include transform(rotate(90deg))
    border-bottom: 1px solid white

    > h3
      display: block
      color: red

  > p
    background: blue
```

Again, these should be seperated by a single line break. Nothing goes after the nested elements. The same order as above should be applied to nested selectors, too.

## Never Write Vendor Prefixes

Autoprefixer handles all that for us. Vendor prefixes slow down development.

Use @mixins whenever possible given to you by Bourbon.

## Break Into As Many Small Files As Makes Sense

There is no penalty to splitting into many small files and this helps the readability of the code

## Partials are named \_partial.scss

This is a common naming convention that indicates this file isn't meant to be compiled by itself. It likely has dependencies that would make it impossible to compile by itself.

Seperate file names using a dash.

## Be Generous With Comments

Use `//` to comment lines. Do not use end of comment lines. Most code should be self-explanatory but there's times where comments are definitely needed, when using `z-index` for example. Space after `//` and always capitalize first letter.

## Variablise All Colours

Chances are a colour isn't one-off, and even if you think it is, once it's in a variable you might see uses for it elsewhere. Variations on that colour can often be handled by Sass mixins like lighten() and darken() - which make updating colours easier.

Magic numbers should also be avoided at all costs, if this is not possible they should be variablised.

## Calculations

Calculations should **always** be wrapped in parentheses with a single space surrounding the operator.

```
.foo
  width: (100% / 3)
```
