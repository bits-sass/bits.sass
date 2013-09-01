# Architecture

## Main.scss

Make use of `@import` to include variables, utilities, helpers, components in
your main.scss file. Here is a sample main.scss:

```scss
/* main.scss */

/* Variables
   ========================================================================== */

/* Global */

@import "variables/global";

/* Base */

@import "variables/base/…";

/* Helpers */

@import "variables/helpers/…";

/* Components */

@import "variables/components/…";

/* Utilities */

@import "variables/utils/…";

/* Helpers
   ========================================================================== */

/* Stand-alone packages */

@import "../bower_components/…";

/* App-specific helpers */

@import "helpers/…";

/* Base styles
   ========================================================================== */

/* Normalize.css */

@import "../bower_components/normalize-css/normalize.scss";

/* Stand-alone packages */

@import "../bower_components/…";

/* App-specific base */

@import "base/…";

/* Utilities
   ========================================================================== */

/* Stand-alone packages */

@import "../bower_components/…";

/* Core */

@import "core/utils/…";

/* Theme */

@import "theme/utils/…";

/* Components
   ========================================================================== */

/* Stand-alone packages */

@import "../bower_components/…";

/* Core */

@import "core/components/…";

/* Theme */

@import "theme/components/…";

/* Shame file for quick fixes / hacks
   ========================================================================== */

@import "shame";
```

You should create a IE 8 specific stylesheet to support media queries.


## Organization

To faciliate code reuse, easy refactoring, and better separate components:

1. Each new group of utilities should exist in a separate file.
2. Each independent component should exist in its own file or package.
3. App-level utility and component files should be kept separate from
   app-agnostic utility and component files. This distinction is reified only
   via 2 top level directories that separate files based on a 'core' and a
   'theme'. The 'bower_components' directory should contain stand-alone
   packages.

Files that are particularly important and/or fundamental to the app structure
can be placed in 'core'. When diffs contain changes to 'core' it should
accurately reflect the potential for a significant, structural part of the UI
to be affected. As such, files in 'core' should end up being modified at a
slower rate than those in 'theme'.

It is possible that the 'core' directory may contain only a few files because
of the usage of bower (and its 'bower_components' directory).

For example:

```
scss
├── _shame.scss
├── main.scss
├── base
|   ├── _typography.scss
|   └── _forms.scss
├── core
|   ├── components
|   |   ├── _button.scss
|   |   ├── _button-group.scss
|   |   └── _grid.scss
|   └── utils
|       ├── _dimension.scss
|       ├── _display.scss
|       ├── _layout.scss
|       └── _text.scss
├── helpers
|   ├── _transition.scss
|   └── _text.scss
├── theme
|   ├── components
|   |   ├── _button.scss
|   |   └── _stream-item.scss
|   └── utils
|       ├── _link.scss
|       └── _text.scss
└── variables
    ├── _global.scss
    ├── base
    |   ├── _typography.scss
    |   ├── _forms.scss
    ├── components
    |   ├── _button.scss
    |   ├── _button-group.scss
    |   └── _grid.scss
    ├── helpers
    |   ├── _transition.scss
    |   └── _text.scss
    └── utils
        ├── _dimension.scss
        ├── _display.scss
        ├── _layout.scss
        └── _text.scss
```

You'll notice that both 'core' and 'theme' contain 'utils' and 'components'
directories. To change a file from 'theme' to 'core' (and vice versa) requires
only a change of top-level directory. Therefore, it's easy to move files
between the 'theme' and 'core' when appropriate. If a component in 'theme' turns
out to be better suited in 'core', then making the change shouldn't be too
difficult.

The files in 'core', 'theme' and 'bower_components' (or any other external dir)
should be `@import`ed in following order:

```scss
/* Stand-alone packages */

@import "../bower_components/…";
@import "../whatever_components/…";

/* Core */

@import "core/utils/display";
@import "core/utils/text";

/* Theme */

@import "theme/utils/text";
```


## Build tools

Bits.sass relies on some form of build process to produce production-ready code.
CSS should be stripped of comments and minified.


## Related reading

* [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)
* [SOLID CSS](http://blog.millermedeiros.com/solid-css/)
* [Idiomatic CSS](https://github.com/necolas/idiomatic-css/)
* [Idiomatic HTML](https://github.com/necolas/idiomatic-html/)
