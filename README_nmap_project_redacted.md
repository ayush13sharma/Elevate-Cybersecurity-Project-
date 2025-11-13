# Nmap Port Scan Project
**Student:** Ayush Sharma
**Date:** 2025-11-13
**Network Scanned:** 192.168.1.0/24
**Tool Used:** Nmap 7.98 (on Windows)

## Commands Used
1. `nmap -sn 192.168.1.0/24 -oN hosts_up.txt`
2. `nmap -sS -p- -T4 192.168.1.0/24 -oA fullscan`
3. `nmap -sV -sC -p- 192.168.1.1 -oN svc_192.168.1.1.txt` (example for router)

## Live Hosts Found
- **192.168.1.1** (ZTE Router) — MAC: REDACTED
- **192.168.1.3** (Local Device) — MAC: REDACTED
- **192.168.1.4** (My PC)

> Note: For public sharing I recommend removing MAC addresses (see Security & Privacy section below).

## Key Findings
| IP Address | Open Ports | Services | Risk | Recommendation |
|-------------|-------------|-----------|-------|----------------|
| 192.168.1.1 | 23 (Telnet - filtered), 53 (DNS), 80 (HTTP), 443 (HTTPS) | Router web + DNS | Medium | Disable Telnet if not required; enforce HTTPS; change default router password; enable router firewall and firmware update. |
| 192.168.1.3 | None (no open TCP ports) | — | Low | Keep firewall ON; maintain updates. |
| 192.168.1.4 | None (local scanner) | — | Low | Keep Windows Firewall and Defender enabled. |

## Files Included
- `hosts_up.txt` (discovery output)
- `fullscan.nmap`, `fullscan.gnmap`, `fullscan.xml` (full scan outputs)
- `svc_192.168.1.1.txt` (service detection example for router)
- `analysis.txt`
- `screenshots/` (terminal screenshots)

## Short Summary (one paragraph)
Scanned the local Wi‑Fi network (192.168.1.0/24) and found 3 active hosts. The router (192.168.1.1) exposes DNS and HTTP/HTTPS management interfaces; Telnet is filtered but should remain disabled. Other hosts show no open TCP services. Recommended actions: secure router (disable unused services, update firmware, change default credentials), keep host firewalls enabled, and patch devices.

## How to reproduce
1. Run discovery:
   ```
   nmap -sn 192.168.1.0/24 -oN hosts_up.txt
   ```
2. Full TCP scan:
   ```
   nmap -sS -p- -T4 192.168.1.0/24 -oA fullscan
   ```
3. Service detection for router:
   ```
   nmap -sV -sC -p 53,80,443,23 192.168.1.1 -oN svc_192.168.1.1.txt
   ```

## Security & Privacy (important)
- **Private IPs (192.168.x.x)** are non-routable on the public internet and cannot be directly reached from outside your local network. Publishing these is generally low risk.
- **MAC addresses** uniquely identify hardware on a local network and can be used for device fingerprinting; while publishing MACs is low risk for remote attackers, it's better not to include full MAC addresses in a public repository. Instead either omit them or replace with vendor name (e.g., `ZTE`).
- **Screenshots** might contain MACs or other sensitive info — blur or redact MACs and any unique identifiers before making screenshots public.
- If you are unsure, create a **public repo** with redacted outputs (no MACs) or make the repo **private**.

