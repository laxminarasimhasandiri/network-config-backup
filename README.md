# 🌐 Network Configuration Backup Report
**Generated:** 2026-05-06 14:25:05  
**Total Devices:** 8  
**Healthy:** 0 | **Warnings:** 6 | **Critical:** 2

---

## 📋 Device Summary

| Hostname | Type | IP Address | Role | Status |
|----------|------|------------|------|--------|
| CORE-SW-01 | Cisco Catalyst | 10.0.0.1 | Core Switch | ⚠️ WARNING |
| DIST-SW-02 | Cisco Nexus | 10.0.0.2 | Distribution Switch | ⚠️ WARNING |
| FW-PALOALTO-01 | Palo Alto PA-820 | 10.0.1.1 | Perimeter Firewall | ⚠️ WARNING |
| SDWAN-EDGE-01 | Cisco Viptela | 10.0.2.1 | SD-WAN Edge | ⚠️ WARNING |
| SDWAN-EDGE-02 | Cisco Viptela | 10.0.2.2 | SD-WAN Edge | ⚠️ WARNING |
| WLC-ARUBA-01 | Aruba Controller | 10.0.3.1 | Wireless Controller | ❌ CRITICAL |
| F5-LTM-01 | F5 BIG-IP | 10.0.4.1 | Load Balancer | ❌ CRITICAL |
| RTR-BGP-01 | Cisco ASR 1001 | 192.168.1.1 | WAN Router | ⚠️ WARNING |

---

## 🔍 Detailed Health Checks

### CORE-SW-01 (`10.0.0.1`)
**Role:** Core Switch | **Type:** Cisco Catalyst  
**Overall Status:** WARNING  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ⚠️ WARN |
| IP address configured | ✅ PASS |
| Routing protocol present | ✅ PASS |

**Issues Found:**
- ⚠️ No security/ACL policy detected

### DIST-SW-02 (`10.0.0.2`)
**Role:** Distribution Switch | **Type:** Cisco Nexus  
**Overall Status:** WARNING  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ⚠️ WARN |
| IP address configured | ✅ PASS |
| Routing protocol present | ✅ PASS |

**Issues Found:**
- ⚠️ No security/ACL policy detected

### FW-PALOALTO-01 (`10.0.1.1`)
**Role:** Perimeter Firewall | **Type:** Palo Alto PA-820  
**Overall Status:** WARNING  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ✅ PASS |
| IP address configured | ✅ PASS |
| Routing protocol present | ⚠️ WARN |

**Issues Found:**
- ⚠️ No routing protocol detected

### SDWAN-EDGE-01 (`10.0.2.1`)
**Role:** SD-WAN Edge | **Type:** Cisco Viptela  
**Overall Status:** WARNING  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ⚠️ WARN |
| IP address configured | ✅ PASS |
| Routing protocol present | ✅ PASS |

**Issues Found:**
- ⚠️ No security/ACL policy detected

### SDWAN-EDGE-02 (`10.0.2.2`)
**Role:** SD-WAN Edge | **Type:** Cisco Viptela  
**Overall Status:** WARNING  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ⚠️ WARN |
| IP address configured | ✅ PASS |
| Routing protocol present | ✅ PASS |

**Issues Found:**
- ⚠️ No security/ACL policy detected

### WLC-ARUBA-01 (`10.0.3.1`)
**Role:** Wireless Controller | **Type:** Aruba Controller  
**Overall Status:** CRITICAL  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ⚠️ WARN |
| IP address configured | ✅ PASS |
| Routing protocol present | ⚠️ WARN |

**Issues Found:**
- ⚠️ No security/ACL policy detected
- ⚠️ No routing protocol detected

### F5-LTM-01 (`10.0.4.1`)
**Role:** Load Balancer | **Type:** F5 BIG-IP  
**Overall Status:** CRITICAL  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ⚠️ WARN |
| IP address configured | ✅ PASS |
| Routing protocol present | ⚠️ WARN |

**Issues Found:**
- ⚠️ No security/ACL policy detected
- ⚠️ No routing protocol detected

### RTR-BGP-01 (`192.168.1.1`)
**Role:** WAN Router | **Type:** Cisco ASR 1001  
**Overall Status:** WARNING  

