## Day 5: man pages, --help, history, aliases

### Commands Practiced
- `man <command>` — full manual for a command (press `/` to search inside, `n` for next match, `q` to quit)
- `<command> --help` — quick reference, faster than `man`
- `history` — view all commands run this session
- `history | grep <command>` — search command history
- `!<number>` — re-run a specific command from history by its number
- `alias name='command'` — create a shortcut (e.g. `alias ll='ls -la'`)
- Making aliases permanent: `echo "alias ll='ls -la'" >> ~/.bashrc` then `source ~/.bashrc`
- `which <command>` / `whereis <command>` — find where a command's executable lives

### Key Takeaways
- Cloud Shell strips out man pages by default (minimized image) — run `sudo unminimize` to restore them.
- **Important lesson**: Cloud Shell only persists the `/home` folder between sessions. Anything installed at the system level (like `unminimize`, `apt install` packages) gets wiped when the session resets/idles out. This mirrors a real DevOps concept — cloud environments are often **ephemeral**, which is exactly why automation tools (Ansible, Docker, startup scripts) exist: to make environment setup repeatable instead of manual.
- `source ~/.bashrc` reloads config changes immediately without needing to restart the terminal.
- `history` becomes a personal, self-built command reference over time — often more useful than external cheat sheets.
