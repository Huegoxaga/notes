# Bash Scripting

## Introduction

- It stores a batch of command in order to complete certain task in one execution.
- It usually has an extension as `.sh`. It also can be run without any extenion or as `.txt`.
- Bash does not have a type system, everything is saved as strings.
- It can be edited by any text editing tool.
- It is recommanded to run the full path of the commands in the scripts.

## Run Script

- Any text file contains commands line by line can be run using `bash filename`.
  - `bash` command run scripts in a seperate session.
  - A script can contain `bash` command to call another script under a sub-session.
  - `LOCAL='123' bash ./child.sh` pass a local environment variable to the sub-session.
- Shebang is used at the first line of the text file to make the file executable by itself.
  - It is an operator look like `#!`
  - It is followed by the path of the interpreter.
  - For bash scripting, use `#!/bin/sh` or `#!/usr/bin/env bash` if the path of bash is unknown.
  - The user needs the `execute` file permission for the script
    - `chmod a+x filename.sh`
  - The file can then be executed by using `./filename`.
  - Add the directory path into the `$PATH` variable to make the script run without `./`.
- Each script will be run in a separate session.
- It import and execute an external bash file for the current session, run `source <filepath>`.
  - `source` is an alias and can be replaced by the built-in command `.`. Ex, One can run `. <filepath>` instead.

## Syntax

### Run Command

- `\` can be placed at the end of each line. It will make the command continue in a new line.
- `;` can be used to separate multiple command in entered one line.
- `!!` will run the last executed command.
- `commandA && commandB` Run next command if previous is command successful.
- `commandA || commandB` Run commands until one is successful.
- `commandA | commandB` pass `STDOUT` of the `commandA` to `STDIN` of `commandB`.
  - `STDOUT`, `STDIN` and `STDERR` is streaming data.
- Three or more commands can be chained with the above operators.
- `commandA ; commandB` Run all commands in one lines.
- `echo "ABC" >> filepath` use redirection operator to write `STDOUT` string to a file at once.
  - `>` is similar to `>>` but `>>` will append content to the file if the file exists, while `>` will overwrite the existing file completely
- `commandA >> filepath` write the `STDOUT` of a command to a file continuously.
- `command < filepath` send the file data to the command.
- File descriptor `0` is the standard input (stdin)
- File descriptor `1` is the standard output (stdout)
- File descriptor `2` is the standard error (stderr)
- `/dev/null` is a special device that discards everything that is written to it
  - `command 2> /dev/null` discard all error messages
  - `2> /dev/null > ~/result.txt` discard all error messages and send output to `result.txt`
- `2>&1` combine `stderr` and `stdout` into the `stdout` stream for further manipulation
  - `1` will includes all the `2` messages afterwards
- `command 2> output.txt` The standard error stream will be redirected to the file only, it will not be visible in the terminal. If the file already exists, it gets overwritten.
- `command 2>> output.txt` The standard error stream will be redirected to the file only, it will not be visible in the terminal. If the file already exists, the new data will get appended to the end of the file.
- `command &> output.txt`Both the standard output and standard error stream will be redirected to the file only, nothing will be visible in the terminal. If the file already exists, it gets overwritten.
- `command &>> output.txt` Both the standard output and standard error stream will be redirected to the file only, nothing will be visible in the terminal. If the file already exists, the new data will get appended to the end of the file.
- `{}` execute some code as a block.
  - terminate each statements with `;` to run some code as a block on a single line.
  - code-block runs in the same environment of the main shell
  - Ex, `{ echo -n "Hello"; sleep 1; echo " World!"; } > hello.txt`
- `()` executes the code inside it in a sub-shell.
  - run on a separate copy of the main shell.
- Special character should be either escaped using `\` like `\*` or enclosed inside quotes like `"*"`.

### Comment

- Any line starts with `#` can be followed by a single line comment.

### Exit

- keyword `exit` is used to stop the script.

### Variables

- declare a new variable using `name=value`.
  - No space between `=` sign.
  - String values need to be surrounded by quotes.
