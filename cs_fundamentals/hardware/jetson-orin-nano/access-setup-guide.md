# Jetson Nano Remote Access Setup Guide

Complete guide for setting up remote access to your Jetson Nano Orin from anywhere in the world.

**Disclaimer**

This file was made by Claude AI by my instructions


---

## Table of Contents
1. [Setting Static IP on Jetson](#1-setting-static-ip-on-jetson)
2. [Setting Up Remote Access with Tailscale](#2-setting-up-remote-access-with-tailscale)
3. [Connecting via SSH](#3-connecting-via-ssh)
4. [Setting Up SSH Keys (No Password)](#4-setting-up-ssh-keys-no-password)
5. [Using VSCode Remote Development](#5-using-vscode-remote-development)
6. [Working with Your GitLab Project](#6-working-with-your-gitlab-project)
7. [Running GPU Code on Jetson](#7-running-gpu-code-on-jetson)
8. [Troubleshooting](#8-troubleshooting)

---

## 1. Setting Static IP on Jetson

### Why?
A static IP ensures your Jetson always has the same local network address (e.g., `192.168.10.88`).

### Steps:

#### Option A: Using GUI (Settings)
1. Open **Settings** → **Network**
2. Click the **gear icon** ⚙️ next to your wired connection
3. Go to **IPv4** tab
4. Change method to **Manual**
5. Fill in:
   - **Address**: `192.168.10.88` (your chosen static IP)
   - **Netmask**: `255.255.255.0`
   - **Gateway**: `192.168.10.1` (your router IP)
   - **DNS**: `8.8.8.8, 8.8.4.4`
6. Click **Apply**
7. Toggle connection OFF then ON

#### Option B: Using Command Line (nmcli)
```bash
# Find active connection
nmcli connection show --active

# Set static IP (replace "profile 1" with your connection name)
sudo nmcli connection modify "profile 1" ipv4.addresses 192.168.10.88/24
sudo nmcli connection modify "profile 1" ipv4.gateway 192.168.10.1
sudo nmcli connection modify "profile 1" ipv4.dns "8.8.8.8 8.8.4.4"
sudo nmcli connection modify "profile 1" ipv4.method manual

# Restart connection
sudo nmcli connection down "profile 1"
sudo nmcli connection up "profile 1"

# Verify
hostname -I
```

### How to Pick a Safe Static IP:
```bash
# Scan network to see what's in use
nmap -sn 192.168.10.0/24

# If nmap not installed:
sudo apt install nmap
```

**Safe IP choices:**
- Low numbers: `192.168.10.10`, `192.168.10.20`, `192.168.10.50`
- High numbers: `192.168.10.200`, `192.168.10.210`, `192.168.10.250`
- Avoid IPs in your router's DHCP range (usually 100-199)

---

## 2. Setting Up Remote Access with Tailscale

### Why Tailscale Instead of Port Forwarding?
- **No router access needed** - works without router login/password
- **More secure** - encrypted VPN tunnel
- **Works anywhere** - even behind firewalls and NAT
- **Free** for personal use

### Installation:

#### On Jetson:
```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

A URL will appear - open it in a browser to authenticate with Google/GitHub/etc.

#### On Your PC:
1. Download Tailscale from https://tailscale.com
2. Install and sign in with the **same account** you used on Jetson

### Verify Setup:
Both devices should appear in your Tailscale admin console with IP addresses starting with `100.x.x.x`

Example:
- Jetson: `100.111.167.48`
- PC: `100.111.167.x`

---

## 3. Connecting via SSH

### Basic SSH Connection:

From your PC (Command Prompt or PowerShell):
```bash
ssh jetson@100.111.167.48
```

Replace `100.111.167.48` with your Jetson's actual Tailscale IP.

### Important Notes:
- Username is `jetson` (or whatever `whoami` shows on your Jetson)
- Password is your Jetson login password
- Your Jetson must be **powered on and connected to internet** to access remotely
- Tailscale runs automatically after setup

### Disconnect:
```bash
exit
```

---

## 4. Setting Up SSH Keys (No Password)

### Why?
- No more typing passwords
- Works with VSCode Remote-SSH
- Fixes issues with special characters in passwords

### Steps (On Your Windows PC):

#### 1. Generate SSH Key:
```bash
ssh-keygen -t ed25519
```

Press **Enter** 3 times (accept defaults, no passphrase)

#### 2. Copy Key to Jetson:

**Option A - If `ssh-copy-id` works:**
```bash
ssh-copy-id jetson@100.111.167.48
```

**Option B - If `ssh-copy-id` doesn't exist:**
```bash
type %USERPROFILE%\.ssh\id_ed25519.pub | ssh jetson@100.111.167.48 "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

Enter your Jetson password **one last time**.

#### 3. Test:
```bash
ssh jetson@100.111.167.48
```

Should connect **without asking for password**!

---

## 5. Using VSCode Remote Development

### Setup:

#### 1. Install Extension:
- Open VSCode
- Extensions (Ctrl+Shift+X)
- Search "Remote - SSH"
- Install (by Microsoft)

#### 2. Connect to Jetson:
- Press `F1` or `Ctrl+Shift+P`
- Type "Remote-SSH: Connect to Host"
- Click "Add New SSH Host"
- Enter: `ssh jetson@100.111.167.48`
- Choose config file (first option)
- Click "Connect"

#### 3. First Connection:
- Choose **Linux** as the platform
- Wait for VSCode to install server components
- Check bottom-left corner - should say "SSH: jetson"

### Now You Can:
✅ Edit files directly on Jetson  
✅ Use integrated terminal (runs on Jetson)  
✅ Run/debug code on Jetson GPU  
✅ Drag & drop files to upload  
✅ Install extensions on remote Jetson  

---

## 6. Working with Your GitLab Project

### Clone Your Repo on Jetson:

#### Via VSCode Terminal (while connected to Jetson):
```bash
cd ~
git clone https://gitlab.com/your-username/your-repo-name.git
cd your-repo-name
```

#### If Private Repo:

**Option A - HTTPS with Token:**
```bash
git clone https://oauth2:YOUR_TOKEN@gitlab.com/your-username/your-repo.git
```

**Option B - SSH (Recommended):**

1. Generate SSH key on Jetson:
```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
```

2. Copy the output and add to GitLab:
   - GitLab → Settings → SSH Keys → Paste key

3. Clone using SSH:
```bash
git clone git@gitlab.com:your-username/your-repo.git
```

### Open Project in VSCode:
- File → Open Folder
- Navigate to your cloned repo
- Start coding!

### Install Dependencies:
```bash
pip3 install -r requirements.txt
```

Or individually:
```bash
pip3 install transformers torch
```

---

## 7. Running GPU Code on Jetson

### Important: Where You Run Matters!

❌ **Don't run on your Windows PC** - it doesn't have a GPU or CUDA  
✅ **Run on Jetson** - it has the GPU

### Verify You're on Jetson:
```bash
hostname  # Should show "jetson"
nvidia-smi  # Should show GPU info
```

### Check CUDA Availability:
```python
import torch
print(f"CUDA available: {torch.cuda.is_available()}")
print(f"CUDA device: {torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'None'}")
```

### Correct GPU Code:

❌ **Wrong:**
```python
pipe = pipeline("text-generation", model="google/gemma-3-1b-it", device="gpu")
```

✅ **Correct:**
```python
from transformers import pipeline
import torch

# Auto-detect GPU
device = 0 if torch.cuda.is_available() else -1
pipe = pipeline("text-generation", model="google/gemma-3-1b-it", device=device)

# Or explicitly use CUDA
pipe = pipeline("text-generation", model="google/gemma-3-1b-it", device="cuda")
```

### Example Working Code:
```python
from transformers import pipeline
import torch

# Check GPU
print(f"CUDA available: {torch.cuda.is_available()}")

# Create pipeline with GPU
device = 0 if torch.cuda.is_available() else -1
pipe = pipeline("text-generation", model="google/gemma-3-1b-it", device=device)

# Generate text
prompt = "Hello, my name is Idil and I think I figured out how to prompt!"
output = pipe(prompt, max_new_tokens=50)
print(output[0]["generated_text"])
```

### Run Your Code:
```bash
python3 your_script.py
```

---

## 8. Troubleshooting

### Static IP Not Sticking

**Symptoms:** IP keeps reverting to DHCP address

**Solution:** Use `nmcli` method instead of GUI:
```bash
sudo nmcli connection modify "your-connection-name" ipv4.method manual
sudo nmcli connection modify "your-connection-name" ipv4.addresses 192.168.10.88/24
sudo nmcli connection down "your-connection-name"
sudo nmcli connection up "your-connection-name"
```

---

### Can't Find Router IP

**Solution:**
```bash
ip route | grep default
```

The IP after "via" is your router/gateway.

---

### SSH Works in Command Prompt but Not VSCode

**Cause:** Special characters in password

**Solution:** Set up SSH keys (see Section 4)

---

### "Torch not compiled with CUDA enabled" Error

**Cause:** Running code on Windows PC instead of Jetson

**Solution:** 
1. Make sure VSCode shows "SSH: jetson" in bottom-left
2. Run code in VSCode terminal (which is on Jetson)
3. Verify with `hostname` command

---

### Can't Connect to Jetson Remotely

**Check:**
- [ ] Is Jetson powered on?
- [ ] Is Jetson connected to internet?
- [ ] Is Tailscale running on both devices?
- [ ] Are both devices logged into same Tailscale account?

**Verify:**
```bash
# On Jetson:
sudo tailscale status

# On PC:
tailscale status
```

---

### Password Doesn't Work for `jetson` User

**Debug steps:**

1. On Jetson, check username:
```bash
whoami
```

2. Use that username instead of `jetson`:
```bash
ssh actual-username@100.111.167.48
```

3. If still not working, set up SSH keys (no password needed)

---

## Quick Reference Card

### Your Network Info:
- **Jetson Static IP:** `192.168.10.88`
- **Router/Gateway:** `192.168.10.1`
- **DNS Servers:** `8.8.8.8, 8.8.4.4`
- **Jetson Tailscale IP:** `100.111.167.48` (example)

### Common Commands:

```bash
# Connect to Jetson
ssh jetson@100.111.167.48

# Check if on Jetson
hostname

# Check GPU
nvidia-smi

# Check CUDA in Python
python3 -c "import torch; print(torch.cuda.is_available())"

# Clone your repo
git clone https://gitlab.com/your-username/your-repo.git

# Install dependencies
pip3 install -r requirements.txt

# Run your code
python3 your_script.py

# Disconnect
exit
```

### Important Reminders:

✅ **Always keep Jetson powered on** for remote access  
✅ **Run GPU code on Jetson**, not on your PC  
✅ **Use SSH keys** to avoid password issues  
✅ **Check bottom-left of VSCode** to confirm connection  
✅ **Clone your GitLab repo** on Jetson to work with it  

---

## Need Help?

### Common Issues Checklist:
1. Is Jetson on and connected to internet?
2. Is Tailscale running on both devices?
3. Are you running code on Jetson (not PC)?
4. Is VSCode showing "SSH: jetson"?
5. Did you install dependencies on Jetson?

### Useful Resources:
- Tailscale Docs: https://tailscale.com/kb/
- NVIDIA Jetson Forums: https://forums.developer.nvidia.com/
- PyTorch CUDA Docs: https://pytorch.org/docs/stable/cuda.html

---

**Last Updated:** February 2026  
**Created for:** School Project - Remote Jetson Development
