# Ente# 4-Building Campus Network Simulation with RIP Routing

![Topology](https://img.shields.io/badge/Architecture-4--Building--Campus-blueviolet?style=for-the-badge)
![Routing Protocol](https://img.shields.io/badge/Protocol-RIP--v2-success?style=for-the-badge)
![Status](https://img.shields.io/badge/Connectivity-100%25--Verified-orange?style=for-the-badge)

**4-Building Campus Network** is a multi-tier, redundant campus network simulation designed and validated in Cisco Packet Tracer. Built with 13 routers, 8 switches, and 8 end-devices distributed across a 4-building setup (2 floors per building), it utilizes Routing Information Protocol Version 2 (RIPv2) to establish full dynamic routing and failover capabilities across 23 subnets.

## 🚀 Network Topology & Core Architecture

The infrastructure employs a centralized core router connected to four building routers, supplemented by redundant building-to-building links to ensure high availability and prevent single points of failure.

### Key Capabilities
- **Hierarchical Routing Architecture**: Tiered design consisting of 1 Core Router, 4 Building Routers, and 8 Floor Routers.
- **Dynamic Routing via RIPv2**: Configured across all 13 routers with disabled auto-summarization (`no auto-summary`) to preserve variable subnetting boundaries.
- **Redundant WAN Pathing**: Cross-connected inter-building links enabling automatic dynamic re-routing in case of link failure.
- **Complete End-to-End Reachability**: Verified 100% ICMP ping and traceroute path resolution across all subnets.

## 📊 IP Addressing & Subnetting Scheme

Subnets range from `192.168.78.0/24` through `192.168.100.0/24`, covering all floor LANs, floor-to-building links, and core-to-building WAN connections.

### LAN Subnets (Floor End-Devices)

| Host PC | Floor LAN Subnet | IP Address | Default Gateway |
| :--- | :--- | :--- | :--- |
| **PC1** | `192.168.78.0/24` | `192.168.78.2` | `192.168.78.1` |
| **PC2** | `192.168.79.0/24` | `192.168.79.2` | `192.168.79.1` |
| **PC3** | `192.168.80.0/24` | `192.168.80.2` | `192.168.80.1` |
| **PC4** | `192.168.81.0/24` | `192.168.81.2` | `192.168.81.1` |
| **PC5** | `192.168.82.0/24` | `192.168.82.2` | `192.168.82.1` |
| **PC6** | `192.168.83.0/24` | `192.168.83.2` | `192.168.83.1` |
| **PC7** | `192.168.84.0/24` | `192.168.84.2` | `192.168.84.1` |
| **PC8** | `192.168.85.0/24` | `192.168.85.2` | `192.168.85.1` |

### WAN Links (Inter-Router Connectivity)

| Network Link | Connects Devices | Subnet Allocated |
| :--- | :--- | :--- |
| **Core WAN 1** | Core Router $\leftrightarrow$ Building 1 Router | `192.168.94.0/24` |
| **Core WAN 2** | Core Router $\leftrightarrow$ Building 2 Router | `192.168.95.0/24` |
| **Core WAN 3** | Core Router $\leftrightarrow$ Building 3 Router | `192.168.96.0/24` |
| **Core WAN 4** | Core Router $\leftrightarrow$ Building 4 Router | `192.168.97.0/24` |
| **Inter-Building Link 1-2** | Building 1 $\leftrightarrow$ Building 2 | `192.168.98.0/24` |
| **Inter-Building Link 2-3** | Building 2 $\leftrightarrow$ Building 3 | `192.168.99.0/24` |
| **Inter-Building Link 3-4** | Building 3 $\leftrightarrow$ Building 4 | `192.168.100.0/24` |

## 🛠 Infrastructure Tech Stack

### Simulated Hardware
- **Routers**: Cisco 2911 Integrated Services Routers (13 units).
- **Switches**: Cisco Catalyst 2960 Series Switches (8 units).
- **Endpoints**: Workstation PCs (8 units).

### Routing Configuration Example (RIPv2)
```cisconetwork
router rip
 version 2
 network 192.168.78.0
 network 192.168.86.0
 no auto-summary
