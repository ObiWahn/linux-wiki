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

