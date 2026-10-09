---
name: nextron-systems-scan-file
description: Submit a file to a self-hosted THOR Thunderstorm instance and read the THOR report, synchronously or asynchronously.
api: nextron-systems:thor-thunderstorm-api
operations:
- info
- status
- check
- checkAsync
- getAsyncResults
generated: '2026-10-09'
method: generated
source: openapi/nextron-systems-thunderstorm-openapi.yml
---
# Scan a file with THOR Thunderstorm

Base URL is your own instance (spec default `http://localhost:8080/api/v1`). The spec declares no authentication.

1. `info` (GET /info) — confirm the instance is THOR Thunderstorm and note its version.
2. `status` (GET /status) — optional: check live load before submitting.
3. Small file / single sample: `check` (POST /check) with `multipart/form-data` containing the file; optional `source` query param labels the THOR log source. The response is the THOR report.
4. Large files or batches: `checkAsync` (POST /checkAsync), same body; keep the returned sample id.
5. `getAsyncResults` (GET /getAsyncResults?id=...) — poll until the result is complete.

Errors: 400 for bad requests, 500 for server-side failures (schema `Error`). The spec documents no idempotency keys — resubmitting a file creates a new scan.
