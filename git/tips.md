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
