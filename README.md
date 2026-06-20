# shielded-stack-ops

Public operations and documentation hub for Zcash light client infrastructure.

This repository contains endpoint metadata, status records, runbooks, maintenance notes, and operator-facing documentation.

## Repository Layout

```text
endpoints/
  mainnet.yaml   Public mainnet endpoint registry.
  testnet.yaml   Public testnet endpoint registry.
status/
  current.json   Current service status snapshot.
runbooks/
  incident-response.md
  maintenance.md
docs/
  endpoint-registry.md
  operator-guide.md
  status-format.md
reports/
  uptime/
```

## Principles

- Keep public endpoint metadata accurate and reviewable.
- Prefer plain text, YAML, and JSON over custom formats.
- Record maintenance and incidents with timestamps.
- Avoid publishing secrets, credentials, IP allowlists, or private hostnames.

## Validation

From the sibling `shielded-stack` repository:

```sh
cargo run --manifest-path rust/Cargo.toml -p ssctl -- registry validate ../shielded-stack-ops/endpoints/mainnet.yaml
cargo run --manifest-path rust/Cargo.toml -p ssctl -- registry validate ../shielded-stack-ops/endpoints/testnet.yaml
```

## Work Tracking

See [ROADMAP.md](ROADMAP.md) for completed setup work and next operational tasks.
