---
title: OverTheWire - Bandit
parent: Linux
---

# OverTheWire - Bandit

I'm starting over from level 0, as I completely forgot how I solved the puzzles up to where I stopped (level 21).
I will not store the passwords here as I do not want to spoil the game.
Each of the below levels have their write-up below them, explaining how I got the password for that level.

## Level 1

Getting the password for level 1 is straight forward. Simply ready the file `readme` that is in the home directory of bandit0.

## Level 2

This starts off seemingly simple. The password is in a file named `-`. How do you read files starting with a `-`?
One way that I used is to cat the file and use the same syntax as when running a bash script: `cat ./-`.
I'm sure there are other ways to do the same thing (as always with Linux), but this is the way I decided to do it.

## Level 3

This one is similar to the above. Thanks to tab-complete it's fairly easy to solve. I just used `cat ./--spaces\ in\ this\ filename--`.
The `\` before the spaces tell the shell interpreter that the space is a literal character.

## Level 4

This password is in a file with 3 periods in front of the file name-- to hide it extra well I guess?

## Level 5

This one could have been tedious. There are a few files that have to be checked, with only 1 containing human-readable text.
I decided to use a for loop to check what kind of file they are, and running `file` against each file.
I got back a list of info telling me what kind of file each is. There was one that is relevant.

## Level 6

This is where it started to get interesting. I had to find a file in a subdirectory within a directory that met the criteria:
- human-readable
- 1033 bytes in size
- not executable

There is one program that comes to mind when I want to find a file: `find`.
Use find with relevant tests to find the file that has the password.
Apparently, you can use file to determine whether a file is human-readable, which is one of the criteria,
but it would be pointless since using the above command only finds one file.

## Level 7

Another use of the `find` command. Honestly, it is quickly becoming my favorite command to find files.
Use find with some relevant tests to find the files that satisfy the criteria.

## Level 8

This one is simple. Use `grep` to find the word "millionth" in the file `data.txt`. The password is next to it on the same line.

## Level 9

This is where new commands come into play. The password only appears once in the file.
To solve this, `uniq` will need to be used, but there is also another command that needs to be used: `sort`.

When I originally tried this puzzle, I was always getting more than one matches with `uniq`, until I understood how it worked.
`uniq` compares a line of text against those adjacent to it. The way the file is setup, none of the lines have similar lines adjacent to them.
That is until you sort the file. Then you see how many duplicates of each line exists. And then you can use `uniq` properly to find the unique line.

## Level 10

This one requires the use of `strings`. That command alone could be used--albeit with a bit of scanning.
I decided to pass the stdout of `strings` to `grep` and search for the "=" that precedes the password.

## Level 11

This one is pretty simple. Use `base64` against the file and you get the password.

## Level 12

This one is a bit tricky. The password was encoded using ROT13.
To decode it, use `tr`. The specific arguments to `tr` will need researching/figuring out,
but you basically need to move each letter over 13 places.

## Level 13

This one is the trickiest yet. It requires decoding a hexdump and extracting numerous archives with different tools.
To do all this, the file will need to be copied to a directory in /tmp.
There's a whole lotta tar, gzip, and bzip2 decompression after using xxd to get the hexdump back to a binary file.
Have fun!

## Level 14

This one is simple. You get a ssh private key to use to login to bandit14. From there you can get the password for level 14,
which you need later on--I guess?
