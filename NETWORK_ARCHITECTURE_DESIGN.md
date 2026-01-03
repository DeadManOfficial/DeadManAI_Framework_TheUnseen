# DEADMANAI NETWORK ARCHITECTURE DESIGN

## Document Metadata

| Attribute | Value |
|-----------|-------|
| **Document ID** | NETWORK_ARCH_V1 |
| **Title** | DeadManAI Network Architecture - Complete Infrastructure Design |
| **Classification** | Infrastructure Design / Implementation Roadmap |
| **Last Updated** | 2026-01-03 |
| **Status** | DESIGN COMPLETE - READY FOR IMPLEMENTATION |
| **Version** | 1.0.0 |
| **Author** | Claude Code / DeadManAI Infrastructure |
| **Based On** | 100 Networking Research Agents + Current Network Baseline |

---

## EXECUTIVE SUMMARY

This document provides a comprehensive network architecture design for **DeadManAI // The Unseen** - a faceless YouTube content creation operation requiring high-bandwidth, low-latency infrastructure for 4K video production, cloud rendering, multi-platform streaming, and NAS-based workflows.

**Design Philosophy:** Human-directed infrastructure with maximum retention velocity (quality content delivery), asset reusability (lasting infrastructure value), and scalability from small studio to multi-creator operation.

**Key Technical Requirements:**
- **Streaming Infrastructure:** NDI network for camera feeds, OBS optimization, multi-platform simultaneous upload
- **Video Production:** 10GbE storage network for 4K editing workflows, NAS with 50TB+ capacity
- **Cloud Integration:** YouTube uploads (100+ Mbps sustained), cloud rendering API access, CDN integration
- **Security:** VLAN segmentation (Production/IoT/Guest/Management), firewall rules, VPN access
- **Scalability:** Small (1 creator) → Medium (3-5 creators) → Large (10+ creators + remote collaborators)

**Total Investment Estimate:**
- **Small (Phase 1):** $6,521
- **Medium (Phase 2):** $10,101 total
- **Large (Phase 3):** $19,139 total

**Current Network State (Baseline):**
- IP Address: 192.168.50.106/24
- Gateway: 192.168.50.1
- Primary Interface: Ethernet 2 (10 Gbps, Active)
- Network Type: Single flat network (no VLANs)
- Infrastructure Gaps: No WiFi, no VLAN segmentation, no NAS, no dedicated streaming network

---

## TABLE OF CONTENTS

