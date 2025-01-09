Tags: [[variables]] [[Bash]] [[Scripting]] [[Parameter Expansion]] #bashVariables

## Parameter Expansion and Variable

**<span style="color:rgb(192, 0, 0)">Parameter</span>** - A parameter is any entity that stores values.
<span style="color:rgb(192, 0, 0)">Variable</span> - A parameter whose values you can manually change


## Creating variables

```Bash
#!/bin/bash

# This Creates the variable Make sure there is no space after the = sign
name="Corey"

# This Calls the variable
echo "Hello ${name}"
```

## Shell Variables

## Home
The home variable is used to store the absolute path to the current user’s home directory.
```Bash
$HOME
```
## Path 
The path variable contains the list of folder that the shell will search for executable files to run as command names.
```Bash
$PATH
```

## User 
```Bash
$USER
```

## Hostname & Hosttype
```Bash
$HOSTTYPE

$HOSTNAME
```

## PS1
```bash
# change the symbol on your terminal 
PS1=“>: “
```


## Parameter Expansion

#### Change variables to lowercase
```Bash
Name=Corey

# This line will take the variable and make all the letters lowercase
Echo ${Name,,}


```


#### UpperCase
```bash
# Makes first letter uppercase
Echo ${user^}

# Make the whole thing uppercase
Echo $(user^^)
```

#### Get The Length of a variable
```bash
Echo ${#name}
```


## Slicing 
#Bash_Slicing
```bash
Numbers=0123456789

Echo ${numbers:0:7}

# This would print 
0123456

# Getting characters backwards
Echo ${numbers: -3:7}

```






