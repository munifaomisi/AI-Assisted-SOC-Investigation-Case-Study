# AI-Prepared Case Note — Human Validation

## AI statement under examination

> Observation: wscript.exe was started by explorer.exe for CASTELLANE\owen.farrelly.

The note also documented an Elastic medium-severity alert, recommended reopening the cited source in Discover, and explicitly required analyst verification. Its AI model received evidence prepared by read-only service searches, rather than directly accessing Elastic.

## Receipt details

- Run ID: `CC-TRIAGE-20260829-0001`
- Lookup count: **4**
- Evidence hash: `0fc91150d63df304218f1eee589d2a0b50ff01f22993e92532365b8f06049491`
- Cited Sysmon record `_id`: `c7f192786adea586a93726c4444735c3fa88a6dedb296c1b557235ad5c6e6d64`

The four pre-draft searches were (1) alert and rule context, (2) process ancestry, (3) host and user baseline, and (4) destination prevalence. The case note recorded 1, 3, 344, and 7 returned records respectively. Those numbers describe retrieved records, not confirmed security incidents.

## Method and findings

1. Reopen **the cited source record**, not an arbitrary similarly named process event.
2. Check `process.name = wscript.exe` and the host/time context.
3. Read native `process.parent.name`: **`explorer.exe`**.
4. Read native `user.name`: **`CASTELLANE\owen.farrelly`**.
5. Compare the original claim, field-by-field, without conflating it with all conclusions in the case.

**Verdict: Supported — specifically for the AI-prepared parent-process/user observation.**

## Limitations

- `winlog.record_id` is a worthwhile additional provenance field but **was not captured** in the provided record evidence; no value is asserted here.
- Supporting a process relationship does not establish whether the behavior was benign or malicious.
- The AI note is a preliminary draft, not a final incident disposition. Human review and an accountable handover remain necessary.

## Operational lesson

**AI assists. Native telemetry validates. The analyst owns the conclusion.**
