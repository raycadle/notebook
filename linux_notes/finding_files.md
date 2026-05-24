---
title: Finding Files
parent: Linux Notes
---

# Finding Files

## find

`find` iterates over the entire filesystem or the path that is given, while `locate` uses a prebuilt database that is updated using `updatedb`.

## locate

`locate` is much faster thanks to its database, but does not find new files until the database is updated. Meanwhile, `find` scans in realtime so it will find new files easily.
