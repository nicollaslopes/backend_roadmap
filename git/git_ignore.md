# Git ignore

When we have files that we don't want to track them with git, we use `gitignore` to solve this. For example, to ignore node_modules or vendor folders, because they are dependencies and there are a lot of files there that don't need to be sent.

Your `.gitignore` file does _not_ necessarily need to be at the root of your project. It's fairly common to have multiple `.gitignore` files in different directories throughout a project. A nested `.gitignore` file only applies to the directory it's in and its sub directories.

```
src/
├── assets/
│   ├── .gitignore
|   ├── cover_art.jpg
│   └── onlydevs.png
├── main.py
├── tests.py
├── venv/
│   └── bin/
|       ├── activate
│       └── python
.gitignore
```

### Wildcards

The `*` character matches any number of characters except for a slash (`/`). For example, to ignore _all_ `.txt` files, you could use the following pattern:

```
*.txt
```

### Comments

You can add comments to your `.gitignore` file by starting a line with a `#`. For example:

```
# Ignore all .txt files
*.txt
```