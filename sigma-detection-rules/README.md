# Detection Engineering – Sigma Detection Rules

**Portfolio project for Detection Engineer / Cybersecurity roles**

This repository demonstrates the complete detection-engineering lifecycle using **Sigma**:

1. Pick one attacker behaviour  
2. Write a high-quality Sigma rule  
3. Convert it to a SIEM query and **prove it fires**  
4. Hunt and document false positives honestly  

---

## Why this project matters

| Value | Explanation |
|-------|-------------|
| Detection engineering pays above SOC | Shows you can build detections, not only triage alerts |
| Teams cannot hire enough of them | Practical, scarce skill |
| Rules on GitHub are portfolio proof | Hiring managers can read your actual work |
| Interviews walk through one rule | You can explain every line under pressure |

---

## Repository structure

```
sigma-detection-rules/
├── rules/                          # Production-style Sigma YAML rules
│   ├── proc_creation_encoded_powershell.yml
│   ├── proc_creation_new_local_admin.yml
│   ├── registry_run_key_persistence.yml
│   └── lsass_memory_access.yml
├── docs/                           # Step-by-step methodology
│   ├── 01_pick_behaviour.md
│   ├── 02_write_the_rule.md
│   ├── 03_convert_and_prove.md
│   └── 04_hunt_false_positives.md
├── lab/                            # Reproduction steps & validation
│   └── reproduce_encoded_powershell.md
├── conversions/                    # Example SIEM queries
│   ├── encoded_powershell_splunk.spl
│   └── README.md
├── README.md
├── LICENSE
└── .gitignore
```

---

## Rules included

| Rule | ATT&CK | Level | Focus |
|------|--------|-------|-------|
| Encoded PowerShell Command | T1059.001 | High | Execution / Defense Evasion |
| New Local Administrator Account | T1136.001, T1078.003 | High | Persistence / Privilege Escalation |
| Registry Run Key Persistence | T1547.001 | Medium | Persistence |
| Suspicious LSASS Memory Access | T1003.001 | High | Credential Access |

All rules follow modern Sigma quality standards:

- Unique UUID
- Clear description + false-positives section
- ATT&CK tags
- Specific field modifiers
- Experimental → testable status

---

## Modern detection-engineering practices used

- **One behaviour per rule** – never “catch-all” logic
- **ATT&CK mapping** as a first-class citizen
- **False-positive ownership** – every exclusion is documented
- **Lab validation** – a rule that never fired is treated as a guess
- **Portable rules** – Sigma as the source of truth, SIEM queries as derived artefacts
- **sigma-cli** conversion pipeline (Splunk, Elastic, Wazuh, etc.)

---

## Quick start

```bash
# Clone
git clone https://github.com/<your-username>/sigma-detection-rules.git
cd sigma-detection-rules

# Install sigma-cli (optional – for conversion)
pip install sigma-cli

# Convert a rule to Splunk
sigma convert -t splunk -p sysmon rules/proc_creation_encoded_powershell.yml
```

Then follow the lab guide in `lab/` to reproduce the behaviour and prove the alert fires.

---

## Tools referenced

- **Sigma** / **sigma-cli** – detection-as-code format
- **MITRE ATT&CK** – technique mapping
- **Splunk** or **Wazuh** / **Elastic** – SIEM backends
- **Sysmon** – rich process / registry telemetry

---

## License

MIT License – see [LICENSE](LICENSE).

---

## Author

Detection Engineering portfolio project – built to demonstrate practical, modern detection skills for cybersecurity roles.
