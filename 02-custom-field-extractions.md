# Custom Field Extractions

## Course work
Explored fields including Source_Address, Destination_Address, Source_Port, Destination_Port, and EventCode. The screenshot shows field discovery, not proof that a custom extraction rule was saved.

## Example SPL
```spl
index=* sourcetype=WinEventLog:Security
| table _time EventCode Source_Address Source_Port Destination_Address Destination_Port
```

## SOC relevance
Use field-level context and event counts to prioritize investigation. High event volume alone does not confirm a threat.

## Screenshot evidence
![Custom Field Extractions](../screenshots/02-field-extraction.png)
