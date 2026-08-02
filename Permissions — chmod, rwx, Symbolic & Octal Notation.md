## Day 8: Permissions — chmod, rwx, Symbolic & Octal Notation

### Core Concept
Every file/folder has permissions defined for 3 categories of people:
- **Owner (u)** — the person who created it
- **Group (g)** — a defined group of users
- **Others (o)** — everyone else

Each category can have 3 possible permissions:
- `r` (read) — view file contents / list folder contents
- `w` (write) — edit file contents / add-delete files in a folder
- `x` (execute) — run as a program / **enter** a folder (`cd` into it)

### Permission String Breakdown
Example: `rw-r--r--` reads as three groups of three:
rw- r-- r--  
owner group others

### Octal (Number) Notation
Each permission has a value: `r=4`, `w=2`, `x=1`. Add them per group.
- `rwx` = 4+2+1 = **7**
- `rw-` = 4+2 = **6**
- `r--` = 4
- `r-x` = 4+1 = 5

So `rw-r--r--` = `644`, and `rwxr--r--` = `744`.

### Commands Practiced
- `chmod <octal> <file>` — e.g. `chmod 644 file`, `chmod 600 file`
- `chmod u+x file` / `chmod g-w file` / `chmod o+r file` — symbolic mode (add/remove one permission at a time for owner/group/others)
- `./scriptname.sh` — run a script (requires execute permission)
- `chmod 000/100 folder` — used to test folder-specific behavior

### Key Takeaways
- **On files**: `x` means "can this be run as a program." A `.sh` file with no `x` permission gives `Permission denied` when run with `./file.sh`.
- **On folders**: permissions mean something different —
  - `r` = can **list** contents (`ls`)
  - `x` = can **enter** the folder (`cd`) and access files inside directly
  - These are **independent**: you can have `x` without `r` (can enter/access known files, but can't browse/list what's there), or `r` without `x` (can see filenames, but can't enter or open anything).
- SSH private keys must be `chmod 600` (owner read/write only) — SSH refuses to use a key file that's readable by others, since that defeats the purpose of it being private.
- Symbolic mode (`u+x`, `g-w`) and octal mode (`744`) express the exact same result — pick whichever is faster for the specific change you're making.
