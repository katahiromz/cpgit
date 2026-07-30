# cpgit by katahiromz

`cpgit` is a lightweight Bash script that functions like the standard `cp` command, but specifically tailored for Git repositories. It copies a local Git repository to a new directory while respecting `.gitignore` rules—excluding untracked or ignored files (such as build artifacts or `node_modules`) while preserving full `.git` history, configuration, and submodules.

## Features

- **`.gitignore` Aware:** Excludes ignored files and build clutter across the main project and submodules.
- **Submodule Support:** Handles repositories containing nested Git submodules natively without breaking references.
- **Zero Third-Party Dependencies:** Uses built-in `git` commands (`checkout-index`), removing the need for external tools like `rsync`.
- **Preserves Git History:** Copies the `.git` directory so your commit history, branches, and remote settings remain intact.
- **Safe Execution:** Checks for missing arguments, invalid source directories, missing `.git` folders, and existing destination paths before running.

## Prerequisites

- `bash`
- `git`

## Installation

1. **Clone or download** the `cpgit` script.
2. **Make it executable:**
```bash
chmod +x cpgit
```
3. **Move it to a directory in your `PATH**` (optional, but recommended for global access):
```bash
sudo mv cpgit /usr/local/bin/
```

## Usage

```bash
cpgit <source_directory> <destination_directory>
```

### Example

```bash
cpgit my-project my-project-copy
```

This will create `my-project-copy`, containing only tracked Git files (including submodules) and the `.git` folder from `my-project`.

## How It Works

1. Uses `git checkout-index` to export only tracked files from the Git index directly to the destination path.
2. Recursively iterates through any submodules using `git submodule foreach` to export their tracked files into the correct relative paths.
3. Copies the original `.git` directory (including `.git/modules` for submodules) directly to the destination directory.

## License

- [MIT](https://www.google.com/search?q=LICENSE)
