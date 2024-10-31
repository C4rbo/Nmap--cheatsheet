## Nmap Cheatsheet

**Nmap** (Network Mapper) is a powerful tool for network discovery and security auditing. Here’s a comprehensive cheatsheet to guide you through its main commands and options.

---

### Basic Scans
- **Default Scan:**  
  ```bash
  nmap <target>
  ```
  Scans the target for the top 1000 commonly open ports with default scripts.

- **Ping Scan (Discover live hosts):**  
  ```bash
  nmap -sn <target>
  ```
  Only checks if the host is up without scanning any ports.

- **Scan Specific Ports:**  
  ```bash
  nmap -p <port> <target>
  nmap -p 22,80,443 <target>     # Scan multiple specific ports
  nmap -p- <target>              # Scan all 65535 ports
  ```

### Port Scan Types
- **TCP Connect Scan:**  
  ```bash
  nmap -sT <target>
  ```
  Uses a full TCP connection, useful when SYN scan isn’t available.

- **SYN Scan (Default, requires root):**  
  ```bash
  nmap -sS <target>
  ```
  Performs a stealthy half-open scan.

- **UDP Scan:**  
  ```bash
  nmap -sU <target>
  ```
  Scans UDP ports (slower than TCP).

### Service and Version Detection
- **Service Version Detection:**  
  ```bash
  nmap -sV <target>
  ```
  Attempts to determine the version of services running on open ports.

- **Aggressive Scan (-A):**  
  ```bash
  nmap -A <target>
  ```
  Enables OS detection, version detection, script scanning, and traceroute.

- **Operating System Detection:**  
  ```bash
  nmap -O <target>
  ```
  Detects the target’s operating system.

### Output Options
- **Save Output to File (Normal):**  
  ```bash
  nmap -oN output.txt <target>
  ```

- **Save Output to File (XML):**  
  ```bash
  nmap -oX output.xml <target>
  ```

- **Save Output to File (Grepable):**  
  ```bash
  nmap -oG output.gnmap <target>
  ```

- **Save All Formats:**  
  ```bash
  nmap -oA output <target>
  ```
  Saves in all available formats (Nmap, XML, Grepable).

### Script Scanning
- **Default Script Scan:**  
  ```bash
  nmap -sC <target>
  ```
  Runs default scripts against target services.

- **Run Specific NSE Scripts:**  
  ```bash
  nmap --script <script-name> <target>
  nmap --script http-enum <target>       # Example of a specific script
  ```

- **Run Multiple Scripts:**  
  ```bash
  nmap --script <script1>,<script2> <target>
  ```

- **Run All Vulnerability Scripts:**  
  ```bash
  nmap --script vuln <target>
  ```
  Runs all vulnerability scripts against the target.

### Timing and Performance
- **Timing Templates (0 - 5):**  
  ```bash
  nmap -T<0-5> <target>
  ```
  Adjusts scan speed, from `-T0` (slowest) to `-T5` (fastest). Example: `-T4` for a fast scan.

- **Max Parallel Hosts:**  
  ```bash
  nmap --max-hostgroup <number> <target>
  ```
  Limits the number of hosts scanned in parallel.

- **Max Rate (Packets per Second):**  
  ```bash
  nmap --max-rate <number> <target>
  ```
  Limits the number of packets sent per second.

### Firewall/IDS Evasion and Spoofing
- **Fragment Packets:**  
  ```bash
  nmap -f <target>
  ```
  Sends fragmented packets, useful for evading basic firewalls/IDS.

- **Randomize Target Scan Order:**  
  ```bash
  nmap --randomize-hosts <target>
  ```

- **Spoof IP Address:**  
  ```bash
  nmap -S <spoofed-IP> <target>
  ```

- **Decoy Scan:**  
  ```bash
  nmap -D RND:<num> <target>
  ```
  Launches a decoy scan, making it harder for the target to identify the true source.

- **MAC Address Spoofing:**  
  ```bash
  nmap --spoof-mac <MAC address/vendor> <target>
  ```
  Example: `--spoof-mac 0A:0B:0C:0D:0E:0F` or use `--spoof-mac Cisco` for a random Cisco MAC.

### Advanced Scanning
- **Scan Specific IP Range/Subnet:**  
  ```bash
  nmap <IP-range>
  nmap <IP>/24
  ```

- **Excluding Hosts:**  
  ```bash
  nmap <target> --exclude <IP>
  nmap <target> --exclude <IP1>,<IP2>
  ```

- **Scan Through a Proxy:**  
  ```bash
  nmap --proxies <socks4|socks5://proxyIP:port> <target>
  ```

### Useful Scan Examples
- **Quick Scan of Top Ports:**  
  ```bash
  nmap --top-ports 20 <target>
  ```
  Scans the top 20 most common open ports.

- **Full TCP and UDP Scan with Service and OS Detection:**  
  ```bash
  nmap -sS -sU -A -p- <target>
  ```

- **Detect Web Vulnerabilities (SQLi, XSS, etc.):**  
  ```bash
  nmap --script http-sql-injection,http-cross-site-scripting <target>
  ```

### NSE Categories
Some popular NSE categories:
- `auth` - for authentication
- `broadcast` - for network discovery
- `brute` - for brute force attacks
- `exploit` - to detect vulnerabilities
- `vuln` - for vulnerability detection

## Legal Disclaimer

**Use responsibly and legally.** This tool is designed for educational purposes and authorized security testing only. Unauthorized scanning of networks and devices is illegal and unethical. Always obtain explicit permission from the network owner before using this tool.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contributing

Contributions are welcome! If you have suggestions for improvements or find bugs, please open an issue or submit a pull request on GitHub.

## Author

- OfficialWebSite: https://nmap.org/
- Documentation for Kali Linux: https://www.kali.org/tools/nmap/ 
- C4rbo (https://github.com/C4rbo)
