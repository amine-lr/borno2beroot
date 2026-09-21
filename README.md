# borno2beroot (Born2beroot)

42 system-administration project: set up a hardened virtual machine from scratch.

Covered: Debian install on a VM, LVM partitions with encryption, SSH (key-only, custom port), UFW firewall, `sudo` + strong password policy, user/groups, `cron`, and a lightweight monitoring script.

## Guide

The full walkthrough lives in this repo:

- [`born2beroot_guide (1).pdf`](<./born2beroot_guide (1).pdf>)

Follow it top to bottom during installation and configuration, then verify each checkpoint (SSH, firewall rules, `cron`, password policy) before evaluation.

## Evaluation checklist

Have these ready to demo on eval day:

- `signature.txt` comparison output
- `lsblk` — LVM partitions with encryption
- `sudo ufw status` / `sudo ss -tunlp` — firewall + listening ports (SSH on custom port)
- `sudo cat /etc/ssh/sshd_config | grep -E "Port|PermitRootLogin|PasswordAuthentication"` — key-only auth, no root login
- `chage -l <user>` and `sudo cat /etc/login.defs | grep -E "PASS_"` — password policy
- `sudo crontab -l` + `journalctl` excerpt — `cron` + monitoring script running
- `hostnamectl`, `apparmor_status` / `sestatus` — hostname and MAC system
