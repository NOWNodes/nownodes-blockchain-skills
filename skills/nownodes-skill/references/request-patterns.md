# Request Patterns

## JSON-RPC

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_blockNumber",
  "params": []
}
```

Send with `POST`, `content-type: application/json`, and `api-key`.

Check both HTTP status and JSON-RPC error objects:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "error": {
    "code": -32601,
    "message": "Method not found"
  }
}
```

## REST

Use path and query parameters from official docs:

```http
GET <REST_ENDPOINT>/<RESOURCE>?limit=10
api-key: <NOWNODES_API_KEY>
```

Validate non-2xx responses before parsing the success schema.

## WebSocket

Use WSS only when supported for the selected chain. Keep reconnect bounded and avoid duplicate subscriptions after reconnect.

Common EVM subscription shape:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_subscribe",
  "params": ["newHeads"]
}
```

Authentication behavior can differ by WebSocket service and client library; check NOWNodes docs for whether the key is sent as a header, protocol option, or documented URL parameter.

## Blockbook

Blockbook is for indexed explorer-style lookups, not generic JSON-RPC. Use exact paths from current docs, for example address, transaction, block, or xpub resources where supported.

```http
GET <BLOCKBOOK_ENDPOINT>/api/v2/address/<ADDRESS>
api-key: <NOWNODES_API_KEY>
```

## Retry And Backoff

- Retry idempotent reads on `429`, transient `5xx`, and network timeouts.
- Use exponential backoff with jitter and a maximum attempt count.
- Do not blindly retry transaction broadcast; handle duplicate transaction, nonce, mempool, and replacement behavior chain-by-chain.

## Broadcast Safety

For methods such as `eth_sendRawTransaction`:

- Make the user confirm the broadcast action before running it.
- Never ask for or store private keys unless the user's application already has a secure signing boundary.
- Prefer examples that accept a pre-signed raw transaction placeholder: `<SIGNED_RAW_TRANSACTION>`.
