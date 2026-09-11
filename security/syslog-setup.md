# Centralized Syslog Setup

## Architecture
```
Network devices (APs, switches, firewalls)
        ↓ UDP 514
rsyslog receiver (Linux server)
        ↓ filtered by source IP
/var/log/network-devices.log
/var/log/firewall.log
```

## Receiver Configuration

```bash
# /etc/rsyslog.d/60-network.conf
module(load="imudp")
input(type="imudp" port="514")

# Route by source IP (MUST load before generic filters)
:fromhost-ip, isequal, "10.0.0.254" /var/log/firewall.log
& stop
:fromhost-ip, startswith, "10.0.0." /var/log/network-devices.log
& stop
```

## Gotchas (from real deployment)

1. **File permissions**: rsyslog runs as user `syslog`, not root. Files must
   be owned `syslog:adm`, not `root:root`. Otherwise: silent "Permission denied"
   in syslog's own log while network logs are dropped.

2. **Filter order**: If you have a broad filter (e.g., "all 10.0.0.x → file1"),
   it will catch firewall logs too. Put specific IP filters BEFORE broad ones.
   Rename config files so specific ones load first (e.g., 59-firewall.conf
   before 60-network.conf).

3. **Multi-interface firewalls**: A firewall with multiple interfaces may
   source syslog from the egress interface IP, NOT the management IP.
   Always sniff to verify the actual source IP before configuring filters.

4. **Logrotate**: Configure rotation BEFORE enabling remote syslog. Firewall
   logs can generate 7+ GB/day (21,000 lines/minute for "Allowed" sessions).

## Verification
```bash
# Test from a remote device
echo "test" | nc -u -w1 <receiver_ip> 514

# Check the log file
tail /var/log/network-devices.log
```
