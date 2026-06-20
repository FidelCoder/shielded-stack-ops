# Maintenance

Use this runbook for planned updates to Zcash node, lightwalletd, host, or
monitoring components.

## Before Maintenance

1. Confirm the maintenance window.
2. Check current endpoint health.
3. Confirm rollback steps for the component being changed.
4. Save configuration diffs and release notes.

## During Maintenance

1. Drain or mark the endpoint as under maintenance if needed.
2. Apply the update.
3. Restart services in dependency order.
4. Watch logs and metrics until the endpoint is stable.

## After Maintenance

1. Confirm external reachability.
2. Confirm the latest block height advances.
3. Update endpoint metadata if ports, domains, or versions changed.
4. Add a maintenance note under `reports/`.

