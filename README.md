# Kanata Installation and Setup Guide

## 1. Download and Install the Binary

First, download the binaries from the [official repository](https://github.com/jtroo/kanata?tab=readme-ov-file).

Put the binary in `/usr/local/bin/` and make it executable:

```bash
chmod +x /usr/local/bin/kanata
```

## 2. Create Your Configuration File

Create your kanata configuration file in your preferred location.

## 3. Set Up Automatic Startup

Create a systemd service file at `~/.config/systemd/user/kanata.service`:

```ini
[Unit]
Description=Kanata keyboard remapper
Documentation=https://github.com/jtroo/kanata

[Service]
Environment=PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/bin
Environment=DISPLAY=:0
Environment=HOME=/path/to/home/folder
Type=simple
ExecStart=/usr/local/bin/kanata --cfg /path/to/kanata/config/file
Restart=never

[Install]
WantedBy=default.target
```

**Note:** Edit the paths in the service file as needed for your system.

## 4. Enable and Start the Service

Run these commands to manage the kanata service:

```bash
# Start the kanata daemon
systemctl --user start kanata.service

# Enable autostart when the current user logs in
systemctl --user enable kanata.service

# Check if the kanata daemon is running
systemctl --user status kanata.service
```
