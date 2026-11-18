# Investigation Report — Encoded PowerShell Alert

**Case:** CC-CASE-0913  
**Analyst:** Munif Alomisi  
**Environment:** TryHackMe, *AI in the Modern SOC*  
**Endpoint:** FIN-LT-0142  
**Alert severity:** Medium  
**Detection rule:** `Encoded PowerShell started by Windows Script Host`

## 1. Context and question

An Elastic Security detection flagged a PowerShell process associated with Windows Script Host. The task was to establish the relevant process lineage, collect correlated network evidence, and assess whether an AI-prepared case statement was supported by its cited native event. This was triage and evidence validation; the investigation was **not** an attribution or malware-confirmation exercise.

## 2. Process evidence

- The selected `wscript.exe` native process event has `@timestamp = 2026-08-07T07:42:31.000Z`.
- A correlated `powershell.exe` process-start event has `@timestamp = 2026-08-07T07:42:43.000Z`.
- Elapsed time: **12 whole seconds**, confirmed by the room question.
- The PowerShell record includes `process.parent.pid = 6064` and `process.parent.entity_id = de65ceea-0b45-5362-824c-12abe5e33edf`.
- Reopening the cited `wscript.exe` document in Discover returned `process.parent.name = explorer.exe` and `user.name = CASTELLANE\owen.farrelly`.

The step-by-step lab workflow also places `curl.exe` later in the process sequence. While the outbound network event was verified, direct parent-entity linking for the `powershell.exe → curl.exe` edge is not displayed in the retained screenshots. Label that edge as lab-guided correlation rather than independently evidenced here.

## 3. Outbound telemetry

An ES|QL search returned one `curl.exe` record at **2026-08-07T07:43:03.000Z**:

| Field | Value |
|---|---|
| `process.name` | `curl.exe` |
| `destination.ip` | `10.40.20.77` |
| `destination.port` | `443` |
| `network.transport` | `tcp` |

Port 443/TCP by itself does not demonstrate HTTPS content, exfiltration, or malicious intent. Destination ownership, payload/bytes transferred, and authorization are not resolved by the recorded evidence.

## 4. AI-assisted note and independent verification

The lab's note summarized the alert and made a narrow claim: `wscript.exe` was started by `explorer.exe` for `CASTELLANE\owen.farrelly`. Its authoring workflow used four read-only searches and a compiled evidence bundle; the language model did not itself access Elastic. The original note explicitly said **“Analyst verification is required.”**

I reopened the specified Sysmon process document and verified the two key native fields. Thus the **specific observation** is **Supported**. That judgement does **not** validate an incident conclusion or eliminate uncertainty around authorization/network purpose.

## 5. Communication / escalation

The lab case contains a saved human **Analyst observation** separate from the AI-prepared note. The training case was tagged `tier2-review`; a **Tier 2 handover** was drafted from the validated evidence, including outstanding questions and a bounded follow-up request. The room's completion is confirmed, but screenshot evidence in this package does not conclusively establish that a final handover comment was saved or that the final case status was changed to **In progress**. These should not be presented as independently verified actions.

## 6. Open questions

1. Was execution authorized for the affected user and endpoint?
2. What service or system owns `10.40.20.77`, and why did `curl.exe` connect to it?
3. What, if anything, was transferred over the connection?
4. Are there additional relevant commands, files, network connections, or follow-on behaviors?

**Conclusion:** Preserve the evidence, maintain analyst oversight, and continue bounded Tier 2 review without treating an AI-authored statement as a final incident verdict.
