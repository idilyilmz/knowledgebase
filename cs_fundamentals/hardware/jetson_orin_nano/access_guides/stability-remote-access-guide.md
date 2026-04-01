# NVIDIA Jetson Orin Nano
Stability & Remote Access Guide
Thermal Management  |  SSH & Tailscale  |  Resource Control  |  Remote Monitoring

## Overview
This guide covers how to keep your NVIDIA Jetson Orin Nano running stably while being accessed remotely via SSH and Tailscale. It addresses thermal management, service reliability, resource optimization, and remote monitoring best practices.

**NOTE**	If your Jetson becomes unresponsive or laggy, a hard reboot is safe. Hold the power button for 10 seconds, wait 5 minutes for cooling, then power back on.

## 1. Thermal Management
The Jetson Orin Nano can overheat under heavy workloads, especially when running in maximum performance mode without adequate cooling. Temperatures above 85°C cause aggressive throttling; above 95°C the board may perform an emergency shutdown.

### 1.1 Set a Sensible Power Mode
MAXN (full power) generates the most heat and is unnecessary for most remote workloads. Use power mode 1 (10W) for a good balance of performance and thermals.

```
# List available power modes
sudo nvpmodel -q --verbose

# Set to 10W mode (recommended for remote work)
sudo nvpmodel -m 1

# Check current power mode
sudo nvpmodel -q
```

### 1.2 Fan Control
Ensure the fan is running at an appropriate speed, especially during heavy workloads.

```
# Check current fan speed (0-255)
sudo cat /sys/devices/pwm-fan/target_pwm

# Force fan to maximum speed
sudo sh -c 'echo 255 > /sys/devices/pwm-fan/target_pwm'
```

### 1.3 Install jtop (Recommended)
jtop is the best real-time monitoring tool for Jetson boards. It shows CPU, GPU, RAM, temperatures, and fan speed in a single dashboard.

```
# Install jetson-stats
sudo pip3 install jetson-stats

# Launch the monitor
sudo jtop
```

### 1.4 Check Temperatures
Use this command to quickly read all thermal zone temperatures. Values are in millidegrees Celsius (divide by 1000 for Celsius).

```
sudo cat /sys/devices/virtual/thermal/thermal_zone*/temp
```

### 1.5 Physical Checks
If overheating persists, verify the following physically:
•	Heatsink is firmly attached and not hot to the touch when idle
•	Fan is spinning (listen or feel for airflow)
•	Device is not enclosed in a case with poor airflow
•	Power supply provides adequate wattage (underpowering causes instability)

## 2. Keep SSH & Tailscale Reliable
SSH and Tailscale must be configured to start automatically on boot and restart if they crash. Without this, a service crash or reboot will leave you locked out remotely.

### 2.1 Enable Services on Boot

```
# Enable SSH and Tailscale to start at boot
sudo systemctl enable ssh
sudo systemctl enable tailscaled

# Verify they are running
sudo systemctl status ssh
sudo systemctl status tailscaled
```

### 2.2 Configure Auto-Restart on Crash
Edit the Tailscale service to automatically restart if it crashes:

```
sudo systemctl edit tailscaled
```

Add the following in the editor and save:

[Service]
Restart=always
RestartSec=5

### 2.3 Manually Restart Services if Needed

```
# Restart Tailscale
sudo systemctl restart tailscaled && sudo tailscale up

# Restart SSH
sudo systemctl restart ssh
```

## 3. Prevent Resource Exhaustion
Background processes and the desktop GUI consume significant CPU and RAM. Reducing their footprint keeps the system stable for remote work.

### 3.1 Disable the Desktop GUI (Headless Mode)
If you are working remotely over SSH and do not need the graphical desktop, disabling it frees up roughly 1 GB of RAM and significant CPU.

```
# Switch to headless (text-only) mode
sudo systemctl set-default multi-user.target
sudo reboot

# To restore the GUI when needed
sudo systemctl set-default graphical.target
sudo reboot
```

### 3.2 Monitor Resource Usage

```
# View top CPU/RAM consumers
top

# Or use htop for a friendlier view
htop
```

### 3.3 Clean Up System Logs
Prevent logs from filling up your storage over time:

```
sudo journalctl --vacuum-size=500M
```

## 4. Control Software Updates
Automatic background updates can disrupt an active SSH session by restarting services or triggering a reboot without warning. Disable them and update manually instead.

### 4.1 Disable Unattended Upgrades

```
sudo systemctl disable unattended-upgrades
sudo apt remove unattended-upgrades -y
```

### 4.2 Update Manually (When Safe)
Run updates yourself at a time when you do not mind a potential reboot:

```
sudo apt update && sudo apt upgrade -y
```

## 5. Remote Health Monitoring
Set up a quick health check alias so you can instantly see the status of your Jetson when connected over SSH.
5.1 Create a Health Alias
Add the following to ~/.bashrc on the Jetson:

# Add to ~/.bashrc
alias health='echo "=== Temperatures ===";
  cat /sys/devices/virtual/thermal/thermal_zone*/temp;
  echo "=== Fan Speed ===";
  cat /sys/devices/pwm-fan/target_pwm;
  echo "=== System Uptime ===";
  uptime;
  echo "=== Memory Usage ===";
  free -h'

Then reload and use it:

source ~/.bashrc
health

5.2 Check Tailscale Connection Status

# Show Tailscale status and assigned IP
tailscale status

# Show your Tailscale IP
tailscale ip

Quick Reference Summary

Goal	Command / Action
Set 10W power mode	sudo nvpmodel -m 1
Max fan speed	sudo sh -c 'echo 255 > /sys/devices/pwm-fan/target_pwm'
Install monitoring tool	sudo pip3 install jetson-stats && sudo jtop
Enable SSH on boot	sudo systemctl enable ssh
Enable Tailscale on boot	sudo systemctl enable tailscaled
Restart Tailscale	sudo systemctl restart tailscaled && sudo tailscale up
Go headless (save RAM)	sudo systemctl set-default multi-user.target
Disable auto-updates	sudo systemctl disable unattended-upgrades
Check system health	health  (after adding alias to ~/.bashrc)
Clean logs	sudo journalctl --vacuum-size=500M


Generated from troubleshooting session — March 2026