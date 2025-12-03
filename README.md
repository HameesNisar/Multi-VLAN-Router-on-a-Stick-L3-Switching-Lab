# Multi-VLAN Router-on-a-Stick & L3 Switching Lab (GNS3)

This project demonstrates a complete Layer 2 + Layer 3 switching environment using VLANs, trunking, Router-on-a-Stick, EIGRP, and OSPF. The lab uses Cisco “EtherSwitch Router” modules to simulate multilayer switches and integrates two different routing approaches:

---

## 🖼 Topology

<img width="1861" height="895" alt="sss" src="https://github.com/user-attachments/assets/117fb7d6-e345-4044-8ee9-a6d8cf5803db" />

- **R38** → Multiple routed physical interfaces (one interface per VLAN)  
- **R39** → **Router-on-a-Stick** using 802.1Q sub-interfaces on a single trunk link  

The goal is to show both methods of inter-VLAN routing inside the same network.

---

## 📘 Overview

This lab demonstrates:

- VLAN creation and segmentation  
- Trunk configuration between Layer 3 EtherSwitch routers  
- Router-on-a-Stick configuration on R39  
- Routed physical interfaces (R38) as an alternate method  
- EIGRP (two ASNs) and OSPF running across VLANs  
- Loopback advertisement inside each VLAN  
- End-to-end route propagation within each VLAN group

Each VLAN contains **four routers**, each advertising **two loopbacks**, and all routers inside that VLAN must share networks through the assigned routing protocol.

---

## 🧩 VLAN & Routing Protocol Mapping

| VLAN | Routing Protocol | Routers Inside | Example Network |
|------|------------------|----------------|-----------------|
| **2** | EIGRP ASN 123 | R6, R14, R22, R30 | 192.168.2.0/24 |
| **3** | EIGRP ASN 123 | R7, R15, R23, R31 | 192.168.3.0/24 |
| **4** | EIGRP ASN 146 | R8, R16, R24, R32 | 192.168.4.0/24 |
| **5** | EIGRP ASN 146 | R9, R17, R33, R25 | 192.168.5.0/24 |
| **6** | EIGRP ASN 146 | R10, R18, R34, R26 | 192.168.6.0/24 |
| **7** | OSPF Process 1 (Area 178) | R27, R11, R19, R35 | 192.168.7.0/24 |
| **8** | OSPF Process 1 (Area 178) | R12, R20, R36, R28 | 192.168.8.0/24 |
| **9** | OSPF Process 1 (Area 178) | R13, R21, R37, R29 | 192.168.9.0/24 |

Each router also advertises **two loopback networks**, and the routing protocol inside the VLAN must exchange all these routes.

---

## 🔧 Technologies Used

### **Layer 2**
- VLAN creation  
- Access ports for router connections  
- 802.1Q trunking between switches  

### **Layer 3**
- Switch Virtual Interfaces (SVIs) for inter-VLAN routing  
- Router-on-a-Stick implementation on R39  
- Routed physical interfaces on R38  
- EIGRP (ASN 123 & ASN 146)  
- OSPF (Process 1, Area 178)  
- Loopback advertisements

---

## 🎯 Lab Objectives

- Build multi-VLAN segmentation using Layer 3 EtherSwitch routers  
- Configure trunk links between switches  
- Implement **Router-on-a-Stick** on R39  
- Implement **routed physical interfaces** on R38  
- Run EIGRP and OSPF inside specific VLANs  
- Ensure all routers inside each VLAN fully exchange loopback routes  
- Validate connectivity and proper route learning


