Proxmox Host: Dell Precision 5820
This document outlines the setup and configuration of the Proxmox Virtual Environment (PVE) host that serves as the foundation for my homelab.

### 1. Hardware Specifications 

The server is a Dell Precision 5820 Workstation. I chose this hardware for its balance of processing power, expandability, and quiet operation.

| Component          | Specification                             | Notes                                     |
| ------------------ | ----------------------------------------- | ----------------------------------------- |
| **Model** | `Dell Precision 5820 Tower`               |                                           |
| **CPU** | `Intel Xeon W-2135 CPU @ 3.70GHz `             | 12 Cores                        |
| **RAM** | `32GB DDR4 ECC`                           | Error Correcting Code memory for stability|
| **Boot Drive** | `1x 256GB NVMe SSD`                       | Used for Proxmox OS (`local`)             |
| **VM Storage** | `2x 512GB NVME SSDs`                        | Configured as a ZFS Mirror for redundancy |
| **Management NIC** | Onboard `Intel I219-LM`                   | Used for the Proxmox management and VMs              |
| **VM NIC** | `Gigabit Dual NIC`               | Passed through to `pfSense` VM            |

### 2. Proxmox Installation
The installation process was straightforward, following the standard Proxmox VE installation guide.

Proxmox VE Version: 9.0.3

Installation Medium: USB drive created with BalenaEtcher.

Filesystem: ext4

### 3. Storage Configuration 
Storage is configured to separate the Proxmox OS from the virtual machine disk images.

OS Drive (local): The 256GB NVMe SSD is dedicated to the Proxmox OS and ISO images.

VM Storage (local-lvm): The two 5112GB NVMe SSDs are configured in a ZFS mirror for redundancy and data integrity for all VM and container storage. This provides fault tolerance if one of the SSDs fails.

### 4. Post-Installation Tweaks
After the base installation, I performed the following steps to prepare the host:

Disabled Enterprise Repository: The enterprise repository was disabled to prevent subscription notices, as this is a non-production environment.

Enabled No-Subscription Repository: Added the Proxmox VE No-Subscription Repository to get timely community-tested updates.

Configured Network: Set a static IP address for the management interface to ensure consistent access to the Proxmox web UI.

### 5. Host Management & Automation Tools

To streamline the creation of LXC containers, I use customized versions of the Proxmox VE Helper Scripts by `tteck`. I store the scripts locally in this repository to ensure reproducibility and track any modifications I make.

The scripts are located in the [`/proxmox/scripts/`](./scripts/) directory and are run directly from the Proxmox host's shell.

### 6. Guest VMs and Containers

This table provides a high-level overview of the guests running on this Proxmox host. Each guest has its own detailed documentation in its respective directory.

| ID   | Hostname        | Type      | Service / Role             | Documentation Link                           |
| ---- | --------------- | --------- | -------------------------- | -------------------------------------------- |
| xxx  | `pfsense`       | VM        | Firewall & Router          | [Link](../pfsense/README.md)                 |
| xxx  | `omv`           | VM        | NAS (OpenMediaVault)       | [Link](../openmediavault/README.md)          |
| xxx  | `media-stack`   | Container | *Arr Stack & Media Server* | *Coming Soon* |
