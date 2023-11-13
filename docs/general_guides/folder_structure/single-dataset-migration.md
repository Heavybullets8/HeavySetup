## Overview

This guide will help you migrate from multiple media datasets to one single dataset. Following this single dataset structure will ensure smooth navigation and better performance.

## Preparing New Dataset

Please See [Dataset](dataset.md) for a recommended structure of the new dataset. 
> Note: The name can be change later.

## Moving Files to new dataset

1.) Open up a `tmux` session so if your shell times out or you want to leave it to run it will continue in your absence.

To start the `tmux` session all you need to do is run
```
tmux
```

2.) To move the data to the new data we just created we are going to be using the `rsync` command to move all files to the new dataset with their structure intact. 

> **ALWAYS DO A DRYRUN BEFORE YOU PROCEED WITH THE LIVE RUN** by adding `-n` or `--dry-run` arguements to rsync

> Replace /mnt/old/dataset/ and /mnt/new/dataset/folder with your datasets.


Dry Run Examples:
```
rsync -aHn /mnt/old/dataset/ /mnt/new/dataset
rsync -aH --dry-run /mnt/old/dataset/ /mnt/new/dataset
```
Append either ` | more` or ` | less` to the end to make to a bit easier if transfer a lot of files to make sure the structure stays how you want it with all files.

Once everything looks good remove `-n` / `--dry-run` from the command. We are then going to add `--progress` and `--remove-source-files` to `rsync`.

> `-aH` retains permissions, and hardlinks while moving files recursively

> `--progress` Shows the user the progress as `rsync` is running.

> `--remove-source-files` will remove all files as they are transfered excluding folders.

```
rsync -aH --progress --remove-source-files /mnt/old/dataset/ /mnt/new/dataset/folder
```
> If you get timed out during the move it's okay. In shell type `tmux a` to resume the session.

## Renaming Dataset

1.) Once all data has been moved, you are free to exit `tmux` using `exit`. You are now free to delete all remnants of the old dataset.

2.) To rename the new media dataset in shell run:

```
zfs rename /old/dataset /new/dataset
```
