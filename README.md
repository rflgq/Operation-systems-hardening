# Operating Systems Hardening Project 🛡️

**Security Implementation for Windows and Linux Systems**

## Overview

System hardening is the primary method of securing an OS by eliminating as many security risks as possible. This project demonstrates the systems hardening process for both Windows and Linux operating systems, addressing critical security challenges like authentication, firewall configuration, and file system security.

The objective is to secure the OS against common attacks using **built-in security policies and configuration tools only** — no third-party antivirus, no penetration testing tools. Just the OS's own native features, reconfigured to shrink the attack surface from the inside out.

## Structure

- [`1-windows-hardening.md`](./1-windows-hardening.md) — 8 tasks covering Local Security Policy, BitLocker, Defender Firewall, Services, Ports, UAC, Audit Policies, and Group Policy.
- [`2-linux-hardening.md`](./2-linux-hardening.md) — 6 tasks covering service hardening, UFW firewall, SSH hardening, automatic updates, file permissions, and Fail2Ban intrusion detection.
- [`screenshots/`](./screenshots) — Supporting screenshots for each task, organized by OS.

## Summary of Coverage

| Area | Windows | Linux |
|---|---|---|
| Account/Auth security | Local Security Policy, UAC | SSH hardening |
| Data protection | BitLocker | File permissions (chmod) |
| Network security | Defender Firewall, Port blocking | UFW |
| Service hardening | Disable unnecessary services | Disable unnecessary services |
| Monitoring/Detection | Audit Policies | Fail2Ban |
| Centralized policy | Group Policy (gpedit.msc) | Automatic security updates |

## Conclusion

The implementation of these hardening steps provides a solid baseline for both Windows and Linux environments. By restricting services, securing authentication, and enabling detection systems, the overall security posture is significantly improved.

**System Secured | Brute-Force Resistant | Audit Enabled**

## Team

- Rimas Dhahi — Team Lead
- Layan Alharbi
- Wujud Alharbi
- Noura Alharbi

---
*Digital safety starts with curiosity ✨*
