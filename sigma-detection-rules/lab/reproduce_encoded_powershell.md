# Lab – Reproduce Encoded PowerShell

## Goal
Generate the exact behaviour that the rule `proc_creation_encoded_powershell.yml` is designed to catch.

## Safe lab command (harmless)

```powershell
# Encode a simple benign command
$cmd = "Write-Host 'Detection Engineering Lab - Encoded PowerShell Test'"
$bytes = [System.Text.Encoding]::Unicode.GetBytes($cmd)
$encoded = [Convert]::ToBase64String($bytes)

# This should trigger the detection
powershell.exe -NoProfile -ExecutionPolicy Bypass -EncodedCommand $encoded
```

## Expected process creation fields

| Field | Example value |
|-------|---------------|
| Image | `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` |
| CommandLine | `... -EncodedCommand VwByAGkAdABlAC0ASABvAHMAdAAgA...` |
| ParentImage | Usually `explorer.exe` or `cmd.exe` in interactive testing |

## Validation checklist

- [ ] Rule converted successfully to target SIEM
- [ ] Alert fired within expected time window
- [ ] Screenshot / log entry saved as proof
- [ ] False-positive review performed on the same host over 24–48 h
