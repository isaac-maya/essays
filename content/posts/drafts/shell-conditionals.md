---
title: "Rethinking QA Metrics"
date: 2023-07-25
draft: true
---

Sure, here's an explanation of each:

1. **Conditionals:**

Conditionals in bash scripting are used to make decisions in the script, and the `if`, `elif` (else if), and `else` statements are used to accomplish this. Here's a basic example:

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

1. **Advanced Conditionals:**

   In addition to basic comparisons, you can use more advanced conditional expressions with `if`. Here are a few examples:

   - String comparisons: 

   ```bash
   if [[ "$str1" == "$str2" ]]; then
       echo "Strings are equal."
   else
       echo "Strings are not equal."
   fi
   ```

   - Checking if a file exists:

   ```bash
   if [[ -e filename ]]; then
       echo "File exists."
   fi
   ```

   - Using logical operators (`&&` for "and", `||` for "or"):

   ```bash
   if [[ "$str1" == "value1" && "$str2" == "value2" ]]; then
       echo "Both conditions are true."
   fi
   ```

1. **Advanced Conditionals:**

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

