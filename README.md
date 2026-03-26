# Linux Dojo

An interactive, gamified terminal tool for practicing Linux command-line skills. Work through challenges in an isolated sandbox, get instant feedback, and level up your shell knowledge.

## Usage

```bash
bash linux-dojo
```

## How It Works

1. Pick a lesson from the menu
2. Read the challenge description
3. Press **Enter** to open an interactive shell in a sandboxed arena
4. Complete the task, then type `exit`
5. The script automatically checks your work and awards points

During a challenge:
- **`h`** — show a hint (earns half points)
- **`s`** — skip the challenge (resets streak)

## Lessons

| # | Topic |
|---|-------|
| 1 | Navigation & Exploration — `ls`, `find`, `pwd`, `cd` |
| 2 | File Operations — `cp`, `mv`, `rm`, `mkdir`, `touch` |
| 3 | Text Processing — `grep`, `sort`, `uniq`, `wc`, `cut` |
| 4 | Streams & Redirection — `>`, `>>`, `\|`, `2>`, `tee`, `xargs` |
| 5 | Permissions — `chmod`, `ls -l`, `find -perm` |
| 6 | Archives & Compression — `tar`, `gzip`, `zip` |
| 7 | find & xargs — advanced searching, `-exec`, pipelines |
| 8 | sed & awk — stream editing, substitution, column extraction |
| 9 | Bash Scripting — variables, loops, conditionals, functions |
| 10 | Process & System — `ps`, `kill`, `date`, `du`, `df`, `id`, `env` |
| 11 | File Comparison — `diff`, `patch`, `comm` |
| 12 | File Integrity — `sha256sum`, `shasum`, `md5sum`, `file` |
| 13 | Pipelines — `tr`, `sort -k`, `uniq -d`, word frequency |
| r | Random challenge from any category |
| ? | Quick reference guide |
| g | Command glossary — detailed manual for every command |

## The `find` Command

`find` searches the filesystem for files matching criteria you specify. Unlike `ls`, it recurses into directories and can act on results.

```bash
find [path] [options] [expression]
```

### Filtering by name

```bash
find . -name "*.log"          # match by filename (case-sensitive)
find . -iname "*.log"         # case-insensitive match
find . -name "report" -type f # exact name, files only
```

### Filtering by type

```bash
find . -type f   # files
find . -type d   # directories
find . -type l   # symbolic links
```

### Filtering by size

```bash
find . -size +1M    # larger than 1 MB
find . -size -100k  # smaller than 100 KB
find . -size 0      # exactly empty
```

### Filtering by time

```bash
find . -mtime -7    # modified in the last 7 days
find . -mtime +30   # modified more than 30 days ago
find . -newer ref   # modified more recently than file "ref"
```

### Filtering by permissions

```bash
find . -perm 644          # exact permission match
find . -perm -u+x         # user-executable (at minimum)
find . -perm /o+w         # world-writable (any match)
```

### Executing commands on results

```bash
find . -name "*.tmp" -delete              # delete matches
find . -type f -exec chmod 644 {} \;     # run a command per file
find . -type f | xargs grep "TODO"       # pipe to xargs for bulk ops
```

### Combining expressions

```bash
find . -type f -name "*.sh" -size +1k    # AND (implicit)
find . -name "*.jpg" -o -name "*.png"    # OR
find . -not -name "*.git"                # NOT
find . \( -name "a" -o -name "b" \) -type f  # grouping
```

### Limiting depth

```bash
find . -maxdepth 1        # current directory only (no recursion)
find . -mindepth 2        # skip top-level entries
```

## File Integrity & Checksums

Checksums let you verify a file hasn't been corrupted or tampered with. A hash is a fixed-length fingerprint of a file's contents — any change produces a completely different hash.

### Generating checksums

```bash
sha256sum file.tar.gz              # compute SHA-256 (Linux)
shasum -a 256 file.tar.gz          # macOS equivalent
shasum -a 512 file.tar.gz          # SHA-512 (stronger)
md5sum file.tar.gz                 # MD5 (fast, but avoid for security)
sha256sum *.txt > checksums.sha256 # checksum multiple files at once
```

### Verifying checksums

```bash
sha256sum -c file.sha256           # verify — exits 0 if OK, 1 if mismatch
shasum -a 256 -c file.sha256       # macOS equivalent
```

The checksum file format is simply `<hash>  <filename>` — one entry per line.

### Identifying file types

```bash
file photo.jpg      # identify by content, not extension
file *              # identify everything in the current directory
```

`file` reads magic bytes at the start of the file, so it correctly identifies files whose extension has been changed or is missing.

### Digital signatures (GPG)

```bash
gpg --verify file.sig file         # verify a detached GPG signature
gpg --fingerprint keyid            # inspect a key's fingerprint
gpg --import pubkey.asc            # import a public key for verification
```

GPG signatures go further than checksums — they prove not just that a file is intact, but that it was signed by a specific private key.

| Tool | Purpose | Trust level |
|------|---------|-------------|
| `md5sum` | fast integrity check | low (broken for security) |
| `sha256sum` | standard integrity check | good |
| `sha512sum` | stronger hash | better |
| GPG signature | authenticity + integrity | strongest |

## Scoring

- **+10–25 points** per correct answer
- **Half points** if a hint was used
- **Streak** — consecutive correct answers (resets on skip or wrong)
- **Level up** every 100 points

## Requirements

- Bash
- Standard Unix utilities (`find`, `grep`, `awk`, `sed`, `tar`, `gzip`, `zip`, etc.)
- A terminal with ANSI color support

No installation, no network access, no packages — just run the script.
