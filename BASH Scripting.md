## Shell Scripting Syntax Elements

1. Variables: In bash, you can define and store data in variables. Data of various types such as numbers, strings and arrays. Values are assigned to variables using the operator ( = ).
The values of the variable can be access using $ sign.

Example: 
1. Assigning value to variable
* `name = 'John'`

2. Retrieving value from variable
* `echo $name`

2. Control Flow: Bash provides control flow statements like if-else, for loops, while loops and case statement to control the flow of execution in your scripts.

Example: 
1. Using if-else to execute script based on a condition.
* **Script to check if a number is positive, negative or zero**


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

**Note: The result of the code above prompt you to type a number, and then condiftions are checked which further print a statement stating the number is positive or negative or zero.**

2. Interating through a list, using For Loop.

* **Script to print number fro 1 to 5 using for loop**
`#!/bin/bash`

`for [ (i = 1; i <= 5; i++) ]`


  `do`

    echo $i
    
  `done`

The result of the above code is seen below:

![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/3a490e00-4e24-4041-92d2-6b1f074bb9a6)



3. Command Substitution: This allows you to capture the output of a command and use it as a value within your script. You can use the backtick or the $()Syntax for command substitution.

Example:

current_date= `date +%Y-%m-%d`

4. Input and output

   Example 1: Accept user input
   `echo "Enter your name?: "`
   
   `read name`
   
 Example 2: Output text to the terminal
 
 `echo "Hello World"`

 Example 2: Output the result of a command into a file

 `echo "hello world" > index.txt`

 Example 3: Pass the content of a file as input to a command.

 `grep "pattern" < input.txt`

Example 4: Pass the result of a command as an input to another command

`echo "hello world" | grep "pattern"` 


5. Functions: Here i created functions using the bash script. I defined and used the function to group some commands to be executed for specific purposes.
it is defined as seen below,

`#!/bin/bash`

`# Define a function to greet the user`

`greet() {`

    `echo "Hello, $1! Nice to meet you."`
`}`

`# Call the greet function and pass the name as an argument`

`greet "John"`


### Creating A Shell Script:

`#!/bin/bash`

`# Prompt the user for their name`

`echo "Enter your name:"`

`read name`

`# Display a greeting with the entered name`

`echo "Hello, $name! Nice to meet you."`

The shell script above saved in a file name "user-input.sh"

1.Prompt you for your name...,

2.Gets the name, and then

3. Display a greeting on your terminal with the entered name.

Additionally, I saved the file and then gave it executable permission with the command below:

`$ sudo chmod +x user-input.sh`

Then i run the script using the command:
`$ ./user-input.sh`


   ### Directory Manipulation and Navigation

*  I wrote a shell script below that performs the following executions.
   
   1. Dissplays the current directory
   2. Create a new directory called "my_directory"
   3. Change to that directory and create two files in that directory.
   4. List the files and move one back level up
   5. remove the "my_directory" and its content
   6. Finally lsits the files in the current directory again.
 

`#!/bin/bash`

`# Display current directory`

`echo "Current directory: $PWD"`



* `# Create a new directory`

`echo "Creating a new directory..."`

`mkdir my_directory`

`echo "New directory created."`





* `# Change to the new directory`

`echo "Changing to the new directory..."`

`cd my_directory`

`echo "Current directory: $PWD"`




* `# Create some files`

`echo "Creating files..."`

`touch file1.txt`

`touch file2.txt`

`echo "Files created."`





* `# List the files in the current directory`

`echo "Files in the current directory:"`

`ls`


* `# Move one level up`

`echo "Moving one level up..."`

`cd ..`

`echo "Current directory: $PWD"`

* `# Remove the new directory and its contents`
  
`echo "Removing the new directory..."`

`rm -rf my_directory`

`echo "Directory removed."`

* `# List the files in the current directory again`
  
`echo "Files in the current directory:"`

`ls`

  

      

 
 


  
