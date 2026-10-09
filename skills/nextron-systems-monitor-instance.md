---
name: nextron-systems-monitor-instance
description: Monitor a THOR Thunderstorm instance's configuration, live status and scan/queue throughput history.
api: nextron-systems:thor-thunderstorm-api
operations:
- info
- status
- sampleHistory
- queueHistory
generated: '2026-10-09'
method: generated
source: openapi/nextron-systems-thunderstorm-openapi.yml
---
# Monitor a THOR Thunderstorm instance

1. `info` (GET /info) — static instance information (version, configuration).
2. `status` (GET /status) — live information about the running instance.
3. `sampleHistory` (GET /sampleHistory) — samples scanned over time; `aggregate` = minutes per value (default 1), `limit` = last N minutes (default infinite).
4. `queueHistory` (GET /queueHistory) — asynchronous requests queued over time; same `aggregate`/`limit` params.

All four are read-only GETs and safe to repeat. 400 is returned for invalid parameters.
