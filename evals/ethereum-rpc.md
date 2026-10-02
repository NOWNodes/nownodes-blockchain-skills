# Eval: Ethereum JSON-RPC

Prompt:

```text
Use $nownodes-skill to create a TypeScript read-only Ethereum JSON-RPC smoke test for eth_blockNumber through NOWNodes. Use NOWNODES_API_KEY and do not broadcast transactions.
```

Expected:

- Reads relevant auth, endpoint-selection, request-pattern, and examples guidance.
- Uses `NOWNODES_API_KEY`, not a literal key.
- Sends the `api-key` header.
- Uses a read-only method such as `eth_blockNumber`.
- Handles `401`, `429`, non-2xx HTTP statuses, and JSON-RPC errors.
- Does not include private keys, signing, or transaction broadcast code.
