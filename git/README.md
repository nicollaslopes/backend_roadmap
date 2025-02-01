# Git
## Introduction

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

## Status

A file can be in one of [several states](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_the_very_basics) in a Git repository. We can use `git status` command to see them. Here are a few important ones:

- `untracked`: Not being tracked by Git
- `staged`: Marked for inclusion in the next commit
- `committed`: Saved to the repository's history