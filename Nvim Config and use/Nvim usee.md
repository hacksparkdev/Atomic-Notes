Tags: [[nvim]] 
Here's a detailed list of the plugins added, how to use them, and all the key bindings configured or changed in the updated `polish.lua`:

---

### **Plugins Added**

1. **[nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)**
   - **Description**: Provides advanced syntax highlighting and better code parsing for various programming languages.
   - **How to Use**:
     - Syntax highlighting is enabled by default for supported languages.
     - To install/update language parsers, run: `:TSInstall <language>` (e.g., `:TSInstall python`).

---

2. **[nvim-lspconfig](https://github.com/neovim/nvim-lspconfig)**
   - **Description**: Configures Language Server Protocols (LSP) for Python and Bash.
   - **How to Use**:
     - Auto-completion and diagnostics work automatically once the file is opened.
     - Use `:LspInfo` to see the LSP status.
     - Hover over symbols for information using `K` (default key binding).

---

3. **[nvim-dap](https://github.com/mfussenegger/nvim-dap)**
   - **Description**: Debug Adapter Protocol for debugging code (Python support added).
   - **How to Use**:
     - Start debugging: `:lua require'dap'.continue()`.
     - Step into: `:lua require'dap'.step_into()`.
     - Step over: `:lua require'dap'.step_over()`.
     - Place breakpoints: `:lua require'dap'.toggle_breakpoint()`.

---

4. **[telescope.nvim](https://github.com/nvim-telescope/telescope.nvim)**
   - **Description**: Fuzzy finder for files, symbols, live grep, and more.
   - **Key Bindings**:
     - `<leader>ff`: Open file search.
     - `<leader>fg`: Live grep (search text in all files).
     - `<leader>fb`: Open buffer search.
     - `<leader>fs`: Search for document symbols.

---

5. **[null-ls.nvim](https://github.com/jose-elias-alvarez/null-ls.nvim)**
   - **Description**: Adds formatters and linters for Python and Bash.
   - **How to Use**:
     - Python: Formatting with `black` and linting with `flake8`.
     - Bash: Formatting with `shfmt`.
     - Use `:Format` to format the current file manually.

---

6. **[vim-fugitive](https://github.com/tpope/vim-fugitive)**
   - **Description**: Git integration for version control.
   - **How to Use**:
     - `:Git` to open the Git interface.
     - `:Gdiff` to view diffs.
     - `:Gstatus` for Git status.

---

7. **[nvim-jqx](https://github.com/gennaro-tedesco/nvim-jqx)**
   - **Description**: JSON viewer for easy navigation and formatting of JSON files.
   - **How to Use**:
     - Open any JSON file, and it automatically provides an interactive view.

---

8. **[nvim-autopairs](https://github.com/windwp/nvim-autopairs)**
   - **Description**: Auto-closes brackets, quotes, and other pairs.
   - **How to Use**:
     - Works automatically while typing.

---

---

### **Key Bindings Added/Changed**

| **Key Binding** | **Mode**  | **Action**                              | **Description**                                           |
|------------------|-----------|-----------------------------------------|-----------------------------------------------------------|
| `<leader>ff`     | Normal    | `:Telescope find_files`                | Open file search.                                         |
| `<leader>fg`     | Normal    | `:Telescope live_grep`                 | Search text in all files using live grep.                 |
| `<leader>fb`     | Normal    | `:Telescope buffers`                   | Search and switch between open buffers.                   |
| `<leader>fs`     | Normal    | `:Telescope lsp_document_symbols`      | Search for document symbols in the current file.          |
| `<leader>r`      | Normal    | `:!python %`                           | Run the current Python file in a terminal.                |
| `<leader>s`      | Normal    | `:!bash %`                             | Run the current Bash script in a terminal.                |

---

### **Key Points**
- The `<leader>` key is set as **space (` `)**.
- To view all available commands, you can:
  - Run `:Telescope keymaps` to see all active key mappings.
  - Use `:Lazy` to manage the plugins.

Let me know if you have any additional questions or changes you'd like!

### Copy in Nvim 

`yy`

### Paste in Nvim

`p`

## Copy all contents of a file 
2. Enter Visual Mode:

    Visual Mode allows you to highlight text.
        Press v to start visual mode and then navigate through the text you want to copy.

3. Select All (Visual Block Mode):

    You can select all content at once by entering visual block mode:
        Press CTRL + V to enter visual block mode.
        Then, use the arrow keys to select the entire text.

4. Copy the Selected Text:

    Once the entire text is selected, press y to copy the highlighted content.

5. Paste the Copied Content:

    You can now paste the copied content anywhere (in a different editor or terminal) using CTRL + V.
