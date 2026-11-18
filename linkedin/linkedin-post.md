# LinkedIn Announcement — English

🛡️ **AI-Assisted SOC Investigation | TryHackMe — Room Completed (100%)**

**AI can accelerate investigations. But can its conclusions be trusted without checking the evidence?**

I completed **AI in the Modern SOC** on TryHackMe, investigating an Encoded PowerShell alert using **Elastic Security and Sysmon telemetry**.

🔍 **Practical investigation highlights:**

▪️ Triaged the alert and traced Windows process ancestry using KQL and native entity IDs.  
▪️ Correlated `wscript.exe` and `powershell.exe` process-start events (12-second interval).  
▪️ Investigated a `curl.exe` network connection using ES|QL (`10.40.20.77:443/TCP`, lab environment).  
▪️ Independently checked an AI-prepared case note against its cited Sysmon record.  
▪️ Documented evidence, uncertainty, and an escalation-ready Tier 2 handover.

🎯 **Key lesson:** A supported AI observation is not the same as a confirmed incident. Reliable SOC work requires provenance, verification, and clear analyst accountability.

**AI assists. Evidence validates. Analysts decide.**

📂 **Technical case study:** [Add GitHub repository URL after publishing]  
🔗 **Lab:** https://tryhackme.com/room/aiinthemodernsoc

👨‍💻 **Munif Alomisi**

🔔 **Follow me for SOC, CTI, Threat News & Vulnerability Analysis!**

#SOC #ElasticSecurity #SIEM #ThreatDetection #IncidentResponse #Sysmon #ESQL #KQL #AIinCyberSecurity #BlueTeam #TryHackMe

---

## Suggested post images (from this repository)

1. `screenshots/01-completion.png` — the 100% room completion.
2. `screenshots/04-process-correlation.png` — native `wscript.exe` timestamp / process correlation.
3. `screenshots/08-network-evidence.png` — verified destination IP, TCP port, and process.
4. `screenshots/07-user-evidence.png` — source-backed AI observation verification.
5. `screenshots/09-analyst-observation.png` — saved human analysis in the case.

Publish repository first, then replace the placeholder with the actual URL.
