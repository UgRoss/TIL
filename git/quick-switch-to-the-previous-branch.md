# Quick switch to the previous branch



```bash
git checkout @{-1}
# or
git checkout - # equivalent to @{-1}
```

This will move you back to the branch you were on previously.

> You can use the @{-N} syntax to refer to the N-th last branch/commit checked out using "git checkout" operation. You may also specify - which is synonymous to @{-1}.

### Read More

[Git documentation](https://git-scm.com/docs/git-checkout#Documentation/git-checkout.txt-ltbranchgt)