1. [Physical Topology](#1-physical-topology)
2. [VLAN Segmentation](#2-vlan-segmentation)
3. [IP Addressing Scheme](#3-ip-addressing-scheme)
4. [Internet Connectivity](#4-internet-connectivity)
5. [WiFi Design](#5-wifi-design)
6. [Storage Network](#6-storage-network)
7. [Streaming Infrastructure](#7-streaming-infrastructure)
8. [Security Layers](#8-security-layers)
9. [Cloud Integration](#9-cloud-integration)
10. [Scalability Path](#10-scalability-path)
11. [Hardware Bill of Materials](#11-hardware-bill-of-materials)
12. [Configuration Templates](#12-configuration-templates)
13. [Implementation Roadmap](#13-implementation-roadmap)
14. [Network Diagrams](#14-network-diagrams)
15. [Risk Mitigation & Disaster Recovery](#15-risk-mitigation--disaster-recovery)
16. [Performance Benchmarks](#16-performance-benchmarks--validation)
17. [DeadManAI Integration](#17-integration-with-deadmanai-workflows)
18. [Next Steps](#18-next-steps--recommendations)

---

## 1. PHYSICAL TOPOLOGY

### 1.1 Network Hierarchy

```
INTERNET
   │
   ├─── ISP Modem (Bridged Mode)
   │
   ├─── Router/Firewall (pfSense / UniFi Gateway)
   │       │
   │       ├─── WAN (ISP uplink)
   │       ├─── LAN1 (Production VLAN trunk)
   │       ├─── LAN2 (IoT VLAN)
   │       └─── LAN3 (Guest VLAN)
   │
   ├─── Core Switch (10GbE Managed L3)
   │       │
   │       ├─── Uplink: 10GbE to Router
   │       ├─── Trunk: Production VLANs (10/20/30/99)
   │       ├─── NAS: 10GbE storage network
   │       └─── Access Switch: 2.5GbE uplink
   │
   ├─── Access Switch (2.5GbE PoE+)
   │       │
   │       ├─── WiFi APs (WiFi 7, PoE+)
   │       ├─── Workstations (2.5GbE)
   │       ├─── Cameras (NDI, PoE)
   │       └─── IoT devices (1GbE)
   │
   ├─── NAS (Network Attached Storage)
   │       │
   │       ├─── 10GbE primary link (VLAN 10)
   │       ├─── 1GbE management link (VLAN 99)
   │       └─── RAID 10 storage pool (50TB+)
   │
   └─── WiFi Access Points (WiFi 7)
           │
           ├─── AP1: Production Studio (VLAN 10/20)
           ├─── AP2: Office/Edit Suite (VLAN 10/20)
           └─── AP3: Guest/IoT coverage (VLAN 30/40)
```

### 1.2 Rack Layout (12U Half-Rack)

```
┌─────────────────────────────────┐
│  1U: Patch Panel (24-port Cat6a) │
├─────────────────────────────────┤
│  2U: Core Switch (10GbE L3)     │
├─────────────────────────────────┤
│  3U: Access Switch (2.5GbE PoE) │
├─────────────────────────────────┤
│  4U: Router/Firewall Appliance  │
├─────────────────────────────────┤
│  5U: NAS (4-bay rackmount)      │
├─────────────────────────────────┤
│  6U: UPS (1500VA rackmount)     │
├─────────────────────────────────┤
│  7U: Cable Management           │
├─────────────────────────────────┤
│  8U: Future Expansion           │
├─────────────────────────────────┤
│  9U: Future Expansion           │
├─────────────────────────────────┤
│ 10U: Future Expansion           │
├─────────────────────────────────┤
│ 11U: Future Expansion           │
├─────────────────────────────────┤
│ 12U: Power Distribution (PDU)   │
└─────────────────────────────────┘
```

### 1.3 Cabling Standards

| Connection Type | Cable Standard | Distance Limit | Speed |
|----------------|----------------|----------------|-------|
| **Core Switch ↔ Router** | DAC (Direct Attach Copper) | 5m | 10GbE |
| **Core Switch ↔ NAS** | Cat6a or Fiber (SFP+) | 55m (copper) / 300m (fiber) | 10GbE |
| **Core Switch ↔ Access Switch** | Cat6a | 100m | 2.5GbE |
| **Access Switch ↔ APs** | Cat6a (PoE+) | 100m | 2.5GbE |
| **Access Switch ↔ Workstations** | Cat6a | 100m | 2.5GbE |
| **Access Switch ↔ Cameras** | Cat6 (PoE) | 100m | 1GbE |

**Rationale for Cat6a:**
- Future-proof for 10GbE expansion
- Supports 2.5GbE at full 100m distance
- Compatible with PoE++ (90W) for WiFi 7 APs
- Standard cost differential vs Cat6 is minimal (~10-15%)

---

## 2. VLAN SEGMENTATION

### 2.1 VLAN Design Philosophy

**Segmentation Strategy:**
1. **Isolation:** Separate production traffic from IoT/guest to prevent interference
2. **Security:** Limit lateral movement (compromised IoT device cannot access NAS)
3. **QoS:** Apply traffic prioritization per VLAN (Production = highest priority)
4. **Scalability:** Room for expansion (VLANs 50-90 reserved for future use)

### 2.2 VLAN Assignments

| VLAN ID | Name | Purpose | Subnet | Gateway | DHCP Pool | Priority |
|---------|------|---------|--------|---------|-----------|----------|
| **10** | PRODUCTION | Production workstations, editing PCs, NAS access | 10.0.10.0/24 | 10.0.10.1 | 10.0.10.100-200 | CRITICAL |
| **20** | STREAMING | Cameras, streaming PC, NDI devices, OBS | 10.0.20.0/24 | 10.0.20.1 | 10.0.20.100-150 | CRITICAL |
| **30** | IOT | Smart lights, sensors, non-critical automation | 10.0.30.0/24 | 10.0.30.1 | 10.0.30.50-200 | LOW |
| **40** | GUEST | Guest WiFi, isolated internet access only | 10.0.40.0/24 | 10.0.40.1 | 10.0.40.10-200 | MEDIUM |
| **99** | MGMT | Network management (switch, AP, router access) | 10.0.99.0/24 | 10.0.99.1 | 10.0.99.10-50 | HIGH |

**Reserved VLANs:**
- **50-60:** Future creator expansion (remote offices, satellite studios)
- **70-80:** Lab/testing environments
- **90-95:** VPN users, remote access

### 2.3 Inter-VLAN Routing Rules

| Source VLAN | Destination VLAN | Access | Rationale |
|-------------|------------------|--------|-----------|
| PRODUCTION (10) | STREAMING (20) | ALLOW | Editing PCs need NDI camera feeds |
| PRODUCTION (10) | IOT (30) | ALLOW (limited) | Control studio lights, teleprompters |
| PRODUCTION (10) | GUEST (40) | DENY | Security isolation |
| STREAMING (20) | PRODUCTION (10) | ALLOW | Cameras send footage to NAS |
| IOT (30) | PRODUCTION (10) | DENY | Compromised IoT cannot access production assets |
| IOT (30) | STREAMING (20) | DENY | IoT isolation from streaming network |
| GUEST (40) | ALL | DENY (except internet) | Guest traffic isolated, internet-only |
| MGMT (99) | ALL | ALLOW | Management network needs full access for troubleshooting |

**Firewall Rule Implementation:**
- Default deny between VLANs
- Explicit allow rules for documented workflows
- Logging enabled for denied inter-VLAN traffic (security auditing)

---

## 3. IP ADDRESSING SCHEME

### 3.1 Subnet Allocation

**VLAN 10 - PRODUCTION (10.0.10.0/24)**
```
10.0.10.1        Gateway (Router interface)
10.0.10.2        NAS primary interface
10.0.10.3-10     Reserved for future servers (render farm, backup NAS)
10.0.10.11-50    Static IPs for production workstations
10.0.10.51-99    Reserved for future expansion
10.0.10.100-200  DHCP pool for production devices
10.0.10.201-254  Reserved
```

**VLAN 20 - STREAMING (10.0.20.0/24)**
```
10.0.20.1        Gateway
10.0.20.10       Streaming PC (OBS primary)
10.0.20.11-20    NDI cameras (static IPs)
10.0.20.21-30    Audio interfaces, capture cards
10.0.20.31-50    Reserved for future streaming equipment
10.0.20.100-150  DHCP pool
```

**VLAN 30 - IOT (10.0.30.0/24)**
```
10.0.30.1        Gateway
10.0.30.10-49    Static IPs for critical IoT (studio lights, teleprompter)
10.0.30.50-200   DHCP pool
```

**VLAN 40 - GUEST (10.0.40.0/24)**
```
10.0.40.1        Gateway
10.0.40.10-200   DHCP pool (full range for guests)
```

**VLAN 99 - MGMT (10.0.99.0/24)**
```
10.0.99.1        Gateway
10.0.99.2        Core Switch management
10.0.99.3        Access Switch management
10.0.99.4-6      WiFi AP management IPs
10.0.99.7        NAS management interface (secondary)
10.0.99.8        Router management
10.0.99.10-50    DHCP pool for management devices
```

### 3.2 DNS Configuration

**Internal DNS (Router/Pi-Hole):**
```
nas.local           → 10.0.10.2
streaming.local     → 10.0.20.10
core-switch.local   → 10.0.99.2
ap-studio.local     → 10.0.99.4
ap-office.local     → 10.0.99.5
ap-guest.local      → 10.0.99.6
```

**External DNS (Cloudflare):**
- Primary: 1.1.1.1
- Secondary: 1.0.0.1
- DNS-over-HTTPS enabled for privacy

### 3.3 DHCP Lease Times

| VLAN | Lease Time | Rationale |
|------|-----------|-----------|
| PRODUCTION | 7 days | Stable devices, minimize DHCP churn |
| STREAMING | 7 days | Fixed equipment, static-like behavior |
| IOT | 24 hours | Frequent reconnects, shorter leases acceptable |
| GUEST | 4 hours | High turnover, reclaim IPs quickly |
| MGMT | 7 days | Infrastructure devices rarely change |

---

## 4. INTERNET CONNECTIVITY

### 4.1 ISP Requirements

**Minimum Specifications:**

| Requirement | Target | Rationale |
|-------------|--------|-----------|
| **Download Speed** | 500 Mbps minimum, 1 Gbps recommended | 4K video downloads, cloud rendering asset retrieval |
| **Upload Speed** | 100 Mbps minimum, 300+ Mbps ideal | YouTube uploads (4K 50 Mbps), cloud backups, multi-platform streaming |
| **Latency** | <20ms to major CDNs | Real-time collaboration, cloud rendering responsiveness |
| **Jitter** | <5ms | Streaming stability (OBS to YouTube/Twitch) |
| **Connection Type** | Fiber (FTTH) preferred, Cable (DOCSIS 3.1) acceptable | Symmetrical speeds for uploads |

**Bandwidth Planning:**

**Scenario 1: Single 4K Upload to YouTube**
- File size: 10GB (15-minute video)
- Target upload time: 15 minutes
- Required upload speed: ~90 Mbps
- **Recommendation:** 100 Mbps upload minimum

**Scenario 2: Simultaneous Multi-Platform Streaming**
- YouTube: 15-20 Mbps (4K 30fps)
- Twitch: 8-10 Mbps (1080p 60fps)
- TikTok: 5-8 Mbps (1080p)
- Total: ~40 Mbps sustained
- **Recommendation:** 100 Mbps upload provides 2.5x overhead

**Scenario 3: Cloud Rendering Upload**
- 100GB project files to AWS/GCP
- Target transfer time: 2 hours
- Required upload: ~115 Mbps
- **Recommendation:** 300 Mbps upload for professional workflows

### 4.2 Failover Strategy

**Option 1: Cellular Backup (Recommended for Small/Medium)**

| Component | Model | Monthly Cost | Specs |
|-----------|-------|--------------|-------|
| **Cellular Modem** | Cradlepoint IBR200 or Peplink MAX BR1 Mini | $300-500 (one-time) | LTE Cat-6, dual SIM |
| **Data Plan** | Business unlimited (T-Mobile, Verizon) | $60-100/month | 50-100GB high-speed, then throttled |
| **Failover Mode** | Auto-detect WAN down → switch to LTE | N/A | 30-60 second failover time |

**Pros:**
- Low upfront cost
- No additional ISP contract
- Works during power outages (with UPS)

**Cons:**
- Lower speeds (20-50 Mbps typical)
- Data caps on most plans
- Not suitable for large uploads

**Option 2: Dual WAN (Recommended for Large)**

| Component | ISP | Monthly Cost | Specs |
|-----------|-----|--------------|-------|
| **Primary WAN** | Fiber (AT&T, Verizon, Local ISP) | $80-150/month | 1 Gbps / 1 Gbps |
| **Secondary WAN** | Cable (Comcast, Spectrum) | $50-100/month | 500 Mbps / 50 Mbps |
| **Load Balancing** | pfSense multi-WAN or UniFi load balancing | N/A | Weighted round-robin |

**Pros:**
- Near-instant failover
- Load balancing for higher aggregate bandwidth
- Full-speed backup connection

**Cons:**
- Higher monthly cost ($130-250/month)
- Requires dual-WAN capable router
- Two ISP accounts to manage

**Recommendation:**
- **Small:** Single ISP + cellular backup
- **Medium:** Single ISP + cellular backup (upgrade to dual WAN if budget allows)
- **Large:** Dual WAN fiber + cable

### 4.3 ISP Modem Configuration

**Mode:** Bridged (passthrough)
- ISP modem acts as transparent gateway
- Router/firewall handles all routing, NAT, DHCP
- Enables advanced features (VPN, QoS, firewall rules)

**Why Not Router Mode?**
- Double NAT issues (port forwarding breaks)
- Limited QoS capabilities on ISP-provided routers
- Cannot implement VLAN segmentation
- Security: single point of failure if ISP router compromised

---

## 5. WIFI DESIGN

### 5.1 WiFi 7 Access Point Strategy

**Reference Research:** R36 (WiFi 7 Comprehensive Analysis), R36 (QoS/WMM Streaming Quality)

**Key Requirements:**
- **Multi-Link Operation (MLO):** 47% throughput improvement for simultaneous 6GHz + 5GHz connections
- **6 GHz Band:** Clean spectrum for production traffic (cameras, laptops)
- **WMM QoS:** Voice/video traffic prioritization for streaming
- **High Client Density:** Support 30+ simultaneous devices per AP

### 5.2 Access Point Placement

**AP1: Production Studio**
- **Location:** Ceiling-mounted, center of studio space
- **Coverage:** 1500 sq ft (studio, recording area)
- **VLANs:** 10 (Production), 20 (Streaming), 99 (Management)
- **Power:** PoE+ (25.5W minimum, 802.3at)
- **Clients:** 10-15 (cameras, laptops, tablets, phones)

**AP2: Office/Edit Suite**
- **Location:** Ceiling or high wall-mount, center of office
- **Coverage:** 800 sq ft (editing workstations, desk area)
- **VLANs:** 10 (Production), 40 (Guest), 99 (Management)
- **Power:** PoE+ (25.5W)
- **Clients:** 5-10 (workstations, personal devices)

**AP3: Guest/Common Area**
- **Location:** Coverage for lobby, waiting area
- **Coverage:** 600 sq ft
- **VLANs:** 30 (IoT), 40 (Guest), 99 (Management)
- **Power:** PoE+ (25.5W)
- **Clients:** 10-20 (guest devices, IoT sensors)

### 5.3 Channel Planning

**6 GHz Band (Production VLAN)**
```
AP1: Channel 31 (320 MHz width, 6425-6745 MHz)
AP2: Channel 63 (320 MHz width, 6745-7065 MHz)
AP3: Disabled (guest traffic doesn't need 6 GHz)
```

**5 GHz Band (Fallback + Legacy)**
```
AP1: Channel 36 (160 MHz width, 5150-5330 MHz)
AP2: Channel 100 (160 MHz width, 5470-5650 MHz)
AP3: Channel 149 (80 MHz width, 5725-5805 MHz)
```

**2.4 GHz Band (Legacy IoT)**
```
AP1: Channel 1 (20 MHz width)
AP2: Channel 6 (20 MHz width)
AP3: Channel 11 (20 MHz width)
```

**Power Levels:**
- 6 GHz: 20 dBm (high power, clean spectrum)
- 5 GHz: 17 dBm (medium power, avoid co-channel interference)
- 2.4 GHz: 14 dBm (low power, minimize overlap)

### 5.4 SSID Configuration

| SSID Name | VLAN | Security | Bands | Purpose | Band Steering |
|-----------|------|----------|-------|---------|---------------|
| **DeadManAI_Prod** | 10 | WPA3-Enterprise (or WPA3-Personal) | 6GHz, 5GHz | Production devices only | Prefer 6GHz |
| **DeadManAI_Stream** | 20 | WPA3-Personal | 6GHz, 5GHz | Cameras, streaming gear | Force 6GHz if capable |
| **DeadManAI_Guest** | 40 | WPA3-Personal (or open w/ captive portal) | 5GHz, 2.4GHz | Guest internet access | Prefer 5GHz |
| **DeadManAI_IoT** | 30 | WPA2-Personal | 2.4GHz only | Legacy IoT devices | N/A |
| **DeadManAI_Mgmt** | 99 | WPA3-Enterprise | 5GHz only | Management interface (hidden) | N/A |

**Band Steering Configuration:**
- **6 GHz Preferred:** Devices supporting WiFi 7 automatically steered to 6 GHz (lower latency, higher throughput)
- **5 GHz Fallback:** WiFi 6/6E devices use 5 GHz
- **2.4 GHz Last Resort:** Only for legacy IoT or extremely weak signal scenarios

### 5.5 QoS Configuration (WMM)

**Enable WMM on ALL SSIDs** (per R36 QoS research)

**Access Category Mapping:**

| Traffic Type | WMM Category | DSCP Marking | Priority | Use Case |
|--------------|--------------|--------------|----------|----------|
| **Voice (VoIP)** | AC_VO | EF (46) | CRITICAL | Voice calls, real-time audio |
| **Video (Streaming)** | AC_VI | AF41 (34) | HIGH | NDI camera feeds, OBS streaming |
| **Best Effort (Web)** | AC_BE | 0 (default) | MEDIUM | Web browsing, general internet |
| **Background (Bulk)** | AC_BK | CS1 (8) | LOW | File transfers, backups |

**EDCA Parameters (Per R36 QoS Standards):**

```
# Voice (AC_VO) - Lowest latency
AIFSN: 2 (shortest wait time)
CWmin: 3 (narrow contention window)
CWmax: 7
TXOP: 1.504 ms

# Video (AC_VI) - Second priority
AIFSN: 2
CWmin: 7
CWmax: 15
TXOP: 3.008 ms

# Best Effort (AC_BE) - Default
AIFSN: 3
CWmin: 15
CWmax: 1023
TXOP: 0 ms

# Background (AC_BK) - Lowest priority
AIFSN: 7 (longest wait time)
CWmin: 15
CWmax: 1023
TXOP: 0 ms
```

**Traffic Prioritization Results (Per R36):**
- Voice/video latency reduction: 93% downlink, 99% uplink (WiFi 6+ OFDMA)
- Jitter reduction: 85%+ (critical for streaming quality)
- Packet loss: <0.1% for AC_VO/AC_VI in dense deployments

---

## 6. STORAGE NETWORK

### 6.1 NAS Requirements

**Workload Analysis:**

| Workflow | Bandwidth Requirement | Storage Requirement |
|----------|----------------------|---------------------|
| **4K 30fps Editing** | 400 MB/s read (ProRes 422) | 10-15 GB per minute of footage |
| **4K 60fps Editing** | 800 MB/s read (ProRes 422 HQ) | 20-30 GB per minute |
| **Multi-cam 4K** | 1200+ MB/s read (3-4 camera angles) | 40-60 GB per minute |
| **Cloud Backup** | 100 MB/s write sustained | Full project archive |
| **Asset Library** | Random read (thumbnails, B-roll) | 10-50TB library |

**NAS Specifications:**

| Component | Specification | Rationale |
|-----------|--------------|-----------|
| **Network Interface** | Dual 10GbE (LACP bonding) | Aggregate 2.5 GB/s throughput for multi-client access |
| **CPU** | Intel Xeon or AMD Ryzen (4+ cores) | Transcoding, Plex streaming, VM hosting |
| **RAM** | 32GB minimum (64GB recommended) | Caching, ZFS/BTRFS metadata, Docker containers |
| **Storage Capacity** | 50TB raw (40TB usable after RAID 10) | 3-6 months of active projects + asset library |
| **RAID Level** | RAID 10 (mirrored striping) | High performance + redundancy (vs RAID 5/6 slower writes) |
| **Hot Spare** | 1 spare drive | Automatic rebuild on failure |
| **Backup Strategy** | 3-2-1 (3 copies, 2 media types, 1 offsite) | Critical project protection |

### 6.2 NAS Hardware Recommendation

**Option 1: Synology RackStation RS1221+ (Recommended Small/Medium)**

| Spec | Value |
|------|-------|
| **Bays** | 8 x 3.5" / 2.5" SATA |
| **CPU** | AMD Ryzen V1500B (4-core) |
| **RAM** | 4GB (expandable to 32GB) |
| **Network** | 4 x 1GbE (upgradeable to 10GbE via PCIe card) |
| **Price** | $1,000-1,200 (bare unit) |

**Upgrade Path:**
- Add Synology E10G21-F2 dual-port 10GbE PCIe card: $550
- Total: $1,550-1,750

**Option 2: QNAP TS-873AU (Best Performance/Value)**

| Spec | Value |
|------|-------|
| **Bays** | 8 x 3.5" SATA |
| **CPU** | AMD Ryzen V1500B (4-core, 2.2 GHz) |
| **RAM** | 8GB (expandable to 64GB) |
| **Network** | 2 x 2.5GbE + 2 x 10GbE SFP+ (built-in) |
| **Price** | $1,400-1,600 |

**Pros:** Native 10GbE, no expansion card needed, slightly faster CPU

**Option 3: TrueNAS Custom Build (Large/Advanced)**

| Component | Model | Price |
|-----------|-------|-------|
| **Case** | Silverstone CS382 (8-bay rackmount) | $450 |
| **Motherboard** | Supermicro X11SCL-IF (Intel C242) | $300 |
| **CPU** | Intel Xeon E-2146G (6-core) | $400 |
| **RAM** | 64GB DDR4 ECC | $250 |
| **Network** | Intel X540-T2 dual 10GbE | $200 |
| **Power Supply** | 650W 80+ Platinum | $150 |
| **Total** | Bare build | $1,750 |

**Pros:** Maximum performance, ZFS native support, open-source TrueNAS SCALE
**Cons:** Requires technical expertise, no commercial support

**Recommendation:**
- **Small:** Synology RS1221+ (ease of use, commercial support)
- **Medium/Large:** QNAP TS-873AU (best performance/price ratio) ← **SELECTED FOR PHASE 1**

### 6.3 Drive Configuration

**Drive Selection:**

| Use Case | Drive Model | Capacity | Quantity | RAID | Usable | Price/Drive |
|----------|-------------|----------|----------|------|--------|-------------|
| **Performance Tier** | WD Red Pro 12TB (7200 RPM) | 12TB | 4 drives | RAID 10 | 24TB | $320 |
| **Capacity Tier** | Seagate Exos X18 18TB | 18TB | 4 drives | RAID 10 | 36TB | $380 |
| **Hot Spare** | Matching drive | 12/18TB | 1 drive | N/A | 0TB | $320-380 |

**Total Drive Costs:**
- **Performance Config:** 4x WD Red Pro 12TB + 1 spare = $1,600 ← **SELECTED FOR PHASE 1**
- **Capacity Config:** 4x Seagate Exos 18TB + 1 spare = $1,900

### 6.4 Network Configuration

**10GbE Connection Topology:**

```
NAS (10.0.10.2)
  │
  ├─── Port 1: 10GbE to Core Switch (VLAN 10 production)
  └─── Port 2: 1GbE to Core Switch (VLAN 99 management)
```

**LACP Bonding (Future Expansion):**
- If NAS has dual 10GbE ports, enable LACP (Link Aggregation Control Protocol)
- Aggregate bandwidth: 20 Gbps (theoretical 2.5 GB/s)
- Provides redundancy: single link failure doesn't break connection

**SMB/NFS Protocol:**
- **SMB3:** Windows/Mac compatibility (preferred for mixed environment)
- **NFS:** Linux workstations (lower overhead, higher performance)
- **Recommendation:** Enable both, use SMB3 for primary access

**Performance Tuning:**
- Enable SMB3 Multichannel (multiple connections per client)
- Disable SMB1 (security risk, deprecated)
- Set MTU to 9000 (jumbo frames for 10GbE network)

---

## 7. STREAMING INFRASTRUCTURE

### 7.1 NDI Network Architecture

**NDI (Network Device Interface) Overview:**
- Protocol for sending video over IP networks
- Standard: NDI 5 (H.264/H.265/HEVC encoding)
- Bandwidth: 100-150 Mbps per 1080p60 camera, 250-400 Mbps per 4K30

**Network Requirements:**

| NDI Stream | Resolution | Bandwidth | Latency Target |
|------------|-----------|-----------|----------------|
| **Camera 1** | 1080p60 | 125 Mbps | <60ms glass-to-glass |
| **Camera 2** | 1080p60 | 125 Mbps | <60ms |
| **Camera 3** | 4K30 | 250 Mbps | <100ms |
| **Total** | Multi-cam | 500 Mbps | Low jitter (<5ms) |

**Dedicated VLAN 20 (Streaming):**
- Isolated from production traffic
- QoS priority: AC_VI (Video)
- MTU: 9000 (jumbo frames reduce CPU overhead)

### 7.2 Streaming PC Specifications

| Component | Specification | Rationale |
|-----------|--------------|-----------|
| **CPU** | Intel i7-13700K or AMD Ryzen 9 7900X | 16+ threads for OBS encoding + NDI processing |
| **GPU** | NVIDIA RTX 4070 (12GB VRAM) | NVENC H.264/HEVC hardware encoding |
| **RAM** | 32GB DDR5 | Multi-stream buffering, browser sources |
| **Storage** | 1TB NVMe SSD (local) + 10GbE NAS link | Fast project files + network asset access |
| **Network** | 10GbE NIC or 2.5GbE (minimum) | NDI ingest + multi-platform upload |

**Network Interface:**
- **Primary:** 10GbE to Core Switch (VLAN 20) - NDI camera feeds
- **Secondary:** 1GbE to Core Switch (VLAN 10) - Internet upload path

### 7.3 OBS Configuration

**Output Settings:**

| Platform | Bitrate | Resolution | FPS | Encoder | Keyframe |
|----------|---------|-----------|-----|---------|----------|
| **YouTube (Primary)** | 15-20 Mbps | 4K (3840x2160) | 30 | NVENC HEVC | 2s |
| **Twitch (Secondary)** | 8 Mbps | 1080p (1920x1080) | 60 | NVENC H.264 | 2s |
| **Recording (Local)** | 50 Mbps | 4K | 60 | NVENC HEVC | 2s |

**Total Upload Bandwidth:** 15 + 8 = 23 Mbps (with 2x overhead → 50 Mbps upload recommended)

**Network Optimization:**
- **Bind to Interface:** Force OBS to use 1GbE upload interface (VLAN 10)
- **Dynamic Bitrate:** Enable CBR (Constant Bitrate) for stable streaming
- **Network Buffering:** 20 seconds (protects against momentary ISP jitter)

### 7.4 Upload Path Optimization

**YouTube Upload Workflow:**

```
Local Recording (NAS 10.0.10.2)
   │
   ├─── OBS saves to NAS via 10GbE (50 Mbps write)
   │
   ├─── Editing PC retrieves from NAS via 10GbE (multi-GB/s read)
   │
   ├─── Export final video to NAS (10GbE write)
   │
   └─── Upload script monitors NAS folder
         │
         └─── Uploads to YouTube via WAN (100+ Mbps)
```

**Automation Script (Python/Bash):**
```bash
#!/bin/bash
# YouTube Auto-Upload Script
# Place in cron: */15 * * * * /path/to/upload.sh

UPLOAD_DIR="/mnt/nas/youtube-ready"
for video in "$UPLOAD_DIR"/*.mp4; do
    youtube-upload \
        --title="$(basename "$video" .mp4)" \
        --category="22" \
        --privacy="unlisted" \
        --client-secrets=client_secrets.json \
        --credentials-file=credentials.json \
        "$video"

    # Move to archive after successful upload
    mv "$video" "/mnt/nas/youtube-archive/"
done
```

### 7.5 Multi-Platform Streaming (Restream.io / Nginx RTMP)

**Option 1: Restream.io (Recommended Small/Medium)**

| Feature | Details |
|---------|---------|
| **Service** | Cloud-based multi-streaming |
| **Cost** | $16/month (Standard) |
| **Platforms** | YouTube, Twitch, Facebook, TikTok (30+ simultaneous) |
| **Bandwidth** | OBS sends single stream to Restream (saves upload bandwidth) |

**Configuration:**
- OBS → Restream RTMP ingest (15 Mbps upload)
- Restream duplicates stream to all platforms
- Net upload: 15 Mbps (vs 40+ Mbps direct multi-streaming)

**Option 2: Self-Hosted Nginx RTMP (Large/Advanced)**

**Server Requirements:**
- VM on NAS or dedicated server
- Nginx with RTMP module
- 4GB RAM, 2 vCPU minimum

**Configuration:**
```nginx
rtmp {
    server {
        listen 1935;
        chunk_size 4096;

        application live {
            live on;
            record off;

            # YouTube RTMP
            push rtmp://a.rtmp.youtube.com/live2/YOUR_STREAM_KEY;

            # Twitch RTMP
            push rtmp://live.twitch.tv/app/YOUR_STREAM_KEY;

            # TikTok RTMP
            push rtmp://live.tiktok.com/live/YOUR_STREAM_KEY;
        }
    }
}
```

**Pros:** No monthly fee, full control, unlimited platforms
**Cons:** Requires technical setup, higher upload bandwidth (30-40 Mbps)

---

## 8. SECURITY LAYERS

### 8.1 Firewall Rules (pfSense / UniFi Gateway)

**VLAN 10 (Production) → Internet:**
```
Allow: HTTPS (443), HTTP (80)
Allow: YouTube API (port 443, destination: upload.youtube.com)
Allow: Cloud Rendering APIs (AWS, GCP, Replicate)
Allow: SSH (22) to trusted IPs only (remote access)
Deny: All other outbound
```

**VLAN 20 (Streaming) → Internet:**
```
Allow: RTMP (1935) to streaming platforms
Allow: RTMPS (443) to streaming platforms
Allow: NDI Discovery (5353 mDNS, 5960-5990 TCP)
Deny: All other outbound
```

**VLAN 30 (IoT) → Internet:**
```
Allow: HTTP/HTTPS for firmware updates (specific domains only)
Allow: NTP (123) for time sync
Deny: All other outbound (prevents C2 communication if compromised)
```

**VLAN 40 (Guest) → Internet:**
```
Allow: HTTP/HTTPS (all destinations)
Allow: DNS (53)
Rate Limit: 50 Mbps per client (prevents bandwidth hogging)
Deny: All RFC1918 private IPs (prevents lateral movement)
```

**VLAN 99 (Management) → All:**
```
Allow: SSH (22), HTTPS (443) for management interfaces
Allow: SNMP (161/162) for monitoring
Log: All connections for audit trail
```

### 8.2 VPN Access (Remote Creators / Collaboration)

**VPN Type:** WireGuard (modern, fast, secure)

**Use Cases:**
- Remote editors accessing NAS
- Collaboration with external creators
- Secure access while traveling

**VPN Configuration:**

| Parameter | Value |
|-----------|-------|
| **Protocol** | WireGuard |
| **VPN Subnet** | 10.0.90.0/24 (VLAN 90) |
| **Encryption** | ChaCha20-Poly1305 |
| **Authentication** | Pre-shared keys (per user) |
| **Speed** | Near-line speed (minimal overhead) |

**Firewall Rules for VPN Users:**
```
VLAN 90 (VPN) → VLAN 10 (Production): Allow NAS access, deny workstations
VLAN 90 (VPN) → VLAN 20 (Streaming): Deny (no need for remote NDI access)
VLAN 90 (VPN) → Internet: Allow
```

**Bandwidth Allocation:**
- QoS priority: MEDIUM (below production, above guest)
- Rate limit: 100 Mbps per VPN client (prevents single user saturating WAN)

### 8.3 Intrusion Detection (Suricata / Snort)

**IDS Deployment:**

| Component | Placement | Ruleset |
|-----------|-----------|---------|
| **Suricata** | Inline on router (pfSense package) | Emerging Threats Open |
| **Monitoring** | VLAN 30 (IoT), VLAN 40 (Guest) | High sensitivity |
| **Alerts** | Email + syslog to management server | Critical events only |

**Alert Rules:**
- Malware C2 communication detection
- Port scanning attempts
- Brute-force SSH/RDP attempts
- Unusual traffic patterns (e.g., IoT device connecting to non-standard ports)

### 8.4 Network Monitoring (SNMP / Grafana)

**Metrics Collection:**

| Metric | Source | Frequency | Retention |
|--------|--------|-----------|-----------|
| **Interface Utilization** | Switches, Router | 1 minute | 90 days |
| **WiFi Client Count** | Access Points | 5 minutes | 30 days |
| **NAS Performance** | NAS SNMP | 1 minute | 60 days |
| **Internet Bandwidth** | Router WAN interface | 30 seconds | 180 days |

**Dashboard (Grafana):**
- Real-time bandwidth graphs
- WiFi client distribution per VLAN
- NAS read/write IOPS
- Alert history (IDS events, high latency)

---

## 9. CLOUD INTEGRATION

### 9.1 YouTube Upload Optimization

**Target Performance:**
- 10GB 4K video upload: 15 minutes (target)
- Required upload speed: ~90 Mbps sustained

**Upload Path:**

```
NAS (10.0.10.2) → Router (QoS priority HIGH) → ISP (100+ Mbps upload) → YouTube CDN
```

**QoS Marking:**
- DSCP: AF31 (High priority bulk transfer)
- WMM: AC_BE (Best Effort, but elevated priority on router)

**Upload Script Optimization:**
```python
# youtube-upload configuration
--rate-limit=15M  # Limit to 15 MB/s (120 Mbps) to leave headroom
--retries=5       # Retry failed chunks
--timeout=300     # 5-minute timeout per chunk
--chunk-size=8M   # 8MB chunks for resumability
```

### 9.2 Cloud Rendering Integration

**Services:**
- **RunwayML:** AI video generation, green screen removal
- **Replicate:** Model hosting for video processing
- **AWS Elastic Transcoder:** Batch video transcoding

**Network Requirements:**

| Service | Upload Requirement | Download Requirement | Latency Sensitivity |
|---------|-------------------|---------------------|---------------------|
| **RunwayML** | 50-100 MB per job (1-5 seconds) | 200-500 MB result (10-30 seconds) | Low |
| **Replicate** | 100-500 MB input | 100-1000 MB output | Medium |
| **AWS Transcoder** | 1-10 GB batch upload | 1-10 GB batch download | Low (async) |

**Optimization:**
- Schedule large uploads during off-hours (2 AM - 6 AM)
- Use AWS Direct Connect or CloudFront for faster transfers (if budget allows)
- Cache frequently used assets locally (B-roll, templates)

### 9.3 CDN Integration (Cloudflare / AWS CloudFront)

**Use Case:** Distribute final videos for website embedding, faster global access

**Configuration:**

| Component | Service | Cost |
|-----------|---------|------|
| **CDN** | Cloudflare (free tier) | $0/month (up to 100GB transfer) |
| **Storage** | Backblaze B2 | $6/TB/month (storage) + $0.01/GB egress to Cloudflare |
| **Bandwidth** | Cloudflare Bandwidth Alliance | Free egress from Backblaze |

**Workflow:**
1. Upload final video to Backblaze B2
2. Cloudflare CDN caches video
3. Embed video on website using CDN URL
4. Net cost: $6/TB storage (no bandwidth fees via Bandwidth Alliance)

---

## 10. SCALABILITY PATH

### 10.1 Small (1 Creator) → Medium (3-5 Creators)

**Capacity Changes:**

| Component | Small | Medium | Upgrade |
|-----------|-------|--------|---------|
| **Internet Upload** | 100 Mbps | 300 Mbps | ISP tier upgrade |
| **NAS Capacity** | 24TB usable | 48TB usable | Add 4x drives, expand RAID |
| **WiFi APs** | 2 APs | 4 APs | Add AP in new studio space |
| **Switch Ports** | 24-port access switch | 48-port access switch | Replace or stack second switch |
| **VLANs** | VLANs 10/20/30/40/99 | Add VLAN 50-52 (creator isolation) | No hardware change |

**Budget:**
- Internet upgrade: $20-50/month recurring
- NAS drives: $1,200-1,600 (one-time)
- Additional APs: $400-800 (2x APs, one-time)
- Switch: $600-1,200 (if replacement needed)
- **Total:** $2,200-3,650 + recurring ISP

### 10.2 Medium (3-5 Creators) → Large (10+ Creators)

**Capacity Changes:**

| Component | Medium | Large | Upgrade |
|-----------|--------|-------|---------|
| **Internet** | 300 Mbps upload | 1 Gbps symmetrical fiber | ISP fiber upgrade |
| **NAS** | 48TB usable | Dual NAS (primary + backup) 100TB+ | Second NAS unit + replication |
| **Core Switch** | Single 10GbE switch | Stacked switches (redundancy) | Second core switch |
| **WiFi** | 4 APs | 8+ APs (multiple studios) | Double AP count |
| **VPN** | 5 users | 20+ users | VPN concentrator or cloud VPN |

**Budget:**
- Fiber upgrade: $150-300/month recurring
- Second NAS: $3,000-5,000 (with drives)
- Second core switch: $1,500-2,500
- Additional APs: $1,600-3,200 (4x APs)
- VPN infrastructure: $500-1,000
- **Total:** $6,600-11,700 + recurring ISP

### 10.3 Growth Triggers

**When to Upgrade:**

| Metric | Small Threshold | Medium Threshold | Large Threshold |
|--------|----------------|-----------------|----------------|
| **Active Projects** | 5-10 projects | 20-30 projects | 50+ projects |
| **Creators** | 1 creator | 3-5 creators | 10+ creators |
| **Upload Frequency** | 2-4 videos/week | 10-15 videos/week | 30+ videos/week |
| **NAS Utilization** | >70% capacity | >80% capacity | >90% capacity |
| **Internet Saturation** | Uploads take >30 min | Uploads queue | Multi-hour queues |

**Early Warning Indicators:**
- Upload times increasing week-over-week
- NAS performance degradation (slow read/write)
- WiFi client disconnects or high latency
- VPN users reporting slowdowns

---

## 11. HARDWARE BILL OF MATERIALS

### 11.1 Phase 1: Small Studio (1 Creator)

| Component | Model | Quantity | Unit Price | Total | Notes |
|-----------|-------|----------|-----------|-------|-------|
| **Router/Firewall** | Netgate 2100 (pfSense) | 1 | $399 | $399 | 2.5GbE WAN, pfSense Plus included |
| **Core Switch** | MikroTik CRS309-1G-8S+IN | 1 | $499 | $499 | 8x 10GbE SFP+, L3 routing |
| **Access Switch** | TP-Link TL-SG3428XMP | 1 | $399 | $399 | 24x 1GbE PoE+, 4x 2.5GbE, 2x 10GbE SFP+ |
| **WiFi AP (WiFi 7)** | TP-Link BE9300 (Omada) | 2 | $250 | $500 | Tri-band WiFi 7, 6 GHz support |
| **NAS** | QNAP TS-873AU | 1 | $1,499 | $1,499 | 8-bay, dual 10GbE, AMD Ryzen |
| **NAS Drives** | WD Red Pro 12TB | 5 | $320 | $1,600 | 4x RAID 10 + 1 spare |
| **10GbE SFP+ Cables** | DAC Twinax 3m | 3 | $25 | $75 | Core switch ↔ NAS, router |
| **Cat6a Cable (bulk)** | 1000ft spool | 1 | $200 | $200 | Workstations, APs |
| **Patch Panel** | 24-port Cat6a | 1 | $80 | $80 | Rack organization |
| **Rack** | 12U wall-mount | 1 | $150 | $150 | Half-rack |
| **UPS** | APC SMT1500RM2U | 1 | $800 | $800 | 1500VA rackmount, 10min runtime |
| **PDU** | Tripp Lite RS1215-RA | 1 | $120 | $120 | 12-outlet rackmount |
| **Misc (connectors, etc)** | Various | 1 | $200 | $200 | RJ45 connectors, cable management |
| **TOTAL PHASE 1** | | | | **$6,521** | Core infrastructure |

**Internet Service:**
- ISP: 500 Mbps down / 100 Mbps up (minimum)
- Monthly Cost: $80-120

**Total First Year:** $6,521 + ($100 x 12) = $7,721

### 11.2 Phase 2: Medium Studio (3-5 Creators)

**Incremental Upgrades:**

| Component | Model | Quantity | Unit Price | Total | Notes |
|-----------|-------|----------|----------|-------|-------|
| **Additional WiFi APs** | TP-Link BE9300 (Omada) | 2 | $250 | $500 | Coverage expansion |
| **NAS Expansion Drives** | WD Red Pro 12TB | 4 | $320 | $1,280 | Expand to 8-drive array |
| **Internet Upgrade** | 1 Gbps / 300 Mbps | N/A | +$50/month | $600/year | ISP tier upgrade |
| **Backup NAS (optional)** | Synology RS1221+ | 1 | $1,200 | $1,200 | Offsite backup target |
| **TOTAL PHASE 2** | | | | **$3,580** | + $600/year ISP |

**Total Medium Studio:** $6,521 + $3,580 = $10,101

### 11.3 Phase 3: Large Studio (10+ Creators)

**Major Upgrades:**

| Component | Model | Quantity | Unit Price | Total | Notes |
|-----------|-------|----------|----------|-------|-------|
| **Second Core Switch** | MikroTik CRS309-1G-8S+IN | 1 | $499 | $499 | Redundancy, stacking |
| **Enterprise WiFi Controller** | Omada Hardware Controller | 1 | $200 | $200 | Centralized AP management |
| **Additional APs** | TP-Link BE9300 (Omada) | 4 | $250 | $1,000 | Multi-studio coverage |
| **Enterprise NAS** | QNAP TS-1635AXU | 1 | $3,500 | $3,500 | 16-bay, quad 10GbE |
| **NAS Drives (18TB)** | Seagate Exos X18 18TB | 8 | $380 | $3,040 | 144TB raw (72TB RAID 10) |
| **Fiber Internet** | 1 Gbps symmetrical | N/A | +$100/month | $1,200/year | Business fiber |
| **VPN Concentrator** | Netgate 4100 | 1 | $799 | $799 | 50+ VPN users |
| **TOTAL PHASE 3** | | | | **$9,038** | + $1,200/year ISP |

**Total Large Studio:** $6,521 + $3,580 + $9,038 = $19,139

---

## 12. CONFIGURATION TEMPLATES

### 12.1 pfSense Firewall Configuration

**Interface Assignments:**

```
WAN: ISP uplink (DHCP or static IP)
LAN1 (VLAN 10): Production - 10.0.10.0/24
LAN2 (VLAN 20): Streaming - 10.0.20.0/24
LAN3 (VLAN 30): IoT - 10.0.30.0/24
LAN4 (VLAN 40): Guest - 10.0.40.0/24
LAN5 (VLAN 99): Management - 10.0.99.0/24
```

**DHCP Server Configuration:**

```bash
# VLAN 10 (Production)
Interface: VLAN10
Range: 10.0.10.100 - 10.0.10.200
Gateway: 10.0.10.1
DNS: 1.1.1.1, 1.0.0.1
Domain: deadmanai.local
Lease Time: 604800 (7 days)

# VLAN 20 (Streaming)
Interface: VLAN20
Range: 10.0.20.100 - 10.0.20.150
Gateway: 10.0.20.1
DNS: 1.1.1.1, 1.0.0.1
Lease Time: 604800

# VLAN 40 (Guest)
Interface: VLAN40
Range: 10.0.40.10 - 10.0.40.200
Gateway: 10.0.40.1
DNS: 1.1.1.1, 1.0.0.1
Lease Time: 14400 (4 hours)
```

**Firewall Rules (VLAN 10 - Production):**

```
# Allow Production to Internet
Pass  IPv4  VLAN10_net  *  *  443  HTTPS
Pass  IPv4  VLAN10_net  *  *  80   HTTP
Pass  IPv4  VLAN10_net  *  *  22   SSH (to trusted IPs only)

# Allow Production to Streaming (NDI access)
Pass  IPv4  VLAN10_net  VLAN20_net  *  5960-5990  NDI

# Allow Production to NAS
Pass  IPv4  VLAN10_net  10.0.10.2  *  445  SMB
Pass  IPv4  VLAN10_net  10.0.10.2  *  2049 NFS

# Block Production to Guest/IoT
Block  IPv4  VLAN10_net  VLAN30_net  *  *
Block  IPv4  VLAN10_net  VLAN40_net  *  *
```

**QoS Configuration (Traffic Shaper):**

```
# WAN Upload Queue (100 Mbps upload assumed)
Queue: qStreamingVideo - 40% (40 Mbps) - AC_VI
Queue: qProduction    - 30% (30 Mbps) - AC_BE elevated
Queue: qVoice         - 10% (10 Mbps) - AC_VO
Queue: qGuest         - 20% (20 Mbps) - AC_BK

# DSCP Matching
qStreamingVideo: DSCP AF41 (34), source VLAN 20
qProduction: DSCP AF31 (26), source VLAN 10
qVoice: DSCP EF (46), all VLANs
qGuest: DSCP CS1 (8) or default, source VLAN 40
```

### 12.2 Switch VLAN Configuration (MikroTik)

**VLAN Creation:**

```routeros
# Create VLANs
/interface vlan
add interface=bridge name=vlan10_prod vlan-id=10
add interface=bridge name=vlan20_stream vlan-id=20
add interface=bridge name=vlan30_iot vlan-id=30
add interface=bridge name=vlan40_guest vlan-id=40
add interface=bridge name=vlan99_mgmt vlan-id=99

# Assign IP addresses (if L3 switch)
/ip address
add address=10.0.10.2/24 interface=vlan10_prod
add address=10.0.20.2/24 interface=vlan20_stream
add address=10.0.99.2/24 interface=vlan99_mgmt

# Bridge VLAN filtering
/interface bridge vlan
add bridge=bridge tagged=sfp-sfpplus1,sfp-sfpplus2 vlan-ids=10,20,30,40,99
add bridge=bridge tagged=ether1-24 untagged=ether1-4 vlan-ids=10  # Production ports
add bridge=bridge tagged=ether1-24 untagged=ether5-8 vlan-ids=20  # Streaming ports
add bridge=bridge tagged=ether1-24 untagged=ether9-12 vlan-ids=30 # IoT ports
add bridge=bridge tagged=ether1-24 untagged=ether13-20 vlan-ids=40 # Guest ports
```

**Port Profiles:**

```routeros
# Production Ports (ether1-4)
/interface ethernet
set ether1-4 poe-out=forced-on poe-priority=high

# AP Ports (ether21-23) - Trunk all VLANs
/interface bridge port
add bridge=bridge interface=ether21 pvid=99
add bridge=bridge interface=ether22 pvid=99
add bridge=bridge interface=ether23 pvid=99
set ether21-23 poe-out=auto-on poe-priority=high
```

### 12.3 WiFi AP Configuration (TP-Link Omada)

**SSID Configuration:**

```yaml
# SSID 1: DeadManAI_Prod
Name: DeadManAI_Prod
VLAN: 10
Security: WPA3-Personal
Password: [secure password]
Bands: 6 GHz (primary), 5 GHz (fallback)
Band Steering: Prefer 6 GHz
Client Isolation: Disabled
Rate Limiting: None
WMM: Enabled (mandatory)

# SSID 2: DeadManAI_Stream
Name: DeadManAI_Stream
VLAN: 20
Security: WPA3-Personal
Password: [secure password]
Bands: 6 GHz only (force high-bandwidth)
Client Isolation: Disabled
Rate Limiting: None
WMM: Enabled (AC_VI priority)

# SSID 3: DeadManAI_Guest
Name: DeadManAI_Guest
VLAN: 40
Security: WPA3-Personal (or Open with portal)
Password: [guest password]
Bands: 5 GHz, 2.4 GHz
Client Isolation: Enabled
Rate Limiting: 50 Mbps per client
WMM: Enabled (AC_BE)
```

**Radio Configuration:**

```yaml
# 6 GHz Radio
Channel Width: 320 MHz (if supported by region)
Channel: Auto (DFS-aware)
Power: 20 dBm
MLO: Enabled (Multi-Link Operation)

# 5 GHz Radio
Channel Width: 160 MHz
Channel: Auto (DFS-aware)
Power: 17 dBm

# 2.4 GHz Radio
Channel Width: 20 MHz
Channel: 1, 6, or 11 (manual assignment per AP)
Power: 14 dBm
```

---

## 13. IMPLEMENTATION ROADMAP

### 13.1 Phase 1: Foundation (Weeks 1-4)

**Week 1: Planning & Procurement**
- [ ] Finalize hardware selection (BOM approval)
- [ ] Order equipment (2-week lead time assumed)
- [ ] Survey physical space (rack location, cable runs)
- [ ] Document current network (baseline complete: CURRENT_NETWORK_BASELINE.md)

**Week 2: Physical Infrastructure**
- [ ] Install 12U rack (wall-mount or floor)
- [ ] Run Cat6a cables to workstation locations
- [ ] Run Cat6a cables to AP mounting points
- [ ] Label all cables (production, streaming, management)
- [ ] Install patch panel

**Week 3: Core Network Setup**
- [ ] Mount and power core switch, router, NAS
- [ ] Connect 10GbE links (router ↔ switch, switch ↔ NAS)
- [ ] Configure VLANs on switch
- [ ] Configure pfSense (WAN, LAN interfaces, DHCP)
- [ ] Test inter-VLAN routing
- [ ] Configure firewall rules

**Week 4: WiFi & Testing**
- [ ] Mount WiFi APs (ceiling or wall)
- [ ] Connect APs to PoE switch ports
- [ ] Configure SSIDs (Production, Streaming, Guest)
- [ ] Test WiFi coverage (walk-through with WiFi analyzer)
- [ ] Verify VLAN assignment per SSID
- [ ] Load test (stream 4K video over WiFi to NAS)

**Deliverables:**
- [ ] Functional network with all VLANs operational
- [ ] WiFi coverage verified
- [ ] NAS accessible from production VLAN
- [ ] Internet connectivity tested (100+ Mbps upload)

### 13.2 Phase 2: Production Integration (Weeks 5-8)

**Week 5: NAS Configuration**
- [ ] Initialize RAID 10 array (4x 12TB drives)
- [ ] Configure SMB shares (/production, /assets, /archive)
- [ ] Configure NFS exports (for Linux workstations)
- [ ] Enable 10GbE jumbo frames (MTU 9000)
- [ ] Test read/write performance (target: 800+ MB/s)
- [ ] Configure automated snapshots (hourly, daily, weekly)

**Week 6: Streaming Infrastructure**
- [ ] Install streaming PC (VLAN 20)
- [ ] Configure NDI cameras (static IPs 10.0.20.11-13)
- [ ] Install OBS, configure NVENC encoding
- [ ] Test NDI → OBS → YouTube workflow
- [ ] Configure QoS (AC_VI for video traffic)
- [ ] Verify latency <100ms glass-to-glass

**Week 7: Workstation Integration**
- [ ] Connect editing PCs to VLAN 10
- [ ] Map network drives (NAS shares)
- [ ] Test 4K editing workflow (DaVinci Resolve, Premiere Pro)
- [ ] Verify 10GbE performance (multi-cam 4K playback)
- [ ] Configure automated backups (Time Machine, Windows Backup)

**Week 8: Security Hardening**
- [ ] Enable Suricata IDS on pfSense
- [ ] Configure firewall logging
- [ ] Deploy Grafana monitoring dashboard
- [ ] Test VPN access (WireGuard)
- [ ] Document access credentials (KeePass, 1Password)
- [ ] Schedule quarterly security audits

**Deliverables:**
- [ ] Full production workflow operational
- [ ] 4K editing confirmed on NAS
- [ ] Streaming to YouTube/Twitch verified
- [ ] Security monitoring active

### 13.3 Phase 3: Optimization & Documentation (Weeks 9-12)

**Week 9: Performance Tuning**
- [ ] Benchmark NAS IOPS (fio, CrystalDiskMark)
- [ ] Optimize SMB multichannel settings
- [ ] Fine-tune QoS (measure streaming latency under load)
- [ ] WiFi channel optimization (WiFi analyzer, interference scan)
- [ ] Load test (simulate 10 concurrent users)

**Week 10: Automation**
- [ ] Deploy YouTube auto-upload script
- [ ] Configure automated NAS backups (rsync to offsite)
- [ ] Setup monitoring alerts (email, Slack, PagerDuty)
- [ ] Schedule automated speed tests (track ISP performance)

**Week 11: Documentation**
- [ ] Create network diagram (Visio, Draw.io)
- [ ] Document IP addressing (spreadsheet)
- [ ] Write runbooks (common tasks, troubleshooting)
- [ ] Record credentials (encrypted vault)
- [ ] Create disaster recovery plan

**Week 12: Training & Handoff**
- [ ] Train team on NAS access, folder structure
- [ ] Document streaming workflow (OBS setup, upload process)
- [ ] Schedule quarterly network reviews
- [ ] Celebrate successful deployment!

**Final Deliverables:**
- [ ] Complete network documentation
- [ ] Optimized performance benchmarks
- [ ] Team trained on infrastructure
- [ ] Disaster recovery plan documented

---

## 14. NETWORK DIAGRAMS

### 14.1 Logical Network Diagram

```
INTERNET (ISP Fiber/Cable)
        │
        │ [WAN - Public IP]
        │
   ┌────▼────┐
   │ Router  │ pfSense / UniFi Gateway
   │ Firewall│ QoS, VPN, IDS
   └────┬────┘
        │ [10GbE Uplink - Trunk VLANs 10/20/30/40/99]
        │
   ┌────▼────┐
   │  Core   │ MikroTik CRS309 (10GbE L3 Switch)
   │ Switch  │ VLAN routing, LACP bonding
   └─┬──┬──┬─┘
     │  │  └───────────────┐
     │  │                  │ [10GbE - VLAN 10]
     │  │              ┌───▼───┐
     │  │              │  NAS  │ QNAP TS-873AU
     │  │              │ 50TB  │ RAID 10, SMB/NFS
     │  │              └───────┘
     │  │
     │  └────────────────┐
     │                   │ [2.5GbE Uplink - Trunk]
     │               ┌───▼────┐
     │               │ Access │ TP-Link 24-port PoE+ Switch
     │               │ Switch │ 2.5GbE, PoE+
     │               └─┬──┬──┬┘
     │                 │  │  │
     │                 │  │  └─── [VLAN 40] Guest Devices
     │                 │  │
     │                 │  └────── [VLAN 20] NDI Cameras (PoE)
     │                 │
     │                 └───────── [VLAN 10] Workstations (2.5GbE)
     │
     └───────────────┐
                     │ [PoE+ - Trunk VLANs]
                 ┌───▼────┐
                 │  WiFi  │ TP-Link BE9300 (WiFi 7)
                 │  APs   │ 6GHz/5GHz/2.4GHz, MLO
                 └────────┘
                     │
                     ├─── SSID: DeadManAI_Prod (VLAN 10)
                     ├─── SSID: DeadManAI_Stream (VLAN 20)
                     ├─── SSID: DeadManAI_Guest (VLAN 40)
                     └─── SSID: DeadManAI_IoT (VLAN 30)
```

### 14.2 Physical Rack Diagram

```
┌───────────────────────────────────────┐
│         12U WALL-MOUNT RACK           │
├───────────────────────────────────────┤
│ 1U  [========================]        │ Patch Panel (24-port Cat6a)
│     [Ethernet Keystones      ]        │
├───────────────────────────────────────┤
│ 2U  [████████████████████████]        │ Core Switch (MikroTik CRS309)
│     [SFP+ Ports ············]         │ 8x 10GbE SFP+, 1x 1GbE Mgmt
│     [Fan ▓▓▓ | Power ◉◉]              │
├───────────────────────────────────────┤
│ 3U  [████████████████████████]        │ Access Switch (TP-Link 24-port)
│     [Ethernet Ports 1-24     ]        │ PoE+ LEDs: ●●●●●●●●
│     [SFP+ Uplink | Power ◉◉ ]         │
├───────────────────────────────────────┤
│ 4U  [▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓]        │ Router (Netgate 2100)
│     [WAN LAN1 LAN2 | Power ◉]         │ pfSense, 2.5GbE
├───────────────────────────────────────┤
│ 5U  [▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓]        │ NAS (QNAP TS-873AU)
│     [ [HDD] [HDD] [HDD] [HDD] ]       │ 8-bay, dual 10GbE
│     [ [HDD] [HDD] [HDD] [HDD] ]       │ RAID 10, 50TB
│     [SFP+ SFP+ | Power ◉◉    ]        │
├───────────────────────────────────────┤
│ 6U  [▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓]        │ UPS (APC SMT1500RM2U)
│     [Battery: ▓▓▓▓▓▓▓▓░░░░░░]        │ 1500VA, 10min runtime
│     [Load: 45% | Power ◉◉   ]         │
├───────────────────────────────────────┤
│ 7U  [≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈≈]        │ Cable Management Panel
│     [Velcro Ties, Vertical Mgr]       │
├───────────────────────────────────────┤
│ 8U  [                         ]       │ Future Expansion
├───────────────────────────────────────┤
│ 9U  [                         ]       │ Future Expansion
├───────────────────────────────────────┤
│ 10U [                         ]       │ Future Expansion
├───────────────────────────────────────┤
│ 11U [                         ]       │ Future Expansion
├───────────────────────────────────────┤
│ 12U [◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉]        │ PDU (12-outlet)
│     [◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉ ◉]        │ Tripp Lite RS1215-RA
└───────────────────────────────────────┘
```

### 14.3 WiFi Coverage Map (Example Studio)

```
┌──────────────────────────────────────────┐
│                                          │
│   [STUDIO SPACE - 1500 sq ft]           │
│                                          │
│   ┌─────────┐        ┌──────────┐       │
│   │ Camera 1│        │ Camera 2 │       │
│   │ (NDI)   │        │ (NDI)    │       │
│   └─────────┘        └──────────┘       │
│                                          │
│              ╔═══════╗                   │
│              ║  AP1  ║ ← Ceiling Mount  │
│              ║ WiFi7 ║    (Center)      │
│              ╚═══════╝                   │
│              /   |   \                   │
│            /     |     \                 │
│          /       |       \               │
│        /   6GHz  |  5GHz   \             │
│      /    (Prod) | (Stream) \            │
│    /             |            \          │
│  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓         │
│  ▓ Coverage: -40 to -60 dBm   ▓         │
│  ▓ Excellent signal strength  ▓         │
│  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓         │
│                                          │
│   [Streaming PC]                         │
│   10.0.20.10                             │
│   ↓ Wired 10GbE to Core Switch          │
│                                          │
└──────────────────────────────────────────┘

┌──────────────────────────────────────────┐
│  [OFFICE/EDIT SUITE - 800 sq ft]        │
│                                          │
│   ┌────────────┐    ┌────────────┐      │
│   │ Workstation│    │ Workstation│      │
│   │ (Wired)    │    │ (Wired)    │      │
│   └────────────┘    └────────────┘      │
│                                          │
│              ╔═══════╗                   │
│              ║  AP2  ║ ← Wall Mount     │
│              ║ WiFi7 ║    (High)        │
│              ╚═══════╝                   │
│              /   |   \                   │
│            /     |     \                 │
│          /       |       \               │
│        /   6GHz  |  5GHz   \             │
│      /   (Prod)  | (Guest)  \            │
│    /             |            \          │
│  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓         │
│  ▓ Coverage: -35 to -55 dBm   ▓         │
│  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓         │
│                                          │
│   [NAS - 10.0.10.2]                     │
│   ↑ 10GbE to Core Switch                │
│                                          │
└──────────────────────────────────────────┘
```

---

## 15. RISK MITIGATION & DISASTER RECOVERY

### 15.1 Single Points of Failure

| Component | Risk | Mitigation | Recovery Time |
|-----------|------|-----------|---------------|
| **Core Switch** | Network outage | Keep spare switch OR stack two switches | 2-4 hours (replace + reconfigure) |
| **Router** | Internet outage | Cellular failover OR dual WAN | 30-60 seconds (automatic) |
| **NAS** | Data loss | RAID 10 + 3-2-1 backups (Backblaze B2) | 4-8 hours (restore from backup) |
| **ISP** | Upload interruption | Cellular backup or dual WAN | 60 seconds (automatic failover) |
| **Power** | Outage | UPS (10min) + generator (if critical) | Immediate (UPS seamless) |

### 15.2 Backup Strategy (3-2-1 Rule)

**3 Copies of Data:**
1. Primary: NAS RAID 10 (live production data)
2. Secondary: Local backup drive (USB 3.0, weekly clone)
3. Tertiary: Cloud backup (Backblaze B2, daily incremental)

**2 Different Media Types:**
- NAS: RAID 10 spinning disks
- Cloud: Object storage (different failure domain)

**1 Offsite Copy:**
- Backblaze B2 (cloud storage, $6/TB/month)
- Automated daily backups using `rclone` or `restic`

**Retention Policy:**
- Daily snapshots: 7 days
- Weekly snapshots: 4 weeks
- Monthly snapshots: 12 months
- Yearly archives: 3 years (critical projects only)

### 15.3 Disaster Recovery Runbook

**Scenario 1: NAS Failure**

1. **Detection:** NAS offline alert (Grafana, email)
2. **Assessment:** Check RAID status (degraded, failed, offline)
3. **Action:**
   - If single drive failure: Hot spare auto-rebuilds (8-12 hours)
   - If multiple drive failure: Restore from Backblaze B2
4. **Recovery Steps:**
   - Mount new NAS or replacement drives
   - Restore latest backup (rclone sync from B2)
   - Verify data integrity (checksums, spot-check files)
   - Resume production (4-8 hour RTO)
5. **Post-Incident:** Review RAID level, consider upgrading to RAID 6

**Scenario 2: Internet Outage**

1. **Detection:** WAN down alert, cellular failover activates
2. **Assessment:** Check ISP status page, call support
3. **Action:**
   - Cellular modem provides 20-50 Mbps backup
   - Prioritize critical uploads (YouTube videos)
   - Defer non-critical cloud sync
4. **Recovery:** ISP restores service (typical: 2-6 hours)
5. **Post-Incident:** Monitor ISP reliability, consider dual WAN if recurring

**Scenario 3: Ransomware / Data Corruption**

1. **Detection:** File encryption detected, unusual NAS activity
2. **Immediate Action:**
   - Disconnect NAS from network (prevent spread)
   - Identify infection vector (workstation, phishing email)
   - Isolate compromised device (disable switch port)
3. **Recovery:**
   - Restore from snapshot BEFORE encryption (NAS snapshots hourly)
   - If snapshots compromised, restore from Backblaze B2
   - Scan all workstations for malware (Malwarebytes, ClamAV)
4. **Post-Incident:**
   - Enable versioning on NAS (immutable snapshots)
   - Implement application whitelisting
   - Security training for team

---

## 16. PERFORMANCE BENCHMARKS & VALIDATION

### 16.1 Target Performance Metrics

| Metric | Target | Validation Method |
|--------|--------|-------------------|
| **NAS Read Speed** | 800+ MB/s | CrystalDiskMark, fio |
| **NAS Write Speed** | 600+ MB/s | Sequential write test |
| **NAS IOPS** | 5,000+ (4K random read) | fio --randread |
| **WiFi Throughput (6GHz)** | 1.5+ Gbps | iperf3 (client to server) |
| **WiFi Latency (6GHz)** | <20ms (95th percentile) | ping, hping3 |
| **Internet Upload** | 100+ Mbps sustained | speedtest-cli, fast.com |
| **Internet Latency** | <20ms to YouTube CDN | ping upload.youtube.com |
| **Streaming Latency** | <100ms glass-to-glass | NDI → OBS timestamp analysis |
| **VLAN Throughput** | 10 Gbps (core), 2.5 Gbps (access) | iperf3 cross-VLAN |

### 16.2 Benchmark Commands

**NAS Speed Test (SMB):**
```bash
# From Windows workstation
CrystalDiskMark.exe --profile Default --target \\nas\production

# From Linux workstation
fio --name=sequential_read --rw=read --size=10G --filename=/mnt/nas/test
fio --name=sequential_write --rw=write --size=10G --filename=/mnt/nas/test
fio --name=random_read_iops --rw=randread --bs=4k --size=1G --filename=/mnt/nas/test
```

**WiFi Throughput Test:**
```bash
# On server (wired to network)
iperf3 -s

# On WiFi client
iperf3 -c <server_ip> -t 60 -i 1 -P 4  # 4 parallel streams, 60 seconds
```

**Internet Speed Test:**
```bash
# CLI speed test
speedtest-cli --secure

# YouTube-specific test
curl -o /dev/null -w '%{speed_upload}' https://upload.youtube.com/upload/test
```

**Latency Monitoring:**
```bash
# Continuous ping to YouTube
ping -i 1 upload.youtube.com | tee -a youtube_latency.log

# Latency histogram
hping3 -S -p 443 upload.youtube.com --fast
```

### 16.3 Performance Validation Checklist

**Week 9 Validation (Per Roadmap):**

- [ ] NAS read speed >800 MB/s (multi-client test)
- [ ] NAS write speed >600 MB/s (sustained 10 minutes)
- [ ] WiFi 6GHz throughput >1.5 Gbps (single client, iperf3)
- [ ] WiFi 5GHz throughput >900 Mbps (fallback test)
- [ ] Internet upload >100 Mbps (speedtest-cli, 3 consecutive tests)
- [ ] YouTube upload <15 min for 10GB file (actual test)
- [ ] NDI latency <100ms (glass-to-glass, NDI Studio Monitor)
- [ ] OBS streaming stable 4K 30fps (no dropped frames, 1-hour test)
- [ ] VLAN isolation verified (guest cannot access NAS, ping test)
- [ ] QoS working (video traffic prioritized during congestion test)

---

## 17. INTEGRATION WITH DEADMANAI WORKFLOWS

### 17.1 3-Factor Ruling Assessment

| Factor | Assessment | Score |
|--------|-----------|-------|
| **Human-in-Loop** | Network design supports human-directed content creation (no autonomous AI) | ✓ PASS |
| **Retention Velocity** | High-bandwidth infrastructure enables quality 4K production, streaming | ✓ PASS |
| **Asset Reusability** | NAS provides centralized asset library, 10GbE enables reuse across projects | ✓ PASS |

**Overall Score:** 3/3 - FULL INTEGRATION

### 17.2 Alignment with Mission (TELOS)

**Mission:** Create high-retention faceless YouTube content using AI-augmented workflows while maintaining absolute human creative direction.

**Network Architecture Supports:**

| Mission Element | Network Feature | Impact |
|----------------|-----------------|--------|
| **High Retention** | 4K editing workflows (10GbE NAS) | Quality visuals improve retention |
| **Faceless Content** | NDI multi-cam streaming | Professional multi-angle production |
| **AI-Augmented** | Cloud rendering integration | Fast AI video generation |
| **Human Direction** | Centralized asset management | Human curates/approves all content |
| **YouTube Focus** | Optimized upload paths (QoS) | Faster publishing, consistent schedule |

### 17.3 Success Metrics Mapping

| CLAUDE.md Metric | Network Contribution | Target |
|------------------|---------------------|--------|
| **CTR (5-7%)** | Fast uploads → consistent schedule → viewer trust | Network enables: On-time publishing |
| **AVD (40-50%)** | 4K quality production (NAS performance) | Network enables: High-quality visuals |
| **30-sec Retention (70%+)** | Multi-cam streaming (NDI) → dynamic editing | Network enables: Professional production |
| **Sub Conversion (1-2%)** | Asset library (B-roll, templates) → consistent branding | Network enables: Reusable brand assets |

### 17.4 Research Integration

**Referenced Research Documents:**

| Research ID | Title | Network Application |
|-------------|-------|---------------------|
| **R36 (WiFi 7)** | WiFi 7 Comprehensive Analysis | Access point selection, MLO configuration, 6GHz deployment |
| **R36 (QoS)** | WiFi QoS & WMM Streaming Quality | QoS configuration, EDCA parameters, traffic prioritization |
| **R28-R29** | Fabric (AI Patterns) | Automation scripts (YouTube upload, network monitoring) |
| **R57-R60** | YouTube Benchmarking | Bandwidth planning (reference creator upload requirements) |

---

## 18. NEXT STEPS & RECOMMENDATIONS

### 18.1 Immediate Actions (Week 1)

1. **Budget Approval:** Review Phase 1 BOM ($6,521), obtain approval
2. **Hardware Procurement:** Order equipment (2-week lead time)
3. **Site Survey:** Measure cable runs, identify rack location
4. **ISP Upgrade:** Contact ISP, upgrade to 500/100 Mbps (or better)

### 18.2 Pre-Implementation Checklist

- [ ] Confirm 6 GHz WiFi availability in your region (check FCC/local regulations)
- [ ] Verify physical space for 12U rack (dimensions: 24"H x 24"W x 24"D typical)
- [ ] Calculate power requirements (rack + workstations <15A circuit)
- [ ] Plan cable pathways (avoid EMI sources, HVAC, fluorescent lights)
- [ ] Review CLAUDE.md foundations (NASA standards, 7-phase cycle)

### 18.3 Long-Term Roadmap (2026-2027)

**Q1 2026:** Phase 1 implementation (foundation network)
**Q2 2026:** Production integration, streaming workflows
**Q3 2026:** Optimization, performance tuning
**Q4 2026:** Evaluate Phase 2 upgrades (medium studio expansion)
**Q1 2027:** Plan Phase 3 (large studio, multi-creator)

### 18.4 Continuous Improvement

**Quarterly Reviews:**
- Benchmark performance (NAS speed, WiFi throughput, upload times)
- Review security logs (IDS alerts, firewall denies)
- Update firmware (switches, APs, NAS)
- Audit backups (test restore, verify integrity)

**Annual Actions:**
- Hardware refresh planning (5-year lifecycle)
- ISP contract renewal (negotiate better rates)
- Capacity planning (storage utilization, bandwidth trends)
- Document lessons learned (what worked, what didn't)

---

## APPENDIX A: GLOSSARY

| Term | Definition |
|------|-----------|
| **LACP** | Link Aggregation Control Protocol - IEEE 802.3ad standard for bonding multiple network links |
| **MLO** | Multi-Link Operation - WiFi 7 feature enabling simultaneous multi-band connections |
| **NDI** | Network Device Interface - Protocol for sending video over IP networks |
| **NVENC** | NVIDIA hardware encoder for H.264/HEVC video encoding |
| **RAID 10** | Mirrored striping - combines RAID 1 mirroring with RAID 0 striping for performance + redundancy |
| **SFP+** | Small Form-factor Pluggable Plus - 10 Gbps fiber/copper transceiver standard |
| **WMM** | WiFi Multimedia - QoS standard for prioritizing voice/video traffic |
| **EDCA** | Enhanced Distributed Channel Access - WiFi QoS mechanism (IEEE 802.11e) |
| **DSCP** | Differentiated Services Code Point - IP packet header field for QoS marking |
| **MTU** | Maximum Transmission Unit - Largest packet size (9000 bytes for jumbo frames) |

---

## APPENDIX B: VENDOR CONTACT INFORMATION

| Vendor | Product Category | Support URL |
|--------|-----------------|-------------|
| **Netgate** | pfSense Router/Firewall | https://www.netgate.com/support |
| **MikroTik** | Core Switches | https://mikrotik.com/support |
| **TP-Link** | WiFi APs, Access Switches | https://www.tp-link.com/us/support/ |
| **QNAP** | NAS | https://www.qnap.com/en-us/support/ |
| **Synology** | NAS | https://www.synology.com/en-us/support |
| **APC** | UPS | https://www.apc.com/us/en/support/ |

---

## APPENDIX C: CITATIONS

1. [WiFi 7 Multi-Link Operation (MLO) - RUCKUS Networks](https://www.ruckusnetworks.com/blog/2023/wi-fi-7-multi-link-operations-mlo/)
2. [WiFi QoS (WMM) Standards - IEEE 802.11e](https://standards.ieee.org/standard/802_11e-2005.html)
3. [NDI Technical Specifications - NewTek](https://www.ndi.tv/tools/)
4. [Synology NAS Specifications](https://www.synology.com/en-us/products/RS1221+)
5. [QNAP NAS Performance Benchmarks](https://www.qnap.com/en-us/product/ts-873au)
6. [pfSense Documentation - VLANs and QoS](https://docs.netgate.com/pfsense/en/latest/)
7. [MikroTik Switch Configuration Guide](https://help.mikrotik.com/docs/display/ROS/Switch+Chip+Features)
8. [TP-Link Omada WiFi 7 Specifications](https://www.tp-link.com/us/business-networking/omada-sdn-access-point/eap783/)
9. [YouTube Upload Requirements](https://support.google.com/youtube/answer/1722171)
10. [Backblaze B2 Pricing](https://www.backblaze.com/cloud-storage/pricing)

---

## VERSION HISTORY

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-01-03 | Initial comprehensive design - 18 sections covering physical topology, VLAN segmentation, IP addressing, internet connectivity, WiFi 7 design, storage network, streaming infrastructure, security, cloud integration, scalability, BOM, configuration templates, implementation roadmap, network diagrams, disaster recovery, performance benchmarks, DeadManAI integration, recommendations. Based on 100 networking research agents + current network baseline (192.168.50.106/24). |

---

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│   Network Architecture Design Complete                        │
│   Ready for Implementation                                    │
│   Total Budget: $6,521 (Phase 1) → $19,139 (Full Scale)      │
│                                                                │
│   Structure enables excellence.                                │
│   Documentation enables continuity.                            │
│   Standards enable scale.                                      │
│   Verification enables trust.                                  │
│                                                                │
│                    // THE UNSEEN //                            │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

# END OF DOCUMENT

**Document Status:** DESIGN COMPLETE - READY FOR IMPLEMENTATION
**Next Action:** Review → Budget approval → Procurement (Phase 1)
**Estimated Implementation Time:** 12 weeks (full Phase 1-3)
**Critical Success Factor:** Follow NASA standards (CLAUDE.md) - document as you build, verify before proceeding