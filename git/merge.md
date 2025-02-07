# Merge

We need have multiple branches because they're most often used to safely make changes without affecting your (or your _team's_) primary branch. However, once you're happy with your changes, you'll want to [merge](https://git-scm.com/docs/git-merge) them back into the main branch so that they make their way into the final product.

We can merge our branch with another one like that.

```sh
$ git merge <branch-that-has-changes>
$ git push
```

From the `main` branch run `git log --oneline --decorate --graph --parents`. This 
should give you a nice visual representation of the merge commit.

```sh
$ git log --oneline --decorate --graph --parents
```