# Data Ingestion Pipeline

## Course work
Reviewed Windows Security events indexed in Splunk, including Windows Filtering Platform events 5156 and 5158.

## Example SPL
```spl
index=* sourcetype=WinEventLog:Security
| stats count by EventCode
| sort - count
```

## SOC relevance
Use field-level context and event counts to prioritize investigation. High event volume alone does not confirm a threat.

## Screenshot evidence
![Data Ingestion Pipeline] <img width="1076" height="661" alt="firewall traffic allowed WT" src="https://github.com/user-attachments/assets/1caafe82-ff0d-4de1-b603-afec1f031016" />
