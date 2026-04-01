# NVIDIA Jetson Orin Nano
## Stability & Remote Access Guide
**Thermal Management | SSH & Tailscale | Resource Control | Remote Monitoring**

---

> **Emergency tip:** If your Jetson becomes unresponsive or laggy, a hard reboot is safe. Hold the power button for 10 seconds, wait 5 minutes for cooling, then power back on.

---

## 1. Thermal Management

The Jetson Orin Nano can overheat under heavy workloads, especially when running in maximum performance mode without adequate cooling. Temperatures above **85°C** cause aggressive throttling; above **95°C** the board may perform an emergency shutdown.

### 1.1 Set a Sensible Power Mode

Use **7W mode** for headless/remote work — it's plenty for SSH sessions and light workloads, and runs much cooler. Only use higher modes if your project actively needs the extra performance.

```bash
# List available power modes
sudo nvpmodel -q --verbose

# Set to 7W mode (recommended for remote/headless work)
sudo nvpmodel -m 2

# Set to 15W mode (if you need more performance)
sudo nvpmodel -m 0

# Check current power mode
sudo nvpmodel -q
```

> **Note:** Changing power mode requires a reboot to take effect. jtop will prompt you with **[Force and reboot]** when you change it via the UI.

### 1.2 Fan Control with jtop

The easiest way to control the fan is directly inside jtop. Press **`6`** to open the Controls tab, where you can select a fan profile:

| Profile | Description | When to use |
|---------|-------------|-------------|
| **quiet** | Fan runs slow, prioritizes silence | Short idle periods |
| **cool** ✅ | Fan ramps up proactively | Recommended for always-on remote work |
| **manual** | You set the fan % yourself | Advanced use |

**Recommended: set your fan profile to `cool`** for continuous remote work.

You can also control the fan manually via command line. First, find the fan control file:

```bash
# Find the fan PWM file (path may vary by kernel version)
sudo find /sys -name "target_pwm" 2>/dev/null

# Or search broadly
sudo find /sys -name "*pwm*" 2>/dev/null
sudo find /sys -name "*fan*" 2>/dev/null
```

Once found:
```bash
# Check current fan speed (0–255)
sudo cat /sys/devices/pwm-fan/target_pwm

# Force fan to maximum speed
sudo sh -c 'echo 255 > /sys/devices/pwm-fan/target_pwm'
```

### 1.3 Install jtop (Recommended)

jtop is the best real-time monitoring tool for Jetson boards. It shows CPU, GPU, RAM, temperatures, fan speed and power in a single dashboard.

```bash
# Install jetson-stats
sudo pip3 install jetson-stats

# Launch the monitor
sudo jtop
```

**jtop keyboard shortcuts:**

| Key | Tab |
|-----|-----|
| `1` | All stats overview |
| `2` | GPU |
| `3` | CPU |
| `4` | Memory |
| `5` | Engine |
| `6` | Controls (fan + power mode) |
| `7` | Info |

### 1.4 Check Temperatures

Values are in millidegrees Celsius — divide by 1000 to get °C (e.g. 44720 = 44.72°C).

```bash
sudo cat /sys/devices/virtual/thermal/thermal_zone*/temp
```

**Safe temperature ranges:**
- ✅ Below 75°C — normal
- ⚠️ 75–85°C — warm, monitor closely
- 🔴 Above 85°C — throttling occurs
- 🚨 Above 95°C — emergency shutdown risk

### 1.5 Physical Checks

If overheating persists, verify the following physically:

- Heatsink is firmly attached and not extremely hot to the touch when idle
- Fan is spinning (listen or feel for airflow)
- Device is not enclosed in a case with poor airflow
- Power supply provides adequate wattage (underpowering causes instability and freezes)

### 1.6 Reading jtop — What to Look For

Based on a healthy system reading, here's what the numbers mean:

| Metric | Healthy range | Warning |
|--------|--------------|---------|
| CPU per core | < 50% at idle | Sustained 90–100% |
| RAM | < 5G / 7.4G | Above 6.5G |
| Temperatures | 40–60°C | Above 80°C |
| Power (VDD_IN) | < 5W headless | Approaching 15W+ |
| Fan RPM | 800–1500 RPM (cool profile) | 0 RPM = fan not spinning |
| Disk | < 80G / 115G | Above 90G |

> **Watch your disk!** If it fills up completely the system will become unstable. See Section 3.3 for cleanup commands.

---

## 2. Keep SSH & Tailscale Reliable

SSH and Tailscale must be configured to start automatically on boot and restart if they crash. Without this, a service crash or reboot will leave you locked out remotely.

### 2.1 Enable Services on Boot

```bash
# Enable SSH and Tailscale to start at boot
sudo systemctl enable ssh
sudo systemctl enable tailscaled

# Verify they are running
sudo systemctl status ssh
sudo systemctl status tailscaled
```

### 2.2 Configure Auto-Restart on Crash

Edit the Tailscale service to automatically restart if it crashes:

```bash
sudo systemctl edit tailscaled
```

Add the following between the comment lines and save:

```ini
[Service]
Restart=always
RestartSec=5
```

