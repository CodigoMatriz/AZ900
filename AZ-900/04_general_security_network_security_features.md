> [Azure Fundamentals Part 4: Describe General Security and Network Security Features](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-general-security-network-security-features/)  
> Microsoft Learn

[TOC]

# Protect Against Security Threats on Azure

Security, a small word for a significant concept with so many factors to consider in order to protect your applications and data.

## Protect Against Security Threats by Using Azure Security Center

### What's Azure Security Center

A monitoring service that provides visibility of your **security posture** across all of your services, be it on Azure or on-premises.

> Security Posture  
> Refers to cybesecurity policies and controls and how well security threats can be predicted, prevented and responded

* Monitor security acorss on-premises and cloud
* Apply required security settings as new resources come online, automatically
* Security recommendations based on current configs, resources and networks
* Continuous resource monitoring and automatic security assessments to identify potential vulnerabilities before they can be exploited
* Detect and block malware from being installed on VMs and other resources using machine learning
* Adaptive controls to define allowed applications
* Detect and analyze potential inbound attacks and investigate threats and any post-breach activity that might have occurred.
* Provide just-in-time access control for network ports. 

### Understand Your Security Posture

Resources are analyzed against security controls of any governance policy assigned, viewing overall regulatory compliance from a security perspective from one place.

<div align="center" style="min-width: 700px; background: #FFF; color: #000">
	<img src="./assets/security_center.png" />
	<p><small>Azure Security Center</small></p>
</div>

Say we want to comply with the Payment Card Industry's Data Security Standard (PCI DSS), the above report demonstrates not all resources are up to par.

**Resource security hygience** is a section that details resource health from a security perspective and recommendations are categorized as low, medium and high.

<div align="center" style="min-width: 700px; background: #FFF; color: #000">
	<img src="./assets/resource_security_hygience.png" />
	<p><small>Resource Security Hygience</small></p>
</div>

#### What's Secure Score?

A measurement of an organization's security posture, based on the percentage of security controls (groups of related security recommendations) satisfied. Remediating all recommendations within a single resource wtihin a control improves the score.

Azure Security Center has a centralized dashboard for monitoring and working on Azure resource security like identities, data, apps, devices and infrastructure.

Secure score helps you:

* Report on the current state of your organization's security posture.
* Improve your security posture by providing discoverability, visibility, guidance, and control.
* Compare with benchmarks and establish key performance indicators (KPIs).

### Protect Against Threats

Security Center has defense capabilities for VMs, network security and file integrity.

* **Just-in-Time VM Access**  
Blocks traffic by default to specific network ports of VMs, but allows traffic for a specified time when an admin requests and approves it.
* **Adaptive Application Controls**  
Control which applications are allowed to run on VMs. Machine learning is used in the background by Security Center to look at running processes within the VM. Creates exception rules for each resource group that holds the VMs and provides recommendations.
* **Adaptive Network Hardening**  
Monitor and compare VM internet traffic to patterns with the orgs current network security group (NSG) settings. Which can generate recommendations whether NSGs should be further locked down.
* **File Integrity Monitoring**  
Configure monitoring for changes on important files, registry settings, applications and other aspects that may indicate a security risk

### Respond to Security Alerts

Able to have a centralized view of security alerts with the ability to dismiss false alerts, investigate further, remediate alerts manually or use an automated response with _workflow automation_. 

Workflow automation uses Azure Logic Apps and Security Center connectors to trigger by a threat detection alert or Security Center recommendation. Can configure the logic app to run an action like send an email or post a message to a Microsoft Teams channel (I prefer Slack).

# Detect and Respond to Security Threats by Using Azure Sentinel

Large scale security management can benefit from a dedicated security information and event management (SIEM) system, which aggregates security data from different sources that support an open-standard logging format.

## Azure Sentinel capabilities

Azure Sentinel is Microsfot cloud-based SIEM.

* **Collect cloud data at scale**  
Collect data across all users, devices, applications and infrastructure (on-premise / cloud)
* **Detect previously undetected threats**  
Minimize false poisitives by using Microsoft's comprehensive analytics and threat intellifence
* **Investigate threats with artificial intelligence**  
Examine suspicious activities at scale, tapping into years of cybersecurity experience from Microsoft
* **Respond to incidents rapidly**  
Use built-in orchestration and automation of common tasks

## Connect Your Data Sources

