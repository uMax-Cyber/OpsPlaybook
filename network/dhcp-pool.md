# DHCP Pool Exhaustion Check

## The #1 Cause of "Connecting..." Wi-Fi Issues

When users report devices stuck on "connecting..." but existing devices work fine,
check DHCP pool exhaustion FIRST. This takes 5 minutes and solves ~30% of complaints.

## Why It's Missed
- "Wired works fine" doesn't exclude DHCP — wired and wireless use different VLANs with separate pools
- Existing devices renew successfully; only NEW devices can't get addresses
- DHCP server doesn't log "pool full" — it just silently stops responding to DISCOVER

## Quick Check

```bash
# Count unique IPs issued (from DHCP server logs)
grep "DHCP Server" /var/log/dhcp.log | \
  grep -oE 'reported_ip="10\.X\.Y\.[0-9]+"' | sort -u | wc -l

# Compare against your pool size
# If issued >= pool_size: POOL EXHAUSTED
```

## Detailed Check (with utilization)

```bash
# Subnet breakdown
grep "DHCP Server" /var/log/dhcp.log | \
  grep -oE 'reported_ip="([0-9]+\.[0-9]+)\.' | \
  sort | uniq -c | sort -rn
```

## Fix
1. Expand the pool (add secondary range if needed)
2. Or shorten lease time (frees expired addresses faster)
3. Or move some devices to a different VLAN

## Prevention
- Monitor pool utilization (alert at 85%)
- Set lease time appropriate to device turnover (2-4h for school/office, not 8h)
