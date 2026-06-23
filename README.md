# wazuh-lab-03-detection-engineering-powershell-detection

## Objective

The objective of this lab was to create and validate a custom Wazuh detection rule capable of identifying PowerShell execution activity from a monitored Windows endpoint.

This lab introduces the core Detection Engineering workflow:

1. Generate activity
2. Collect telemetry
3. Analyze events
4. Create detection logic
5. Validate detection
6. Investigate alerts

---

## Environment

| Component | Details |
|------------|------------|
| SIEM Platform | Wazuh 4.14.5 |
| Manager OS | Rocky Linux |
| Endpoint OS | Windows 11 |
| Agent Name | DESKTOP-9MMM37V |
| Detection Type | Custom Rule |
| Rule ID | 100500 |

---

## Detection Rule

The following custom rule was added to:

```text
/var/ossec/etc/rules/local_rules.xml
```

```xml
<group name="custom,powershell">

  <rule id="100500" level="8">
    <match>powershell.exe</match>
    <description>PowerShell Execution Detected</description>

    <mitre>
      <id>T1059.001</id>
    </mitre>

  </rule>

</group>
```

---

## Validation Process

### Step 1

Create the custom detection rule.

### Step 2

Validate the rule using:

```bash
sudo /var/ossec/bin/wazuh-logtest
```

### Step 3

Input:

```text
powershell.exe
```

### Step 4

Verify that Rule ID 100500 is triggered.

### Step 5

Restart Wazuh Manager.

```bash
sudo systemctl restart wazuh-manager
```

### Step 6

Generate PowerShell activity on the Windows endpoint.

```powershell
Get-Process
Get-Service
Get-Date
```

### Step 7

Investigate generated events within Wazuh.

---

## MITRE ATT&CK Mapping

| Technique ID | Technique |
|--------------|-----------|
| T1059.001 | PowerShell |

---

## Skills Demonstrated

- Detection Engineering
- Custom Rule Development
- Wazuh Rule Validation
- Alert Tuning
- MITRE ATT&CK Mapping
- Threat Detection Testing

---

## Outcome

A custom detection rule was successfully developed and validated using Wazuh Logtest. The lab demonstrated the complete lifecycle of detection creation, testing, and investigation within a SIEM environment.
