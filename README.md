# Fixing Overheating Programmatically

## Issue
Personal Laptop (Asus TUF A15 2020) with Linux is touching 96 degrees which was too warm for comfortable usage and it significantly impacted the battery and overall performance of the device.

##  Solutions:
- Cleaning the internal fans and changing thermal paste.
    - It reduces overheating but during heavy workload it still heated and and drained charge significantly.

- After some research I found out that Linux CPU boost feature is always on and not properly optimized for the device.
- I found Linux (Ubuntu) use's a file to enable/disable cpu boost 
    - In my case it was: `/sys/devices/system/cpu/cpufreq/boost`

- I wrote a shell script to control the boost parameter based on the cpu temps. `limit-boost`
    - make sure the file is executable and store it in `/usr/local/bin/limit-boost`
    - this program uses lm-sensors for cpu temperature infomation 
        - search for the package for your distribution and install it before using.

- and to deploy the script as a service used systemd service `limit-boost.service`
    - this file need to be stored in `/etc/systemd/system/limit-boost.service`.

- to enable the service `sudo systemctl enable limit-boost.service`.
