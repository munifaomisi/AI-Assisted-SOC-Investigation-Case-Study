# ES|QL — Outbound `curl.exe` Evidence

Use **Discover → ES|QL**, with a time window covering 2026-08-07 07:40–07:55 UTC. The network event was confirmed by the session screenshot (`screenshots/08-network-evidence.png`).

```esql
FROM logs-windows.sysmon-castellane
| WHERE host.name == "FIN-LT-0142"
  AND process.name == "curl.exe"
  AND destination.ip == "10.40.20.77"
| KEEP @timestamp, process.name, destination.ip, destination.port, network.transport
| SORT @timestamp ASC
```

**Observed row:**

```text
@timestamp              2026-08-07 07:43:03.000 UTC
process.name            curl.exe
destination.ip          10.40.20.77
destination.port        443
network.transport       tcp
```

The training's more precise method is to first retrieve the `curl.exe` process **own** `process.entity_id` from the process-ancestry lookup, then locate a network event with that same ID. A full `curl.exe` entity ID was not captured in the supplied screenshots; do not invent it. Example template:

```esql
FROM logs-windows.sysmon-castellane
| WHERE host.name == "FIN-LT-0142"
  AND event.category == "network"
  AND process.entity_id == "<VERIFIED_CURL_ENTITY_ID>"
  AND destination.ip IS NOT NULL
| KEEP @timestamp, host.name, process.name, process.entity_id, destination.ip, destination.port, network.transport, winlog.record_id
| SORT @timestamp ASC
```

Replace the placeholder only with a value copied from the native `curl.exe` event.
