# Introduction

Git is the distributed **version control system**. Nearly every developer in the world uses it to manage their code. Developers use Git to:

* Keep a history of their code changes
* Revert mistakes made in their code
* Collaborate with other developers
* Make backups of their code
* And much more

## Basic commands

* git init
* git status
* git add file-name
* git commit -m "my first commit"
* git push
* git pull
* git log

## Quick config

Git comes with a [configuration](https://git-scm.com/docs/git-config) both at the global and the repo (project) level. Most of the time, you'll just use the global config.

Let's see if our identity (`user.name` and `user.email`)are already set. 

```sh
git config --get user.name
git config --get user.email
```

If they aren't, set them. I recommend using your GitHub username and email.

```sh
git config --add --global user.name "github_username_here"
git config --add --global user.email "email@example.com"
```

We can also see our global git configurations.

```sh 
cat ~/.gitconfig
```

## Status

A file can be in one of [several states](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_the_very_basics) in a Git repository. We can use `git status` command to see them. Here are a few important ones:

- `untracked`: Not being tracked by Git
- `staged`: Marked for inclusion in the next commit
- `committed`: Saved to the repository's history


