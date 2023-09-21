# NMap Commands Cheat Sheet

## Network Scanning

### Host Discovery
- **ARP Ping Scan**: Performs an ARP ping scan to discover hosts on the network.
  - Command: `nmap -sn -PR <target IP>`
- **UDP Ping Scan**: Performs a UDP ping scan to discover hosts.
  - Command: `nmap -sn -PU <target IP>`
- **ICMP Echo Ping Scan**: Sends ICMP echo requests to discover hosts.
  - Command: `nmap -sn -PE <target IP>`
- **ICMP Echo Ping Sweep**: Sends ICMP echo requests to a range of IPs.
  - Command: `nmap -sn -PE <IP range>`
- **ICMP Timestamp Ping Scan**: Performs ICMP timestamp requests to discover hosts.
  - Command: `nmap -sn -PP <target IP>`
- **ICMP Address Mask Ping Scan**: Performs ICMP address mask requests to discover hosts.
  - Command: `nmap -sn -PM <target IP>`
- **TCP Syn Ping Scan**: Performs TCP SYN ping scan.
  - Command: `nmap -sn -PS <target IP>`
- **TCP Ack Ping Scan**: Performs TCP ACK ping scan.
  - Command: `nmap -sn -PA <target IP>`
- **IP Protocol Ping Scan**: Performs IP protocol ping scan.
  - Command: `nmap -sn -PO <target IP>`

### Port and Service Discovery
- **TCP Connect Scan**: Performs a full TCP connect scan.
  - Command: `nmap -sT -v <target IP>`
- **TCP SYN Stealth Scan**: Performs a stealthy TCP SYN scan.
  - Command: `nmap -sS -v <target IP>`
- **TCP Xmas Scan**: Performs a TCP Xmas scan (FIN, URG & PUSH flags set).
  - Command: `nmap -sX -v <target IP>`
- **TCP Maimon Scan**: Performs a TCP Maimon scan (FIN & ACK flags set).
  - Command: `nmap -sM -v <target IP>`
- **TCP ACK Flag Probe Scan**: Performs a TCP ACK flag probe scan.
  - Command: `nmap -sA -v <target IP>`
- **UDP Scan**: Performs a UDP port scan.
  - Command: `nmap -sU -v <target IP>`
- **NULL Scan**: Performs a NULL scan.
  - Command: `nmap -sN -T4 -A -v <target IP>`
- **IDLE/IPID Header Scan**: Performs an IDLE/IPID header scan with a spoofed IP.
  - Command: `nmap -sI -v <target IP>`
- **SCTP INIT Chunk Scan**: Sends SCTP INIT chunk.
  - Command: `nmap -sY -v <target IP>`
- **SCTP Cookie Echo Scan**: Sends SCTP Cookie Echo.
  - Command: `nmap -sZ -v <target IP>`
- **Service Version Detection**: Performs service version detection.
  - Command: `nmap -sV -v <target IP>`
- **Aggressive Scan**: Performs aggressive scan.
  - Command: `nmap -A -v <target IP>` or `nmap -T4 -A -v <target IP>`

### OS Discovery
- **SMB OS Discovery**: Uses NSE script to discover OS over SMB.
  - Command: `nmap --script smb-os-discovery.nse <target IP>`

### Scan Beyond IDS/Firewall
- **Fragmentation**: Fragments packets to bypass filters.
  - Command: `nmap -f <target IP>`
- **Source Port Manipulation**: Sets source port for packets.
  - Command: `nmap --source-port <target IP>`
- **MTU Manipulation**: Sets maximum transaction unit.
  - Command: `nmap --mtu 8 <target IP>`
- **Decoy Scan**: Performs a decoy scan with random IP.
  - Command: `nmap -D RND:10 <target IP>`
- **Spoofed MAC Address Scan**: Performs TCP SYN scan with spoofed MAC.
  - Command: `nmap -sS -Pn --spoof-mac <spoofed MAC address> <target IP>`

## Enumeration

### NetBIOS Enumeration
- **Nmap Script**: Uses NSE script for NetBIOS enumeration.
  - Command: `nmap -sV -v --script nbstat.nse <target IP>`
- **NetBIOS Statistics**: Uses NSE script to retrieve NetBIOS statistics.
  - Command: `nmap -sU -p 137 --script nbstat.nse <target IP>`

### SNMP Enumeration
- **SNMP System Description**: Retrieves SNMP system description.
  - Command: `nmap -sU -p 161 --script snmp-sysdescr <target n/w>`
- **SNMP Processes**: Retrieves running SNMP processes with ports.
  - Command: `nmap -sU -p 161 --script snmp-processes <target n/w>`
- **SNMP Win32 Software**: Lists applications on target machine.
  - Command: `nmap -sU -p 161 --script snmp-win32-software <target n/w>`
- **SNMP Interfaces**: Retrieves SNMP interfaces.
  - Command: `nmap -sU -p 161 --script snmp-interfaces <target n/w>`

### LDAP Enumeration
- **LDAP Brute-Force**: Performs brute-force LDAP authentication.
  - Command: `nmap -p 389 --script ldap-brute --script-args ldap.base='"cn=users,dc=CEH,dc=com"' <target n/w>`

### DNS Enumeration
- **DNS Service Discovery**: Discovers DNS services using NSE script.
  - Command: `nmap --script broadcast-dns-service-discovery <target domain>`
- **DNS Brute-Force**: Performs DNS brute-force for subdomains.
  - Command: `nmap -T4 -p 53 --script dns.brute <target domain>`
- **DNS SRV Enum**: Enumerates common service records for a domain.
  - Command: `nmap --script dns-srv-enum --script-args "dns-srv-enum.domain='<target domain>'"`

### SMTP Enumeration
- **SMTP User Enumeration**: Enumerates SMTP users.
  - Command: `nmap -p 25 --script smtp-enum-users <target IP>`
- **SMTP Open Relay**: Enumerates SMTP open relay.
  - Command: `nmap -p 25 --script smtp-open-relay <target IP>`
- **SMTP Commands**: Enumerates SMTP commands.
  - Command: `nmap -p 25 --script smtp-commands <target IP>`

### WEB Enumeration
 - **Enumerating a web application**
   - Commnad: `nmap -sV --script=http-enum <target IP>`
   - Command: `nmap --script hostmap-bfk -script-args hostmap-bfk.prefix=hostmap- www.goodshopping.com` For hostname enumeration
   - Command: `nmap -p 80 --script http-waf-detect certifiedhacker.com` For Firewall detection
   - Command: `nmap --script http-trace certifiedhacker.com` For HTTP-Trace


### Others
 - **For detecting sniffing**
   - Command: `nmap --script=sniffer-detect [Target IP Address/ IP Address Range]`
     

## NSE Scripts

- **nbstate.nse**: NetBIOS Enumeration
- **snmp-sysdescr**: SNMP System Description
- **snmp-processes**: SNMP Processes
- **http-enum**: For enumerating a web application
- ...

---

Replace placeholders such as `<target IP>`, `<IP range>`, `<target n/w>`, `<spoofed MAC address>`, and `<target domain>` with appropriate values.

Feel free to further customize the content as needed
