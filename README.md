# Bits.sass

A structural UI toolkit.

Practically a fork of Nicolas Gallagher's [SUIT](https://github.com/suitcss) rewritten using [SASS](http://sass-lang.com/)
and considerably extended.

## Installation

__Bower:__ `bower install --save bits-sass`

This command installs all subpackages. See the list below.

## Packages

Each package is stand-alone, contains its own documentation and tests, and is written to follow
a common set of [naming conventions and authoring practices](docs/overview.md).
Dependencies are best managed using [Bower](http://bower.io) – a package manager for the web.

__Utilities__: [all](https://github.com/bits-sass/utils), [detailed info](https://github.com/bits-sass/docs/utilities.md)

* [Dimension](https://github.com/bits-sass/utils-dimension)
* [Display](https://github.com/bits-sass/utils-display)
* [Image](https://github.com/bits-sass/utils-image)
* [Layout](https://github.com/bits-sass/utils-layout)
* [Link](https://github.com/bits-sass/utils-link)
* [Offset](https://github.com/bits-sass/utils-offset)
* [Space](https://github.com/bits-sass/utils-space)
* [State](https://github.com/bits-sass/utils-state)
* [Text](https://github.com/bits-sass/utils-text)

__Mixins__: [all](https://github.com/bits-sass/mixins)

* [Miscellaneous](https://github.com/bits-sass/mixins-misc)
* [Responsive](https://github.com/bits-sass/mixins-responsive)
* [Text](https://github.com/bits-sass/mixins-text)

__Components__: [detailed info](https://github.com/bits-sass/docs/components.md)

* [Arrange](https://github.com/bits-sass/arrange)
* [Button](https://github.com/bits-sass/button)
* [Button group](https://github.com/bits-sass/button-group)
* [Flexible embeds](https://github.com/bits-sass/flex-embed)
* [Grid](https://github.com/bits-sass/grid)
* [Grid layouts](https://github.com/bits-sass/grid-layouts)

__Themes__:

* TBA

## Features

**[Read about the design decisions and authoring principles of Bits.sass](docs/overview.md)**.

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

