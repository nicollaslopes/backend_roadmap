# Configurations

## Quick Config

Git comes with a [configuration](https://git-scm.com/docs/git-config) both at the global and the repo (project) level. Most of the time, you'll just use the global config.

Let's see if our identity (`user.name` and `user.email`)are already set. 

```sh
$ git config --get user.name
$ git config --get user.email
```

If they aren't, set them. I recommend using your GitHub username and email.

```sh
$ git config --add --global user.name "github_username_here"
$ git config --add --global user.email "email@example.com"
```

We can also see our global git configurations.

```sh 
$ cat ~/.gitconfig
$ cat .git/config

or 

$ git config --list
```

## Get and Unset

We've used `--list` to see _all_ the configuration values, but the `--get` flag is useful for getting a single value.

```sh
$ git config --get <key>
$ git config --get user.name
```

The `--unset` flag is used to remove a configuration value. We can use `--unset-all` if we want to purge all instances of a key. For example:

```sh
$ git config --unset <key>
$ git config --unset user.name

$ git config --unset-all example.key
```

Typically, in a key/value store you aren't allowed to have duplicate keys. Strangely enough, Git doesn't care.

## Locations

There are several locations where Git can be configured. From more general to more specific, they are:

- **system**: `/etc/gitconfig`, a file that configures Git for all users on the system
- **global**: `~/.gitconfig`, a file that configures Git for all projects of a user
- **local**: `.git/config`, a file that configures Git for a specific project
- **worktree**: `.git/config.worktree`, a file that configures Git for part of a project

If you set a configuration in a more specific location, it will override the same configuration in a more general location. For example, if you set `user.name` in the local configuration, it will override the `user.name` set in the global configuration.

![image](https://github.com/user-attachments/assets/efca8f2f-9e8e-4a60-9420-fff4bd31da34)


