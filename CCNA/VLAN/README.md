# Cisco VLAN Configuration Lab

## 📌 Overview
This lab demonstrates how to configure VLANs on a Cisco switch using EVE-NG. Three PCs are connected to a single switch, with each PC assigned to a separate VLAN.

## 🎯 Objectives
- Create and configure VLANs.
- Assign switch ports to specific VLANs.
- Configure access ports.
- Test connectivity using ICMP ping.
- Understand VLAN isolation and broadcast domains.

## 🖥️ Topology

- **SW1:** Cisco Switch
- **PC1:** VLAN 10
- **PC2:** VLAN 20
- **PC3:** VLAN 30

## 🌐 IP Addressing

Each VLAN should use a different IP subnet.

| Device | VLAN | IP Address | Subnet Mask |
|---|---|---|---|
| PC1 | VLAN 10 | 10.0.10.5 | 255.255.255.0 |
| PC2 | VLAN 20 | 10.0.20.2 | 255.255.255.0 |
| PC3 | VLAN 30 | 10.0.30.3 | 255.255.255.0 |

> Note: These are recommended addressing values. The screenshot shows all PCs using the 10.0.0.0/24 subnet, which should be corrected for a proper VLAN design.

## ⚙️ Switch Configuration

### 1. Create VLANs

```cisco
enable
configure terminal

vlan 10
 name VLAN10
exit

vlan 20
 name VLAN20
exit

vlan 30
 name VLAN30
exit
```

### 2. Configure Access Ports

```cisco
interface Ethernet0/1
 switchport mode access
 switchport access vlan 10
 no shutdown
exit

interface Ethernet0/2
 switchport mode access
 switchport access vlan 20
 no shutdown
exit

interface Ethernet0/3
 switchport mode access
 switchport access vlan 30
 no shutdown
exit
```

### 3. Verify Configuration

```cisco
show vlan brief
show interfaces status
show running-config
```

## 🧪 Testing

1. Configure each PC with its assigned IP address and subnet mask.
2. Ping the switch-connected PCs.
3. Verify that PCs in different VLANs cannot communicate directly without inter-VLAN routing.

Example:

```text
PC1> ping 10.0.10.5
```

A PC should be able to ping its own IP address. To test connectivity between different devices, use their actual IP addresses.

## 📚 Key Concepts

- **VLAN:** Logically separates a Layer 2 network into different broadcast domains.
- **Access Port:** Assigns an endpoint-facing switch port to a single VLAN.
- **VLAN Isolation:** Devices in different VLANs are separated at Layer 2.
- **Inter-VLAN Routing:** Required for communication between different VLAN subnets.

## 📝 Lab Notes

- VLAN configuration alone does not provide communication between different VLANs.
- Different VLANs should normally use different IP subnets.
- A Layer 3 switch or router can provide inter-VLAN routing when required.

## 🛠️ Environment

- EVE-NG
- Cisco IOS switch
- VPCS endpoints

## ✅ Status

Basic VLAN creation and access-port configuration completed. IP addressing and connectivity tests should be verified after correcting the subnet design.
