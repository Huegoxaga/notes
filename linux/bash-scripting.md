# Bash Scripting

## Introduction

- It stores a batch of command in order to complete certain task in one execution.
- It usually has an extension as `.sh`. It also can be run without any extenion or as `.txt`.
- Bash does not have a type system, everything is saved as strings.
- It can be edited by any text editing tool.
- It is recommanded to run the full path of the commands in the scripts.

## Run Script

- Any text file contains commands line by line can be run using `bash filename`.
- Shebang is used at the first line of the text file to make the file executable by itself.
  - It is an operator look like `#!`
  - It is followed by the path of the interpreter.
  - For bash scripting, use `#!/bin/sh` or `#!/usr/bin/env bash` if the path of bash is unknown.
  - The user needs the `execute` file permission for the script.
  - The file can then be executed by using `./filename`.
  - Add the directory path into the `$PATH` variable to make the script run without `./`.
- Each script will be run in a separate session.

## Syntax

### Comment

- Any line starts with `#` can be followed by a single line comment.

- `\` can be placed at the end of each line. It will make the command continue in a new line.
- `commandA && commandB` can be used to run two command from left to right.
- `;` can be used to separate multiple command in entered one line.

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
- `$RANDOM` generate a 16-bit random number between `0` to `32767`.
  - use modulus calculation to generate numbers in certain range. `$RANDOM % 11` will get random number from 0 to 10.

### User Input

- use `read name` will prompt the user to enter a value for the variable `name`.

### Array

- Declare an array, `arrayName=('A' 'B' 'C' 'D')`.
- Print an array element, `echo ${arrayName[3]}`.
  - Index starts at 0.
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
  - Both `=` and `==` works.
  - `>` and `<` needs to be escaped, `'b' \> "a"`.
- `test` command can be used to evaluate boolean expression.
  - If the result is true the command status will be 0, If the result is false the command status will be 1.
  - `test` command has alias command `[` that requires a `]` at the end. Ex, `[3 -gt 1]`
- `!` can be used to negate a condition.`![true && true]` or `[!false && true]`
- `&&` means `and`. `||` means `or`. They can be used to connect boolean expression.
  - Use parentheses to make them run in order `([ 1 -le 5 ] && [ 3 -lt 9 ]) || ([ 1 -gt 1 ] && [ 1 -ne 0 ])`
  - `&&` can also be used to connect to valid command. When evaluate two valid commands they will be execute at the meantime.

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
