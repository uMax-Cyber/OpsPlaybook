# Wi-Fi Diagnosis Runbook

## Methodology: Top-Down (NOT Bottom-Up)

**Never start with wireshark.** Follow this order:

### Step 0: DHCP Pool (5 min)
See [dhcp-pool.md](dhcp-pool.md) — this is the most common cause.

### Step 1: Scope (5 min)
- Which SSID? Which VLAN? Which APs?
- Which device types? (phones vs printers vs laptops)
- Constant or intermittent? Peak hours or random?
- New devices only, or existing too?

### Step 2: Passive Metrics (10 min)
From controller API, check:
- RSSI distribution (clients < -70dBm = coverage issue)
- Channel utilization per AP (>60% = congestion)
- Retry rates (tx_retries > 1000 = retransmission storm)
- Client count per AP (>20 on single radio = overloaded)
- Roaming quality (% of "bad roams" where both APs < -75dBm)

### Step 3: DHCP Path (10 min)
- Pool size vs utilization
- Lease events: Discover without Offer = server not responding
- Check for NAK/Decline (conflict detection)

### Step 4: Time Correlation (5 min)
- Config problem: constant, all day, same devices
- Load problem: peaks during busy periods, different devices each time

### Step 5: Targeted Capture (ONLY NOW)
- Capture at the gateway vNIC (not random port)
- Look for: DHCP Discover without Offer, EAPOL failures, retransmissions
- 60-90 seconds is usually sufficient

### Step 6: Synthesis
Symptom → log evidence → packet evidence → root cause → recommendation

## Real Cases

| Symptom | Root Cause | Fix |
|---------|-----------|-----|
| New devices "connecting..." | DHCP pool exhausted (459/455) | Expanded pool ×2 |
| Client on 1F connects to 3F AP | No min RSSI kick, sticky client | Set min RSSI -75dBm |
| IP+link OK but no packets | 58k retransmissions (congestion) | Enabled 5GHz after RAM upgrade |
| Random drops during calls | No 802.11r fast roaming | Enabled fast roaming |
