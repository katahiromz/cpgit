# cpgit by katahiromz

`cpgit` is a lightweight Bash script that functions like the standard `cp` command, but specifically tailored for Git repositories. It copies a local Git repository to a new directory while respecting `.gitignore` rules—excluding untracked or ignored files (such as build artifacts or `node_modules`) while preserving the full `.git` history and configuration.

## Features

- **`.gitignore` Aware:** Excludes ignored files and build clutter during the copy process.
- **Preserves Git History:** Copies the `.git` directory so your commit history, branches, and remote settings remain intact.
- **Safe Execution:** Checks for missing arguments, invalid source directories, missing `.git` folders, and existing destination paths before running.

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

This will create `my-project-copy`, containing only tracked Git files and the `.git` folder from `my-project`.

## How It Works

1. Uses `git archive` to pipe tracked files directly into the destination directory without temporary files.
2. Copies the original `.git` directory directly to the destination path.

## License

[MIT](https://www.google.com/search?q=LICENSE)
