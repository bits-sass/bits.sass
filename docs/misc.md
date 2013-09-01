# Miscellaneous considerations

## Working with JavaScript

### js-someName

Use the `id` attribute and `js-*` class names are reserved for JavaScript-only
use. Application-specific data or content can be stored in `data-*`
attributes.

* JavaScript may use any component-level classes in selectors.
* JavaScript may add/remove the component-level state class `is-expanding`.
* JavaScript may add/remove utilities classes.
* JavaScript may JavaScript-specific utility classes prefixed with `js-`.

The example below includes a dedicated JavaScript utility class to which
behaviour is bound. It is independent of any specific UI component.

```html
<a class="js-showProfile" data-user-id="22" href="{url}">...</a>
```