# Incident Report – DNS & ICMP Network Traffic Analysis

## 1. Summary
Users were unable to access the website **www.yummyrecipesforme.com**, receiving the error message:  
**"destination port unreachable"**.  
Network packet analysis revealed repeated **ICMP “udp port 53 unreachable”** responses from the DNS server, indicating DNS service failure.

## 2. Tools Used
- tcpdump
- Linux command line
- DNS/UDP analysis
- ICMP error inspection

## 3. Packet Capture Summary
Captured packets show:
- Client IP: **192.51.100.15**
- DNS Server IP: **203.0.113.2**
- Repeated DNS queries to UDP port 53
- Repeated ICMP error replies: *udp port 53 unreachable*

## 4. Root Cause
The DNS service on the server **was not listening or was unreachable on UDP port 53**.  
Possible causes:
- DNS service crashed
- Firewall blocking port 53
- Misconfiguration
- DoS attack on DNS

## 5. Conclusion
The failure of the DNS service prevented domain resolution, which caused the website to be inaccessible.  
**Impacted protocol: DNS over UDP (Port 53)**.
