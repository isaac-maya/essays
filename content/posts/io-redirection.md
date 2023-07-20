	
---
title: I/O & Redirection
date: 2023-07-20
draft: false
---

![Retro PC Picasso Style](../../images/io.png)

## 1. Input/Output (I/O)

I/O operations typically involve three data streams: Standard Input (stdin), Standard Output (stdout), and Standard Error (stderr).

![Diagram](../../images/stdin-stdout-stderr.png)

## 2. Redirecting Output

The **>** operator redirects the output of a command to a file.

```bash
ls > files.txt
```
List files and save the list to a file

## 3. Appending Output

Use **>>** to add output to an existing file without deleting the current content.

```bash
date >> disk_usage.txt; df -h >> disk_usage.txt
```
Collect the free disk space on your system every hour. 

## 4. Redirecting Errors

**2>** redirects error messages. 

```bash
ls /nonexistent_directory 2> errors.txt
```

## 5. Combining Outputs

Combine stdout and stderr into one stream using **>&**. 

```bash
find / -name "*.jpg" > all_jpg_files.txt 2>&1
```

## 6. Input Redirection

Use **<** to provide input to programs.

```bash
mysql -u username -p database_name < queries.sql
```

Provide SQL commands via a file

## 7. Piping in Linux

Piping **|** lets you use the output of one command as input for another.

```bash
cat all_jpg_files.txt | grep "/home/"
```

