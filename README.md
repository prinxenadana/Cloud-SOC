# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud Honeynet / SOC](https://i.imgur.com/ZWxe03e.jpg)

## Introduction

In this project, I built a mini honeynet in Azure and ingestes log sources from various resources into a Log Analytics workspace, which is then used by Microsoft Sentinel to build attack maps, trigger alerts, and create incidents. I measured some security metrics in the insecure environment for 24 hours, applied some security controls to harden the environment, measured metrics for another 24 hours. The metrics we will show are:

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture Before Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/aBDwnKb.jpg)

## Architecture After Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/YQNa9Pp.jpg)

The architecture of the  honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

BEFORE: Initially, all resources were set up to be accessible from the internet. Virtual Machines and other resources had wide-open Network Security Groups and firewalls, allowing access from anywhere.

AFTER: Following the changes, Network Security Groups were configured to only allow traffic from designated admin workstations. Additionally, resources were protected by their firewalls and by using Private Endpoints

## Attack Maps Before Hardening / Security Controls
![Screenshot 2024-04-28 124432](https://github.com/prinxenadana/Cloud-SOC/assets/168138441/89ad143f-4f6b-4940-a76e-43edf1e34160)

![Screenshot 2024-04-28 124055](https://github.com/prinxenadana/Cloud-SOC/assets/168138441/00a31851-bd3f-48cf-a9f4-40e833d267c6)

![Screenshot 2024-04-28 124156](https://github.com/prinxenadana/Cloud-SOC/assets/168138441/bda8fc4e-aa5d-4a27-882d-f9381433ebf1)

![Screenshot 2024-04-28 124527](https://github.com/prinxenadana/Cloud-SOC/assets/168138441/136d185a-b648-418e-9dee-07f9d3bb6f2c)




## Metrics Before Hardening / Security Controls and After Hardening /Security Controls

![image](https://github.com/prinxenadana/Cloud-SOC/assets/168138441/e3cd7978-e1f7-4149-8678-50ca47776d99)

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity  after hardening.```


## Conclusion
In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

