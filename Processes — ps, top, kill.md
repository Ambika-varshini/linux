## Day 10: Processes — ps, top, kill

### Commands Practiced
- `ps aux` — list all running processes with details (USER, PID, %CPU, %MEM, STAT, COMMAND)
- `sleep <seconds> &` — start a long-running dummy process in the background (`&` = don't block the terminal)
- `ps aux | grep <name>` — filter process list to find a specific process and its PID
- `jobs` — list background jobs tied to the current terminal session
- `fg` — bring a background job to the foreground
- `Ctrl+Z` — pause (not kill) a foreground process
- `bg` — resume a paused job in the background
- `kill <PID>` — terminate a specific process by its PID
- `top` — live, auto-refreshing view of all processes and system resource usage (`q` to quit)

### Key Takeaways
- **PID (Process ID)** is a unique number assigned by the kernel to every running process, in sequential order as things start. Since process names aren't unique, PID is the only reliable way to target one specific process with `kill`.
- Processes that finish naturally (like `sleep 200` completing after 200 seconds) simply disappear from `ps aux` output — unlike files, there's nothing left over to clean up manually.
- `%CPU` = how much processing power a process is using right now. `%MEM` = how much RAM it's holding. Both near `0.0` for idle processes like `sleep`; real background services (e.g. `dockerd`) show non-zero usage even when idle.
- In `top`, press `Shift+P` to sort by CPU usage or `Shift+M` to sort by memory usage — the standard first step when diagnosing "why is this server slow."
- `USER` column in `ps aux`/`top` directly ties back to Day 9 — every process is owned by whichever user/account started it (or `root` for system-level processes).
