## Day 9: Users & Groups 

### Commands Practiced
- `whoami` — shows current logged-in user
- `id` — shows UID (user ID), GID (primary group ID), and all groups the user belongs to
- `sudo useradd <name>` — create a new user (requires sudo — affects the whole system)
- `sudo passwd <name>` — set a password for a user
- `sudo usermod -aG <group> <user>` — add an existing user to a group (`-aG` = append to group, without removing existing group memberships)
- `groups <user>` — list all groups a specific user belongs to
- `sudo groupadd <name>` — create a new group
- `sudo deluser <name>` — remove a user from the system
- `cat /etc/group` — view all groups that exist on the system

### Key Takeaways
- `id` output format: `uid=1000(ambicavarshini) gid=1000(ambicavarshini) groups=1000(ambicavarshini),4(adm),27(sudo),996(docker)` — this means my user ID is 1000, my primary group is my own username-named group, and I additionally belong to `adm`, `sudo`, and `docker` groups (each giving different system privileges).
- `usermod -aG group user` **must include `-a` (append)** — leaving it out replaces all of a user's existing group memberships with just the one specified, which can accidentally strip access.
- Being in the `docker` group is why some users can run `docker` commands without typing `sudo` every time — group membership grants access to specific system resources.
- New group memberships (`usermod -aG`) typically require a fresh login session to fully take effect.
- A group must exist (`groupadd`) before you can add anyone to it — confirmed by hitting `usermod: group 'group' does not exist` when testing an invalid group name.
