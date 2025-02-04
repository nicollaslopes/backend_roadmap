# Logs

The [git log](https://git-scm.com/docs/git-log) command shows a history of the commits in a repository. This is what makes Git a version control system. You can see:

- Who made a commit
- When the commit was made
- What was changed

```sh
$ git log
$ git log --oneline
$ git log --pretty=format:'%h %d %s - %cn, %cr'
```

We can also limit the maximum number of commits shown, and more importantly, to run it without the interactive pager.

```sh
$ git --no-pager log -n 10

# or

$ git log -3
```
