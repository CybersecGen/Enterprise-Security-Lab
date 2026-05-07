# Enterprise Security Lab (Homelab – SOC Simulation & Infrastructure Failure Analysis)

**Environment:** Isolated Virtual Enterprise Lab (Decommissioned)  
**Domain:** Systems Administration / SOC Operations / Network Security / Active Directory / SIEM  
**Focus:** Enterprise infrastructure design, security monitoring, and adversary simulation under real-world resource constraints  

---

## 1. Overview

GxnSec is a self-built enterprise homelab designed to simulate a small corporate IT and security environment.

The project was used to develop practical skills in:

- Windows Active Directory administration  
- Network architecture and segmentation  
- Endpoint and server management  
- Security monitoring and SIEM operations  
- Basic offensive security simulation  
- Infrastructure troubleshooting and system reliability analysis  

The environment is no longer active due to stability and resource limitations, but the project provided valuable hands-on experience in enterprise system design and security operations.

---

## 2. Objectives

- Design and implement a functional enterprise network environment  
- Deploy Active Directory services for centralized identity management  
- Configure Windows and Linux endpoints in a domain environment  
- Simulate internal attack scenarios using adversary tools  
- Implement centralized logging and SIEM-based monitoring  
- Develop troubleshooting skills across distributed systems  

---

## 3. Architecture

### 3.1 Core Infrastructure

- **Domain Controller:** Windows Server (Active Directory, DNS, DHCP)  
- **Endpoints:** Windows 11 Enterprise, Ubuntu Desktop  
- **Security Stack:** Wazuh SIEM, Security Onion IDS/Network Monitoring  
- **Attack Platform:** Kali Linux  
- **Supporting Services:** Internal mail simulation (Postfix / MailHog)  

---

### 3.2 Network Configuration

- Network Type: VirtualBox NAT Network (isolated environment)  
- Subnet: 10.0.0.0/24  
- DHCP Range: 10.0.0.100 – 10.0.0.200  

---

### 3.3 Host Configuration

| Hostname            | IP Address       | Role |
|---------------------|------------------|------|
| gxnsec-dc           | 10.0.0.5         | Domain Controller (AD DS, DNS, DHCP) |
| gxnsec-admin        | 10.0.0.8         | Corporate Server |
| gxnsec-sec-box      | 10.0.0.10        | SIEM / Security Monitoring Server |
| gxnsec-sec-work     | 10.0.0.103       | SOC Analyst Workstation |
| gxnsec-win-client   | 10.0.0.100       | Windows Endpoint |
| gxnsec-linux-client | 10.0.0.101       | Linux Endpoint |
| gxnsec-attacker     | Dynamic          | Attack Simulation Host |

---

## 4. Security Stack

| Component | Tool | Purpose |
|-----------|------|---------|
| SIEM | Wazuh | Log aggregation, correlation, alerting |
| Network Monitoring | Security Onion | Traffic analysis and intrusion detection |
| Endpoint Logging | Sysmon + Windows Event Logs | Endpoint visibility |
| Attack Simulation | Kali Linux | Adversary emulation and testing |

---

## 5. Implementation

### 5.1 Virtualization & Network Setup

- Built using VirtualBox NAT networking in an isolated lab environment  
- Configured internal communication between all systems  
- Used VM snapshots for rollback and iterative testing  

---

### 5.2 Active Directory Deployment

- Installed and configured Windows Server as Domain Controller  
- Configured DNS for internal name resolution  
- Joined Windows endpoints to domain  
- Enabled centralized authentication and identity management  

---

### 5.3 Endpoint & Service Deployment

- Provisioned Windows and Linux endpoints  
- Configured user accounts and access control policies  
- Deployed supporting services for internal simulation purposes  

---

### 5.4 SIEM & Monitoring Deployment

- Installed Wazuh for centralized logging and alerting  
- Integrated Sysmon and Windows Event Logs for endpoint telemetry  
- Deployed Security Onion for network-level monitoring and IDS visibility  
- Established baseline alerting for suspicious behavior detection  

---

## 6. Security Operations & Attack Simulation

Simulated adversary techniques using Kali Linux to replicate realistic attack scenarios:

- Network reconnaissance and enumeration  
- Credential-based initial access attempts  
- Privilege escalation techniques  
- Lateral movement across domain infrastructure  
- Persistence mechanisms  
- Simulated data exfiltration scenarios  

---

## 7. Defensive Operations (SOC Simulation)

From a SOC perspective, the following activities were performed:

- Monitoring SIEM alerts in Wazuh  
- Investigating suspicious endpoint and network activity  
- Correlating logs across multiple systems  
- Validating detection coverage across simulated attack paths  
- Identifying gaps in logging and visibility  

---

## 8. Engineering Limitations & System Stability Issues

The environment experienced significant operational constraints under sustained load.

### 8.1 SIEM Instability

- Wazuh stack exhibited instability during extended runtime  
- Elasticsearch performance bottlenecks under high log ingestion  
- Frequent service degradation under multi-VM load  

---

### 8.2 Network & Infrastructure Challenges

- DNS misconfigurations impacted Active Directory reliability  
- Intermittent VM-to-VM communication issues  
- Time synchronization inconsistencies affected authentication stability  

---

### 8.3 Hardware Constraints

- 32GB RAM system reached resource saturation under full lab load  
- CPU bottlenecks during concurrent security tool execution  
- Storage and I/O pressure from multiple virtual machines  

---

### 8.4 Platform Limitations

- Migration to Apple Silicon reduced virtualization compatibility  
- Performance limitations using UTM virtualization environment  
- Reduced support for enterprise security tooling  

---

### 8.5 Outcome

Due to the above constraints, the environment was decommissioned after multiple rebuild cycles.

---

## 9. Key Lessons Learned

- Enterprise environments require careful resource planning and architecture design  
- Active Directory stability depends heavily on DNS and time synchronisation  
- SIEM platforms require dedicated compute resources for reliable operation  
- Incremental infrastructure deployment is more effective than full-stack builds  
- Distributed systems troubleshooting is a critical skill in both SOC and cloud roles  
- Real-world security engineering involves balancing visibility, performance, and cost  

---

## 10. Project Status

This environment has been archived due to:

- Hardware limitations under sustained workload  
- SIEM instability in constrained environments  
- High maintenance overhead from repeated rebuild cycles  

---

## 11. Future Improvements

If rebuilt, the following improvements would be implemented:

- Migration to cloud infrastructure (Azure / AWS)  
- Separation of SIEM components into dedicated scalable services  
- Infrastructure-as-Code (Terraform / Ansible) deployment  
- Modular phased rollout approach instead of monolithic design  
- Cloud-native logging and detection pipelines  

---

## 12. Summary

This lab provided practical experience in enterprise system administration, identity management, network architecture, and security operations.

While the environment was not maintained in a production-stable state, the process of designing, deploying, and troubleshooting it provided valuable insight into:

- Enterprise infrastructure design  
- Security monitoring and detection engineering  
- System reliability and scalability constraints  
- Real-world limitations of SIEM and logging platforms  

These experiences directly support a transition into SOC engineering and cloud security engineering roles, particularly in areas such as identity security, monitoring architecture, and detection engineering.
