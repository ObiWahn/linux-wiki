# systemd

## Links

- [issues](https://github.com/systemd/systemd/issues)

## Commands

- `loginctl enable-linger <user>` enable lingering
- `systemd-analyze verify <service>` find problem with unit
- `systemctl --user daemon-reload` re-read units
- `systemctl --user import-environment` import env
- `systemctl --user (start|stop|status) <service>` start / stop / status
- `journalcrl --user -xy <service>` show log of service

## units

### user locations

 - `/usr/lib/systemd/user/` where units provided by installed packages belong.
 - `~/.local/share/systemd/user/` where units of packages that have been installed in the home directory belong.
 - `/etc/systemd/user/` where system-wide user units are placed by the system administrator.
 - `~/.config/systemd/user/` where the user puts their own units.

