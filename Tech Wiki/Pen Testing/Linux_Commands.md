# Useful Linux Commands

Tags: [[Useful_Linux_Commands]] [[Penetration Test]] #LinuxCommands


# Uniq 

The `uniq` command in Linux is used to filter out or report duplicate lines in a file or stream of text. It processes sorted input and ensures that only unique lines are displayed, or duplicates are highlighted based on the options provided.

### Basic Syntax:
```bash
uniq [OPTION] [INPUT [OUTPUT]]
```

### Key Points:
- **Requires Sorted Input**: The `uniq` command works best on sorted input because it only compares adjacent lines. Use `sort` to prepare the input if necessary.
- **Input and Output**: By default, `uniq` reads from standard input and writes to standard output.

---

### Common Use Cases and Examples:

1. **Display Unique Lines**:
   ```bash
   uniq file.txt
   ```
   Outputs only unique adjacent lines from `file.txt`.

2. **Display Duplicate Lines**:
   ```bash
   uniq -d file.txt
   ```
   Displays only lines that are duplicated in the input.

3. **Count Occurrences**:
   ```bash
   uniq -c file.txt
   ```
   Precedes each line with the number of times it occurs.

4. **Ignore Case**:
   ```bash
   uniq -i file.txt
   ```
   Treats lines as identical if they differ only in case.

5. **Output Only Non-Duplicates**:
   ```bash
   uniq -u file.txt
   ```
   Outputs only lines that are not repeated.

6. **Output to a File**:
   ```bash
   uniq file.txt output.txt
   ```
   Writes the filtered result to `output.txt`.

---

### Example Workflow:
Given a file `names.txt` with the following content:
```
Alice
Bob
Bob
Charlie
Alice
```

#### Command:
```bash
sort names.txt | uniq
```

#### Output:
```
Alice
Bob
Charlie
```

---

### Combining with Other Commands:
You can combine `uniq` with other commands like `sort` and `grep` to create powerful pipelines:
```bash
sort file.txt | uniq -c | sort -nr
```
- Sorts the file, counts occurrences, and sorts the result numerically in reverse order (useful for finding the most common lines).

Let me know if you'd like more examples or advanced use cases!


#### base64 Decode
#Base64Decode

```Bash
echo 'base64 code' | base64 -d
```

### Decode Rotate 13 Cipher

```Bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

```


