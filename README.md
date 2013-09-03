# Bits.sass

A structural UI toolkit.

Practically a fork of Nicolas Gallagher's [SUIT](https://github.com/suitcss) rewritten using [SASS](http://sass-lang.com/)
and considerably extended.

See [documentation](docs/README.md).

## Installation

__Bower:__ `bower install --save bits-sass`

This command installs all subpackages. See the list below.

## Packages

Each package is stand-alone, contains its own documentation and tests, and is written to follow
a common set of [naming conventions](docs/naming-conventions.md).
Dependencies are best managed using [Bower](http://bower.io) – a package manager for the web.

__Utilities__: [all](https://github.com/bits-sass/utils), [detailed info](docs/utilities.md)

* [Dimension](https://github.com/bits-sass/utils-dimension) /
  [_responsive_](https://github.com/bits-sass/responsive-utils-dimension)
* [Display](https://github.com/bits-sass/utils-display) /
  [_responsive_](https://github.com/bits-sass/responsive-utils-display)
* [Image](https://github.com/bits-sass/utils-image)
* [Layout](https://github.com/bits-sass/utils-layout)
* [Link](https://github.com/bits-sass/utils-link)
* [Offset](https://github.com/bits-sass/utils-offset)
* [Space](https://github.com/bits-sass/utils-space) /
  [_responsive_](https://github.com/bits-sass/responsive-utils-space)
* [State](https://github.com/bits-sass/utils-state)
* [Text](https://github.com/bits-sass/utils-text)

__Helpers__: [all](https://github.com/bits-sass/helpers)

* [Miscellaneous](https://github.com/bits-sass/helpers-misc)
* [Responsive](https://github.com/bits-sass/helpers-responsive)
* [Text](https://github.com/bits-sass/helpers-text)

__Components__: [detailed info](docs/components.md)

* [Arrange](https://github.com/bits-sass/arrange) /
  [_responsive_](https://github.com/bits-sass/responsive-arrange)
* [Button](https://github.com/bits-sass/button)
* [Button group](https://github.com/bits-sass/button-group)
* [Flexible embeds](https://github.com/bits-sass/flex-embed)
* [Grid](https://github.com/bits-sass/grid) /
  [_responsive_](https://github.com/bits-sass/responsive-grid)

## Features

* Very small footprint.
* Individually versioned modules.
* Provides common, utility classes.
* Provides common, structural UI patterns.
* Consistent class name conventions.
* Testing friendly.
* Responsive friendly.
* Work more with HTML than CSS.
* Theme-independence.
* Designed for teams working on large web sites and applications.
* Easy to extend and build upon.


## Example

HTML:

```html
<article class="app-Excerpt u-cf">
  <img class="app-Excerpt-thumbnail u-sizeFit" src="{src}" alt="">
  <div class="u-sizeFill">
    <h1 class="app-Excerpt-title u-textGamma"><a href="{url}">{content}</a></h1>
    <p class="app-Excerpt-text">{content}</p>
  </div>
</article>
```

CSS:

```css
/**
 * Excerpt component
 *
 * @require u-cf
 * @require u-sizeFit
 * @require u-sizeFill
 *
 * <article class="app-Excerpt u-cf">
 *   <img class="app-Excerpt-thumbnail u-sizeFit" src="{src}" alt="">
 *   <div class="u-sizeFill">
 *     <h1 class="app-Excerpt-title">{content}</h1>
 *     <p class="app-Excerpt-text">{content}</p>
 *   </div>
 * </article>
 */

.app-Excerpt {
  line-height: 1.2857em;
}

.app-Excerpt-thumbnail {
  margin-right: 10px;

  border: 2px solid #000;
  border-radius: 3px;
}

.app-Excerpt-title {
  margin: 0 0 15px;
  padding-bottom: 5px;

  border-bottom: 1px solid #ccc;
}
```


## Suggested tooling

* [autoprefixer](https://github.com/ai/autoprefixer)
* [csslint](https://github.com/stubbornella/csslint)
* [html-inspector](https://github.com/philipwalton/html-inspector)
* [rework](https://github.com/visionmedia/rework)


## Browser support

* Google Chrome (latest)
* Opera (latest)
* Firefox 4+
* Safari 5+
* Internet Explorer 8+