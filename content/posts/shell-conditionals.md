---
title: "Shell Scripting pt.2"
date: 2023-07-25
draft: true
---
# Conditionals

Conditionals are used to make decisions in the script, and the `if`, `elif` (else if), and `else` statements are used to accomplish this. Here are some examples:



## 1. Condition tests

```bash
if [ "$variable" -lt 10 ]
then
    echo "Variable is less than 10."
elif [ "$variable" -eq 10 ]
then
    echo "Variable is equal to 10."
else
    echo "Variable is greater than 10."
fi
```

In this script, `-lt` stands for "less than", `-eq` for "equal to". These are condition tests. If the condition after `if` is true, the commands between `then` and `elif` (or `else` if there's no `elif`) get executed. If the condition is false, we move to the next condition (`elif` or `else`).


## 2. String comparisons:

   ```bash
   if [[ "$str1" == "$str2" ]]; then
       echo "Strings are equal."
   else
       echo "Strings are not equal."
   fi
   ```

## 3. Checking if a file exists:

   ```bash
   if [[ -e filename ]]; then
       echo "File exists."
   fi
   ```

## 4. Using logical operators (`&&` for "and", `||` for "or"):

   ```bash
   if [[ "$str1" == "value1" && "$str2" == "value2" ]]; then
       echo "Both conditions are true."
   fi
   ```

## 5. Case statements

   Bash supports `case` statements, which can simplify complex conditional logic. Here's an example:

   ```bash
   case "$variable" in
   pattern1)
       echo "Pattern 1"
       ;;
   pattern2)
       echo "Pattern 2"
       ;;
   *)
       echo "Default case"
       ;;
   esac
   ```

   The `*` serves as the default case if no other patterns match. Each case ends with `;;`.

