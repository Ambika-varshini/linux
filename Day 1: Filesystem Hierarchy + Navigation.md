# Linux for DevOps Journey

Learning Linux fundamentals as a foundation for DevOps.
Practicing hands-on using Google Cloud Shell.

## Day 1: Filesystem Hierarchy + Navigation

### Concepts Learned
Linux organizes everything under a single root (`/`). Key directories:

| Folder | Purpose |
|---|---|
| `/etc` | Configuration files (nginx, ssh, cron, etc.) |
| `/var` | Variable data — logs live in `/var/log` |
| `/home` | User home directories |
| `/usr` | Installed programs and their files |
| `/bin`, `/usr/bin` | Executable commands |
| `/tmp` | Temporary files, cleared on reboot |

### Commands Practiced
- `pwd` — print current working directory
- `ls`, `ls -la` — list files (with `-la` showing hidden files + details)
- `cd <path>` — change directory
- `cd` (no argument) — go to home directory
- `cd ..` — go up one directory level
- `tree` — visualize folder structure (installed via `sudo apt install tree -y`)

### Decoding `ls -la` output
Example line:
| Part | Example | Meaning |
|---|---|---|
| File type | `d` | `d` = directory, `-` = file, `l` = symlink |
| Permissions | `rwxr-x---` | Owner / Group / Others access |
| Links | `7` | Number of hard links |
| Owner | `ambicavarshini` | File owner |
| Group | `ambicavarshini` | Group owner |
| Size | `4096` | Size in bytes |
| Modified date | `Jul 26 14:31` | Last modified timestamp |
| Name | `.` | File/folder name |

**Permission breakdown** (`rwxr-x---`):
- `rwx` → Owner: read, write, execute
- `r-x` → Group: read, execute (no write)
- `---` → Others: no access

### Key Takeaway
`/etc` = configuration files, `/var/log` = system logs. These two directories will be visited constantly in real DevOps work — troubleshooting configs and reading logs is a daily task.
