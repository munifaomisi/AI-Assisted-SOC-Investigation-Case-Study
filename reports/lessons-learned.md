# Lessons Learned

1. **Alert != incident.** A medium-severity alert starts an investigation, not a final verdict.
2. **Trace specific process instances.** `process.entity_id` / `process.parent.entity_id` are stronger lineage anchors than process names alone.
3. **Timestamps matter.** Comparing native timestamps established a 12-second process interval.
4. **Network metadata is bounded evidence.** `curl.exe` communicating to port 443/TCP confirms an event, not the content, intent, or ownership of the destination.
5. **AI-generated case notes need provenance.** The drafted observation was verified against an exact cited Sysmon document; the limited observation was Supported.
6. **Distinguish verified and missing fields.** No `winlog.record_id` value is invented; not all chain edges or post-handover status changes are captured in supplied evidence.
7. **Professional escalation preserves context.** The next analyst needs the detection, native evidence, reference IDs, unresolved questions, and a bounded next action.
8. **The analyst retains accountability.** AI accelerates summarization; the final assessment requires human judgement and appropriate authorization.
