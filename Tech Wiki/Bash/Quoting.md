Tags: [[Bash]] [[Command Line]] [[Scripting]]

Quoting is about Removing Special Meanings. 

## Three Types of Quoting

1. Backslash ( \ ):  Removes special meaning from next character. 
2. Single Quotes ( ' ' ): Removes special meaning from all characters inside. 
3. Double Quotes ( " " ): Removes special meaning from all except dollar signs ( $ ) and backticks ( ` ` ).

### Escape with `\`

```Bash

echo john \& Janes

# This will print John and Jane. 
# If we do not use the \ We will get an error because the & is not being used corectly.

```

### How to use a backslash in Terminal. 

```Bash
# Example. We need to set a variable like file path.
filepath=C:\Users\corey\Documents
# This wouldn't work because the backslash is escaping what is after it. 

filepath=C: \\Users\\Corey\\Documents
# With \\ We can use the \ in the variable.
```

#### Single Quotes

```Bash
# We can use '' to have the same effect as the \
# Example:
filepath='C:\Users\Corey\Downloads'
# Single quotes removes the special meaning of everything inside it.
# So this wouldn't work.
filepath='C:\Users\$USER\Downloads'
```





