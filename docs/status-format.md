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
      "status": "active",
      "region": "eu-west",
      "operator": "example",
      "reachable": true,
      "latest_block_height": 3000000,
      "estimated_block_height": 3000000,
      "height_lag": 0,
      "latency_ms": 120,
      "checked_at_unix": 1782000000,
      "message": "ok"
    }
  ]
}
```

## Manual Update

From the sibling `shielded-stack` repository:

```sh
cargo run --manifest-path rust/Cargo.toml -p ssctl -- \
  registry status \
  ../shielded-stack-ops/endpoints/mainnet.yaml \
  ../shielded-stack-ops/endpoints/testnet.yaml \
  --output ../shielded-stack-ops/status/current.json
```

## Automated Update

The `Update Status` workflow validates both registries, probes active endpoints, writes `status/current.json`, and commits the file when it changes.
