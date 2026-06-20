# Operator Guide

This guide covers the public records needed to operate Zcash light client
endpoints transparently.

## Adding an Endpoint

1. Add the endpoint to `endpoints/mainnet.yaml` or `endpoints/testnet.yaml`.
2. Include a stable `id`, public `url`, broad `region`, and `status`.
3. Confirm the endpoint is reachable from outside the host network.
4. Update `status/current.json` after the first successful probe.

## Removing an Endpoint

1. Change the endpoint status to `retired`.
2. Add a short note explaining the change.
3. Remove it from active service lists after clients have had time to update.

## Status Records

`status/current.json` is intended for simple machine-readable status. Historical
records should live under `reports/`.

