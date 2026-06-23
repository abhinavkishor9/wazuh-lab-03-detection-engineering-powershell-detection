# Troubleshooting Notes

## Issue 1

### Problem

Custom rule not generating alerts.

### Investigation

Verified whether the rule was loaded successfully.

### Resolution

Validated rule using:

```bash
sudo /var/ossec/bin/wazuh-logtest
```

Confirmed that Rule ID 100500 was triggered.

---

## Issue 2

### Problem

No results returned for:

```text
rule.id:100500
```

### Investigation

Reviewed Threat Hunting dashboard filters and selected time range.

### Resolution

Expanded the search window from:

```text
Last 15 minutes
```

to:

```text
Last 24 hours
```

and refreshed the dashboard.

---

## Issue 3

### Problem

Threat Hunting displayed:

```text
No results match your search criteria
```

### Investigation

Verified active filters.

Observed:

```text
manager.name: localhost.localdomain
agent.id:001
```

### Resolution

Reviewed filters and performed broader event searches.

---

## Issue 4

### Problem

Detection worked in Wazuh Logtest but not within dashboard searches.

### Investigation

Determined that matching telemetry may not yet be collected from the endpoint.

### Resolution

Generated additional PowerShell activity:

```powershell
Get-Process
Get-Service
Get-Date
```

and re-ran investigations.

---

## Issue 5

### Problem

Difficulty exiting Wazuh Logtest.

### Resolution

Use:

```text
Ctrl + C
```

to return to the shell prompt.

---

## Lessons Learned

- Always validate custom rules using Wazuh Logtest before testing in production.
- Detection logic can be valid even when underlying telemetry is missing.
- Threat Hunting filters can hide valid events.
- Expanding the search window often helps identify delayed event ingestion.
- Detection Engineering requires validation of both rules and telemetry sources.
