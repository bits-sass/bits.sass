# Responsive web design

Most Bits.sass's utilities and components have a responsive counterpart. They
duplicate their original functionality, but have a `v[n]-` prefix and are
applied only on `n` breakpoint.

```scss
@media only screen and (min-width: 40em) {
  .v4-u-size2of5 { /* same as .u-size2of5 */ }
  .v4-Button { /* same as .Button + !important */ }
  .v4-Arrange--middle { /*  same as .Arrange--middle + !important */ }
}
```

This way, application responsive design can be controlled directly via HTML
classes making you spend less time writting CSS.

## Important considerations

* All properties should have `!important` so they override random component's
styling
* Original descendants should be included in component modifiers, ie.:

```scss
@media only screen and (min-width: 40em) {
  .v4-Arrange { /* … */ }

  .v4-Arrange--middle {
    .Arrange-sizeFit,
    .Arrange-sizeFill,
    .v4-Arrange-sizeFit,
    .v4-Arrange-SizeFill {
      vertical-align: middle !important;
    }
  }
}
```

## How to

Every responsive counterpart should be in a separate file. All the styles
need to be inside a mixin that takes breakpoint name as an argument.

Grid component example:

```scss
@mixin bits-grid-responsive($breakpoint) {
  $prefix: unquote("#{$bits-components-ns}#{$breakpoint}-"); /* bits-v[n]- */

  .#{$prefix}Grid {
    display: block !important;
    padding: 0 !important;
    margin: 0 !important;

    text-align: left !important;
    text-rendering: optimizespeed;
    letter-spacing: -0.31em !important;
  }

  .opera:-o-prefocus,
  .#{$prefix}Grid {
    word-spacing: -0.43em !important;
  }

  .#{$prefix}Grid-cell {
    -moz-box-sizing: border-box !important;
    box-sizing: border-box !important;
    display: inline-block !important;
    margin: 0 !important;
    padding: 0 !important;
    width: 100% !important;
    vertical-align: top !important;

    text-align: left !important;
    text-rendering: auto !important;
    letter-spacing: normal !important;
    word-spacing: normal !important;
  }
}
```

The mixin can be included via an @each loop

```scss
$grid-breakpoints: v2 v3 v4 v5 v6;

@each $bp in $grid-breakpoints {
  @include breakpoint($bp) {
    @include bits-grid-responsive($bp);
  }
}
```

Here, `breakpoint` mixin from `bits-sass-helpers-responsive` handles including
the right media query based on breakpoint name.