Save with `Ctrl+X` → `Y` → `Enter`, then apply:

```bash
sudo systemctl daemon-reload
```

### 2.3 Manually Restart Services if Needed

```bash
# Restart Tailscale
sudo systemctl restart tailscaled && sudo tailscale up

# Restart SSH
sudo systemctl restart ssh
```

### 2.4 Check Tailscale Connection Status

```bash
# Show Tailscale status and assigned IP
tailscale status

# Show your Tailscale IP
tailscale ip
```

---

## 3. Prevent Resource Exhaustion

### 3.1 Disable the Desktop GUI (Headless Mode)

**If you normally run without a display connected, do this.** The GUI runs in the background wasting ~200MB of RAM and CPU even when no monitor is plugged in:

- `gnome-shell` — ~127MB RAM
- `Xorg` — ~62MB RAM
- `xdg-desktop-portal` — ~17MB RAM

```bash
# Switch to headless (text-only) mode — do this if you work remotely
sudo systemctl set-default multi-user.target
sudo reboot

# To restore the GUI when you need a display temporarily
sudo systemctl set-default graphical.target
sudo reboot
```

### 3.2 Monitor Resource Usage

```bash
# View top CPU/RAM consumers
top

# Or use htop for a friendlier view
htop
```

### 3.3 Clean Up Disk Space

Your Jetson has 115G total. Keep disk usage below 80% to avoid instability.

```bash
# Check what's eating your disk
du -h --max-depth=1 / 2>/dev/null | sort -rh | head -15

# Clean apt cache and unused packages
sudo apt autoremove -y && sudo apt clean

# Trim system logs to 500MB
sudo journalctl --vacuum-size=500M
```

---

## 4. Control Software Updates

Automatic background updates can disrupt an active SSH session by restarting services or triggering a reboot without warning. Update manually instead, at a time you choose.

### 4.1 Disable Unattended Upgrades (if installed)

```bash
# Check if it's installed first
dpkg -l | grep unattended

# If installed, disable and remove it
sudo systemctl disable unattended-upgrades
sudo apt remove unattended-upgrades -y
```

> **Note:** If you get `Unit file unattended-upgrades.service does not exist`, it was never installed — you're already safe, nothing to do.

### 4.2 Verify Auto-Updates are Off

```bash
cat /etc/apt/apt.conf.d/20auto-upgrades 2>/dev/null
```

If this outputs `APT::Periodic::Update-Package-Lists "1"`, disable it:

```bash
sudo sed -i 's/1/0/g' /etc/apt/apt.conf.d/20auto-upgrades
```

If there is no output, auto-updates are already fully disabled. ✅

### 4.3 Update Manually (When Safe)

Run updates yourself at a time when you don't mind a potential reboot:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 5. Remote Health Monitoring

### 5.1 Create a Health Alias

Add this to `~/.bashrc` on the Jetson for a one-command vitals check:

```bash
nano ~/.bashrc
```

Paste at the bottom:

```bash
alias health='echo "=== Temperatures ==="; cat /sys/devices/virtual/thermal/thermal_zone*/temp; echo "=== Fan Speed ==="; cat /sys/devices/pwm-fan/target_pwm 2>/dev/null; echo "=== Memory ==="; free -h; echo "=== Uptime ==="; uptime'
```

Save (`Ctrl+X` → `Y` → `Enter`), then reload:

```bash
source ~/.bashrc

# Run it anytime after SSH-ing in
health
```

---

## Quick Reference Summary

| Goal | Command / Action |
|------|-----------------|
| Set 7W power mode (headless) | `sudo nvpmodel -m 2` |
| Set 15W power mode | `sudo nvpmodel -m 0` |
| Check current power mode | `sudo nvpmodel -q` |
| Install monitoring tool | `sudo pip3 install jetson-stats && sudo jtop` |
| Set fan to cool profile | Press `6` in jtop, select `[cool]` |
| Find fan PWM file | `sudo find /sys -name "target_pwm" 2>/dev/null` |
| Max fan speed (manual) | `sudo sh -c 'echo 255 > /sys/devices/pwm-fan/target_pwm'` |
| Enable SSH on boot | `sudo systemctl enable ssh` |
| Enable Tailscale on boot | `sudo systemctl enable tailscaled` |
| Restart Tailscale | `sudo systemctl restart tailscaled && sudo tailscale up` |
| Go headless (save RAM) | `sudo systemctl set-default multi-user.target && sudo reboot` |
| Restore GUI | `sudo systemctl set-default graphical.target && sudo reboot` |
| Check disk usage | `du -h --max-depth=1 / 2>/dev/null \| sort -rh \| head -15` |
| Clean disk | `sudo apt autoremove -y && sudo apt clean` |
| Trim logs | `sudo journalctl --vacuum-size=500M` |
| Manual update | `sudo apt update && sudo apt upgrade -y` |
| Check system health | `health` (after adding alias to ~/.bashrc) |
| Check Tailscale IP | `tailscale ip` |

---

*Generated from troubleshooting session — April 2026*
https://claude.ai/share/216e7b34-0488-4788-b586-17149c270028