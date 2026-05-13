# Module 11.2.3: Configure DHCP on a Wireless Router
**Course**: Cisco Networking Basics - Junior Cybersecurity Analyst Pathway  
**Date**: May 12, 2026  
**Lab Duration**: ~35 minutes

## Objective
Configure DHCP on a wireless router, adjust the IP range, and verify clients receive addresses automatically.

## Key Steps Completed
- **Part 1**: Connected 3 PCs to the wireless router using Ethernet
- **Part 2**: Observed default DHCP settings and identified gateway 192.168.0.1. PC0 received 192.168.0.100 from DHCP.
- **Part 3**: Changed router IP to 192.168.5.1 and renewed DHCP leases
- **Part 4**: Modified DHCP pool to start at 192.168.5.126 with 75 max users
- **Part 5**: Verified PC0 received 192.168.5.126 and PC1 received 192.168.5.127

## Troubleshooting Note
After changing the DHCP Start IP to 192.168.5.126 and clicking Save Settings, PC0 still showed 192.168.0.100. 

**What happened**:  
PC0 was holding onto its old lease from the 192.168.0.0/24 pool. Changing the pool doesn’t force clients to drop their lease, and Packet Tracer doesn’t always auto-restart the DHCP service.

**How I fixed it**:  
I clicked Save Settings on the router again to restart the DHCP service. Then I toggled PC0 from DHCP → Static → DHCP. PC0 released 192.168.0.100 and got 192.168.5.126 from the new pool.

**Why it matters for SOC**:  
Stale leases like this show up in DHCP logs as IP mismatches. In a real SOC you’d check the lease table, force a release/renew, and correlate it with user activity logs to avoid false positives during an incident.

## SOC Relevance
DHCP and IP addressing are foundational for SOC work:
1. **Log correlation** — I use source IPs in Splunk/ELK to track activity. Knowing how DHCP assigns IPs prevents false positives when IPs change.
2. **Rogue device detection** — Controlling DHCP scope helps spot unauthorized devices.
3. **Incident response** — Renewing DHCP and checking `ipconfig` is a standard first step when a user reports connectivity issues.

## Reflection
If I found a device with IP 192.168.5.201 in this network, I’d flag it as outside the DHCP scope. That’s a potential rogue device or static IP conflict requiring investigation.
