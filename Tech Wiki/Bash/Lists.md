Tags: [[Bash]] [[Scripting]] [[Bash Lists]] #Bash #Lists 

### Create lists in Bash Terminal 
```Bash
echo {1,2,Open,Penis,43}
# There cannot be any spaces in the operation. 
```

### Range List
```Bash
echo {1..10}
# This will print 1 2 3 4 5 6 7 8 9 10 

# Add how you want to count at the end
echo {1..10..2}
# This will print 1 3 5 7 9
```

### Letter List
```Bash
echo {a..z}
# This will print a b c d e f g h i j k l m n o p q r s t u v w x y z
```

### Use Expansion 
```Bash
# Create folders.
mkdir month{01..12} 
# This will create folders called month01 month02 etc....

# You can do the same thing with the touch command.
```

