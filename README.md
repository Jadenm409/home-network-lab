# Home Network Lab

## Overview
Set up a personal home lab to get hands-on experience with networking
and basic security concepts. Started because I wanted to understand
what's actually happening on a network beyond just using it.

## Environment
- **Lab Machine:** Kali Linux 2024.2 running on a Dell Inspiron 15
  (Intel Core i5, 16GB RAM, 512GB SSD)
- **Primary Workstation:** MacBook Pro (macOS Ventura 13.6)
- **Windows Endpoint:** Windows 11 Pro (used as target machine for testing)
- **Router:** ASUS RT-AX58U (192.168.1.1) running custom firmware
- **Network:** /24 subnet with 8+ connected devices across 2 SSIDs

## Tools I've Used

### Wireshark
- Captured live traffic on my home network using monitor mode on wlan0
- Analyzed TCP three-way handshakes and identified ARP, DNS, HTTP,
  and ICMP traffic
- Practiced writing display filters like `ip.addr == 192.168.1.105`
  and `tcp.port == 443`
- Captured over 10,000 packets in a single session and filtered down
  to specific conversations between hosts

### nmap
- Scanned my /24 subnet to enumerate all active hosts and open ports
- Used `-sV` flag for service version detection and `-O` for OS fingerprinting
- Discovered open ports on my own devices I didn't know were exposed
- Example scan: `nmap -sV -O 192.168.1.0/24`

### hping3
- Crafted custom TCP, UDP, and ICMP packets to test how hosts respond
- Ran controlled flood tests on my own router to observe behavior
  under stress: `hping3 -S --flood -V 192.168.1.1`
- Monitored results in real time with Wireshark running simultaneously

### iperf3
- Set up iperf3 in client/server mode between my MacBook and Kali machine
- Measured consistent throughput of ~450 Mbps on 5GHz WiFi
- Tested UDP bandwidth and observed packet loss under high load conditions
- Command used: `iperf3 -c 192.168.1.105 -u -b 1G`

### mtr
- Used mtr to trace network path from my machine to external hosts
- Identified a consistent latency spike at my ISP's second hop (~18ms)
- Combined with ping to isolate whether issues were local or upstream

## What I'm Still Learning
- Getting more comfortable reading full packet captures in Wireshark
- Working toward CompTIA Network+ to formalize what I've learned hands-on
- Exploring more security testing concepts in a controlled environment
