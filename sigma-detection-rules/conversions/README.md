# Converted Queries

This folder contains example conversions of the Sigma rules for common SIEM backends.

## How the conversions were generated

```bash
# Splunk (Sysmon pipeline)
sigma convert -t splunk -p sysmon rules/proc_creation_encoded_powershell.yml \
  > conversions/encoded_powershell_splunk.spl

# Elasticsearch / Elastic Security (ECS)
sigma convert -t elasticsearch -p ecs_windows rules/proc_creation_encoded_powershell.yml \
  > conversions/encoded_powershell_elastic.json

# Wazuh (uses similar query language)
sigma convert -t elasticsearch -p ecs_windows rules/proc_creation_encoded_powershell.yml \
  > conversions/encoded_powershell_wazuh.txt
```

Keep the original Sigma YAML as the source of truth. Converted queries are derived artefacts.
