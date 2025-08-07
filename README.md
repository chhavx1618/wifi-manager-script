# WiFi Network Manager for Linux (`wifi_manager.sh`)

This script provides a command-line utility to manage WiFi networks on a Linux system using `wpa_supplicant`. It is designed specifically for the wireless interface `wlp8s0`, but you can modify it to work with any other interface.

## Features

- Add new WiFi networks (supports both open and WPA/WPA2-secured)
- Remove existing WiFi networks from configuration
- List all configured networks and their priorities
- Scan for nearby available WiFi networks and show signal strength
- Connect to available configured networks
- Show current WiFi connection and IP status

This is for wlp8s0 interface.
To use it for another interface (e.g., `wlan0`), update the `INTERFACE` and `CONFIG_FILE` variables in the script accordingly.

## Configuration File

The script modifies the following wpa_supplicant configuration file:

` /etc/wpa_supplicant/wpa_supplicant-wlp8s0.conf `


This file must be writable by the script using `sudo`, and used by the `wpa_supplicant` service.

## Usage

Make the script executable:

```bash
chmod +x wifi_manager.sh
````

Then run with one of the following commands:

./wifi_manager.sh add       # Add a new WiFi network
./wifi_manager.sh remove    # Remove an existing network by SSID
./wifi_manager.sh list      # List all configured networks with priorities
./wifi_manager.sh scan      # Scan and show available networks with signal strength
./wifi_manager.sh connect   # Reconnect using current configuration
./wifi_manager.sh status    # Show current connection and IP address

##### Notes
You must run the script with sufficient privileges (e.g., via sudo) to modify system-level configuration and restart services.

Changes take effect immediately by restarting the wpa_supplicant-wlp8s0 systemd service.

Network priority helps determine which network to connect to when multiple are available.

##### Dependencies
wpa_supplicant

iw

iputils (for ip command)

grep, sed, tee, and other core UNIX utilities

Example
To add a WPA2 network:

````
./wifi_manager.sh add
#Enter SSID: my-network
#Enter password: ******
#Enter priority: 5


To scan for nearby WiFi:

./wifi_manager.sh scan
To check current status:

./wifi_manager.sh status

````


## Note
All contributions, suggestions and improvements are appreciated!
