
# Network Traffic Monitoring and IP Blocking Script

## Description
This script monitors network traffic to detect and block potential threats such as high packet rates and specific worm signatures. It uses `scapy` for packet sniffing and `iptables` for dynamically blocking suspicious IP addresses. The script is designed with the capability to:
- Detect and block Nimda worm traffic.
- Block IPs exceeding a set packet rate threshold.
- Utilize whitelists and blacklists for customized monitoring.

## Features
- **Real-time Network Monitoring**: Captures packets and inspects their source and payload.
- **Nimda Worm Detection**: Detects HTTP requests containing known Nimda worm signatures and blocks the source IP.
- **IP Rate Limiting**: Blocks IPs with traffic exceeding the defined packet rate threshold (default: 40 packets/second).
- **Logging**: Records events in timestamped log files for later analysis.
- **Whitelist and Blacklist Support**: Excludes whitelisted IPs from monitoring and automatically blocks blacklisted IPs.

## Installation
1. **Ensure Root Privileges**: The script must be run as root.
2. **Install Required Python Packages**:
   ```bash
   pip install scapy
   ```
3. **Create Whitelist and Blacklist Files**:
   - `whitelist.txt`: List of trusted IPs (one IP per line).
   - `blacklist.txt`: List of known malicious IPs (one IP per line).

## Usage
1. Save the script to a file, e.g., `network_monitor.py`.
2. Run the script with root privileges:
   ```bash
   sudo python3 network_monitor.py
   ```
3. Logs will be saved in the `logs` directory.

## Dependencies
- **Python 3.x**
- **scapy**: For packet sniffing and inspection.
- **iptables**: For managing IP blocking at the network level.

## Code Structure
- **read_ip_file**: Reads IPs from the given file and returns them as a set.
- **is_nimda_worm**: Checks if a packet contains a Nimda worm signature.
- **log_event**: Logs an event message to a timestamped file.
- **packet_callback**: Main callback function for handling packet analysis and blocking logic.

## Configuration
- **THRESHOLD**: Change the `THRESHOLD` variable to adjust the packet rate limit.
- **Log Path**: By default, logs are stored in a `logs` directory.

## Example Log Entry
```
Blocking IP: 192.168.1.100, packet rate: 45.0
```

## License
This project is licensed under the MIT License.

## Contributors
- [Dev Gusain]

## Security Note
Ensure your whitelist and blacklist files are secure and accurate to prevent accidental blocking of critical IPs.
