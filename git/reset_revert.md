# Reset and Revert

One of the major benefits of using Git is the ability to undo changes.
## Reset

If we add a file (or more) to the stage/index area and want to redo this action by returning to the workspace, we can run this command.

```sh
$ git reset <file-name>

# for all files
$ git reset
```

## Undoing commit

### Git Reset Soft

If we want to revert the commit (going back to the desired commit), just use the following command with the **--soft** parameter, the commit will be undone and the committed file(s) will return to the stage/index area.

```sh
$ git reset --soft <commit-hash>

# example
$ git reset --soft bb9b885

```

### Git Reset Hard

If we want to go back to a previous commit and discard all the changes, we can run this command.

```sh
$ git reset --hard <commit-hash>
```

 If you were to simply delete a _committed_ file, it would be trivially easy to recover because it is tracked in Git. However, if you used `git reset --hard` to undo committing that file, it would be deleted for good.

Always be careful when using `git reset --hard`. It's a powerful tool, but it's also a dangerous one.

# Revert

The idea of ​​revert is to remove a specific commit, so everything that was changed and created in that commit will no longer exist (there is a high chance of conflicts when it is an old commit) and a new commit is created referring to that revert.

```sh
$ git revert <commit-hash>
```
