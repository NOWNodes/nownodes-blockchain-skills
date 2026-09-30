# Examples

All examples use placeholders. Replace endpoint placeholders with exact URLs from current NOWNodes docs.

## TypeScript JSON-RPC Fetch

```ts
const apiKey = process.env.NOWNODES_API_KEY;
if (!apiKey) throw new Error("Missing NOWNODES_API_KEY");

async function rpc<T>(method: string, params: unknown[] = []): Promise<T> {
  const response = await fetch("<CHAIN_ENDPOINT>", {
    method: "POST",
    headers: {
      "content-type": "application/json",
      "api-key": apiKey
    },
    body: JSON.stringify({ jsonrpc: "2.0", id: 1, method, params })
  });

  if (response.status === 401) throw new Error("NOWNodes authentication failed");
  if (response.status === 429) throw new Error("NOWNodes rate limit exceeded");
  if (!response.ok) throw new Error(`NOWNodes HTTP ${response.status}`);

  const payload = await response.json();
  if (payload.error) throw new Error(`NOWNodes RPC error: ${payload.error.message}`);
  return payload.result as T;
}

const blockNumberHex = await rpc<string>("eth_blockNumber");
console.log(Number.parseInt(blockNumberHex, 16));
```

## Python JSON-RPC Requests

```py
import os
import requests

api_key = os.environ["NOWNODES_API_KEY"]

response = requests.post(
    "<CHAIN_ENDPOINT>",
    headers={"api-key": api_key, "content-type": "application/json"},
    json={"jsonrpc": "2.0", "id": 1, "method": "eth_blockNumber", "params": []},
    timeout=10,
)

if response.status_code == 401:
    raise RuntimeError("NOWNodes authentication failed")
if response.status_code == 429:
    raise RuntimeError("NOWNodes rate limit exceeded")
response.raise_for_status()

payload = response.json()
if "error" in payload:
    raise RuntimeError(payload["error"])

print(int(payload["result"], 16))
```

## REST GET

```ts
const apiKey = process.env.NOWNODES_API_KEY;
if (!apiKey) throw new Error("Missing NOWNODES_API_KEY");

const response = await fetch("<REST_ENDPOINT>/<RESOURCE>", {
  headers: { "api-key": apiKey }
});
if (!response.ok) throw new Error(`NOWNodes REST HTTP ${response.status}`);
const data = await response.json();
```

## REST POST

```ts
const apiKey = process.env.NOWNODES_API_KEY;
if (!apiKey) throw new Error("Missing NOWNODES_API_KEY");

const response = await fetch("<REST_ENDPOINT>/<RESOURCE>", {
  method: "POST",
  headers: {
    "content-type": "application/json",
    "api-key": apiKey
  },
  body: JSON.stringify({ value: "<REQUEST_VALUE>" })
});
if (!response.ok) throw new Error(`NOWNodes REST HTTP ${response.status}`);
const data = await response.json();
```

## Blockbook Address Lookup

```bash
curl -sS '<BLOCKBOOK_ENDPOINT>/api/v2/address/<ADDRESS>' \
  -H "api-key: ${NOWNODES_API_KEY}"
```

## WebSocket Subscription

```ts
import WebSocket from "ws";

const apiKey = process.env.NOWNODES_API_KEY;
if (!apiKey) throw new Error("Missing NOWNODES_API_KEY");

const ws = new WebSocket("<WSS_ENDPOINT>", {
  headers: { "api-key": apiKey }
});

ws.on("open", () => {
  ws.send(JSON.stringify({
    jsonrpc: "2.0",
    id: 1,
    method: "eth_subscribe",
    params: ["newHeads"]
  }));
});

ws.on("message", (message) => {
  const event = JSON.parse(message.toString());
  console.log(event);
});
```

## MarketData Request

```ts
const apiKey = process.env.NOWNODES_API_KEY;
if (!apiKey) throw new Error("Missing NOWNODES_API_KEY");

const response = await fetch("<MARKETDATA_ENDPOINT>/<RESOURCE>", {
  headers: { "api-key": apiKey }
});
if (!response.ok) throw new Error(`NOWNodes MarketData HTTP ${response.status}`);
console.log(await response.json());
```

## Ethers Provider Boundary

Ethers provider header support varies by version. If the selected version cannot attach custom headers cleanly, use a small JSON-RPC fetch wrapper for reads, or configure a documented custom transport. Keep signing in the wallet/application layer and send only signed payloads to broadcast methods after explicit confirmation.

## Viem Transport Boundary

Use viem HTTP/custom transport options that support headers in the selected version. Keep the API key in headers, not source code.
