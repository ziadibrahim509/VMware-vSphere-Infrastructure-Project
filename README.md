# VMware vSphere Enterprise Virtualization Architecture

An enterprise-grade cloud computing and virtualization infrastructure project designed to abstract, pool, and orchestrate physical hardware resources into highly available, resilient, and scalable software-defined data center (SDDC) entities.

---

## 👥 Project Team
* **Tarek Abdelrahman Elsayed**
* **Ziad Ibrahim Mohamed**
* **Yousef Mohamed aboelata**

**Supervised by:** Eng. Ekram Abdelwahab  
**Institution:** Information Technology Institute (iTi)

---

## 📌 Project Overview
This project presents the full engineering lifecycle of a high-performance virtualized ecosystem using the **VMware vSphere Suite**. It establishes a reliable virtual infrastructure capable of running mission-critical enterprise workloads (such as healthcare datastores and databases) by enforcing centralized resource governance, business continuity parameters, automated workload distribution, and robust storage fabrics.


---

## 🏗️ Core Architectural Components

### 1. VMware ESXi (Type 1 Hypervisor)
* Operates directly on bare-metal physical servers to completely decouple compute, memory, and networking layers from physical dependencies.
* Implements robust hardware consolidation metrics while delivering native performance, secure-boot system integrity, and full-disk VM encryption capabilities.
* **Essential VM Footprints Used:**
  * `.vmx` - Primary Virtual Machine Configuration Scheme.
  * `.vmdk` - Virtual Disk File holding the guest OS and persistent data storage layers.
  * `.nvram` - Persistent state for VM BIOS/UEFI firmware settings.
  * `vmware.log` - Sequential environment telemetry and execution system records.

### 2. Centralized Orchestration: VMware vCenter Server
* Deployed as an optimized virtual appliance running over a secure Linux-based **Photon OS** instance.
* Aggregates distributed hypervisors under a single unified pane of glass with granular inventory logging, cross-infrastructure automation, and centralized API endpoints.
* Architectural deployment scale guidelines followed based on infrastructure dimensions:
  * **Tiny Environment:** Up to 10 Hosts / 100 VMs (2 vCPUs, 12 GB RAM)
  * **Small Environment:** Up to 100 Hosts / 1000 VMs (4 vCPUs, 19 GB RAM)
  * **Medium Environment:** Up to 400 Hosts / 4000 VMs (8 vCPUs, 28 GB RAM)
  * **Large Environment:** Up to 1000 Hosts / 10000 VMs (16 vCPUs, 37 GB RAM)
  * **X-Large Environment:** Up to 2500 Hosts / 45000 VMs (24 vCPUs, 56 GB RAM)

---

## 🌐 Virtual Networking Topologies

The network topology contains segmented traffic lanes designed to ensure logical isolation, scalability, and robust performance policies.

* **vSphere Standard Switch (vSS):** Handled simple host-level localized parameters and port rules mapped with independent configurations.
* **vSphere Distributed Switch (vDS):** Implemented centralized fabric spanning multiple cluster hosts to inject strict uniform policies (traffic shaping, NetFlow diagnostics, Port Mirroring, and Private VLAN structures).
* **Logical Structuring Objects:**
  * **Port Groups:** Bridges logical boundary controls, VLAN tags, and multi-NIC NIC teaming setups.
  * **VMkernel Adapters (`vmk`):** Exclusively dedicated to low-latency host infrastructure lines, explicitly mapping out specialized lanes:
    * `Management Traffic` (vCenter/SSH host-level interface communication)
    * `vMotion Traffic` (Real-time live execution migration context state sync)
    * `Provisioning Traffic` (Rapid template replication and cloning transfers)
    * `Storage Traffic` (iSCSI block-level access and file-level NFS bindings)
    * `vSAN Traffic` (Software-defined distributed multi-node storage pool sync)
    * `FT Logging` (Continuous synchronous runtime transaction mirror execution lines)

---

## 💾 Storage Layer Architecture
The storage layout separates block-level performance paths from file-level utility storage targets to guarantee absolute operational persistence:

* **Direct-Attached Storage (DAS):** Leveraged localized physical disks (HDDs/SSDs) for fast sandboxed non-critical environments.
* **Network-Attached Storage (NAS - NFS protocol):** Shared file-level container architecture hosted over standard TCP/IP lanes, ideal for holding template files, backup binaries, and master `.iso` collections.
* **Storage Area Network (SAN):** High-throughput block storage presented as Logical Unit Numbers (LUNs) formatted with the clustered **VMFS (VMware File System)**, empowering concurrent host execution structures.

---

## 🚀 Advanced Business Continuity & Cluster Operations

### 🔄 Dynamic Live Workload Mobility (Migrations)
* **Cold Migration:** Non-disruptive migration path for offline virtual environments during scheduled maintenance.
* **vMotion:** Moves active running memory allocations and current CPU contexts across physical hosts in real-time without user or service interruption.
* **Storage vMotion:** Leverages Changed Block Tracking (CBT) increments to move operational virtual disk arrays between heterogeneous physical arrays live.
* **Shared Nothing vMotion:** Orchestrates simultaneous compute state vMotion and storage state migration across distinct hosts lacking overlapping physical storage fabrics.

### 🛡️ Enterprise High Availability (vSphere HA)
* Employs the **Fault Domain Manager (FDM)** agent framework across cluster members to continuously run health checks.
* Utilizes a highly robust **Master-Slave Selection and Election Protocol** where a Master Node evaluates heartbeat health checks over the management network within 15-second tracking phases.
* Integrates **Datastore Heartbeating** to effectively isolate structural network split-brain scenarios from true bare-metal host crashes, orchestrating immediate automated VM failover restarts onto remaining healthy host footprints.
* Configures strict **Admission Control** validation loops to enforce cold standby cluster capacity requirements, mitigating resource starvation risks during failure scenarios.

### ⚖️ Workload Balancer & Resource Optimization (vDRS)
* Continuously calculates compute consumption across the host cluster ecosystem.
* Triggers automatic micro-vMotion load adjustments to resolve resource contention issues and maximize performance.
* Features **Distributed Power Management (DPM)** to dynamically put redundant hardware hosts into sleep states during minimal system runtime demands, drastically driving down power overhead.

### 🪞 Continuous Zero-Downtime Operations (Fault Tolerance - FT)
* Spawns a secondary synchronized virtual entity running in real-time shadow execution sync with the primary processing instance.
* Delivers complete hardware failover isolation with zero data loss or connection drops for critical application engines.

---

## 🛠️ Standardization & Lifecycle Management
* **VM Templates:** Standardized master gold images stored in unified **Content Libraries** for automated, policy-compliant VM provisioning.
* **vSphere Lifecycle Manager (vLCM):** Centralized lifecycle controller enforcing automated hypervisor patching, drivers, and server firmware state baselines.
