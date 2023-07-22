---
title: "Rethinking QA Metrics"
date: 2023-07-25
draft: true
---

2. **Loops:**

Loops are used to repeat a section of code a number of times. Bash scripting has three basic loop structures: the `for` loop, the `while` loop, and the `until` loop.

- `for` loop:

```bash
for variable in 1 2 3 4 5
do
    echo "This is pass $variable"
done
```

This script will print the statement "This is pass $variable" five times, with `$variable` being replaced by numbers from 1 to 5.

- `while` loop:

```bash
count=1
while [ $count -le 5 ]
do
    echo "Count: $count"
    let count=count+1
done
```

In this script, as long as the condition `[ $count -le 5 ]` (count is less than or equal to 5) is true, the script will continue to echo the count and increment it.

- `until` loop:

```bash
count=1
until [ $count -gt 5 ]
do
    echo "Count: $count"
    let count=count+1
done
```

The `until` loop is very similar to the `while` loop, but it continues until the test (following the `until` keyword) is true. In this script, as long as the count is not greater than 5, it echoes the count and increments it.
2. **Advanced Loops:**

   You can do more with loops than just iterating over lists of values or while a condition is true. Here are a few more advanced examples:

   - Using a C-style for loop:

   ```bash
   for (( i=0; i<5; i++ )); do
       echo "i is $i"
   done
   ```

   - Reading lines from a file:

   ```bash
   while IFS= read -r line; do
       echo "Line: $line"
   done < "file.txt"
   ```

   - Using `break` and `continue` to control loop execution. `break` stops the loop, while `continue` skips to the next iteration:

   ```bash
   for (( i=0; i<10; i++ )); do
       if [[ "$i" -eq '5' ]]; then
           break
       fi
       echo "i is $i"
   done
   ```
2. **Advanced Loops:**

   You can use `select` to create simple menus:

   ```bash
   options=("Option 1" "Option 2" "Quit")
   select opt in "${options[@]}"
   do
       case $opt in
           "Option 1")
               echo "You chose option 1"
               ;;
           "Option 2")
               echo "You chose option 2"
               ;;
           "Quit")
               break
               ;;
           *) echo "invalid option $REPLY";;
       esac
   done
   ```

   The `select` construct generates a menu from the items in an array. The user's choice is stored in the `opt` variable, and the `REPLY` variable holds the chosen number.
hese examples should give you a sense of the advanced features available in bash scripting. As you become more familiar with these concepts, you'll be able to write more complex and powerful scripts.
