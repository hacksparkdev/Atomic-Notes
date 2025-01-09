Tags: [[Bash]] [[Scripting]] [[Linux]] [[Cybersecurity]] #Bash


### Running a Bash Script
```Bash
# Every Bash script needs this at the top.
#!/bin/bash
```

### Echo
```Bash
#!/bin/bash

echo "This is a print Statement"
exit 0 
```

#### Exit Statement (0 = successful, 1-245 = unsuccessful)

### Make Script Executable
```Bash
chmod +x NameofScript
```

### Commenting

```Bash
#!/bin/bash

# This is a Comment
echo "This prints"
```

### Creator information

```Bash
#!/bin/bash

# Author: Corey Jones
# Date Created: 12/10/2024
# Last Modified: 12/10/2024

# Description
# This files is just to show what i should put in my scripts.

#Usage
# Nameofscript
```


### Chmod Calculator #ChmodCalculator
https://chmod-calculator.com/


### Changing file permissions so the owner can only use it

```Bash
chmod 755 NameofFile
```

### Recommended For running 
```Bash
chmod 744 NameofFile
```


### Simple Back up Script

```Bash
#!/bin/bash

# Author: Corey Jones
# Date Created: 12/10/2024
# Last Modified: 12/10/2024

# Description
# This script backs up files.

tar -cvf ~/Desktop/Bash/my_backup_"$(date +%d-%m-%Y)".tar ~/* 2>/dev/null
exit 0
```


### Get System Path #SystemPath

```Bash
echo "$PATH"
```

### Run file from anywhere in terminal

we will need to add our folder path to our .profile file.

```bash
nvim ~/.profile
```

Now add the file path.

```Bash
export PATH = "$PATH: $HOME/pathtofile"
```

