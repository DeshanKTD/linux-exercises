# Bash Scripting Basics Labsheet

## Introduction
Bash (Bourne Again SHell) is a Unix shell and command language. This labsheet will guide you through the basics of bash scripting, covering essential commands and scripting techniques.

## Prerequisites
- A Unix-based operating system (Linux or macOS).
- Basic understanding of the command line interface.

## Initial Setup
1. **Open Terminal**: On your Unix-based OS, open the terminal application.

## Creating Your First Script
1. **Create a New Script File**:
   ```bash
   touch first_script.sh
   ```

2. **Make the Script Executable**:
   ```bash
   chmod +x first_script.sh
   ```

3. **Open the Script in a Text Editor**:
   ```bash
   nano first_script.sh
   ```

4. **Add Shebang and a Simple Command**:
   At the top of the file, add the shebang line and a simple echo command:
   ```bash
   #!/bin/bash
   echo "Hello, World!"
   ```

5. **Save and Close the File**:
   Press `CTRL + X`, then `Y`, and `Enter` to save and exit in Nano.

6. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

## Basic Commands and Concepts

### Variables
1. **Define and Use a Variable**:
   ```bash
   #!/bin/bash
   name="John"
   echo "Hello, $name"
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

### User Input
1. **Prompt the User for Input**:
   ```bash
   #!/bin/bash
   echo "Enter your name:"
   read name
   echo "Hello, $name"
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

### Conditional Statements
1. **If Statement**:
   ```bash
   #!/bin/bash
   echo "Enter a number:"
   read number
   if [ $number -gt 10 ]; then
     echo "The number is greater than 10."
   else
     echo "The number is 10 or less."
   fi
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

### Loops
1. **For Loop**:
   ```bash
   #!/bin/bash
   for i in 1 2 3 4 5
   do
     echo "Number: $i"
   done
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

2. **While Loop**:
   ```bash
   #!/bin/bash
   counter=1
   while [ $counter -le 5 ]
   do
     echo "Counter: $counter"
     ((counter++))
   done
   ```

3. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

### Functions
1. **Define and Use a Function**:
   ```bash
   #!/bin/bash
   function greet() {
     echo "Hello, $1"
   }
   greet "World"
   greet "Alice"
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

## File Operations

### Create and Write to a File
1. **Create and Write to a File**:
   ```bash
   #!/bin/bash
   echo "This is a sample text." > sample.txt
   echo "Another line of text." >> sample.txt
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

3. **Check the File Content**:
   ```bash
   cat sample.txt
   ```

### Read from a File
1. **Read and Display File Content**:
   ```bash
   #!/bin/bash
   while IFS= read -r line
   do
     echo "$line"
   done < sample.txt
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

## Putting It All Together
1. **Create a Comprehensive Script**:
   ```bash
   #!/bin/bash
   echo "Enter your name:"
   read name
   echo "Hello, $name" > greetings.txt

   echo "Enter a number:"
   read number
   if [ $number -gt 10 ]; then
     echo "The number is greater than 10." >> greetings.txt
   else
     echo "The number is 10 or less." >> greetings.txt
   fi

   echo "Numbers from 1 to 5:" >> greetings.txt
   for i in 1 2 3 4 5
   do
     echo "Number: $i" >> greetings.txt
   done

   echo "Reading the file:"
   cat greetings.txt
   ```

2. **Run the Script**:
   ```bash
   ./first_script.sh
   ```

## Conclusion
Congratulations! You have completed the basics of bash scripting. You now know how to create scripts, use variables, get user input, work with conditional statements, loops, functions, and perform file operations. Keep practicing to become proficient in bash scripting.