# VMware Virtual Datacenter Implementation (Enterprise Lab)

## Project Overview
This project is a full-scale virtual datacenter implementation designed to simulate a real enterprise IT infrastructure using VMware technologies. The environment includes centralized management, high availability, distributed resource scheduling, identity management, and shared storage architecture.

The goal of this project is to demonstrate practical skills in virtualization, datacenter design, and enterprise infrastructure services including compute, network, storage, and identity services.

---

## Architecture Design

Network Infrastructure:

- Domain Name: amir.fakerov
- Network Subnet: 192.168.4.0/24
- Default Gateway: 192.168.4.1

### Core Infrastructure Services

- Active Directory / DNS / NTP Server: 192.168.4.3
- VMware vCenter Server: 192.168.4.50 (VCSA-100.amir.fakerov)
- ESXi Host 1: 192.168.4.10
- ESXi Host 2: 192.168.4.20

---

## Infrastructure Components

- VMware ESXi Hosts (2 nodes)
- VMware vCenter Server (VCSA)
- Windows Server (Active Directory, DNS, NTP)
- Shared Storage (iSCSI-based)
- Virtual Machines (Windows-based workloads)

---

## Identity and Network Services (Active Directory)

A Windows Server was deployed as a Domain Controller using Active Directory to provide centralized identity and network services across the entire datacenter.

Active Directory provides:

### Centralized Authentication
- Domain-based authentication for users and administrators
- Eliminates local accounts on individual systems
- Unified login across infrastructure

### DNS Services
- Internal name resolution for ESXi hosts, vCenter Server, and virtual machines
- Ensures consistent communication across all components

### Time Synchronization (NTP)
- Central time source for all systems
- Ensures time consistency across infrastructure
- Required for authentication and logging services

### Role-Based Access Control (RBAC)
- Users and groups managed in Active Directory
- Different permission levels:
  - Administrator
  - Read-only users
  - Restricted users

### Integration with VMware vCenter
vCenter Server is integrated with Active Directory to enable centralized authentication and role-based access control for infrastructure management.

---

## Virtualization Layer

Two VMware ESXi hosts were deployed to provide compute resources for virtual machines and form the foundation of the datacenter.

---

## vCenter Server Deployment

- VMware vCenter Server Appliance (VCSA) deployed
- Static IP configured: 192.168.4.50
- Integrated with Active Directory domain
- Centralized management for ESXi hosts and virtual machines

---

## Cluster Configuration

Cluster Name: Main_Cluster

### High Availability (HA)
- Automatically restarts virtual machines in case of host failure
- Ensures service continuity and minimal downtime

### Distributed Resource Scheduler (DRS)
- Balances workloads across ESXi hosts
- Automatically optimizes resource distribution

---

## vMotion

- Live migration of running virtual machines between ESXi hosts
- Zero downtime during migration
- Dedicated network used for vMotion traffic

---

## Storage Configuration

- Shared storage implemented using iSCSI
- Common datastore accessible by both ESXi hosts
- Enables vMotion and HA functionality

---

## Resource Management

### Resource Pools

- Operations Pool
  - VM01 (high priority workload)

- Test Pool
  - VM02, VM03, VM04 (lower priority workloads)

---

## Cluster Rules

- Anti-affinity rule configured:
  - VM02 and VM03 cannot run on the same ESXi host

---

## Fault Tolerance (FT)

Fault Tolerance was not implemented due to lab limitations.

Concept:
- Provides zero-downtime protection for critical workloads
- Runs a secondary VM in parallel on another host

---

## Troubleshooting Scenarios

### vCenter 503 Error
- Cause: services not fully initialized
- Resolution: restarted vCenter services

### iSCSI Storage Issue
- Cause: network or configuration mismatch
- Resolution: rescan storage adapters and verify connectivity

### VM Network Issue
- Cause: incorrect portgroup configuration

- Fix: corrected network mapping

---

## Screenshots

Add screenshots in /screenshots folder:

- Cluster view

- vMotion migration

- HA failover test

- Resource Pool configuration

- ---

## Key Achievements

- Designed and implemented an enterprise-grade virtual datacenter architecture
- Successfully configured High Availability (HA), Distributed Resource Scheduler (DRS), and vMotion
- Implemented Active Directory-based identity and access management
- Integrated centralized authentication with VMware vCenter Server
- Designed workload prioritization using Resource Pools
- Implemented shared storage infrastructure using iSCSI
- Created and tested real-world troubleshooting scenarios (vCenter, storage, and networking issues)

- ---

## Conclusion

This project demonstrates hands-on experience in designing, deploying, and managing enterprise virtual infrastructure using VMware technologies.

It covers core datacenter concepts including compute virtualization, storage architecture, networking, identity management, high availability, and workload optimization.

The implementation reflects real-world enterprise scenarios, including centralized management, service continuity, and infrastructure troubleshooting, providing a strong foundation for cloud and virtualization engineering roles.

