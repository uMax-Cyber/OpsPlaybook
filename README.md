# Infrastructure Runbooks

Production-tested operational runbooks for homelab/enterprise infrastructure: Proxmox VE, UniFi networking, Sophos firewalls, and AI-agent operations. Each runbook documents the exact procedure, common traps, and verification steps — learned from real incidents.

## Philosophy

Every runbook follows the same structure:
1. **What** — the operation being performed
2. **Why** — when you'd need this
3. **Steps** — exact commands, in order
4. **Verify** — how to confirm success
5. **Traps** — real failures that occurred, so you don't repeat them

## Contents

### 🖥 Sysadmin
- [VM Creation Runbook](sysadmin/vm-creation.md) — cloud-init provisioning with golden template
- [Disk Resize Runbook](sysadmin/disk-resize.md) — online two-stage resize
- [SSH Recovery Runbook](sysadmin/ssh-recovery.md) — fixing cloudimg SSH after VM recreate

### 🌐 Network
- [Wi-Fi Diagnosis Runbook](network/wifi-diagnosis.md) — top-down methodology (DHCP first)
- [DHCP Pool Check](network/dhcp-pool.md) — the #1 cause of "connecting..." issues
- [Port Audit Procedure](network/port-audit.md) — full switch inventory with anomaly detection
- [Topology Mapping](network/topology-mapping.md) — building network tree from API

### 🔒 Security
- [Weekly Security Audit](security/weekly-audit.md) — automated checklist
- [Syslog Setup](security/syslog-setup.md) — centralized logging from all network devices

## Stack
- Proxmox VE 9.x (3 standalone nodes)
- UniFi Controller (96 managed devices)
- Sophos Firewall (2 gateways, XML API)
- Python + Bash (stdlib only)
- rsyslog for centralized logging

## Why Runbooks?

Infrastructure fails in predictable ways. The same 5 traps cause 80% of VM provisioning failures. The same 3 issues cause most Wi-Fi complaints. Documenting them means:
- New team members ramp up faster
- 3 AM incidents get resolved by following steps, not debugging
- AI agents can follow procedures reliably

## License
MIT
