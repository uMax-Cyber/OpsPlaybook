# VM Creation Runbook (Cloud-Init + Golden Template)

## Prerequisites
- Golden template (VMID 9000) on target node
- Root SSH access to Proxmox node
- Free IP in target subnet (scan first!)

## Steps

### 1. Get Free VMID
```bash
ssh root@<node> "pvesh get /cluster/nextid"
```

### 2. Scan for Free IP
```bash
# On the target node — silence = free
for i in $(seq 50 100); do
  ping -c1 -W1 10.0.0.$i &>/dev/null || echo "10.0.0.$i free"
done
```
⚠️ **Trap**: An IP that responds to ping is OWNED by someone. Only use silent IPs.

### 3. Clone Template
```bash
ssh root@<node> "qm clone 9000 <NEWID> --full 1 --name <name>"
```

### 4. Configure Cloud-Init
```bash
ssh root@<node> "qm set <NEWID> \
  --ciuser ubuntu \
  --cipassword '<generated>' \
  --ipconfig0 ip=<free_ip>/24,gw=<gateway> \
  --sshkeys /root/.ssh/id_rsa.pub"
```

### 5. Start and Wait for Agent
```bash
ssh root@<node> "qm start <NEWID>"
# Guest agent installs on first boot (60-120 seconds)
# Poll until ready:
for i in $(seq 1 15); do
  sleep 10
  ssh root@<node> "qm agent <NEWID> ping" &>/dev/null && break
done
```

### 6. Verify (ALL must pass before reporting to user)
```bash
# Agent reachable?
ssh root@<node> "qm agent <NEWID> ping"

# IP correct?
ssh root@<node> "qm agent <NEWID> network-get-interfaces"

# SSH by key works?
ssh ubuntu@<ip> "echo KEY_OK"

# SSH by password works?
# (see ssh-recovery.md for common issue)

# MAC matches ARP?
ssh root@<node> "ip neigh | grep <ip>"
```

## Common Traps
1. LXC template ≠ VM disk (don't import .tar.zst as disk)
2. Busy IP causes silent conflict (always scan)
3. cipassword doesn't enable password SSH (cloudimg override)
4. VM recreate resets all SSH settings
5. Guest agent needs 60-120s on first boot
