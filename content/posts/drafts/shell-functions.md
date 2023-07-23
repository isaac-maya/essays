---
title: "Rethinking QA Metrics"
date: 2023-07-25
draft: true
---
3. **Functions:**

Functions allow you to modularize your script and reuse sections of code. Here's a simple example:

```bash
function say_hello() {
    echo "Hello, $1"
}

say_hello "world"
```

In this script, `say_hello` is a function that takes one argument (`$1`). When you call `say_hello "world"`, the script will print "Hello, world".

Remember, this is a very basic introduction to these topics. There's much more to learn about bash scripting, including more advanced features of these structures and additional structures not covered here.


3. **Advanced Functions:**

   Functions in bash can do more than just encapsulate code. They can also take arguments and return values. Here's an example of a function that calculates the factorial of a number:

   ```bash
   factorial() {
       if [[ "$1" -le '1' ]]; then
           echo '1'
       else
           last=$( factorial "$(( $1 - 1 ))" )
           echo "$(( $1 * last ))"
       fi
   }

   echo "Factorial of 5 is $( factorial 5 )"
   ```

   This function uses recursion to calculate the factorial. Note how it calls itself with the expression `factorial "$(( $1 - 1 ))"`, and how it uses `echo` to return a value.

These examples just scratch the surface of what you can do with conditionals, loops, and functions in bash scripting. Bash has a rich set of features that make it a powerful tool for automating tasks on Unix-like systems.




3. **Advanced Functions:**

   Bash functions can also be used to manipulate variables in the parent script. Here's an example where a function modifies a global variable:

   ```bash
   my_var="Original value"

   change_var() {
       my_var="Changed value"
   }

   echo $my_var
   change_var
   echo $my_var
   ```

   In this script, the `change_var` function changes the value of `my_var` from "Original value" to "Changed value". When `my_var` is echoed after the function call, it reflects the new value.

   Bash also supports local variables within functions, which won't affect the global scope:

   ```bash
   my_var="Original value"

   change_var() {
       local my_var="Changed value"
       echo $my_var
   }

   echo $my_var
   change_var
   echo $my_var
   ```

   In this script, `my_var` within the function is a local variable. Its change doesn't affect the global `my_var`, so the second `echo $my_var` outside the function still prints "Original value".

These examples should give you a sense of the advanced features available in bash scripting. As you become more familiar with these concepts, you'll be able to write more complex and powerful scripts.