# Dashboard Design & Visualization

## Course work
Designed a Firewall analysis dashboard showing network event details and a pie chart comparing allowed and blocked traffic. The screenshot shows the dashboard in an editing state.

## Example SPL
```spl
index=* sourcetype=WinEventLog:Security
| eval traffic_type=case(EventCode=5156 OR EventCode=5158,"allowed firewall traffic",EventCode=5157 OR EventCode=5159,"blocked firewall traffic")
| where isnotnull(traffic_type)
| stats count by traffic_type
```

## SOC relevance
Use field-level context and event counts to prioritize investigation. High event volume alone does not confirm a threat.

## Screenshot evidence
![Dashboard Design & Visualization](../screenshots/04-dashboard.png)
