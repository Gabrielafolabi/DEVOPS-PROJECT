## Shell Scripting Syntax Elements

1. Variables: In bash, you can define and store data in variables. Data of various types such as numbers, strings and arrays. Values are assigned to variables using the operator ( = ).
The values of the variable can be access using $ sign.

Example: 
1. Assigning value to variable
* `name = 'John'`

2. Retrieving value from variable
* `echo $name`

2. Control Flow: Bash provides control flow statements like if-else, for loops, while loops and case statement to control the flow of execution in your scripts.

Example: Using if-else to execute script based on a condition.
* #` Script to check if a number is positive, negative or zero`


`#!/bin/bash`

`read -p "Enter a number: " num`

`if [ $num -gt 0];`

`then`

`  echo "The number is positive."`

`elif [ $num -lt 0 ];`

`  then`

`    echo "The number is negative"`

`else` 

`  echo "the number is zero."`

`fi`
