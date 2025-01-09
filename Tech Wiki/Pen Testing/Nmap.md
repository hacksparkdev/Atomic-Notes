Tags: [[Penetration Testing]] [[Tags/Enumeration]] #nmap

### Saving scans 
#SavingScans

```Bash
# Save to txt file
sudo nmap -oN nameoffile.txt [target]
```

```Bash
# Save in all formats
sudo nmap -oA nameoffile [target]
```

```Bash
sudo nmap -oX output.xml [target]
```

### Convert XML to HTML
```Bash
xsltproc nameoffile.xml -o nameoffile.html
```

### Service enumeration with Nmap
#ServiceEnumerationNmap

```bash
sudo nmap -sC $TARGET
```



