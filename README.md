# tui-battery-health

A small terminal UI and CLI for managing the Acer WMI battery charge limit on Linux.

When enabled, charging is limited to 80% to help reduce battery wear. The tool also shows current charge, charging status, and battery temperature when those values are available.

## Requirements

- An Acer laptop supported by the Linux `acer-wmi-battery` driver
- `pkexec`, `modprobe`, `tee`, and `awk`
- `gum` for the interactive menu
- Permission to authenticate through PolicyKit when changing the setting

The control is hardware- and kernel-dependent. This tool does not modify firmware or guarantee that every Acer model supports the limit.

## Install

```sh
install -Dm755 battery-health "$HOME/.local/bin/battery-health"
```

Ensure `~/.local/bin` is on your `PATH`, then run:

```sh
battery-health
```

## Usage

```text
battery-health              Open the interactive TUI
battery-health --status     Show current status
battery-health --enable     Enable the 80% charge limit
battery-health --disable    Disable the limit
battery-health --toggle     Toggle the limit
battery-health --help       Show help
```

The script targets `/sys/class/power_supply/BAT1` and the Acer WMI battery driver's `health_mode` control. If your system exposes a different battery path, update the constants near the top of the script.

## License

MIT. See [LICENSE](LICENSE).
