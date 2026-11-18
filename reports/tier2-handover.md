# Proposed Tier 2 Handover

> **Publication status:** This is a cleaned, GitHub-ready handover derived from the completed exercise. The actual saved final Tier 2 comment and final `In progress` status are **not independently confirmed** in the screenshots retained here. The analyst observation and `tier2-review` tag **are** shown as saved.

**Case:** `CC-CASE-0913`  
**Case UUID:** `699f152b-2daf-49f6-ae57-620793724c6e`  
**Priority:** Medium  
**Requested workflow:** Tier 2 review; retain open pending further investigation

**Assisted run:** `CC-TRIAGE-20260829-0001`; evidence hash `0fc91150d63df304218f1eee589d2a0b50ff01f22993e92532365b8f06049491`.

**Detection:** `Encoded PowerShell started by Windows Script Host` on `FIN-LT-0142`.

**Process trail:** Native records support an `explorer.exe → wscript.exe → powershell.exe` sequence, with `wscript.exe` at 07:42:31 UTC and `powershell.exe` at 07:42:43 UTC (12 seconds), PowerShell parent PID 6064. The lab's guided workflow identifies `curl.exe` in the subsequent chain; direct entity-ID linkage for the last edge is not reproduced in this published screenshot set.

**Outbound record:** `curl.exe`, `10.40.20.77:443/TCP`, 2026-08-07 07:43:03 UTC (ES|QL record).

**AI observation verdict:** **Supported**, narrowly: the cited Sysmon record has `process.parent.name = explorer.exe` and `user.name = CASTELLANE\owen.farrelly`. The statement alone does not establish malicious activity.

**Remaining evidence gaps:** authorization and business context, destination ownership/purpose, content or volume of network transfer, and additional behaviors.

**Bounded Tier 2 next step:** Correlate the exact `curl.exe` event with surrounding endpoint/network telemetry and approved asset inventories. Determine destination purpose and whether activity was expected. Record any additional source references and reasoned disposition.

**Safety / decision ownership:** Preserve the case and evidence. Any real-world containment action requires organizational authorization. Human analysts retain responsibility for the final conclusion.