| Check | Result |
|-------|--------|
| Hostname configured | ✅ PASS |
| Security policy present | ⚠️ WARN |
| IP address configured | ✅ PASS |
| Routing protocol present | ✅ PASS |

**Issues Found:**
- ⚠️ No security/ACL policy detected

---

## 📁 Config Backups

### CORE-SW-01
```
hostname CORE-SW-01
!
vlan 10
 name SERVERS
vlan 20
 name MANAGEMENT
vlan 30
 name USERS
!
interface Vlan10
 ip address 10.10.10.1 255.255.255.0
 no shutdown
!
spanning-tree mode rapid-pvst
spanning-tree vlan 10,20,30 priority 4096
!
ip routing
router ospf 1
 router-id 10.0.0.1
 network 10.10.0.0 0.0.255.255 area 0
!
end
```

### DIST-SW-02
```
hostname DIST-SW-02
!
vlan 10,20,30,40,50
!
interface Port-channel1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
!
ip routing
router ospf 1
 router-id 10.0.0.2
 passive-interface default
 no passive-interface GigabitEthernet0/1
!
end
```

### FW-PALOALTO-01
```
# Palo Alto Running Config Snapshot
# Device: FW-PALOALTO-01 | IP: 10.0.1.1
security-policy:
  - name: Allow-Internal-Outbound
    from: trust
    to: untrust
    application: [web-browsing, ssl, dns]
    action: allow
  - name: Block-All
    from: any
    to: any
    action: deny
nat-policy:
  - name: Outbound-NAT
    from: trust
    to: untrust
    source-translation: dynamic-ip-and-port
```

### SDWAN-EDGE-01
```
# Cisco Viptela vEdge Config
# Device: SDWAN-EDGE-01 | IP: 10.0.2.1
system:
  host-name: SDWAN-EDGE-01
  system-ip: 10.0.2.1
  site-id: 100
  organization-name: Enterprise-SD-WAN
vpn 0:
  interface ge0/0:
    ip address 10.0.2.1/24
    tunnel-interface:
      encapsulation ipsec
      allow-service: all
vpn 512:
  interface eth0:
    ip dhcp-client
```

### SDWAN-EDGE-02
```
# Cisco Viptela vEdge Config
# Device: SDWAN-EDGE-02 | IP: 10.0.2.2
system:
  host-name: SDWAN-EDGE-02
  system-ip: 10.0.2.2
  site-id: 100
  organization-name: Enterprise-SD-WAN
vpn 0:
  interface ge0/0:
    ip address 10.0.2.2/24
    tunnel-interface:
      encapsulation ipsec
      allow-service: all
vpn 512:
  interface eth0:
    ip dhcp-client
```

### WLC-ARUBA-01
```
# Aruba Controller Config
# Device: WLC-ARUBA-01 | IP: 10.0.3.1
wlan ssid-profile CORP-WIFI
  essid "Corp-Wireless"
  wpa-passphrase encrypted
  dot1x
  auth-server ISE-Server
aaa authentication-server radius ISE-Server
  host 10.0.5.10
  key encrypted
ap-group CAMPUS-APs
  virtual-ap CORP-WIFI
```

### F5-LTM-01
```
# F5 BIG-IP Running Config
# Device: F5-LTM-01 | IP: 10.0.4.1
ltm virtual VS-WEB-443 {
    destination 10.0.4.1:443
    ip-protocol tcp
    pool POOL-WEB-SERVERS
    profiles { http { } ssl-client { } }
}
ltm pool POOL-WEB-SERVERS {
    members {
        10.10.10.101:80 { address 10.10.10.101 }
        10.10.10.102:80 { address 10.10.10.102 }
    }
    monitor http
}
```

### RTR-BGP-01
```
hostname RTR-BGP-01
!
router bgp 65001
 bgp router-id 192.168.1.1
 neighbor 203.0.113.1 remote-as 65002
 neighbor 203.0.113.1 description ISP-UPSTREAM
 network 192.168.0.0 mask 255.255.0.0
!
ip route 0.0.0.0 0.0.0.0 203.0.113.1
!
end
```

---
*Auto-generated by Network Configuration Backup Tool*  
*Author: Laxmi Narasimha | Senior Network Engineer*