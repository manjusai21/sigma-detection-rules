# Resume Bullet Points – Detection Engineering / Sigma Project

Use these as inspiration. Adapt the wording to match your actual experience and the job description.

---

## Strong, ready-to-use bullets

**Detection Engineering – Sigma Rules Portfolio**

- Designed and authored production-style **Sigma detection rules** mapped to MITRE ATT&CK techniques (T1059.001, T1003.001, T1547.001, T1136.001), focusing on high-fidelity behavioural detections rather than simple IOC matching.
- Built an end-to-end detection lifecycle: behaviour research → Sigma YAML rule creation → conversion to Splunk / Elastic / Wazuh queries via **sigma-cli** → lab validation that the alert actually fires.
- Implemented false-positive reduction methodology by baselining legitimate activity, documenting every exclusion with ownership and business justification, and re-testing detections after each change.
- Created portable, SIEM-agnostic detections using Sigma as the single source of truth, enabling consistent coverage across multiple backends without rewriting logic.
- Documented lab reproduction steps and conversion artefacts so that any detection can be independently verified and demonstrated in interviews.

---

## Shorter / more concise versions

- Developed Sigma-based detection rules for encoded PowerShell, LSASS access, registry persistence and local admin creation, fully mapped to MITRE ATT&CK.
- Converted Sigma rules into Splunk and Elastic queries and validated true-positive alerts in a controlled lab environment.
- Applied structured false-positive analysis and exclusion governance to improve signal-to-noise ratio of detections.
- Maintained detection-as-code practices with version-controlled YAML rules, clear documentation and reproducible lab tests.

---

## Skills & tools you can list

**Detection & Threat**
- Sigma / sigma-cli
- MITRE ATT&CK
- Detection engineering lifecycle
- False-positive analysis & tuning
- Behavioural detection design

**SIEM / Telemetry**
- Splunk (SPL)
- Wazuh / Elastic Security
- Windows Security Event Logs
- Sysmon

**Practices**
- Detection-as-code
- Lab validation of detections
- ATT&CK technique mapping
- Documentation of exclusions & ownership

---

## Talking points for interviews

When asked about this project, be ready to walk through **one rule** in detail:

1. Why you chose that behaviour  
2. How you researched it (ATT&CK + public rules + red-team write-ups)  
3. Why the detection logic is written the way it is  
4. How you proved it fires  
5. What false positives you found and how you handled them  

This demonstrates senior-level detection engineering thinking, not just “I wrote a YAML file”.
