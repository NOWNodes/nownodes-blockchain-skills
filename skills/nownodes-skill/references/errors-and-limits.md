# Errors And Limits

## HTTP 400

Likely malformed request, wrong method, invalid JSON, missing params, or wrong endpoint type. Confirm JSON-RPC body shape, REST path, and content type.

## HTTP 401

Likely missing, invalid, expired, revoked, or incorrectly transmitted API key.

Checks:

- `NOWNODES_API_KEY` exists and is not empty.
- Request sends `api-key` header unless docs say otherwise.
- Logs do not expose the key.
- The key belongs to the intended account/workspace.

## HTTP 403

Likely forbidden capability, disabled method, plan restriction, account restriction, or endpoint not included in the plan.

Check whether the user needs Archive, Trace/Debug, dedicated node access, or another plan capability.

## HTTP 429

The client is rate limited.

Recommended response:

- Back off with jitter.
- Reduce polling frequency.
- Cache immutable data.
- Batch where supported.
- Move high-throughput workloads to a plan or dedicated setup that matches the workload.

## HTTP 500 / 502 / 503 / 504

Possible gateway, service, upstream node, or temporary network failure.

Recommended response:

- Retry idempotent reads with bounded backoff.
- Run a simple read-only smoke test such as block number or chain id.
- Capture response status, sanitized headers, and request id if available.
- Avoid retrying broadcasts without chain-specific duplicate handling.

## JSON-RPC Errors

- `-32600`: invalid request.
- `-32601`: method not found or unsupported by endpoint.
- `-32602`: invalid params.
- `-32603`: internal error or upstream failure.

## Shared vs Dedicated Nodes

Shared/public access can have different throughput, latency, and method availability from dedicated nodes. Do not promise dedicated-node behavior for shared endpoints.
