---
title: "Advanced Shell | GREP"
date: 2023-07-13T13:55:28-06:00
draft: false
---

## Recursive Search

-R searches all files and dirs in the directory.

```
 grep -R "search_text" /home/user/
```

## Search doesn’t include

-v displays lines that do not match the pattern.

```
grep -v "search_text" filename
```

## Count

-c returns the number of lines that match the pattern.

```
grep -c "search_text" filename
```