- Access variable using `$name`
  - When printing the variable, double quotes are required. Ex, `echo "Good Morning! $name"`
  - It can also accessed by using `${name}`.
    - `${name}` can be placed inside a string surrounded by double quotes.
- Using backticks to save command as variable
  ```bash
  BASH_VERSION=`bash --version`
  echo $BASH_VERSION
  ```
- Save or Print or Save the ouput of a command in a variable using `$()`.
  ```bash
  result=$(pwd)
  echo $result
  #or
  echo $(pwd)
  ```
- Strings can be concatenated if two variable are placed together without space. Ex, `$A$B`.
- Strings can be concatenated using `+=`.
- `${#VAR}` will return the length of a string that is stored in variable `VAR`
- Internal Variables
  - `$RANDOM` generate a 16-bit random number between `0` to `32767`.
    - use modulus calculation to generate numbers in certain range. `$RANDOM % 11` will get random number from 0 to 10.
  - `$OLDPWD` (OLDPrintWorkingDirectory) contains directory before the last cd command.
  - `$PWD` (PrintWorkingDirectory) The current working directory you are in at the moment.
  - `$HOME` The home directory of the user.
  - `$PATH` The search path for finding binaries for commands.
  - `$BASH_VERSION` Shows the version of bash that is running.
- Positional Parameters
  - In any script, `$0` returns the path of the script file relative to the `PWD` of the terminal.
  - `$N` points to the `N`th argument passed to the command(script).
    - `$1` is the first argument after the command.
    - `$2` is the second argument, and so on.
    - If an argument is missing, `$N` will be empty.
  - Positional parameters are read-only and can not be modified. Stored them in a variable to modify it or calculate its length.
- Other Special Characters
  - `$*` returns all arguments as a single string.
  - `"$*"`returns all arguments and expands to a word
  - `"$@"` returns a list of all arguments.
  - `$#` stores the count of the number of arguments a script file has received.
  - `$?` stores the returned value or exit status code of a command or function.
  - `$_`, Absolute path of the shell binary file that is executing the script
  - `$!`, Process ID of last executed command in the background, empty of no background command was extecuted
  - `$$`, Process ID of executing Bash script, returns a decimal number

### User Input

- use `read name` will prompt the user to enter a value for the variable `name`.

### Array

- Declare an array, `arrayName=('A' 'B' 'C' 'D')`.
- Print an array element, `echo ${arrayName[3]}`.
  - Index starts at 0.
- `echo ${arrayName[*]}` returns all elements.
- `${#ARRAY[*]}` returns the array length.
- `${!ARRAY[*]}` returns a list of indices.
- It can work with `for..in` loop as:
  ```bash
  for ITEM in ${ARR[@]}; do
    echo "GREET: $ITEM"
  done
  ```
  - `@` will be treated as all the possible index of an array.
  - `*` will expand the array to a single word.
- Sequence generation
  - `echo {0..10}` generate a list of number from 0 to 10.
  - `echo $(seq 0 10)` generate a list of number from 0 to 10.
  - `echo $(seq 0 3 10)` generate a list of number from 0 to 10 with step 3.
    - step can be a negative number. It will generate the list in reversed order.

### Arithmetic Operations

- All common arithmetic operations works here including `%`, `++` or `+=`.
- `let` Command
  - `let RESULT=1+1; echo $RESULT;`
  - `let RESULT="1 + 1"; echo $RESULT;`
  - `let "RESULT = 5 * 5"; echo $RESULT`
- `expr` Command
  - It evaluate the express followed and print the result.
  - needs space in between operators. `expr 1 + 5`
  - Without using quotes special characters like `*` need to be escaped. `expr 5 \* 1`
- `$((expression))` syntax
  - `RESULT=$((1 + 1))` evaluate expression and store it in a new variable.
  - `VAR=1; (( VAR += VAR ));` declare a variable and modify without `$`.

### Comparison

- For numbers use the following operators:
  - `-eq` Equal
  - `-ne` Not equal
  - `-gt` Greater than
  - `-ge` Greater than or equal
  - `-lt` Less than
  - `-le` Less than or equal
  - For example: `$10 -gt 20`.
