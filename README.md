# Automated Inventory Synchronization (Proxmox VE to NetBox DCIM)
> An automated infrastructure synchronization pipeline that fetches Virtual Machine (VM) and Linux Container (LXC) data from Proxmox VE and synchronizes it to NetBox (Data Center Infrastructure Management / DCIM) using Ansible and REST APIs.

---

## Project Overview
In large-scale data center operations, discrepancies often occur between actual virtual servers running on virtualization platforms and manual documentation records. This project addresses the challenge at the Department of Communication, Informatics, Statistics, and Code of Bekasi City (Diskominfostandi) by automating the synchronization of 168+ VM/LXC assets from **Proxmox VE** to **NetBox**, which serves as the ultimate *Source of Truth*.

---

## Tech Stack & Tools
* **Automation Engine:** Ansible (Playbooks).
* **Virtualization Source:** Proxmox VE (KVM & LXC).
* **DCIM / Source of Truth:** NetBox.
* **Integration Protocol:** REST API (HTTP Request/Response, JSON).
* **Operating System:** Linux Server.
* **Version Control:** Git & GitHub.

---

## Architecture & Workflow
1. **Data Retrieval:** Ansible connects to **Proxmox VE** and fetches actual operational data (VMID, hostname, operational status, IP addresses, MAC addresses, CPU, RAM, storage, and tags) via REST API.
2. **Data Processing & Comparison:** The playbook processes and compares the retrieved data against existing records in **NetBox**.
3. **Automated Actions (CRUD Logic):** 
   * **Create:** Adds new VMs/LXCs detected in Proxmox that do not yet exist in NetBox.
   * **Update:** Modifies attributes if changes occur in the virtual environment.
   * **Delete / Prune:** Handles decommissioned servers.
4. **Validation & Logging:** Generates execution logs to validate synchronization success and prevent duplicate entries

---

## Repository Structure
```text
proxmox-netbox-inventory-sync/
├── playbooks/
│   └── sync_proxmox_to_netbox.yml   # Main Ansible synchronization playbook
├── inventory/
│   └── hosts.ini                    # Target environment inventory configuration
└── README.md                        # Project documentation
```

## Key Features
- **Automated Asset Discovery: Automatically detects new, modified, or deleted virtual servers from Proxmox VE without manual data input.**
- **Reliable Source of Truth: Maintains accurate documentation inside NetBox DCIM, eliminating human error and data discrepancies.**
- **REST API Integration: Leverages secure HTTP endpoints to seamlessly bridge the virtualization platform and inventory management system.**

## Author
**Salsabila Bachtiar**
- Informatics Student | Aspiring DevOps & Cloud Engineer  
[LinkedIn](https://www.linkedin.com/in/salsabila-bachtiar-30161724a) | [GitHub](https://github.com/bache1)
