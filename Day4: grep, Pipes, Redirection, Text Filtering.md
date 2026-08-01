## Day 4: grep, Pipes, Redirection, Text Filtering

### Commands Practiced
- `grep "pattern" file` — search for lines matching a pattern
- `grep -i "pattern" file` — case-insensitive search
- `grep -c "pattern" file` — count matching lines
- `grep -n "pattern" file` — show matching lines with line numbers
- `grep -i "error\|warning" file` — match multiple patterns (OR condition)
- `|` (pipe) — send output of one command as input to the next
- `wc -l` — count lines (often chained after grep to count matches)
- `sort file` — alphabetize lines
- `uniq` — remove consecutive duplicate lines (works best after `sort`)
- `>` / `>>` — redirect filtered output into a new file

### Key Takeaways
- Piping (`|`) is the core Linux philosophy: small, simple commands chained together to do powerful things. `cat file | grep "X" | wc -l` = read file → filter lines → count them.
- Don't need `cat` before `grep` — `grep "pattern" file` works directly. Using `cat` first is a common but unnecessary habit ("useless use of cat").
- Redirecting `grep` output (`grep "ERROR" file > errors.log`) is exactly how real incident triage works — pulling just the relevant lines out of a huge log file.
