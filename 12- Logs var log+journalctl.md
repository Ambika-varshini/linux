## Day 12: Logs — /var/log + journalctl (conceptual)

### Commands Practiced
- `ls -la /var/log` — list all system log files
- `sudo tail -N /var/log/syslog` — view recent general system activity
- `sudo tail -f /var/log/syslog` — live-follow logs as new events happen
- `sudo grep "pattern" /var/log/<file>` — search a specific log for relevant lines
- `sudo grep "pattern" /var/log/<file> | wc -l` — count how many times something occurred

### journalctl (conceptual — needs systemd, unavailable in Cloud Shell)
- `sudo journalctl -u <service>` — logs for one specific service
- `sudo journalctl -f` — live-follow all system logs
- `sudo journalctl --since "1 hour ago"` — time-filtered logs
- `sudo journalctl -p err` — only error-priority logs
- Difference from /var/log: journalctl is a structured, centralized, queryable log database covering all services + kernel + boot events, instead of separate plain-text files per topic.

### Key Takeaways
- Log files often have restricted permissions (e.g. `auth.log` is `640`, root/adm-group only) — ties back directly to Day 8, confirming why `sudo` is needed to read many logs.
- `/var/log/auth.log` records every `sudo` usage and user/group change on the system — proved this by seeing Cloud Shell's own account provisioning (`useradd`, group additions) logged automatically at container startup, the exact same actions practiced manually on Day 9.
- Combining `grep` (Day 4) with real log files is one of the most common actual troubleshooting patterns in DevOps — searching massive logs for one specific event or error.
- Log rotation (logrotate) automatically compresses (`.gz`) and archives old logs, starting a fresh file, to prevent logs from consuming all disk space over time (directly connects to Day 6's `df -h` showing 91% disk usage — unmanaged logs are a common real cause of that).
- Absence of an expected log entry (e.g., no `docker` lines in a given time window) is itself diagnostic information during real troubleshooting.
