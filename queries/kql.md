# KQL Search Examples — Elastic Timeline / Discover

Use **KQL search mode** (not ES|QL) and a data view containing the relevant Sysmon events. Set the date range to include **7 August 2026**. These are queries from or consistent with the practical steps; event-field availability may vary by view.

## Find the process pair

```kql
host.name: "FIN-LT-0142" and process.name: ("wscript.exe" or "powershell.exe")
```

## Isolate the PowerShell events whose parent PID matches the graded value

```kql
host.name: "FIN-LT-0142" and process.name: "powershell.exe" and process.parent.pid: 6064
```

## Find the exact wscript parent process instance

The PowerShell `process.parent.entity_id` equals the parent's **own** `process.entity_id`.

```kql
host.name: "FIN-LT-0142" and process.name: "wscript.exe" and process.entity_id: "de65ceea-0b45-5362-824c-12abe5e33edf"
```

## Key fields to inspect in the native source event

```text
@timestamp
host.name
process.name
process.entity_id
process.parent.name
process.parent.pid
process.parent.entity_id
user.name
winlog.record_id  # provenance field; value not verified in this repository
```

**Careful:** A matching process name alone does not uniquely establish process lineage. Prefer `process.entity_id` and `process.parent.entity_id` together with host and time context.
