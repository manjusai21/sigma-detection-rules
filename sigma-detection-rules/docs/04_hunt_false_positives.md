# Step 4 – Hunt Your Own False Positives

Every exclusion is a hole in your net. Write down **why** you cut it.

## Things that often look malicious but are legitimate

| Category | Examples |
|----------|----------|
| IT deployment | SCCM, Intune, Ansible, Chocolatey scripts |
| Backup & monitoring | Veeam, Commvault, Datadog agents, AV memory scanners |
| Your own admins | Domain admins running encoded scripts for automation |
| Scheduled tasks | Anything that runs at 2 a.m. from a service account |

## What to do

1. **Baseline one quiet week first**  
   Let the rule run in “log only” mode and collect every hit.

2. **Add filters, comment every one**  
   ```yaml
   filter_legitimate_av:
     SourceImage|endswith:
       - '\MsMpEng.exe'
       - '\MsSense.exe'
   # Reason: Windows Defender / Microsoft Defender for Endpoint
   # Owner: Security Engineering – reviewed 2026-09-08
   ```

3. **Name the owner of each exclusion**  
   Future you (or the next detection engineer) needs to know who approved the hole.

4. **Retest the rule after every change**  
   Confirm the true-positive still fires and the false-positive is gone.

## Modern practice

- Treat false-positive reduction as a first-class deliverable, not an afterthought.
- Keep an `exclusions.md` or inline comments that explain the business justification.
- Prefer broad-but-safe filters (known good binaries) over suppressing the entire technique.
