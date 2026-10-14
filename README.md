# Splunk SOC Portfolio | Firewall Log Analysis

![SIEM](https://img.shields.io/badge/SIEM-Splunk-20232A) ![Focus](https://img.shields.io/badge/Focus-SOC%20Analysis-1473E6) ![Language](https://img.shields.io/badge/Language-SPL-orange)

## Project overview

This repository documents my hands-on Splunk course work across **Data Ingestion Pipeline, Custom Field Extractions, Statistical Analysis via SPL, and Dashboard Design & Visualization**. I explored Windows Security telemetry, inspected firewall-related fields, used SPL to summarize activity, and designed a firewall analysis dashboard. The goal was to develop a practical workflow for turning raw events into SOC investigation leads.

**Workflow:** Ingest → Extract → Search → Aggregate → Visualize → Investigate.

## 01 — Data Ingestion Pipeline

I reviewed indexed Windows Security logs in Splunk and observed Windows Filtering Platform event codes **5156** (permitted connection) and **5158** (permitted bind). This establishes a starting point for exploring network activity.

![Data ingestion evidence](screenshots/01-data-ingestion.png)

[Chapter details](chapters/01-data-ingestion-pipeline.md)

## 02 — Custom Field Extractions

I examined extracted security fields including `Source_Address`, `Destination_Address`, `Source_Port`, `Destination_Port`, and `EventCode`. These attributes help analysts isolate connections and organize searches. The screenshot documents **field discovery**; it does not independently verify that a custom extraction rule was saved.

![Field extraction evidence](screenshots/02-field-extraction.png)

[Chapter details](chapters/02-custom-field-extractions.md)

## 03 — Statistical Analysis via SPL

I practiced using statistical aggregation to transform many security events into concise summaries. These example searches can help surface high-volume sources, frequently observed ports, and event-code patterns.

```spl
index=* sourcetype=WinEventLog:Security
| stats count by EventCode
| sort - count
```

```spl
index=* sourcetype=WinEventLog:Security
| where isnotnull(Source_Address)
| stats count by Source_Address
| sort - count
```

[Chapter details](chapters/03-statistical-analysis.md) · [More SPL queries](queries/)

## 04 — Dashboard Design & Visualization

I designed a **Firewall analysis** dashboard containing a table of network connection details and a chart comparing **allowed versus blocked firewall traffic**. The dashboard provides an accessible view of event-level evidence and traffic distribution.

![Firewall analysis dashboard](screenshots/04-dashboard.png)

[Chapter details](chapters/04-dashboard-design.md)

## Skills demonstrated

| Category | Skills |
|---|---|
| SIEM | Splunk Enterprise, log ingestion and searching |
| Log analysis | Windows Security events, firewall-related telemetry |
| Field analysis | Source/destination addresses and ports, EventCode |
| SPL | `stats count`, `sort`, `table`, filtering |
| Visualization | Dashboard tables and traffic distribution charts |
| SOC workflow | Event triage, investigative prioritization, contextual analysis |

## SOC analyst takeaway

**High-volume activity is an investigative lead, not proof of malicious behavior.** Analysts should consider timing, source and destination context, asset roles, and corroborating logs before escalating a finding.

## Repository contents

- `chapters/` — documentation for each course chapter
- `queries/` — reusable example SPL searches
- `screenshots/` — screenshots from my Splunk course environment with machine-identifying text obscured

## About me

I am a **cybersecurity professional and project manager** building hands-on skills in security operations, SIEM monitoring, incident response, and cloud security. This project demonstrates my ability to approach network security telemetry analytically and communicate technical work clearly.

## Security and accuracy notes

- Visible machine-name identifiers in screenshots were obscured before publication. Please inspect the images yourself before publishing, especially if other private details were not recognized.
- Loopback addresses such as `127.0.0.1`, timestamps, event codes, and field names remain visible to preserve technical context.
- Searches are examples and may require adapting index names and field names to your environment.
- The screenshots do not establish a confirmed security incident, and no malicious activity is claimed.
