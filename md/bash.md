#Introduction to Shell Scripting with Bash

 

-
-
##What is a script, what are some examples

A script is a file containing a series of commands for a shell to run.  
Scripts are used for many purposes including system configuration, automating tasks, and even [checking on your stock portfolio](https://davidwalsh.name/stock-quotes-command-line).

-
## Know your shell

Most *nix shells behave similarly, but knowing which one you use is important.  
`echo $SHELL` will usually tell you your shell.  
We use Bash, the default in OS X and many other systems.

-
### Some Shell examples

- Bash - Bourne again shell, combines features from sh, tcsh, and ksh
- sh - Bourne Shell, named for developer Stephen Bourne at Bell Labs
- ksh - Korn shell
- csh - C shell, improved in tcsh
- cmd.exe - Windows Command Prompt<sup>1</sup>
- PowerShell - Windows PowerShell<sup>1</sup>

<sup>1</sup>These are windows shells. They have completely different commands and philosophies from *nix. We won't be covering them here.

Note: This slide needs some formatting work.

-
## Other popular scripting languages

- [Python](https://www.python.org/)
- [Perl](https://www.perl.org/)

-
-
### Writing a simple script

A tiny script:

```
#!/bin/bash
echo "Hello Bash!"
```
User-written scripts are traditionally named with a .sh extension eg: script.sh  
System scripts don't necessarily follow this convention.

-
## Comments

Comments in bash are marked with a `#` character.
Comments can be on a line of their own or after a command. Anything after the `#` is ignored by the shell

```
#!/bin/bash
#Prints a welcoming message
echo "Hello Bash!" #print the message
```

-
## Making scripts executable

- Add execute permissions to a script with `chmod +x script.sh`
- Remember the #! in the file? That's how the kernel knows what program to execute (try changing it to `#!/usr/bin/vim`)

-
## Ways to call scripts

- `bash script.sh` - runs the script in another instance of bash
- `source script.sh` - runs each line of the file as if you had typed them
- `. script.sh` - a synonym for `source script.sh`
- `./script.sh` - executes the file. Must have execute permissions (chmod +x)

-
## Scripts can call other scripts

script1.sh

```
#!/bin/bash
. script2.sh
```
script2.sh

```
#!/bin/bash
echo "Welcome to Bash Scripting"
```
When run:

```
$ . script1.sh
Welcome to Bash Scripting
```

-
## In-Class Exercise

1. Write the scripts from the previous slide and try to run them using each method described before.
2. Add execute permissions to the scripts and run them again
3. Change the shebang (#!) to `/usr/bin/vim` and run the script again

What happens? What are the differences? Why?

-
-
## Variables

Assign variable names with `=`. Reference variables with the `$` prefix. Example:

```
$ myvar=42
$ echo $myvar
42
```

-
## Input and output

Write output to the terminal using `echo` or `printf` (gives you a bit more control).  
You can read input using the `read` command. `read` stores input in a variable given as its argument. Example:

```
$ read name
> Bob
$ echo "Hello $name"
Hello Bob
``` 

-
-
### functions

Functions are named blocks of code you can call within a script by the name. Functions are defined with the `function` keyword and curly brackets (`{}`) around the commands. 

-
### Example

**funscript.sh**:

```
#!/bin/bash

function say_hello {
    echo "Hello"
}

say_hello
echo "Goodbye"
```
When called:

```
$ . funscript.sh
Hello
Goodbye
```

-
## Script arguments

When running a script you can pass extra information to it as arguments. eg: `. script.sh arg1 arg2 arg3`  
Access arguments in the script with the numbered variables `$1`, `$2` etc. `$0` is the name of the script and `$#` the number of arguments given. `$*` contains a list of all the arguments.


-
## Exit codes

Commands and programs set a code to the `$?` variable when they exit.

- 0 - success
- anything else - failure; Read the man pages for that program for details.

-
## Flow control statements 

Scripts don't have to execute one command after another blindly. Flow control lets you choose whether to run certain commands, or to repeat commands until a certain point.

-
## If then else

```
if [ statement ]; then
	echo "statement was true"
else
	echo "Statement was false"
fi
```

Evaluates `statement` and runs the `then` block if true, `else` block if false.  
`statement` can use comparison operators, file operators, or other commands.

-
### comparison operators

Bash has two sets of comparison operators, one for string comparisons and one for numeric comparisons.

-
#### Numeric comparison operators

- `x -eq y` - x is equal to y
- `x -ne y` - x is not equal to y
- `x -lt y` - x is less than y
- `x -le y` - x is less than or equal to y
- `x -gt y` - x is greater than y
- `x -ge y` - x is greater than or equal to y

-
#### String comparison operators

- `x = y` - equality
- `x != y` - inequality
- `x < y` - x less than y*
- `x > y` - x greater than y*
- `-n x` - x is not null
- `-z x` - x is null

*Must be escaped with \ or [[]]

-
### file evaluation operators

Bash also has operators for checking the status of a desired file:

<!-- table -->
- `-d file` - file exists and is a directory
- `-e file` - file exists
- `-f file` - file exists and is a regular file
- `-r file` - you have read permission on file
- `-s file` - file exists and is not empty
- `-w file` - you have write permissions on file
- `file1 -nt file2` - file1 is newer than file2
- `file1 -ot file2` - file1 is older than file2

-
### In-class Exercise

- Write a shell script that takes two arguments and prints which one is greater (lexicographically/alphabetically)
- Change the script to compare numbers and print which is greater; If they are equal, print that.
- Write a new script that takes a file name and tells whether that file exists, and if it is a directory or not.

-
# Loops

-
### For loops

```
for script in *.sh; do
    echo "Script named: $script"
done
```
<!--
C-style...
-->

-
### While loops

```
while read line; do
    echo "$((counter++)): $line"
done
```

-
## Arithmetic
All bash variables are strings and will be treated as such by default. Force them to be evaluated as arithmetic statements with `$((statement))`. For example:

```
$foo=1
$bar=2
$echo $foo+$bar
1+2
$echo $(($foo+$bar))
3
```

-
## In-Class exercise

Write a script that counts the total number of regular files and directories in the current directory. Print out the total for each, and the total number of items in the current directory.

<!--

# More powerful features


## Regular Expressions (regex)


### Tiny regex primer (greater depth comes in week 6-ish)


### Grep regex example -->