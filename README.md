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


