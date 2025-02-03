# Branches

A **git branch** allows you to keep track of different changes separately. You can check which branch you're currently on and create new one by running:

```sh
$ git branch

$ git branch <new-branch-name>
```

After that, we can switch to this branch.

```sh
git switch  <new-branch-name>
```

We've been using Git default `master` branch. Interestingly, Github (a website where you can remotely store Git projects) recently changed its default branch from `master` to `main`. As a general rule, I recommend using `main` as your default branch if you work primarily with `GitHub`, as we will.

How to rename a Branch.

```sh
$ git branch -m oldname newname
```

Run `git log --decorate=full`. You should see that instead of just using your branch name, it will show the full ref name. A [ref](https://git-scm.com/book/en/v2/Git-Internals-Git-References) is just a pointer to a commit. All branches are refs, but not all refs are branches.

Run `git log --decorate=no`. You should see that the branch names are no longer shown at all.

```sh
$ git log --oneline
$ git log --decorate=full
```

To delete a branch, we can run this command.

```sh
$ git branch -D <branch-name> 
```
