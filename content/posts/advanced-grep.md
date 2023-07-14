---
title: "Advanced GREP"
date: 2023-07-13T13:55:28-06:00
draft: false
---

![Retro PC Picasso Style](../../images/advanced_shell.png)


## 1. Recursive Search

**-R** searches all files and dirs in the directory.

```
 grep -R "search_text" /home/user/
```

## 2. Search doesn’t include

**-v** displays lines that do not match the pattern.

```
grep -v "search_text" filename
```

## 3. Count

**-c** returns the number of lines that match the pattern.

```
grep -c "search_text" filename
```

## 4. Line Number

**-n** displays the line numbers with output lines.

```
grep -n "search_text" filename
```

## 5. Ignore capitaliztion

**-I** makes the search case insensitive.

```
grep -i "search_text" filename
```

## 6. Extended Regexp

**-E** lets you use additional regular expression features.

```
grep -E 'pattern1|pattern2' filename
```

This command will search for lines containing either "pattern1" or "pattern2".

## 7. File pattern

**-include, —exclude** specify search based on filename.

```
grep -R --include="*.txt" "search_text" /home/user/
```

This will search recursively but only look files ending with ".txt".

## 8. Word-Regexp

**-w** only returns lines where the pattern matches the whole “word”.

```
grep -w "search_text" filename
```

In you're looking for "log", it won't return "blog" or "logic" because "log" is not a whole word in these instances.


## 9. After & Before

Print the lines that appear after (**-A**), before (**-B**), or on either side (**-C**) of the matching pattern.

```
grep -A 5 -B 5 "search_text" filename
```

This command will print out 5 lines before and after each line that matches "search_text".
