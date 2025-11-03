---
date: 2025-11-03
authors:
  - nedevski
categories:
  - General
title: Debugging random HDD spin-ups in Unraid
description: haha
tags:
  - Unraid
  - Immich
  - NAS
---
 
Everyone wants lower idle power consumption. Spinning down disks that are not frequently used is a great way to do that. However I recently had an issue with Immich randomly waking up both the `data2` disk and the `parity` disk. I had moved its database to the `cache`, no files were accessed and yet - the drives were spinning up. So I had to investigate!

<!-- more -->

I installed the File Activity plugin, but that didn't capture any files being accessed.
That's when I learned about `fatrace`. It's a tool that monitors all file activity across the system and by that I really mean ALL file activity. When I tried saving the raw output of the command to file it grew to 100MB in 15-20 seconds!

## Debugging the issue

Since Unraid 7, the plugins that included `fatrace` are not compatible, that's why we need to install it manually

Keep in mind that as this article gets outdated, so will the link below. If needed, find a link to a newer version.

```bash
# Change to a working directory
cd /tmp

# Get the package
wget https://slackware.halpanet.org/slackdce/packages/15.0/x86_64/system/fatrace/fatrace-0.19.1-x86_64-1_slackdce.txz

# Install the package
upgradepkg --install-new fatrace-0.19.1-x86_64-1_slackdce.txz
```

After that we can run `fatrace -t` to monitor all activity. The `-t` flag simply adds the timestamp to the log. However as I already mentioned, we need to filter out the log, otherwise we will overwhelm our console.

To ensure proper filtering, we need to merge all errors with the regular log output (merging `stderr` and `stdout` in a single output). For that we use `2>&1` after our `fatrace` command.

Now we can finally use `grep` properly and filter our logs.

```bash
# Monitor a single folder
fatrace -t 2>&1 | grep "/mnt/disk2/folder"

# Provide multiple grep arguments to monitor multiple folders
fatrace -t 2>&1 | grep -e "/mnt/disk2/folder1" -e "/mnt/cache/folder1
```


## The solution (in my case)

With those commands I was able to see that for some reason my Immich database was split between `disk2` and `cache` and in some instances the Immich server accessed the cache, but in others - `disk2`, which naturally woke up the disk.

To ensure I don't mess up something, rather than merging the files manually I used the "unbalanced" plugin. After that all of my files were moved on the Cache drive and my drives stopped waking up randomly!