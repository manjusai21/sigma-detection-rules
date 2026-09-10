# Step 2 – Write the Rule

Sigma rules are deliberately small and readable. A solid rule is often **under 40 lines**.

## Anatomy of a good Sigma rule

```yaml
title: Encoded PowerShell Command
id: <unique-uuid>
status: experimental          # experimental → test → stable
description: |
  Clear explanation of what this detects and why it matters.
references:
  - https://attack.mitre.org/techniques/T1059/001/
author: Your Name
date: 2026/09/08
tags:
  - attack.execution
  - attack.t1059.001
logsource:
  category: process_creation
  product: windows
detection:
  selection_image:
    Image|endswith:
      - '\powershell.exe'
      - '\pwsh.exe'
  selection_encoded:
    CommandLine|contains:
      - ' -enc '
      - ' -encodedcommand '
  condition: selection_image and selection_encoded
falsepositives:
  - Legitimate IT automation scripts
level: high
```

## Key quality points

- **One behaviour only** – do not mix encoded PowerShell and LSASS access in the same rule.
- **YAML uses spaces, never tabs.**
- Always include a meaningful `description` and `falsepositives` section.
- Map to ATT&CK with tags (`attack.tXXXX.YYY`).
- Prefer specific field modifiers (`|endswith`, `|contains`, `|startswith`) over broad wildcards.
- Give every rule a stable UUID (`id` field).

## Modern best practices (2025–2026)

- Use `status: experimental` until you have proven the rule in a lab and reviewed false positives.
- Include `fields:` so analysts see the most useful columns first.
- Prefer `category` + `product` over hard-coded EventIDs when the backend supports it (more portable).
- Document known false positives honestly – recruiters and hiring managers notice this.
