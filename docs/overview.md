# Overview

Bits.sass aims to loosely couple document semantics, presentation, and behaviour so
as to be able to modify any one of them with minimal impact on the others.

1. Write less CSS by codifying common structural and stylistic patterns in a way
   that allows them to be reused in different contexts.

2. Use HTML as the place where traits are combined. Tend towards applying HTML
   classes directly to the elements you want to affect.

3. Write small, independent, content-agnostic packages with few, known
   dependencies as opposed to monolithic frameworks, toolkits, or UI parts.

4. Avoid content-derived HTML class names as these cannot be design- and
   content-agnostic.


## Architecture overview

Bits.sass uses "meaningful hyphens" in HTML class names. At least one hyphen is used
to separate types and names, but not words. All component names must use "Pascal
case"; all other names must be "Camel case".

Although the major architectural division is between **utilities** and
**components**, a layer of finer separation of responsibilities is build upon
it.

There are 5 distinct prefixes that are used for all class names that aren't for
components. This helps to identify their specific responsibility.

* `u-`: A utility.
* `u-is`: A state-utility.
* `is-`: A custom, component-state (scoped to the component).
* `with-`: A component mixin.
* `js-`: A JavaScript hook (not for CSS use).

The complete set of naming patterns is as follows:

**Utilities**: [see more](utilities.md)

* `u-utilityName`
* `u-isGlobalStateName`

**Components**: [see more](components.md)

* `ComponentName`
* `ComponentName--modifierName`
* `ComponentName-descendantName`
* `is-stateOfComponent`
* `with-ComponentName`

**Misc**: [see more](misc.md)

* `js-aName`

### Namespace

All components and utilities use a default namespace of 'bits-'. This can be
overridden by setting `bits-components-ns` or `bits-utils-ns` variables
to a different value.

## Authoring guidelines

Bits.sass aims to make it easier for teams to work with, and reuse, HTML/CSS.

* Favour readable and understand class names for components and their
  constituent parts. Use names that are as short as possible but as long as
  necessary.

* Use short, low-specificity CSS selectors.

* Limit the scope of style inheritance in your components, e.g., use `.Grid >
  .Grid-cell` rather than `.Grid .Grid-cell`.

* Use classes rather than tags in selectors, as much as is practical, e.g., use
  `.List-item` rather than `.list li`. This helps make components more reusable
  and robust.

Trait composition takes place on the element:

```html
<div class="ComponentName u-utilityName">
```

If you need to adjust a generic component within your specific component, do
not hijack it or scope the adjustment within your component. Create a new part
of YOUR component that will take care of the adjustment, and then add your hook
to the HTML element.

BAD:

```html
<div class="Tweet">
  <i class="Icon Icon--retweet"></i>
  …
</div>
```

```scss
/* In _tweet.scss */
.Tweet .Icon {
  position: absolute;
  top: 0;
}
```

GOOD:

```html
<div class="Tweet">
  <i class="Tweet-icon Icon Icon--retweet"></i>
  …
</div>
```

```scss
/* In _tweet.scss */
.Tweet-icon {
  position: absolute;
  top: 0;
}
```

If your component can be affected by a state change in a parent component
(e.g., a `:hover` or `:focus` interaction), then you may depend on the parent
component's class in your component's CSS file. In general, a ruleset should
always be in the file of the component that matches the last class in the
selector. For example:

```scss
/**
 * These styles are in the '_tweet.scss' component file because the last
 * class in each rule is for a descendant element of the 'Tweet' component.
 */

.StreamItem:hover {
  .Tweet-icon {
    color: red;
  }
}

.StreamItem.is-collapsed:hover {
  .Tweet-actions {
    visibility: visible;
  }
}
```

## Main.scss

Make use of `@import` to include variables, utilities, helpers, components and in your
main.scss file. Here is a sample main.scss:

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

@import "../bower_components/normalize-css/normalize.css";

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

Your build process should inline the CSS and wrap it any specified Media
Queries (you should create a production build of your CSS that omits Media
Queries if you require IE 8 support).


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
Imports should be inlined, CSS should be stripped of comments and minified, and
Media Queries should wrap the code from every import that appends them.


## Related reading

* [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)
* [SOLID CSS](http://blog.millermedeiros.com/solid-css/)
* [Idiomatic CSS](https://github.com/necolas/idiomatic-css/)
* [Idiomatic HTML](https://github.com/necolas/idiomatic-html/)