- For strings use `>`, `<`, `<=`, `>=`, `==`, `!=`
  - Use `-z` to check if the string is empty. `-z ''`
  - Use `-n` to check if the string is non-empty.
  - Use `-f` to see if a file exist.
  - Both `=` and `==` works.
  - `>` and `<` needs to be escaped, `'b' \> "a"`.
- `test` command can be used to evaluate boolean expression.
  - If the result is true the command status will be 0, If the result is false the command status will be 1.
  - `test` command has alias command `[` that requires a `]` at the end. Ex, `[3 -gt 1]`
- `!` can be used to negate a condition.`![true && true]` or `[!false && true]`
- `&&` means `and`. `||` means `or`. They can be used to connect boolean expression.
  - Use parentheses to make them run in order `([ 1 -le 5 ] && [ 3 -lt 9 ]) || ([ 1 -gt 1 ] && [ 1 -ne 0 ])`
  - `&&` can also be used to connect to valid command. When evaluate two valid commands they will be execute at the meantime.

### Pattern Matching

##### `glob`(global) patterns

- `xyz`, Match exactly `xyz` and nothing more. Ex, `photo.db` for `photo.db`
- `*`, Match any 0 or more characters. Ex, `*s.db` for `photos.db`, `users.db`... (files with s.db suffix).
- `?`, Matches any single character. Ex, `?ing.db` for `king.db`, `ping.db`, `ring.db`
- `[...]`, Matches one character listed inside the brackets. Ex, `[pr]ing.txt` will match `ping.txt` and `ring.txt`.
- `[start-end]`, Matches any character from the start till the end of a set. Supported patterns are `a-z`, `A-Z` and `0-9`. Ex, `[m-z]ing.*` will match `ping.db`, `ping.txt`, `ring.db` and `ring.txt`.
- `[!...]`, Matches one character not included in the brackets. Ex, `[!pr]ing.txt` will match `king.txt`.
- `[!start-end]`, Matches any character not included from the till the end of a set. Ex, `[!m-z]ing.*` can match `king.db` and `king.txt`.
- `*.txt *.db` will match all files end with `txt` and `db` extension.

##### `extglob`(extended global) patterns

- run `shopt -s extglob` to enable `extglob` for the current shell session
  - run `shopt -u extglob` to disable `extglob` for the current shell session
  - run `shopt extglob` to see the status for `extglob`
- `!(*.txt|*.db)` will find files do not end with `txt` and `db`.
- `!(patterns)`, Match anything that does not match the 'patterns'. Match filenames without `photo` but next with `.db`. Ex, `!(photo).db`, it will match `photophoto.db`,`photos.db`, `photoss.db`, `photosss.db`.
- `?(patterns)`, Match zero or one occurances of the 'patterns', Match filename with `photo` but next with optional `photo`. Ex, `photo?(photo).db`, it will match `photo.db` and `photophoto.db`.
- `*(patterns)`, Match zero or more occurances of the 'patterns'. Match filenames with `photo` but next 0 or more occurances of `s`.Ex, `photo*(s).t*`, it will match `photo.txt`, `photos.txt`, `photoss.txt`, `photosss.txt`.
- `+(patterns)`, Match one or more occurances of the 'patterns'. Match filenames with `photo` but next 1 or more occurances of `s`.Ex, `photo+(s).txt` will match `photos.txt`, `photoss.txt` and `photosss.txt`.
- `@(patterns)`, Match one occurance of the 'patterns', Match filenames with `photo` but next exactly one occurance of `s`. Ex, `photo@(s).db` will match `photos.db`.

### If Condition

- `if`
  ```bash
  if [ "$PROCEED" = "YES" ]
  then
      echo "Performing task..."
  fi
  #or in one line like
  if [ 'proceed' == "proceed" ]; then echo "Performing task..."; fi
  ```
  - use `[[` instead of `[` if the condition contains pattern matching.
  - `[[` can also avoid wrapping variables inside double-quotes.
- `if-else`
  ```bash
  echo 'Enter a number?'
  read number
  if [ $number -gt 100 ]
  then
      echo 'It is greater than 100.'
  else
      echo 'It is smaller than 100.'
  fi
  ```
