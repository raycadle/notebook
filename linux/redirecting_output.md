---
title: Redirecting Output
parent: Linux
---

# Redirecting Output

Redirecting command output is a wonderful thing. For instance, I used a find command to find files larger than 20MB and smaller than 50MB. I have errors printed to stdout, while stdout is redirected to a file.

Command:
```bash
find / -type f -size +20M -size -50M 2>&1 >> foundfiles.txt
```

Explanation:
The `find` command is hella powerful. It searches the entire file system for anything that matches the parameters it is given.
In this case, I give it 3 parameters: type and 2 size parameters.
The `-type` tells the `find` command the type of file to look for. Obviously.
The `-size` parameters tell `find` the size of the files, either more than or less than a given value. Again, obviously.
`2>&1` redirects any errors from stderr to stdout.
`>> foundfiles.txt` appends the output of the `find` command into a file named `foundfiles.txt`.
