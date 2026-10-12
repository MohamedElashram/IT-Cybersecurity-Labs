# CCNA Lab: VLAN Trunking Protocol (VTP)

## 📌 Overview

This lab demonstrates the configuration of **VLAN Trunking Protocol (VTP) in Transparent Mode** using three Cisco switches in an EVE-NG environment.

The lab focuses on VLAN creation, trunk configuration, access port assignment, and VTP verification.

## 🎯 Objectives

- Understand VTP Transparent Mode.
- Configure VTP on multiple switches.
- Create and name VLANs.
- Configure trunk links between switches.
- Assign access ports to specific VLANs.
- Verify VLAN and trunk configurations using Cisco IOS commands.

## 🖥️ Lab Topology

The lab consists of three switches:

- SW1
- SW2
- SW3

The switches are connected using trunk links to carry traffic for multiple VLANs.

**Topology Screenshot**

Add a screenshot of your EVE-NG topology here.

## 🗂️ VLAN Configuration

| VLAN ID | VLAN Name | Purpose |
|---|---|---|
| 10 | HR | Human Resources |
| 20 | Sales | Sales Department |
| 30 | Finance | Finance Department |

## ⚙️ VTP Configuration

All switches are configured in Transparent Mode.

```cisco
vtp domain VTP-LAB
vtp mode transparent
```

In Transparent Mode, each switch maintains its own VLAN configuration locally. VLANs must be created manually on each switch.

## 🔌 Port Configuration

| Switch | Interface | Mode | Assignment |
|---|---|---|---|
| SW1 | Ethernet0/0 | Trunk | Inter-switch connection |
| SW1 | Ethernet0/2–3 | Access | VLAN 30 – Finance |
| SW2 | Ethernet0/0–1 | Trunk | Inter-switch connections |
| SW2 | Ethernet0/2–3 | Access | VLAN 20 – Sales |
| SW3 | Ethernet0/0 | Trunk | Inter-switch connection |
| SW3 | Ethernet0/2–3 | Access | VLAN 10 – HR |

*Note: Verify the interface assignments against the actual lab topology.*

## 📁 Configuration Files

The switch configurations are organized as follows:

```text
VTP/
├── README.md
├── SW1.txt
├── SW2.txt
└── SW3.txt
```

Each configuration file contains the commands for its respective switch.

## 🧪 Verification Commands

Use the following commands to verify the lab:

```cisco
show vtp status
show interfaces trunk
show vlan brief
show running-config
```

### Expected Results

- All switches operate in VTP Transparent Mode.
- VLANs 10, 20, and 30 are configured locally on each switch.
- Trunk interfaces are operational.
- Access ports belong to their intended VLANs.

## 📚 Key Concepts

**VTP Transparent Mode:** VLAN changes are maintained locally instead of being learned and applied from VTP advertisements.

**VLAN:** A Layer 2 logical segmentation of a switched network.

**Trunk Port:** Carries traffic for multiple VLANs between network devices.

**Access Port:** Connects an end device to a specific VLAN.

**Inter-VLAN Routing:** Communication between different VLANs requires a Layer 3 device configured for routing.

## 🛠️ Lab Environment

- EVE-NG
- Cisco IOS switch images
- CCNA Switching and VLAN Technologies

