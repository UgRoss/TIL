---
description: ℹ️ Use copy(VALUE) to copy value to the clipboard
---

# You can copy\(\) from the console

### Description

`copy()` can be used inside Chrome/Firefox DevTools to copy specified value or object to the clipboard.

### Example

```javascript
const movie = {
  title: 'Guardians of the Galaxy',
  year: 2014,
  runningTime: 122,
  language: 'English',
}

// ⬇️ Copy movie object to the clipboard
copy(movie);
```

