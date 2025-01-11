### Quick Notes

In compressed files the the headers will indicate how the files are compressed. Here is a list of compression types and there Headers. 

### 1. **Gzip** (`gzip`):
   - Magic Header: `\x1F\x8B\x08`
   - This is the standard gzip file format.

### 2. **Bzip2** (`bzip2`):
   - Magic Header: `BZh91AY`
   - This identifies the compressed file as a **Bzip2** format.

### 3. **XZ** (`xz`):
   - Magic Header: `FD 37 7A 58 5A 00`
   - This indicates a **XZ** compressed file.

### 4. **7z** (7-Zip):
   - Magic Header: `377ABCAF271C` (in hexadecimal)
   - This identifies **7z** files.

### 5. **ZIP**:
   - Magic Header: `PK\x03\x04`
   - This is the standard **ZIP** archive format.

### 6. **RAR**:
   - Magic Header: `52 61 72 21 1A 07 00`
   - This identifies **RAR** files.

### 7. **DEFLATE**:
   - Magic Header: `0x08 0x00`
   - This represents the **DEFLATE** compression used in formats like `zip`.

### 8. **Zlib**:
   - Magic Header: `0x78 0x9C`
   - This identifies **Zlib** compressed data, which can be used inside `gzip`, `zlib`, etc.

### 9. **LZMA**:
   - Magic Header: `5D 00`
   - This indicates **LZMA** compression.

---

### **Common Signatures in Hexadecimal:**
- **Gzip**: `1F 8B 08`
- **Bzip2**: `42 5A 68 39 31`
- **7z**: `37 7A BC AF 27`
- **ZIP**: `50 4B 03 04`
- **RAR**: `52 61 72 21 1A`
- **DEFLATE**: `08 00`
- **Zlib**: `78 9C`
- **LZMA**: `5D 00`

---

### **Tools to Identify Compression Type**:
- **`file`**: This command can identify file types, including compressed formats.
  ```bash
  file yourfile
  ```
- **`xxd`**: Use this to inspect the first few bytes to identify headers.
  ```bash
  xxd -l 4 data.bin
  ```

With this list, you can easily identify the file type by matching its header to one of these standards. Let me know if you need more assistance!

## Change the extension of a file to unzip or decompress

First we will need to check the hex with `xxd`.

```Bash
xxd nameoffile
```

This will give you the `signiture`. After finding the signiture we can convert the file and unzip it. 

```Bash
xxd hexdump_data
00000000: 3030 3030 3030 3030 3a20 3166 3862 2030  00000000: `1f8b` 0
00000010: 3830 3820 6466 6364 2065 6236 3620 3032  808 dfcd eb66 02
00000020: 3033 2036 3436 3120 3734 3631 2033 3232  03 6461 7461 322
00000030: 6520 202e 2e2e 2e2e 2e2e 662e 2e64 6174  e  .......f..dat
00000040: 6132 2e0a 3030 3030 3030 3130 3a20 3632  a2..00000010: 62
00000050: 3639 2036 6530 3020 3031 3365 2030 3263  69 6e00 013e 02c
00000060: 3120 6664 3432 2035 6136 3820 3339 3331  1 fd42 5a68 3931
00000070: 2034 3135 3920 2062 696e 2e2e 3e2e 2e2e   4159  bin..>...
00000080: 425a 6839 3141 590a 3030 3030 3030 3230  BZh91AY.00000020
00000090: 3a20 3236 3533 2035 3963 6120 3833 6232  : 2653 59ca 83b2

```
As we see above this is a gzip. Now lets convert it. 

```Bash
mv hexdump_data hexdump.gz
```
Now we can unzip the file and repeat if needed. 

## SSH / OpenSSH / Keys

SSH uses public key authentication, the authentication entity has a public key and a private key. 
The `Private` Key is kept on the computer you log in from, while the `Public` key is stored on the .ssh/autheorized_keys. When loging into your computer 
through ssh the public key locks messages in a way that can only be unlocked by your private key. 

SSH uses RSA for its keys. 

`Key-based` authenticatio uses two keys, one `public` key that anyone is allowed to see, and another `private` key that only the owner is allowed to see.
The  `public` key is sotred on the computer you want to log in to and the `private` key is stored on the computer you are logging in from. 

## Generating RSA Keys

```Bash
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa
```

## Use Private SSH key to login to session

```Bash
ssh nameoffile username@localhost
```
#### Using Netcat

```Bash
nc localhost 30000
```

#### Create a SSL/TSL connection with `openssl`

```bash
openssl s_client -connect localhost:30001
```


