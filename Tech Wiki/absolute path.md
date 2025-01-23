Tags: [[Linux]] [[Terminal]] [[Cybersecurity]] [[File Inclusion]]


In **Bash** or any terminal environment, **relative paths** and **absolute paths** are used to navigate and specify the location of files and directories. Here's an explanation of each:

---

### **1. Absolute Path**

- An **absolute path** specifies the location of a file or directory from the **root directory (`/`)**.
- It is a complete path and starts with `/`, which represents the root.
- It provides the full hierarchy of directories to locate the file, so it is independent of your current working directory.

#### Example:

Suppose the file `example.txt` is located in the `/home/user/docs` directory:

```bash
/home/user/docs/example.txt
```

This is an absolute path because it starts from the root `/`.

#### Key Characteristics:

- Always starts with `/`.
- Fully specifies the location.
- Can be used from any working directory.

---

### **2. Relative Path**

- A **relative path** specifies the location of a file or directory **relative to the current working directory (`pwd`)**.
- It does not start with `/` but instead depends on your **current location** in the directory structure.
- Commonly uses special symbols:
    - `.` (dot) represents the current directory.
    - `..` (double dot) represents the parent directory.

#### Example:

Suppose your current working directory is `/home/user`, and you want to access `example.txt` in the `docs` directory:

```bash
docs/example.txt
```

This is a relative path because it depends on the current directory (`/home/user`).

#### Key Characteristics:

- Does not start with `/`.
- Shorter and context-dependent.
- Simpler for navigating within nearby directories.

---

### **Practical Examples**

1. **Absolute Path**
    
    ```bash
    cat /home/user/docs/example.txt
    ```
    
    This command works regardless of the current working directory.
    
2. **Relative Path**
    
    - Current directory: `/home/user`
    
    ```bash
    cat docs/example.txt
    ```
    
    This works because `docs` is a subdirectory of the current directory.
    
3. **Using `..` for Parent Directory**
    
    - Current directory: `/home/user/docs`
    
    ```bash
    cat ../example.txt
    ```
    
    This navigates to the parent directory (`/home/user`) and looks for `example.txt`.
    

---

### **How to Choose Between Them**

- **Absolute Path**: Use it when scripting or when you want to ensure the path works regardless of the current directory.
- **Relative Path**: Use it for convenience when working interactively and the file or directory is close to your current location.