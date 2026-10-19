# SOC-Analyst-HomeLab
Hands-on SOC Analyst portfolio project demonstrating log collection, threat detection, alert analysis, incident investigation, and security documentation.


<img src="https://img.shields.io/badge/Objective-Cybersecurity-000000?style=for-the-badge&logo=hackthebox&logoColor=00ff88" />

The goal of this project is to build a small, realistic SOC environment where I can practice the daily activities of a SOC Analyst L1.
<ul>
  <li>Collecting security telemetry</li>
   <li>Monitoring Windows endpoints</li>
   <li>Investigating security alerts</li>
   <li>Performing alert triage</li>
   <li>Mapping activity to MITRE ATT&CK</li>
   <li>Performing basic threat hunting</li>
   <li>Writing incident reports</li>
   <li>Creating and testing detection rules</li>
   <li>Identifying suspicious activity</li>
   <li>Extracting Indicators of Compromise (IOCs)</li>
</ul>

# 🏗️ Lab Architecture
                         🛡️ SOC HOME LAB
                              │
                ┌─────────────┴─────────────┐
                │                           │
          Kali Linux                   Windows 10
         Attacker VM                  Victim VM
                │                     Sysmon + UF splunk
                │                           │
                │     Simulated Attacks     │
                └─────────────┬─────────────┘
                              │
                       Security Events
                              │
                              ▼
                     ┌─────────────────┐
                     │  Ubuntu Server  │
                     │     Splunk      │
                     │ Search + Report │
                     │ + Dashboard     │
                     └────────┬────────┘
                              │
                              ▼
                     ┌─────────────────┐
                     │   SOC Analyst   │
                     │                 │
                     │ Alert Triage    │
                     │ Investigation   │
                     │ Threat Hunting  │
                     │ Incident Report │
                     └─────────────────┘

# Network
Use an isolated Host-Only/Internal Network for the lab:

              SOC-LAB Network
             192.168.56.0/24
                     │
       ┌─────────────┼─────────────┐
       │             │             │
   (Kali VM)       (Windows 10)    (Ubuntu Server)
  .56.xx           .56.xx          .56.xx
  ATTACKER         VICTIM          SPLUNK


 
<table>
   <td>
Technology Purpose</td></table>
</table>
<ul>
  <li>Splunk -> SIEM, log collection and alert monitoring.</li>
  <li>Sysmon -> Windows endpoint telemetry.</li>
  <li>Windows -> Endpoint monitoring.</li>
  <li>Linux -> SOC infrastructure and security tools</li>
  <li>MITRE Attack -> Adversary behavior mapping</li>
</ul>

# Lab Specifications 
<ul>
  <li><b>Host Hardware:</b> Dell Optiplex XE2,16GB RAM,256GB SSD </li>
  <li><b>Network:</b> Dual bridges (LAN + isolated lab network)</li>
  <li><b>VM resources:</b> 
    Kali-attacker: 1 core, 3GB RAM, 40GB disk
    Windows 10-victim: 2 cores, 3GB RAM, 35GB disk </li>
    Splunk-Server: 2 cores, 4GB RAM, 40GB disk
</ul>

#Lab Components 
<h2>SIEM-SPlunk</h2>
<li>Splunk Enterprise receives Sysmon logs from the Windows 10 endpoint via the Universal Forwarder. Used for detection engineering, SPL queries, and adversary simulation validation.</li>
<h2>Kali-Linux</h2>
<li>Attack platform on an isolated network segment. Used for adversary simulation against the Windows 10 target.</li>
<h2>Windows-10</h2>
<li>Target endpoint with Sysmon (SwiftOnSecurity config), Splunk Universal Forwarder, and splunk server installed on ubuntu.Dual-NIC for isolated attack surface and log forwarding.</li>

