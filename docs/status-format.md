# Status Format

`status/current.json` is the current machine-readable service snapshot.

## Format

```json
{
  "updated_at": "2026-06-21T00:00:00Z",
  "summary": {
    "total_services": 1,
    "reachable_services": 1,
    "degraded_services": 0,
    "unreachable_services": 0
  },
  "services": [
    {
      "id": "example-mainnet",
      "network": "mainnet",
      "url": "https://example.com:9067",
      "reachable": true,
      "latest_block_height": 3000000,
      "latency_ms": 120,
      "checked_at_unix": 1782000000,
      "message": "ok"
    }
  ]
}
```

## Update Process

1. Validate endpoint registry files.
2. Probe active endpoints.
3. Update `status/current.json` with the latest observed values.
4. Add an incident or maintenance note when user-visible behavior changes.
