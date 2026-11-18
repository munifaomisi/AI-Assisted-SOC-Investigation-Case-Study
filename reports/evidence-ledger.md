# Evidence Ledger

This ledger distinguishes **verified native fields**, **graded task values**, **workflow text**, and **unknowns**.

| ID | Claim | Basis | Confidence / scope |
|---|---|---|---|
| E01 | Detection rule name and host | TryHackMe graded result; `screenshots/03-alert-answers.png` | Confirmed in lab |
| E02 | `process.parent.pid = 6064` | Graded result in Task 4 | Confirmed in lab |
| E03 | PowerShell parent entity ID | Native PowerShell Table field shown during investigation | Confirmed in lab |
| E04 | `wscript.exe` at 07:42:31 UTC | `screenshots/04-process-correlation.png` | Native timestamp |
| E05 | `powershell.exe` at 07:42:43 UTC | Timeline process event captured during investigation | Native timestamp; 12 s difference |
| E06 | AI note run ID, four lookups, hash | Original `AI-prepared case note` comment provided in session | Copied from lab case |
| E07 | AI cited `wscript.exe` event | Exact Elasticsearch document `_id` in original AI note; Discover same ID | Confirmed match |
| E08 | `process.parent.name = explorer.exe` | `screenshots/06-parent-process-evidence.png` | Confirmed for cited native event |
| E09 | `user.name = CASTELLANE\owen.farrelly` | `screenshots/07-user-evidence.png` | Confirmed for cited native event |
| E10 | `curl.exe` → `10.40.20.77:443/TCP` | `screenshots/08-network-evidence.png` | Confirmed for ES\|QL returned record |
| E11 | Analyst observation saved | `screenshots/09-analyst-observation.png` | Confirmed human-written comment |
| E12 | `tier2-review` tag added | `screenshots/10-tier2-tag.png` | Confirmed tag |
| E13 | Room completed | `screenshots/01-completion.png` | Confirmed 8 tasks / 100% |
| U01 | Native `winlog.record_id` | Not captured in supplied screens | **Unverified; do not invent** |
| U02 | Direct `powershell.exe` → `curl.exe` parent link | Lab workflow describes it; full linkage not screenshot-verified here | **Do not overstate** |
| U03 | Final Tier 2 comment saved | Draft seen in editor, but not saved confirmation in supplied images | **Unverified** |
| U04 | Case status changed to `In progress` | Guide and screenshots show requested state, but final live status not shown | **Unverified** |
| U05 | Malicious execution / exfiltration / authorization | Not established by available evidence | **Unknown** |

### Reopen the cited native event

- **Data view:** `Castellane endpoint telemetry`
- **Index:** `.ds-logs-windows.sysmon-castellane-2026.08.29-000001`
- **Document `_id`:** `c7f192786adea586a93726c4444735c3fa88a6dedb296c1b557235ad5c6e6d64`
- **Evidence ID:** `CC-EVID-6dc0d390c3890b3ade8ff3cf3ab370c40d5a9e95e79da5742d3a8395dec44fc4`
- **PowerShell parent entity ID:** `de65ceea-0b45-5362-824c-12abe5e33edf`

### AI execution receipt

- **Run ID:** `CC-TRIAGE-20260829-0001`
- **Lookups:** `4`
- **Evidence hash:** `0fc91150d63df304218f1eee589d2a0b50ff01f22993e92532365b8f06049491`

These identifiers are lab references, **not** credentials or external indicators of compromise.
