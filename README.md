# Merge driver for google-java-format

A very simple merge driver that allows you to automatically rebase and merge
commits using [google-java-format](https://github.com/google/google-java-format).

## Prerequsites

Download the all-deps jar of Google Java Format from:
https://github.com/google/google-java-format/releases
and save it alongside this script

## Git Wrapper

`git-wrapper` contains a wrapper script which will install this merge driver,
and then uninstall it immediately after the command has completed. This
wrapper can be used for running rebases.

```shell
$ /path/to/git-wrapper rebase central/branches/default/tip
```

Do note that if a merge conflict occurs, `git-wrapper rebase --continue`
should be used rather than using `git` directly.

## Manual Setup

In `.git/config`:

```
[merge "google-format"]
  name = google-format merge driver
  driver = /path/to/google-format-merge %O %A %B %P
  recursive = binary
```

In `.git/info/attributes`:

```
*.java merge=google-format
```

And you should be ready, happy gitting.
