
---
# Shell_Scripting

[HOME](../README.md)

---

# Basics
## Variables
- There are no datatypes.
- Accessing a non-existing value returns `null`.
- Spaces can break the script.
```sh
var="abc"        # var <- abc    (Always use double quotes)
var=$(command)   # var <- Output of command
var=$((math))    # var <- Result of a mathematical ecuation
```

 - Note that things between single quotes are not evaluated.
```sh
var="A"
echo '$var'    # >>> var
echo "$var"    # >>> A
```

## Special Variables
- `$?` exit status of last command
- `$$` process number of current shell
- `$HOME` working directory of the user.
- `$PATH` path where the shell looks for commands.
- `$USER` current user.
- `$HOSTNAME` hostname of the computer running the script.
- `$SECONDS` number of seconds the current script has been running.
- `$RANDOM` random number.
## Comments
```sh
# This is a comment
# This is also a comment
echo Hello World # This is a another comment
```


---
# Conditional Structures
## Expressions

- Expressions return `0` as `true` or any other value as `false`.
- Keywords `true` and `false` return its respective value

```sh
# Alternative 1
test $var -eq 0

# Alternative 2
[$var -eq 0]
```

### Numerical values
- `N -eq M` → $N = M$`
- `N -ne M` →  $N \ne M$
- `N -gt M` → $N > M$`
- `N -lt M` → $N < M$`
- `N -ge M` → $N \ge M$`
- `N -le M` → $N \le M$`

### File types
- `-s file` → Check if file exists and if it is non-empty.
- `-f file` → Check if file exists and if it is normal.
- `-d file` → Check if file is a directory.
- `-w file` → Check if file is writable.
- `-r file` → Check if file is readable.
- `-x file` → Check if file is executable.
### String values
- `S = R` → Check if S is equal to R.
- `S != R` → Check if S is not equal to R.
- `-z S` → Check if length of S is `0`.
- `-n S` → Check if length of S is not `0`.

## If-else

```sh
if expression
	then ...
elif expression
	then ...
else 
	...
fi
```

## Case (switch)

```sh
case "$var" in
1) ...    # If var == 1
;;
2) ...    # If var == 2
;;
*) ...    # Else
esac
```

---
# Parameters
```sh
$promt> <filename> <arg1> <arg2> ...
```

- Params. can be accessed with `$i` being `i` the param number (`$1`, `$2).
- `$0` is always the filename.
- `$#` is the number of arguments specified.
- `shift` command removes the first arg and re-enumerates.
- `$*` is a string containing all specified args (`"arg1 arg2 arg3"`)
	- Unexpected behaviour if special characters or spaces.
	- `$@` must be instead.

---
# Repetitive Structures
## For
- General expression
```sh
for i in list
do
    # Code
done
```

- Other
```sh
# Print the arguments
for i
do
	echo i
done

# Print numbers from 1 to 5
for i in 1 2 3 4 5
do
    echo "Number: $i"
done

# Print numbers from 2 to 10
for i in {2..10}
do
    echo "Output: $i"
done

# List all files in the current directory
for file in *
do
    echo "File: $file"
done

# Print each character of a string
for char in "Hello, World!"
do
    echo "Character: $char"
done

```

## While
```sh
while expression
do
    # Code
done
```

## Loop keywords
- `continue` jumps to the next loop iteration.
- `break` jumps out of the loop

---
# Console I/O
## Input
```sh
# Basic usage
read var       # Ask for an input
echo "$var"    # Access and display the input

# Provide custom message (-s)
read -p "Introduce data: " data

# Hide input (-s)
read -sp "Introduce password: " password

# Limitting input length (-n)
read -n 3 var

# Timeout for input (-t)
read -t 5 var
```
## Output
```sh
# Standard Output (STDOUT)
echo "Something"
echo "Something" >&1

# Standard Error (STDERR)
echo "Something" >&2
```
