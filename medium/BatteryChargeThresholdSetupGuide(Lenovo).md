# Ubuntu Battery Charge Threshold Setup Guide (Lenovo)

This guide covers setting up battery charge thresholds on Linux systems to extend battery life by limiting charging to a specific range (e.g., 75-85%).
This method was tested with Ubuntu 24.04.2.

## Quick Reference

**For Lenovo systems (ThinkPad, etc.):**

```bash
# Set thresholds manually
sudo sh -c 'echo 75 > /sys/class/power_supply/BAT0/charge_control_start_threshold'
sudo sh -c 'echo 85 > /sys/class/power_supply/BAT0/charge_control_end_threshold'

```

## Step-by-Step Setup

### 1. Identify Your System

First, check your system manufacturer:

```bash
sudo dmidecode -s system-manufacturer
sudo dmidecode -s system-product-name

```

### 2. Check Available Battery Controls

### For Lenovo/ThinkPad Systems:

```bash
# Check if battery threshold controls are available
ls -la /sys/class/power_supply/BAT0/ | grep threshold

```

Expected output should include:

- `charge_control_start_threshold`
- `charge_control_end_threshold`

### 3. Set Battery Thresholds

### Method A: Lenovo/ThinkPad (Linux Power Supply Interface)

1. **Check current settings:**
   
    ```bash
    echo "Start: $(cat /sys/class/power_supply/BAT0/charge_control_start_threshold)%"
    echo "End: $(cat /sys/class/power_supply/BAT0/charge_control_end_threshold)%"
    
    ```
    
2. **Set new thresholds (75-85% example):**
   
    ```bash
    sudo sh -c 'echo 75 > /sys/class/power_supply/BAT0/charge_control_start_threshold'
    sudo sh -c 'echo 85 > /sys/class/power_supply/BAT0/charge_control_end_threshold'
    
    ```
    
3. **Verify settings:**
   
    ```bash
    echo "Start: $(cat /sys/class/power_supply/BAT0/charge_control_start_threshold)%"
    echo "End: $(cat /sys/class/power_supply/BAT0/charge_control_end_threshold)%"
    
    ```
    

### 4. Make Settings Persistent (Systemd Service)

Create a systemd service to maintain settings across reboots:

1. **Create the service file:**
   
    ```bash
    sudo nano /etc/systemd/system/battery-charge-thresholds.service
    
    ```
    
2. **For Lenovo/ThinkPad systems, add this content:**
   
    ```
    [Unit]
    Description=Set Battery Charge Thresholds
    After=multi-user.target
    
    [Service]
    Type=oneshot
    ExecStart=/bin/sh -c 'echo 75 > /sys/class/power_supply/BAT0/charge_control_start_threshold'
    ExecStart=/bin/sh -c 'echo 85 > /sys/class/power_supply/BAT0/charge_control_end_threshold'
    RemainAfterExit=true
    
    [Install]
    WantedBy=multi-user.target
    
    ```
    
3. **Enable and start the service:**
   
    ```bash
    sudo systemctl enable battery-charge-thresholds.service
    sudo systemctl start battery-charge-thresholds.service
    
    ```
    
4. **Verify the service is working:**
   
    ```bash
    sudo systemctl status battery-charge-thresholds.service
    
    ```
    



## Troubleshooting

### Common Issues:

1. **Permission denied when writing to /sys/class/power_supply/:**
    - Make sure to use `sudo` and the `sh -c` wrapper
    - Correct: `sudo sh -c 'echo 75 > /sys/class/power_supply/BAT0/charge_control_start_threshold'`
    - Wrong: `sudo echo 75 > /sys/class/power_supply/BAT0/charge_control_start_threshold`
2. **Thresholds reset after reboot:**
    - The systemd service wasn't created or enabled properly
    - Check service status: `sudo systemctl status battery-charge-thresholds.service`
3. **Battery threshold files don't exist:**
    - Your system may not support software-controlled charging thresholds
    - Try using TLP or manufacturer-specific tools
    - Some older systems don't support this feature

### Verification Commands:

```bash
# Check if your system supports battery thresholds
find /sys/class/power_supply/ -name "*threshold*" 2>/dev/null

# Monitor battery status
upower -i /org/freedesktop/UPower/devices/battery_BAT0

# Check current power supply information
cat /sys/class/power_supply/BAT0/status
cat /sys/class/power_supply/BAT0/capacity

```

## Recommended Threshold Values

- **Conservative (maximize battery life):** 40-80%
- **Balanced (good compromise):** 75-85%
- **Performance (less restriction):** 80-90%

## Notes

- Lower thresholds extend battery life but reduce available capacity
- These settings primarily benefit systems that are plugged in frequently
- Modern batteries have built-in protection, but software limits provide additional benefit
- Some manufacturers (like ASUS) have their own specific tools and methods
- Always test the method that works for your specific system and hardware configuration.
- After I set this up, I've experienced a sudden crash several times when I unplugged USB-C cable from my Lenovo laptop. It might have something to do with this configuration.

