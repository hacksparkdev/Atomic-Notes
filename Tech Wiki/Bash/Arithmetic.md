Tags: [[Bash]] [[Scripting]] [[Programming]] #Artihmetic

To perform arithmetic in Bash you would use `$(())`
Example:
```Bash
#!/bin/bash

echo $((2 + 2))
```

#### Use of variables
```Bash
#!/bin/bash

x=12
y=4

echo $((x + y))
```

 #### Modulo `%` is getting the remainder. We can use modulo to figure out if a number is even or odd.

   
 