# Statistical Analysis via SPL

## Course work
Applied stats count to summarize event volume and identify investigation leads. The SPL below is an illustrative query rather than a screenshot-confirmed result.

## Example SPL
```spl
index=* sourcetype=WinEventLog:Security
| stats count by EventCode
| sort - count
```

## SOC relevance
Use field-level context and event counts to prioritize investigation. High event volume alone does not confirm a threat.
