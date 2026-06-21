# Endpoint Registry

Endpoint registry files live in `endpoints/`.

## Format

```yaml
network: mainnet
updated_at: "2026-06-21T00:00:00Z"
endpoints:
  - id: example-mainnet
    url: https://example.com:9067
    region: eu-west
    operator: example
    capabilities:
      - grpc
      - tls
    status: active
    notes: Public lightwalletd endpoint.
```

## Field Notes

- `id` should be stable, lowercase, and use hyphens instead of spaces.
- `url` should be the public client-facing endpoint with an explicit port.
- `region` should be a broad region label, not an exact address.
- `operator` should identify the responsible operator or organization.
- `capabilities` can include `grpc`, `tls`, or `tor`.
- `status` should be `active`, `maintenance`, or `retired`.
- `updated_at` must use UTC timestamp form: `YYYY-MM-DDTHH:MM:SSZ`.

## Validation Rules

- Endpoint IDs must be unique.
- Endpoint URLs must be unique.
- Endpoint IDs must not start or end with a hyphen.
- Endpoint IDs must not contain repeated hyphens.
- Endpoint URLs must start with `http://` or `https://`.
- Endpoint URLs must include a host and explicit port.
- Endpoint URLs must not include a path, query string, or fragment.
- Active endpoints must include the `grpc` capability.
- Capabilities must not be duplicated.

## Validation

From the sibling `shielded-stack` repository:

```sh
cargo run --manifest-path rust/Cargo.toml -p ssctl -- registry validate ../shielded-stack-ops/endpoints/mainnet.yaml
cargo run --manifest-path rust/Cargo.toml -p ssctl -- registry validate ../shielded-stack-ops/endpoints/testnet.yaml
```

## Probe Active Endpoints

```sh
cargo run --manifest-path rust/Cargo.toml -p ssctl -- registry probe ../shielded-stack-ops/endpoints/mainnet.yaml --json
```
