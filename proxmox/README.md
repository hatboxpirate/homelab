Proxmox Host: Dell Precision 5820
This document outlines the setup and configuration of the Proxmox Virtual Environment (PVE) host that serves as the foundation for my homelab.

1. Hardware Specifications 
The server is a Dell Precision 5820 Workstation. I chose this hardware for its balance of processing power, expandability, and quiet operation.

Model: Dell Precision 5820 Tower

CPU: Intel Xeon W-2135 CPU @ 3.70GHz 

RAM: 32GB DDR4 ECC

VM Storage: 2x 512GB NVME SSDs

Network Interface Cards (NICs):

Onboard Intel I219-LM (Used for Proxmox Management and VMs)

Gigabit Dual NIC(Passed through to pfSense)

2. Proxmox Installation
The installation process was straightforward, following the standard Proxmox VE installation guide.

Proxmox VE Version: 9.0.3

Installation Medium: USB drive created with BalenaEtcher.

Filesystem: ext4

3. Storage Configuration 
Storage is configured to separate the Proxmox OS from the virtual machine disk images.

OS Drive (local): The 256GB NVMe SSD is dedicated to the Proxmox OS and ISO images.

VM Storage (local-lvm): The two 5112GB NVMe SSDs are configured in a ZFS mirror for redundancy and data integrity for all VM and container storage. This provides fault tolerance if one of the SSDs fails.

4. Post-Installation Tweaks
After the base installation, I performed the following steps to prepare the host:

Disabled Enterprise Repository: The enterprise repository was disabled to prevent subscription notices, as this is a non-production environment.

Enabled No-Subscription Repository: Added the Proxmox VE No-Subscription Repository to get timely community-tested updates.

Configured Network: Set a static IP address for the management interface to ensure consistent access to the Proxmox web UI.
