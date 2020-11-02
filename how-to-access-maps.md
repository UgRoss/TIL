# How to access Maps

The most common case of sass maps usage is just accessing them. It can be done with the help of `map-get($map, $key)` function.

Example:

```css
$breakpoints: (
  small: 767px,
  medium: 992px,
  large: 1200px
);

@media (min-width: #{map-get($breakpoints, $breakpoint)}) {
    ...
}
```

### Read More

* [Sass Maps](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#Maps)
* [Sass Interpolation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#Interpolation_____)
* [Sass `map-get` function](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_get-instance_method) 

