---
title: Module 3 - System Access and File System
parent: RHCSA Notes
nav_order: 3
layout: default
---

# Module 3 - System Access and File System

## find vs locate

`find` iterates over the entire filesystem or the path that is given, while `locate` uses a prebuilt database that is updated using `updatedb`.

`locate` is much faster thanks to its database, but does not find new files until the database is updated. Meanwhile, `find` scans in realtime so it will find new files easily.

## Wildcards

Can be used as a substitute for characters in a command or search.

### Types

`*` - represents zero or more characters
`?` - represents a single character
`[]` - represents a range of characters

## Links

- inode - Pointer or number of a file on the drive.
- You cannot create soft or hard links within the same directory with the same name.

### Softlinks vs Hardlinks

#### Softlink

- Link will be removed if the linked file is removed or renamed.
- Link will have different inode from linked file.

```bash
ln -s /home/user/file.txt /home/user/my-dir/soft-link
```

#### Hardlink

- Removing or renaming the linked file will not affect the hardlink.
- Link will point to file inode, i.e. will have the same inode.
- Hard links only work within the same partition.

```
ln /home/user/file.txt /home/user/my-dir/hard-link
```
