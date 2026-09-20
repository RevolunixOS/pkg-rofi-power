# rofi-power

Rofi power menu for locking the session, logging out, suspending, hibernating,
rebooting, or powering off. Destructive actions pass through a confirmation
menu.

## Build and install

```bash
nix build github:RevolunixOS/pkg-rofi-power
nix profile install github:RevolunixOS/pkg-rofi-power
```

Launch it with:

```bash
rofi-power
```

## Requirements

The wrapper provides Rofi and Hyprlock. The current script also expects an
adi1090x-style Rofi theme selector at:

```text
~/.config/rofi/applets/shared/theme.bash
```

Suspend attempts to pause MPD through `mpc`, mute audio through `amixer`, and
run `sudo systemctl suspend`. Those commands and any required privilege rules
must be configured on the host.

## Safety notes

- Logout executes `kill -9 -1`, terminating processes visible to the user.
- Suspend, hibernate, reboot, and poweroff alter system state immediately after
  confirmation.
- The script assumes systemd and a graphical session.
- The menu is adapted from an adi1090x Rofi applet; keep the attribution in the
  source.

Test the lock and confirmation flow before binding the command to a key.

## License

See [`LICENSE`](LICENSE).
