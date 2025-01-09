Tags: [[Burpsuite]] [[Command Injection]] [[Cybersecurity]] [[Penetration Testing]] [[Filter Evasion]]

## References 
This website has ways to bypass filters.
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Command%20Injection#bypass-without-space

### Bypassing space Filters
#bypassspace

If a filter is stopping us from executing a command we can test and see which part of the command is causing the issue. 

If the space or `+` is causing the command to be blocked we can use a `Filter bypass`. There are a few filter bypasses we can use. 

- **${IFS}
	- a special shell variable called the internal Field Separator. It contains white space characters(space, tab, newline) It will be interpreted as a space. This can be used instead of the + symbol if it is being blocked**. 
- Example: ls${IFS}-la 

We can also use `%09`.

### Bypass for `;` filter

#Bypassemicolon

To by pass a semicolon we can use environment variables. If we wanted to get a semicolon we could use:
```Bash
echo ${LS_COLORS:10:1}
# THIS WILL PRINT:
;
```

If we were using Burpsuite we would not use the echo command. If we had a filter that wouldn't let us use the `space +` or `;` we could use.

#spacesemicolonfilter
```bash
${LS_COLORS:10:1}${IFS}
```

Get `/`
```bash
# The $HOME & $PATH Environment Variable have th forward slash at 0:1 So 
echo $HOME
#would give 
/Path/To/home
# To retrive the forward slash you would use 
echo ${HOME:0:1}
#This would give you 
/
```

On Windows it would look something like this
```powershell
echo %HOMEPATH:~6, -11%
# THIS WOULD PRODUCE A 
\
```


