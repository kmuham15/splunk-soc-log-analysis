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
![Data Ingestion Pipeline] 
