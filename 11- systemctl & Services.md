## Day 11: systemctl & Services (Conceptual — Cloud Shell doesn't support systemd)

### Why Hands-On Wasn't Possible Today
Cloud Shell runs in a **container**, not a full VM. Containers skip the normal Linux boot process — PID 1 is directly `bash` instead of `systemd` (confirmed via Day 10's `ps aux` output). Since `systemctl` depends on systemd being PID 1, it fails with: `System has not been booted with systemd as init system (PID 1). Can't operate.`
Key lesson: containers and full VMs behave differently at the OS level — this is part of why Docker containers typically run a single process instead of a full service-managed system.

### Commands (to run on a real server/VM later)
- `sudo systemctl status <service>` — check if a service is active, its main PID, memory usage, recent logs
- `sudo systemctl stop <service>` — stop a service
- `sudo systemctl start <service>` — start a service
- `sudo systemctl restart <service>` — stop + start together (common after config changes)
- `sudo systemctl enable <service>` — auto-start the service on boot
- `sudo systemctl disable <service>` — prevent auto-start on boot
- `systemctl list-units --type=service --state=running` — list all currently running services

### Key Takeaways
- A "service" isn't magic — it's an ordinary process (visible in `ps aux`) that systemd manages through a standardized start/stop/restart interface.
- `systemctl stop` vs `kill <PID>`: `systemctl` knows the process without manual lookup, performs a clean/graceful shutdown, remembers boot behavior (`enable`/`disable`), and can be configured to auto-restart a crashed service. `kill` is a blunt, manual, one-time action with no memory of state.
- `enable`/`disable` only controls **boot behavior** — it doesn't start or stop the service right now, only whether it happens automatically on the next reboot.
