# &lt;base&gt;

### Description

The HTML `<base>` tag is used to specify a base URI/URL for relative links. For example, you can specify the base link once, and then all the relative links will use that URL as a starting point.

**ℹ️ The `<base>` tag must be between the document's `<head>` tags. Also, there must be no more than one base element per document.**

### **Example**

```markup
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />

    <title>Test Site</title>

    <base href="https://example.com/" target="_blank" />
  </head>
  <body>
    <p>Hello! <a href="hello">Check this out.</a></p>
  </body>
</html>
```

### Read more

* [MDN \| HTML Base Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/base)

