# Investigation Notes

## Objective

Validate a custom detection rule designed to identify PowerShell execution activity on a Windows endpoint.

---

## Detection Rule

Rule ID:

```text
100500
```

Description:

```text
PowerShell Execution Detected
```

MITRE Technique:

```text
T1059.001
```

---

## Test Activity

The following commands were executed on the Windows endpoint:

```powershell
Get-Process
Get-Service
Get-Date
```

The purpose was to generate PowerShell activity for detection testing.

---

## Rule Validation

The rule was validated using:

```bash
sudo /var/ossec/bin/wazuh-logtest
```

Input:

```text
powershell.exe
```

Expected Result:

```text
Rule ID: 100500
```

---

## Investigation Steps

1. Confirmed Windows agent status.
2. Generated PowerShell activity.
3. Reviewed event collection.
4. Validated detection logic.
5. Verified MITRE ATT&CK mapping.

---

## Findings

The custom rule successfully matched the PowerShell execution string during rule validation testing.

The detection logic was accepted by the Wazuh Manager without configuration errors.

---

## Conclusion

The custom PowerShell detection rule was successfully created and validated, demonstrating the foundational workflow of Detection Engineering within Wazuh.
