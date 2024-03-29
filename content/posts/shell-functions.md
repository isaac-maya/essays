---
title: "Shell Scripting pt.1"
date: 2023-08-02
draft: false
---
# Functions

Functions allow you to reuse code and much more. Here are some examples:

## 1. Modularize 

```bash
function say_hello() {
    echo "Hello, $1"
}

say_hello "world"
```

Function `say_hello` takes one argument (`$1`). When you call the function, it will print "Hello, world".


## 2. Return values

Functions in BASH can do more than just encapsulate code. They can also take arguments and return values. Here's an example of a function that calculates the factorial of a number:

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


## 3. Global variables


Here's an example where a function modifies a global variable:

   ```bash
   my_var="Original value"

   change_var() {
       my_var="Changed value"
   }

   echo $my_var
   change_var
   echo $my_var
   ```


## 4. Local variables

Bash also supports local variables within functions, which won't affect the 
global scope:

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
