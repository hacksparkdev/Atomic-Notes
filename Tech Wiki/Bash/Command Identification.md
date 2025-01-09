Tags: [[Bash]] [[Scripting]] [[Programming]] 

## Simple Commands
--- 
#### Example

```bash
echo 123
```


#### Break up command line

```bash
echo abc echo 123
# This would be printed as echo abc echo 123 which is probably not what you inteded.

echo 123 ; echo abc
# This would give you 123 abc on a new line. 
```


## Compound Commands
---
Each compound command starts with a **reserved word** and is terminated by a corresponding reserved word. 

```bash
if [[2 -gt 1]]; then
	echo "Hello World"
fi
``` 

