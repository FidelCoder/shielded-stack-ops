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
    status: active
    notes: Public lightwalletd endpoint.
```

## Field Notes

- `id` should be stable and lowercase.
- `url` should be the public client-facing endpoint.
- `region` should be a broad region label, not an exact address.
- `operator` should identify the responsible operator or organization.
- `capabilities` can include values such as `grpc`, `tls`, or `tor`.
- `status` should be `active`, `maintenance`, or `retired`.

