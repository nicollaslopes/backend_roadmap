# Tips

If you screw up a commit message, you can change it with the `--amend` flag. We can also use `--no-edit` flag to not change the commit message.

```sh
$ git commit --amend -m "new commit message here"
$ git commit --amend --no-edit
```

We can add all files using `.` which means our current directory. That is, all the files will be added at once.

```sh
$ git add .
```

Instead of we just create a branch using `git branch new branch-name` we can create and switch to it immediately. 

```sh
$ git switch -c <new-branch-name>
```

We can customize our log command.

```sh
$ git log --pretty=format:'%C(blue)%h %C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
```

If you want to view all the files that have been changed in the current branch.

```sh
$ git show --name-only

# if you want to view all the files that have changed in the current branch
$ git show 755bcb91dc2e69d2c3aa60a96d112fcd4c2a2816
```

