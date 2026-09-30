# Framework Recipes

## Raw Fetch

Required env:

```text
NOWNODES_API_KEY
```

Use `fetch` with `api-key`, `content-type`, timeout/abort handling, and JSON-RPC error parsing. Smoke test with `eth_blockNumber` or a chain-specific read-only method.

## Python Requests

Required env:

```text
NOWNODES_API_KEY
```

Use `requests.post(..., timeout=10)` for JSON-RPC and `requests.get(..., timeout=10)` for REST/Blockbook. Call `raise_for_status()` after special handling for `401` and `429`.

## Ethers.js

Use when the project already uses ethers for EVM chains. Confirm the ethers version can attach custom headers to its JSON-RPC transport. If not, create a minimal fetch RPC client for read-only calls and leave ethers for local signing or contract encoding.

Smoke tests:

- `eth_chainId`
- `eth_blockNumber`

Signing boundary:

- Keep private keys in the wallet or secure signer.
- Do not send private keys to NOWNodes.
- Ask for explicit confirmation before broadcasting `eth_sendRawTransaction`.

## Viem

Use `http` or custom transport with headers if available in the installed viem version. Run `getChainId` and `getBlockNumber` as read-only smoke tests.

## Web3.js

Confirm provider/header support for the installed major version. If headers are awkward, prefer a raw JSON-RPC wrapper for node calls and keep Web3.js for ABI utilities.

## Hardhat

Put endpoints and keys in env-backed config. Do not commit `.env`.

```ts
const nownodesApiKey = process.env.NOWNODES_API_KEY;
```

Use read-only tasks for smoke tests before enabling deployment or verification workflows.

## Foundry

Foundry RPC URLs are usually URL-based. If the endpoint requires headers and Foundry cannot pass them for the desired command, use a documented NOWNodes URL form only if official docs allow it, or run a separate header-capable smoke test.

## Python web3.py

Header support can be added through request kwargs or middleware depending on the version and provider. Verify with `web3.eth.block_number` and avoid loading private keys into scripts unless the user explicitly requests a signing workflow.

## WebSocket Clients

Use WSS only where supported. Add reconnect backoff, subscription resubmission, duplicate event handling, and graceful shutdown.
