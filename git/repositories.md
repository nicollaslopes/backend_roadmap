# Repositories

To create a local repository, we can create a folder and initialize a Git repository.

```sh
$ mkdir test-repository
$ cd test-repository
$ git init
```

Once we create a any file, we can stage it (add it to the "index") with the `git add` command before committing it later. A commit is a snapshot of the repository at a given point in time. It's a way to save the state of the repository, and its how Git keeps track of changes to the project.

```sh
$ git add <path-to-file>
$ git commit -m "first commit"
```

We can see the git status.

```sh
git status
```

To push our data to a remote repository, we can us (If this is your first time, you need to add the remote directory url running the first command below). Otherwise, we can just run `git push` command. 

```sh
git remote add origin <url.git>
git push
```

The [git log](https://git-scm.com/docs/git-log) command shows a history of the commits in a repository. This is what makes Git a version control system. You can see:

- Who made a commit
- When the commit was made
- What was changed

```sh
git log
```

We can also limit the maximum number of commits shown, and more importantly, to run it without the interactive pager.

```sh
git --no-pager log -n 10

or

git log -3
```
