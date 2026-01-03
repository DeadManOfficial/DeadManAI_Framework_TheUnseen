# DeadManAI Current Network Baseline
**Discovery Date:** 2026-01-03
**Location:** C:\Users\Administrator

---

## EXECUTIVE SUMMARY

**Network Type:** Home/Small Office
**Primary Connection:** 10 Gbps Ethernet (Ethernet 2)
**Internet Performance:** Excellent (12ms avg ping to 8.8.8.8)
**Gateway Latency:** <1ms (local network)
**Total Bandwidth Usage:** 90.79 GB received, 4.75 GB sent

---

## 1. NETWORK INTERFACES

| Interface | Status | MAC Address | Speed | Purpose |
|-----------|--------|-------------|-------|---------|
| **Ethernet 2** | UP | 34:5A:60:61:54:8A | **10 Gbps** | Primary production network |
| vEthernet (WSL) | UP | 00:15:5D:67:17:71 | 10 Gbps | Docker/WSL virtualization |
| Ethernet | Disconnected | 34:5A:60:61:54:89 | 0 bps | Unused |

---

## 2. IP ADDRESSING

### Production Network (Ethernet 2)
- **IP Address:** 192.168.50.106
- **Subnet Mask:** /24 (255.255.255.0)
- **Network:** 192.168.50.0/24
- **Gateway:** 192.168.50.1 (E8:9C:25:89:42:60)
- **DNS Servers:**
  - Primary: 8.8.8.8 (Google Public DNS)
  - Secondary: 8.8.4.4 (Google Public DNS)
  - Tertiary: 192.168.50.1 (Local gateway)

### Virtualization Network (WSL/Hyper-V)
- **IP Address:** 172.24.16.1
- **Subnet Mask:** /20
- **Network:** 172.24.16.0/20
- **Purpose:** Docker containers, WSL2 instances

### Link-Local (Ethernet - Disconnected)
- **IP Address:** 169.254.103.184/16
- **Status:** Auto-assigned (no DHCP)

---

## 3. DISCOVERED DEVICES

| IP Address | MAC Address | Status | Notes |
|------------|-------------|--------|-------|
| **192.168.50.1** | E8:9C:25:89:42:60 | REACHABLE | **Gateway/Router** |
| 192.168.50.106 | 34:5A:60:61:54:8A | LOCAL | **This PC (DeadManAI workstation)** |
| 192.168.50.112 | 28:E6:A9:47:D1:B8 | STALE | Unknown device |
| 192.168.50.97 | B8:B4:09:DC:8A:54 | STALE | Unknown device |

---

## 4. NETWORK TOPOLOGY

```
INTERNET
   │
   │ (ISP Connection - Speed unknown)
   │
   └─ 192.168.50.1 (Gateway/Router)
         │
         │ 192.168.50.0/24 Network
         │
         ├─ 192.168.50.106 (DeadManAI PC) ← PRIMARY WORKSTATION
         │     └─ Ethernet 2 (10 Gbps)
         │     └─ WSL/Docker (172.24.16.1/20)
         │
         ├─ 192.168.50.112 (Unknown device)
         └─ 192.168.50.97 (Unknown device)
```

---

## 5. INTERNET CONNECTIVITY

**Test Results:**
- **Target:** 8.8.8.8 (Google DNS)
- **Ping:** 12ms average
- **Status:** CONNECTED ✅
- **Stability:** Excellent

**Gateway Performance:**
- **Target:** 192.168.50.1
- **Ping:** <1ms average
- **Status:** Optimal local network performance

---

## 6. ACTIVE SERVICES

**Network Shares:**
- ADMIN$ (C:\Windows) - Remote Admin
- C$ (C:\) - Default share
- G$ (G:\) - Default share (likely DeadManAI storage)
- IPC$ - Remote IPC

**Firewall Status:**
- Domain profile: ENABLED
- Private profile: ENABLED
- Public profile: ENABLED

---

## 7. BANDWIDTH USAGE STATISTICS

| Interface | Received | Sent | Ratio |
|-----------|----------|------|-------|
| Ethernet 2 | 90.79 GB | 4.75 GB | 19:1 download-heavy |
| WSL (Hyper-V) | 12 KB | 456 KB | Development/Docker traffic |

**Analysis:**
- Heavy download usage indicates content consumption/research
- Low upload suggests limited content distribution currently
- 19:1 ratio typical for consumer connection

---

## 8. DNS ACTIVITY (Recent Lookups)

**Networking Research:**
- sdn.systemsapproach.org
- www.eve-ng.net
- www.tanaza.com
- noviflow.com
- www.alliedtelesis.com

**Development:**
- kubernetes.docker.internal
- host.docker.internal
- api.anthropic.com (Claude API)

**Tools:**
- obsproject.com (OBS Studio)

---

## 9. CURRENT LIMITATIONS

1. **No WiFi:** No wireless access points detected
2. **No VLAN segmentation:** Single flat network (192.168.50.0/24)
3. **Unknown devices:** Two unidentified devices on network (security concern)
4. **No redundancy:** Single internet connection, single gateway
5. **No dedicated production network:** All devices on same subnet
6. **Firewall all enabled:** May need rules tuning for production workflows

---

## 10. INFRASTRUCTURE GAPS

### Missing for Content Creation:
- ❌ Dedicated streaming VLAN
- ❌ Guest network isolation
- ❌ IoT device segmentation
- ❌ Network-attached storage (NAS)
- ❌ Managed switches (likely consumer router/switch)
- ❌ QoS policies for streaming
- ❌ Bandwidth monitoring tools
- ❌ Network redundancy/failover
- ❌ WiFi coverage
- ❌ IP camera network

---

## 11. STRENGTHS

✅ **10 Gbps Ethernet** - Excellent local bandwidth for video editing
✅ **Low latency** - Sub-millisecond gateway, 12ms internet
✅ **Google DNS** - Reliable, fast DNS resolution
✅ **Docker/WSL ready** - Virtualization infrastructure present
✅ **Network stability** - Consistent connectivity

---

## 12. RECOMMENDATIONS

### Immediate (Phase 1):
1. Identify unknown devices (192.168.50.112, 192.168.50.97)
2. Document gateway/router make/model and capabilities
3. Test actual ISP upload/download speeds
4. Implement network monitoring (PRTG, LibreNMS)

### Short-term (Phase 2):
1. Add managed switch for VLAN segmentation
2. Deploy NAS for video editing workflows
3. Implement QoS for streaming priority
4. Add WiFi access points

### Long-term (Phase 3):
1. Dual WAN for redundancy
2. Dedicated streaming/production network
3. Security camera network
4. Full network monitoring suite

---

## 13. NETWORK EXPANSION PATH

**Current State:**
- Single flat network
- Consumer-grade infrastructure
- 2-4 devices total

**Target State (DeadManAI Production):**
- Multi-VLAN segmented network
- Managed infrastructure
- Dedicated streaming, storage, security networks
- 10+ devices (cameras, NAS, workstations, encoders)

---

**Document Status:** BASELINE ESTABLISHED
**Next Update:** After infrastructure upgrades
