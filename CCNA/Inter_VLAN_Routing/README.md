# Inter-VLAN Routing Using a Layer 3 Switch

## Overview
This lab demonstrates Inter-VLAN Routing using a Cisco Layer 3 Switch. Routing is configured using Switched Virtual Interfaces (SVIs) and the `ip routing` command.

## Objectives
- Create and configure VLANs.
- Assign switch ports to VLANs.
- Configure SVIs as default gateways.
- Enable Inter-VLAN Routing.
- Verify connectivity between different VLANs.

## Topology

- **L3_SW G0/0** → PC5 (VLAN 10)
- **L3_SW G0/1** → PC4 (VLAN 10)
- **L3_SW G0/2** → PC3 (VLAN 20)
- **L3_SW G0/3** → PC2 (VLAN 20)

## VLAN Configuration

| VLAN ID | VLAN Name | Network |
|---|---|---|
| 10 | SALES | 192.168.10.0/24 |
| 20 | HR | 192.168.20.0/24 |

## IP Addressing Table

| Device | VLAN | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| PC5 | 10 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC4 | 10 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| PC3 | 20 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |
| PC2 | 20 | 192.168.20.11 | 255.255.255.0 | 192.168.20.1 |
| L3_SW SVI | 10 | 192.168.10.1 | 255.255.255.0 | N/A |
| L3_SW SVI | 20 | 192.168.20.1 | 255.255.255.0 | N/A |

## Configuration Steps

1. Create VLAN 10 (SALES) and VLAN 20 (HR).
2. Assign G0/0 and G0/1 to VLAN 10.
3. Assign G0/2 and G0/3 to VLAN 20.
4. Configure the SVI for each VLAN.
5. Enable routing using `ip routing`.
6. Configure IP addresses and default gateways on all PCs.

The complete configuration is available in `L3\_SW-Config.txt`.

## Verification Commands

Run these commands on the switch:

```text

show vlan brief

show ip interface brief

show ip route

show running-config

```

Expected connected routes:

```text

C 192.168.10.0/24 is directly connected, Vlan10

C 192.168.20.0/24 is directly connected, Vlan20

```

## Connectivity Tests

From PC5, run:

```text

ping 192.168.10.11

ping 192.168.20.10

ping 192.168.20.11

```

Successful replies confirm connectivity within VLAN 10 and between VLANs.

## Troubleshooting

- Verify VLAN assignments using `show vlan brief`.
- Verify SVI status using `show ip interface brief`.
- Ensure each SVI is up/up.
- Verify `ip routing` is enabled.
- Check each PC's IP address, subnet mask, and default gateway.
- Confirm the switch interfaces match the actual hardware interface names.

## Learning Challenge

1. Move PC2 to VLAN 10 and test connectivity.
2. Restore PC2 to VLAN 20.
3. Disable `ip routing` and test communication between VLANs.
4. Re-enable routing and verify the routing table.

## Security Note

Inter-VLAN Routing allows communication between VLANs by default when no ACLs or other restrictions are configured. Use Access Control Lists (ACLs) if communication between SALES and HR must be restricted.

## Skills Practiced

- VLAN Configuration
- Layer 3 Switching
- Switched Virtual Interfaces (SVI)
- Inter-VLAN Routing
- IP Addressing and Default Gateways
- Network Troubleshooting