- `if-elif-else`
  ```bash
  VALUE=-10
  if [ "$VALUE" -lt 0 ]; then
      echo "VALUE is less than 0"
  elif [ "$VALUE" -eq 0 ]; then
      echo "VALUE is 0"
  else
      echo "VALUE is greater than 0"
  fi
  ```
- Nested `if-else`
  ```bash
  VALUE=10
  if [ "$VALUE" -lt 0 ]; then
      echo "VALUE is less than 0"
  else
      echo "VALUE is greater than 0"
      if [ "$VALUE" -le 10 ]; then
          echo "VALUE is less than or equal to 10"
      else
          echo "VALUE is greater than 10"
      fi # end of nested if block
  fi # end of parent if block
  ```
- `case`
  ```bash
  case STRING in
     globPattern1)
       statements
     ;;
     globPattern2 ) statements ;;
     * )
       statements
     ;;
   esac
  ```
  - `case`, `in` and `esac` keywords are required.
  - `)` marks the end of the pattern
  - `;;` marks the end of the statements for a pattern-block.
  - `STRING` contains a pattern listed in the case block
  - `statements` of that pattern-block will get execute and case statement will exit immediately.
  - `* )` will be the default case. The statement is contains will be executed if all previous case does not match.
  - The exit status code for the case block will be the statement exit status code of the matching case. If no case matches the exit status code will be 0.

### Loops

- Use `exit` to break out of loops.
- `for...in` loop
  ```bash
  files=/filepath/
  for file in $files
  do
    echo $(basename $file)
  done
  ```
  - If the `in` and variable followed is missing, the script need to run with a parameter. `./filename.sh $VAR`
- for loop
  ```bash
  for (( i = 0; i < 5; i++ )); do
      echo "The number is: $i"
  done
  # Use two variables in loop
  for (( n = 0, i = 1; n < 5; n++, i += i )); do
      echo -n "$i, "
  done
  # infinite for loop
  for ((;;))
  ```
- `while` loop
  ```bash
  NUMBER=1
  while [ $NUMBER -lt 5 ]; do
      echo "Number is: $((NUMBER++))"
  done
  # infinite while loop
  while true
  do
    # perform action
  done
  # or
  while :
  do
    # perform action
  done
  ```
- `until` loop
  ```bash
  NUMBER=1
  until [ $NUMBER == 4 ]
  do
      echo "Number is: $((NUMBER++))"
  done
  # infinite until loop
  until false
  do
      echo "Hello World"
  done
  ```

### Functions(Procedure)

- define functions
  ```bash
  function function_name() {
   # statements
  }
  # function using parameters
  function show_fruits(){
    echo "Local Args: \$1:$1 | \$2:$2"
  }
  ```
  - `function` keyword is optional. it is not supported in other shells like `sh`.
- invoke functions. run `function_name` as a command.
  - If it has parameter, run `function_name arg1 arg2`.
- A function executes in the same session of the script.
- When a function has parameters as positional parameters. They are inside function body, they do not interfere with the outer scope.
- variables defined outside the scope are accessible inside the function
- A variable that written inside the function will be written to the global scope.
  - use keyword `local` to prevent the variable inside a function to be able to accessed outside the function. Ex, `local LAST_NAME=$2`.
- `return` keyword can be used to return a value after function execution. `return $RANDOM`
  - Use `$?` to read the returned value after a function is invoked.
  - the value returned by the function should be from 0 to 255.
  - `0` meaning the function executed successfully
  - `1-255` meaning there was some problem with the function execution.
  - If a function does not return a value, the exit status of the function is the exit status of the last statement executed inside the function body.
- A function can be used inside `$()` or double backticks to print to output.
- A function in Bash has inline form as `function name(){ //statement; }` where `;` is mandatory)

### Useful Snippets

- refresh sudo priviliege throughout the lifetime of the script

```bash
sudo -v
while true; do sudo -n true; sleep 120; kill -0 "$$" || exit; done 2>/dev/null &
```
