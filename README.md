# My Homelab Journey 

Welcome to my homelab repository! This is the central hub where I document the architecture, configurations, and ongoing projects within my personal lab environment. The primary goal of this homelab is to be a playground for learning, experimenting with new technologies, and self-hosting useful services.

This repository serves as my "Infrastructure as Code" and documentation source of truth.

---

##  Current Infrastructure

The lab is in its foundational stage, focusing on establishing a robust and secure core network and virtualization platform.

* **Virtualization Host:** The entire lab is built on a single `Dell Precision 5820` workstation running **Proxmox VE**. This hypervisor hosts all virtual machines and containers, providing a flexible and powerful foundation.
    *  *Detailed host configuration can be found in the [`/proxmox`](./proxmox/) directory.*

* **Firewall & Routing:** Network security and routing are handled by a virtualized instance of **pfSense**. This gives me granular control over network traffic, firewall rules, and VPN access.
    *  *VM setup and initial configuration notes are in the [`/pfsense`](./pfsense/) directory.*

* **Network Segmentation:** The physical network is powered by a `UniFi Lite 8 PoE` switch. I am in the process of implementing VLANs to segment traffic for security and management.
    *  *The network diagram and VLAN plan are documented in the [`/networking`](./networking/) directory.*

---

##  Project Roadmap

This is a living list of projects I plan to tackle. Completed items will be checked off as the lab evolves.

### Near-Term Goals
- [ ] **Self-Hosted NAS:** Deploy **OpenMediaVault (OMV)** in a VM with dedicated storage passthrough to serve as a centralized network-attached storage solution for files and backups.
- [ ] **Media Server Stack:** Build a complete media ecosystem using the *arr stack (`Sonarr`, `Radarr`, `Prowlarr`) alongside `Jellyfin` for streaming.
- [ ] **Automated Backups:** Configure Proxmox Backup Server or a similar solution to ensure all critical VMs and data are backed up regularly.

### Future Plans
- [ ] **Cybersecurity Lab:** Create a dedicated, isolated VLAN to build a security lab for learning penetration testing and defensive security tools (e.g., Security Onion, Kali Linux).
- [ ] **Home Automation:** Deploy `Home Assistant` to integrate and automate various smart home devices.
- [ ] **Infrastructure Automation:** Learn and implement **Ansible** to automate the configuration and deployment of new VMs and services.

---

##  Repository Structure

This repository is organized by project or technology area.

* **/proxmox/**: Contains documentation for the main PVE host hardware and software configuration.
* **/pfsense/**: Holds notes and configuration details for the virtualized pfSense firewall.
* **/networking/**: Includes network diagrams, VLAN plans, and switch configurations.
