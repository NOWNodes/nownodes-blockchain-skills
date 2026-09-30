# Migrations

Use migrations to preserve behavior while changing provider-specific auth and endpoint configuration.

## Shared Checklist

- Inventory current endpoints, chains, networks, methods, and WebSocket subscriptions.
- Replace provider-specific keys with `NOWNODES_API_KEY`.
- Switch auth to `api-key` header unless official NOWNodes docs require otherwise.
- Run read-only parity checks: chain id, latest block, representative balance, representative block or transaction.
- Keep a rollback switch in config or environment variables.
- Verify method support before removing old provider fallback.

## From GetBlock

- Auth differs by provider and endpoint style; move to NOWNodes `api-key` header by default.
- Do not assume identical hostnames or method availability.
- Parity check JSON-RPC results on a recent block and a finalized historical block.

## From Alchemy

- Remove Alchemy-specific enhanced APIs unless replacing them with NOWNodes-supported equivalents.
- Re-check WebSocket subscriptions and any trace/debug methods.
- Replace URL-embedded keys with env-backed NOWNodes auth.

## From Infura

- Replace project-id/project-secret assumptions with `NOWNODES_API_KEY`.
- Check method coverage for archive, trace/debug, and filters.
- Keep transaction signing in the application wallet/signer.

## From QuickNode

- Review any marketplace add-ons or custom methods used through QuickNode.
- Confirm equivalent NOWNodes capability or keep a provider-specific fallback.
- Compare latency/rate needs against the selected NOWNodes plan.

## From Public RPC

- Add authentication, error handling, and rate limit behavior.
- Re-test chain id to avoid accidentally changing network.
- Remove implicit trust in unauthenticated public endpoints.

## From Self-Hosted Node

- Inventory custom node flags, archive mode, debug APIs, txpool methods, and indexing assumptions.
- Confirm whether NOWNodes shared, archive, trace/debug, or dedicated setup matches the workload.
- Keep a rollback path to the self-hosted endpoint until parity checks pass.
