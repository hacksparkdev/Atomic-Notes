Tags: [[Bash]] [[Command Line]] [[Scripting]] [[Quoting]]


## Tokenisation
--- 

The Shell breaks the command lines into tokens. 

**Token**: A sequence of character that is considered as a single unit. 
### Metacharacter:
- |
- &
- ;
- ()
- <>
- space, tab, newline

**Word**: A token that does not contain an unquoted metacharacter.
**Operator**: A token that contains at least one unquoted metacharacter.

The difference between words and operators is: **Words** never contain unquoted metacharacter, **Operators** always contain unquoted metacharacters

## Command Identification
---
**Simple Commands**: Are just a bunch of individual words, and each simple command is terminated by a control operator. 

**Compound Commands**: Provide bash with its programming constructs, such as if statements, for loops, while loops, etc.

## Expansions
---


## Quote Removal
---

We often add quotes to control how the command is interpreted, so this step will simply remove all those supportive quotes.

## Redirection



After completing these 5 steps, bash will then execute the command line that is left over. 
