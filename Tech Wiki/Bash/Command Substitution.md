Tags: [[Bash]] [[Scripting]] #Bash  #CommandSubstitution

Command substitution in Bash allows the output of a command to be captured and used as input for another command or assigned to a variable. There are two ways to perform command substitution:

    Using backticks (`).
    Using the $(command) syntax (preferred because it's easier to read and nest).

#### Example 
```Bash
#!/bin/bash

time=$(date +%H:%m:%S)
echo "Hello $USER, the time is $time"
```

