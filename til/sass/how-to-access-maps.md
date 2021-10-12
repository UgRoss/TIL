---
description: ℹ️ use "map-get($map, $key)' to get value from map.
---

# How to access Maps

### Description

To access a values from SASS Map use `map-get($map, $key)` function. This function returns the value associated with the given key.

### Example:

```scss
$breakpoints: (
  small: 767px,
  medium: 992px,
  large: 1200px
);


@media (min-width: #{map-get($breakpoints, "medium")}) {
  // ...
}
```

### Read More

* [Sass Maps](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#Maps)
* [Sass Interpolation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#Interpolation\_\_\_\_\_)
* [Sass `map-get` function](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_get-instance_method) 
