---
description: ℹ️ Use "git checkout -" to switch to the previous branch
---

# Quick switch to the previous branch

### Description

To move back to the branch you were on previously you can use:

```bash
git checkout @{-1}
# or
git checkout - # equivalent to @{-1}
```

> You can use the @{-N} syntax to refer to the N-th last branch/commit checked out using "git checkout" operation. You may also specify - which is synonymous to @{-1}.

### Read More

* [Git Docs](https://git-scm.com/docs/git-checkout#Documentation/git-checkout.txt-ltbranchgt)

