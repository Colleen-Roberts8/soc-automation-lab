# soc-automation-lab
Automated SOC Incident Response &amp; Threat Intelligence Pipeline using Wazuh, Shuffle SOAR, VirtusTotal API, and TheHive 5.

# Automated SOC Incident Response & Threat Intelligence Pipiline

## Overview
This project demonstrates an automated Security Operations Center (SOC) workflow designed to detect endpoint threats, enrich alert telemetry, and automate incident ticketing in real time.

## Architecture & Data Flow
1. **Detection:** Windows 11 Endpoint generates security events (e.g., Mimikatz credential dumping / T1003).
2. **SIEM Analysis:** Wazuh Manager parses and triggers an alert via rule '100002'.
3. **SOAR Orchestration:** Shuffle SOAR catches the Wazuh webhook payload.
4. **Regex Extraction:** SHA-256 hashes are extracted from event logs using dynamic regex parsing.
5. **Threat Intelligence Enrichment:** Shuffle queries VirusTotal v3 API for file reputation analysis.
6. **Incident Management:** Enriched alerts are automatically created in TheHive 5 for analyst triage.
7. **Notification:** Automated email alerts are dispatched to the SOC team.

## Technologies & Frameworks
* **SIEM:** Wazuh
* **SOAR:** Shuffle SOAR
* **Threat Intel:** VirusTotal v3 API
* **Incident Response:** TheHive 5
* **Virtualization/OS:** Ubuntu Server, Windows 11 Enterprise, VirtualBox
* **Frameworks:** MITRE ATTACK (T1003 - Credential Dumping)

## Key Achievements & Learnings
* Configured REST API authentication, custom service accounts, and API keys across isolated security tools.
* Handled dynamic variable mapping in Shuffle ('$exec.id', '$Webhook_1.body...') to overcome payload formatting and duplicate entry errors,
* Engineering custom integration blocks in 'ossec.conf' for real-time webhook delivery.
