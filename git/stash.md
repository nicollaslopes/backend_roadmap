# Stash

If we want to save a change that has been made to continue later, we can use `stash`to do so. The file will go back to to the way it was before it was modified, and the changes will be saved in a "separate local" or "stash" to be used whenever you want.

```sh
$ git add .
$ git stash

# to see what is saved in the stash
$ git stash list
```

There are two ways to restore the changes, with `apply` and `pop`. `Apply` will return with the changes but will still be saved in `stash` (not recommended because it will accumulate a lot of garbage). and the `pop` will return the changes and remove from the `stash list`.

```sh
$ git stash apply

# if we want to clrear the list
$ git stash clear
```

Or using pop.

```sh
$ git stash pop

# to pop a specific stash
$ git stash pop stash@{1}
$ git stash pop stash@{2}
```
