# Shell Scripting Cheat Sheet

## Basic Commands

- **echo**: Prints text to the terminal.
  ```sh
  echo hello
  ```

- **cat**: Displays the contents of a file.
  ```sh
  cat filename
  ```

- **ls**: Lists the files in the current directory.
  ```sh
  ls
  ```

- **pwd**: Prints the current directory path.
  ```sh
  pwd
  ```

- **chmod**: Changes the file permissions.
  ```sh
  chmod u+x filename
  ```

## Vim Text Editor

- **Insert Mode**: Press `i` to enter insert mode.
- **Exit Insert Mode**: Press `Esc` to exit insert mode.
- **Write and Quit**: Press `:w` to write and `:q` to quit.
- **Write and Quit Together**: Press `:wq` to write and quit.

## Creating and Running a Shell Script

1. Create a new file `shelltest.sh`.
2. Add the shebang line to specify the shell.
   ```sh
   #!/bin/bash
   ```
3. To run the script:
   ```sh
   bash shelltest.sh
   ```
4. To run with the shebang line, make the script executable:
   ```sh
   chmod +x shelltest.sh
   ./shelltest.sh
   ```

## Useful Commands

- **ls -l**: Lists files with detailed information including permissions.
- **chown**: Changes file ownership.
  ```sh
  chown user:group filename
  ```
- **cp**: Copies files or directories.
  ```sh
  cp /source/path /destination/path
  ```

## Example of Copy Command

### Not Recommended
```sh
cp /my/location/from /my/location/to
cp /my/location/here /my/location/there
```

### Better
```sh
cp $MY_LOCATION_FROM $MY_LOCATION_TO
cp "MY_LOCATION_FROM/here" "MY_LOCATION_TO/there"
```

## Example of Move Command

### same like as copy command

```sh
mv $MY_LOCATION_FROM $MY_LOCATION_TO
mv "MY_LOCATION_FROM/HERE" "MY_LOCAION_TO/THERE"
```

## Printing and Reading Input

- **echo**: Used to print text.
  ```sh
  echo "your name?"
  read name
  echo "hello $name"
  ```

## Positional Arguments

Arguments can be passed to a script and accessed using `$1`, `$2`, etc.
```sh
echo "hello $1 $2"
./shelltest.sh john martin
```

## Piping and Filtering

- **grep**: Filters output.
  ```sh
  ls -l /usr/bin | grep bash
  ```

## Redirecting Output

- **Overwrite**: Redirects output to a file, overwriting existing content.
  ```sh
  echo 'hello world' > hello.txt
  ```

- **Append**: Redirects output to a file, appending to existing content.
  ```sh
  echo 'have a good day' >> hello.txt
  ```


 **Passing Arguments**
   - The script starts by prompting the user for two arguments using `$1` and `$2`, which typically represent the first and second command-line arguments passed to the script.
   - However, in this context, the script is trying to read input directly into `$1` and `$2`, which isn't standard practice. Instead, arguments should be passed when running the script.

 **Echoing Input**
   - After capturing input, the script uses `echo` to print a greeting message.
   - Example:
     ```bash
     echo 'hi', $2
     echo 'hello', $1
     ```

 **Asking for User's Name**
   - The script asks the user for their name and then greets them.
   - Example:
     ```bash
     echo 'Is you New what is your Name ?'
     read ans
     echo 'hi Wellcome' $ans
     ```

 **Displaying Current Date**
   - The script prints the current date using the `date` command.
   - Example:
     ```bash
     echo 'today' `date`
     ```

 **Listing Files in a Directory**
   - The script asks the user to input a directory path and then lists the files in that directory using the `ls` command.
   - Example:
     ```bash
     echo 'what are you looking for'
     read path
     echo -e 'here is your path'
     ls $path
     ```
### Conditional Statements

The script uses the `if`, `elif`, and `else` constructs to perform different actions based on the value of a number input by the user.

### Operators Used:
- **`-gt` (greater than):** Checks if the first number is greater than the second.
- **`-lt` (less than):** Checks if the first number is less than the second.
- **`-ge` (greater than or equal to):** Checks if the first number is greater than or equal to the second.
- **`-le` (less than or equal to):** Checks if the first number is less than or equal to the second.
- **`-eq` (equal to):** Checks if two numbers are equal.

### Script Explanation

1. **Introduction and User Prompt:**
   - The script starts by printing a message to indicate that a conditional statement is being used.
   - It then prompts the user to enter a number.

2. **Evaluating the Number:**
   - The script reads the number into the variable `num`.
   - It uses `if`, `elif`, and `else` to check the value of `num`:
     - If `num` is greater than 0, it prints "your number is positive".
     - If `num` is less than 0, it prints "your number is negative".
     - If `num` equals 0, it prints "uhh you enter zero".
     - If the input is invalid or doesn't match the above conditions, it prints "you can't enter a number".

3. **Ending the Conditional Block:**
   - The `fi` keyword is used to end the `if` block.

### Full Script

```bash
#!/bin/bash

# Introduction message
echo 'In this conditional statement is working'

# Prompting user to enter a number
echo 'enter a number'
read num

# Evaluating the number
if [ $num -gt 0 ]; then
  echo 'your number is positive'
elif [ $num -lt 0 ]; then
  echo 'your number is negative'
elif [ $num -eq 0 ]; then
  echo 'uhh you enter zero'
else
  echo "you can't enter a number"
fi
```

### `while` Loop

The `while` loop in this script increments a number (`i`) starting from the value provided by the user until it reaches 10.

#### Code:
```bash
#!/bin/bash

# Prompt the user to enter a starting number
read nub

# Assign the user's input to the variable 'i'
i=$nub

# 'while' loop to increment 'i' until it reaches 10
while [ $i -lt 10 ]; do
  echo "$i"
  ((i += 1))
done
```

## Overview of `For` Loop Statement

 Read the input into the variable 'inp'
read inp

 'for' loop to iterate over each element in 'inp'
```bash
for i in $inp
do
   echo $i
done
```

## Overview of `case` Statement

The `case` statement in shell scripting allows you to execute different code blocks based on the value of an expression. It is similar to `switch` statements in other programming languages.

### Syntax

```
case -expression- in
  pattern1)
      # Code to execute if expression matches pattern1
      ;;
  pattern2)
      # Code to execute if expression matches pattern2
      ;;
  *)
      # Default case: code to execute if no patterns match
      ;;
esac
```

```bash
#!/bin/bash

# Sample case statement

echo "Enter a number between 1 and 3:"
read num

case $num in
  1)
    echo "You entered one."
    ;;
  2)
    echo "You entered two."
    ;;
  3)
    echo "You entered three."
    ;;
  *)
    echo "Invalid input. Please enter a number between 1 and 3."
    ;;
esac
```
