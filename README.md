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
| r | Random challenge from any category |
| ? | Quick reference guide |

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
