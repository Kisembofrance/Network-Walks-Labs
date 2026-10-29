### Week 1 - Cyber Security Lab Setup (PM1)

This repository contains the configuration, troubleshooting steps, and validation benchmarks for the Week 1 Network Walks cyber security lab environment. 

### Lab Objectives

* Configure an isolated virtual infrastructure sandbox layout.
* Deploy and optimize a pre-built Kali Linux workspace image environment.
* Establish standard manual static IP mapping.
* Validate external internet routing and domain name system translations.

### Environment Architecture Details

* **Hypervisor Platform:** Oracle VirtualBox 7.x
* **Guest Operating System:** Kali Linux 2026.3 (x86_64)
* **Network Mode Allocation:** Dedicated Isolated NAT Network
* **Subnet Schema Allocation:** 10.0.0.0/24
* **Hacking Machine Identity Static IP:** 10.0.0.2
* **Virtual Subnet Default Router Gateway:** 10.0.0.1
* **Primary Public Name Resolver Server:** 8.8.8.8

### Engineering & Troubleshooting Challenges Resolved

### 1. Host Machine Drive Space Failure (WinRAR Write Error)

* **Problem:** Unpacking the 3.60 GB .7z virtual machine image archive failed with a WinRAR disk write error.
* **Analysis:** The archive expanding sequence requires 15+ GB of free storage workspace. The local C: drive host space bounds were exhausted.
* **Resolution:** Relocated the archive payload downpath entirely to Local Disk (D:), which possessed ample free storage volumes, allowing clean expansion.

### 2. Network Routing Failure (Destination Host Unreachable)

* **Problem:** Internal terminal interface ping connectivity testing returned an address unreachable routing loop.
* **Analysis:** The global VirtualBox NATNetwork preferences defaulted to an IPv4 prefix schema map of 10.0.2.0/24, failing to recognize or route packets belonging to the guest's 10.0.0.2 manual network boundary.
* **Resolution:** Adjusted the hypervisor's global network controller properties path. Reconfigured the IPv4 prefix mapping accurately to 10.0.0.0/24, disabled unneeded IPv6 stacks, and committed changes. Outbound data flows stabilized instantly with 0% packet loss.

### Verification Checkpoint Snapshots

* **System Restore Landmark Point:** Saved configuration baseline state labeled Clean Baseline Setup.# Network-Walks-Labs
