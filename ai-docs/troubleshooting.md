# Troubleshooting Summary

## 401

Check that `NOWNODES_API_KEY` is set, non-empty, active, and sent as the `api-key` header unless chain-specific docs require otherwise. Redact keys in logs.

## 403

Check plan access, endpoint availability, disabled methods, region/account restrictions, and whether the requested capability requires a dedicated or archive node.

## 429

Apply bounded exponential backoff with jitter. Reduce polling frequency, batch where the chain supports it, cache immutable responses, or request higher limits.

## 500 or Gateway Errors

Retry only idempotent read calls. Capture request id or response metadata if available. Compare with a simple read-only method such as `eth_blockNumber` or a block height lookup.

## Wrong Data Shape

Confirm whether the task uses JSON-RPC, REST, Blockbook, or MarketData. Similar concepts can use different response schemas across API surfaces.
