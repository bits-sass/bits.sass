# Bits.scss

A structural UI toolkit based on Nicolas Gallagher's SUIT and written using SASS.

Practically a fork of Nicolas Gallagher's [SUIT](https://github.com/suitcss) rewritten using [SASS](http://sass-lang.com/)
and considerably extended.

## Installation

__Bower:__ `bower install --save bits-scss`

This command installs all subpackages. See the list below.

## Packages

Each package is stand-alone, contains its own documentation and tests, and is written to follow
a common set of [naming conventions and authoring practices](docs/overview.md).
Dependencies are best managed using [Bower](http://bower.io) – a package manager for the web.

__Utilities__: [all](https://github.com/bits-scss/utils), [detailed info](https://github.com/bits-scss/docs/utilities.md)

* [Dimension](https://github.com/bits-scss/utils-dimension)
* [Display](https://github.com/bits-scss/utils-display)
* [Image](https://github.com/bits-scss/utils-image)
* [Layout](https://github.com/bits-scss/utils-layout)
* [Link](https://github.com/bits-scss/utils-link)
* [Offset](https://github.com/bits-scss/utils-offset)
* [Space](https://github.com/bits-scss/utils-space)
* [State](https://github.com/bits-scss/utils-state)
* [Text](https://github.com/bits-scss/utils-text)

__Mixins__: [all](https://github.com/bits-scss/mixins)

* [Miscellaneous](https://github.com/bits-scss/mixins-misc)
* [Text](https://github.com/bits-scss/mixins-text)

__Components__: [detailed info](https://github.com/bits-scss/docs/components.md)

* [Arrange](https://github.com/bits-scss/arrange)
* [Button](https://github.com/bits-scss/button)
* [Button group](https://github.com/bits-scss/button-group)
* [Flexible embeds](https://github.com/bits-scss/flex-embed)
* [Grid](https://github.com/bits-scss/grid)
* [Grid layouts](https://github.com/bits-scss/grid-layouts)

__Themes__:

* TBA

## Features

**[Read about the design decisions and authoring principles of Bits.scss](docs/overview.md)**.

* Highly modular; each module is individually versioned.
* Provides common, low-level utility classes.
* Provides common structural UI patterns.
* Responsive grid.
* Consistent class name conventions.
* Work more with HTML than CSS.
* Theme-independence.
* Designed for large web sites and applications.
* Easy to build your application's custom toolkit on top of Suit.
* Very small footprint.


## Why?

* Monolithic UI frameworks don't make it easy to use, share, and version
  specific UI traits and components.
* Complex applications need to loosely couple content, document semantics, and
  presentational structure to make it easier to change any layer while minimizing the
  impact on other layers.
* Complex applications need to clearly surface and scope the relationship
  between all HTML classes (and their attached styles and behaviour).
* Complex applications can accumulate technical debt when components are not
  kept independent of one-another, or the dependencies aren't clear.


## How?

* Build progressive enhancement into the UI layers themselves. Use low-level
  utilities to build up a skeleton UI.
* Codify the separation of responsibilities by using structured class names
  that reflect different purposes and relationships.
* Provide clear, constrained, and explicit authoring principles.
* Use multiple classes in HTML templates to combine styles.
* Organize discrete UI features into small, standalone packages / files.

## Requirements

* Sass 3.2+

## Browser support

* Google Chrome (latest)
* Opera (latest)
* Firefox 4+
* Safari 5+
* Internet Explorer 8+

