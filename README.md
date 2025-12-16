# RyzenChill ❄️

A lightweight bash daemon to keep your AMD Ryzen laptop cool by dynamically managing CPU boost.

## The Problem
Running Linux on laptops (like the Asus TUF A15) can sometimes lead to aggressive CPU boosting, resulting in high temperatures (90°C+) and battery drain.

## The Solution
**RyzenChill** (`rchill`) monitors your CPU temperature using `lm-sensors`. If the temperature exceeds a set threshold (default: 75°C), it temporarily disables CPU boost to let the system cool down, re-enabling it once safe.

## Prerequisites
- Linux OS
- `lm-sensors` (must be installed and configured)
- Root/Sudo access

## Installation

1. **Clone the repo:**
   ```bash
   git clone https://github.com/shaw4m4n/Fixing-Overheating-Programmatically.git
   mv Fixing-Overheating-Programmatically RyzenChill
   cd RyzenChill
   ```
   *(Note: The repository URL is currently unchanged, but we are renaming the local folder to match the new project name)*

2. **Install the script:**
   ```bash
   sudo cp rchill /usr/local/bin/
   sudo chmod +x /usr/local/bin/rchill
   ```

3. **Install and start the service:**
   ```bash
   sudo cp rchill.service /etc/systemd/system/
   sudo systemctl daemon-reload
   sudo systemctl enable --now rchill.service
   ```

## Configuration
To change the temperature limit (default 75°C), simply edit the script:
```bash
sudo nano /usr/local/bin/rchill
```
Change `75` in `if [[ $temp -gt 75 ]]` to your desired temperature.