# Step 1 – Pick One Behaviour to Catch

> **Rule of thumb:** One behaviour per rule. Never write a “catch everything” rule.

## Good First Targets

| Behaviour | ATT&CK | Why it’s a strong starting point |
|-----------|--------|----------------------------------|
| Encoded PowerShell commands | T1059.001 | Extremely common in real attacks, easy to simulate |
| New local admin account | T1136.001 / T1078.003 | Clear persistence signal |
| Registry Run key persistence | T1547.001 | Classic, well-documented technique |
| LSASS memory access | T1003.001 | High-value credential dumping indicator |

## Research Process

1. **Read the ATT&CK technique page**  
   Understand the procedure examples, data sources, and mitigations.

2. **Search the public SigmaHQ repository**  
   See how existing rules approach the same technique. Learn from quality examples and avoid reinventing broken logic.

3. **Read one red-team / threat-intel write-up**  
   Real attacker behaviour is often messier than the textbook description.

4. **Reproduce the noise in your own lab**  
   If you cannot make the behaviour happen, you cannot prove your rule works.

## Output of this step

- A single, clearly defined behaviour
- Mapped ATT&CK technique ID(s)
- List of data sources you will need (process creation, registry, security events, etc.)
