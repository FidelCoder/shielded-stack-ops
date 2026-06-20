# Incident Response

Use this runbook when a public endpoint is unavailable, lagging, or returning
unexpected responses.

## Triage

1. Confirm the affected network and endpoint URL.
2. Compare the endpoint height against a trusted block explorer or node.
3. Check host metrics for CPU, memory, disk, and network saturation.
4. Check `zcashd` sync status before restarting `lightwalletd`.
5. Record start time, observed symptoms, and the current mitigation.

## Mitigation

1. Remove unhealthy endpoints from public rotation when possible.
2. Restart only the smallest affected component.
3. Keep a copy of relevant logs before rotating or truncating them.
4. Add a maintenance note when user-visible impact is expected.

## Recovery

1. Confirm the endpoint is reachable from outside the host network.
2. Confirm block height is recent and advancing.
3. Confirm latency is within normal bounds.
4. Restore the endpoint to public metadata.
5. Write a short incident record under `reports/`.

