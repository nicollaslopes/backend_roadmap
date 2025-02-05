# Tags

If we want to create annotated tags, we can run this command.

```sh
$ git tag 1.0 -m "release 1.0"

# output:

259adf3 (HEAD -> main, tag: show, tag: 1.0, origin/main, test) test - username, 2 days ago

070716b first commit - username, 2 days ago
```

Using tag in a specific commit.

```sh
$ git tag -a "0.1.beta" -m "release 0.1.beta" 070716b

#output: 

259adf3 (HEAD -> main, tag: show, tag: 1.0, origin/main, test) test - username, 2 days ago

070716b (tag: 0.1.beta) first commit - username, 2 days ago
```

When we run `git push` by default does not send any tags that have been created, so we need to use the flag below.

```sh
$ git push origin master --folow-tags
```

If we want to delete the tags locally and on the server, we can run: 

```sh
$ git tag -d "release 0.1.beta"
$ git push --delete origin "release 0.1.beta"
```