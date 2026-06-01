---
title: Links
parent: Linux
---

# Links

- inode - Pointer or number of a file on the drive.
- You cannot create soft or hard links within the same directory with the same name.

## Softlink

- Link will be removed if the linked file is removed or renamed.
- Link will have different inode from linked file.

```bash
ln -s /home/user/file.txt /home/user/my-dir/soft-link
```

## Hardlink

- Removing or renaming the linked file will not affect the hardlink.
- Link will point to file inode, i.e. will have the same inode.
- Hard links only work within the same partition.

```
ln /home/user/file.txt /home/user/my-dir/hard-link
```
