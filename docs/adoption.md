# Adoption

This repository becomes useful when it contains real public `lightwalletd` endpoints and publishes their current health as JSON.

## Practical Use Case

Zcash light wallets and backend services need reliable `lightwalletd` servers. A single hard-coded endpoint can become stale, overloaded, or unreachable. This repository gives operators and application builders a public place to track which endpoints exist and whether they are currently healthy.

## Adoption Path

1. Run a public `lightwalletd` endpoint.
2. Add the endpoint to `endpoints/mainnet.yaml` or `endpoints/testnet.yaml`.
3. Validate the registry from the sibling `shielded-stack` repository.
4. Generate `status/current.json`.
5. Publish the updated registry and status file.
6. Applications consume `status/current.json` to select healthy endpoints.

## Endpoint Consumer Logic

Applications should treat the status file as a discovery input, not as a security boundary.

A simple consumer can:

- select services where `status` is `active`
- require `reachable` to be `true`
- prefer the lowest `height_lag`
- use `latency_ms` as a tie-breaker
- retry another endpoint when a probe or wallet request fails

## Operator Requirements

An endpoint should be added only when:

- it is publicly reachable from outside the operator network
- it serves the expected Zcash network
- it responds to the `lightwalletd` `GetLightdInfo` gRPC method
- it has a stable hostname and explicit port
- the operator can respond to maintenance or incident reports

## Current State

The registry currently has no endpoints. This is valid for bootstrapping, but it does not yet provide network discovery value. The first practical milestone is adding one working mainnet endpoint and one working testnet endpoint, then generating a non-empty `status/current.json`.
