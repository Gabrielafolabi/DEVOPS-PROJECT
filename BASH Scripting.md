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
  
   Filename: navigating-linux-filesystem.sh
   
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

Note: File was saved and give execution permission `$ chmod + x navigating-linux-filesystem.sh`

Then, i run the script using `$ ./ navigating-linux-filesystem.sh`


### File Operation and Sorting

I create the script that peforms the following below:

1. Create three files (file1.txt, file2.txt, file3.txt)
2. Displays the file in their current order
3. Sort them Aphabetically
4. Save the sort file in the sorted_file.txt
5. Display the sorted files, remove the original files
6. rename the sorted file to sorted_file_sorted_alphabetically_txt
7. Diplay the content of the final sortd file.

Filename: sorting.sh


`#!/bin/bash`


`# Create three files`


`echo "Creating files..."`

`echo "This is file3." > file3.txt`

`echo "This is file1." > file1.txt`

`echo "This is file2." > file2.txt`

`echo "Files created."`



`# Display the files in their current order`

`echo "Files in their current order:"`

`ls`



`# Sort the files alphabetically`

`echo "Sorting files alphabetically..."`


`ls | sort > sorted_files.txt`

`echo "Files sorted."`




`# Display the sorted files`

`echo "Sorted files:"`

`cat sorted_files.txt`



`# Remove the original files`

`echo "Removing original files..."`

`rm file1.txt file2.txt file3.txt`

`echo "Original files removed."`



`# Rename the sorted file to a more descriptive name`

`echo "Renaming sorted file..."`

`mv sorted_files.txt sorted_files_sorted_alphabetically.txt`

`echo "File renamed."`



`# Display the final sorted file`


`echo "Final sorted file:"`


`cat sorted_files_sorted_alphabetically.txt`


Note: `$ sudo chmod + x sorting.sh`

Run the script with: `$ ./sorting.sh`



### Working with Numbers and Calculation

I wrote a shell script that does the following below:

1. Defines two variables num1 and num2 with numeric values
2. Perform basic arithmetic operations ( +, - , multiplication, division and modulus), then displays the result)
3. Raising num1 to the power of two
4. Square root of num2 and displaying the result

Filename : Calculation.sh


`#!/bin/bash`



`# Define two variables with numeric values`


`num1=10`

`num2=5`




`# Perform basic arithmetic operations`

`sum=$((num1 + num2))`

`difference=$((num1 - num2))`


`product=$((num1 * num2))`


`quotient=$((num1 / num2))`


`remainder=$((num1 % num2))`




`# Display the results`


`echo "Number 1: $num1"`

`echo "Number 2: $num2"`

`echo "Sum: $sum"`

`echo "Difference: $difference"`

`echo "Product: $product"`

`echo "Quotient: $quotient"`

`echo "Remainder: $remainder"`




`# Perform some more complex calculations`

`power_of_2=$((num1 ** 2))`

`square_root=$(awk "BEGIN{ sqrt=$num2; print sqrt }")`




`# Display the results`

`echo "Number 1 raised to the power of 2: $power_of_2"`

`echo "Square root of number 2: $square_root"`




  

      

 
 


  
