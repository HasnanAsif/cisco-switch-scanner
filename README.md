# Cisco Catalyst Switch Port Scanner
A Python-based script designed to scan Cisco Catalyst switches for active and inactive ports

This Python script enables network administrators to identify active and inactive ports on Cisco Catalyst switches.
The purpose is to help network administrators identify inactive ports, allowing them to disconnect unused connections and free up space for new devices.

## Supported Connection Types
The script works with both:
- SSH (Preferred)
- Telnet

Note: Telnet is highly insecure and should be avoided. However certain systems still use switches that are running older OSs that do not support SSH. Due to this, support has been provided.

## How It Works
1. Reads all IPs from switches.txt.
2. Attempts to connect to each IP from file.
3. If SSH fails, retry with Telnet. If both fail, move to the next switch.
4. If connection was successful, run `show int status` to show all switches and their status.
5. Extract data from command.
6. Format data.
7. Store data in correct files and .TXT files.
8. Move to next switch until list is done, and then repeat every 30 minutes.

## Inactive Port Tracking
These files list all ports for an IP that have been `notconnect` since the start of the scanning process. If a port becomes active, then it will be removed from the list.
