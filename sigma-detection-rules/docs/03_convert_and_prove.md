# Step 3 – Convert It and Prove It Fires

> A rule that never fired in front of you is a **guess**, not a detection.

## Conversion pipeline

```bash
# Install sigma-cli (modern backend)
pip install sigma-cli

# Convert to Splunk SPL
sigma convert -t splunk -p sysmon rules/proc_creation_encoded_powershell.yml

# Convert to Wazuh / Elastic
sigma convert -t elasticsearch -p ecs_windows rules/proc_creation_encoded_powershell.yml

# Convert to Sigma’s own query language for testing
sigma convert -t lucene rules/proc_creation_encoded_powershell.yml
```

## Prove it fires – lab workflow

1. **Deploy** the converted query as a saved search / alert in Splunk, Wazuh, or Elastic.
2. **Make the noise** – run the exact attacker behaviour in a controlled VM:
   ```powershell
   powershell.exe -enc <base64-encoded-payload>
   ```
3. **Watch it fire** – screenshot the alert. That screenshot is your proof.
4. Record the timestamp, host, and the exact command line that triggered it.

## Evidence you should keep in the repo

- `lab/` folder with reproduction commands
- Screenshot or text log of the successful alert
- Notes on which conversion target you used

This step turns a YAML file into a **demonstrable skill**.
