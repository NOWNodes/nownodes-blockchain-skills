# Authentication

Use `NOWNODES_API_KEY` from the environment. Do not hardcode keys, print keys, commit keys, or include user secrets in examples.

Default HTTP authentication:

```text
api-key: <NOWNODES_API_KEY>
```

Check current chain-specific docs before asserting non-default header names, URL query parameters, WSS auth behavior, or service-specific requirements.

## TypeScript Fetch

```ts
const apiKey = process.env.NOWNODES_API_KEY;
if (!apiKey) throw new Error("Missing NOWNODES_API_KEY");

const response = await fetch("<CHAIN_ENDPOINT>", {
  method: "POST",
  headers: {
    "content-type": "application/json",
    "api-key": apiKey
  },
  body: JSON.stringify({
    jsonrpc: "2.0",
    id: 1,
    method: "eth_blockNumber",
    params: []
  })
});
```

## Curl

```bash
curl -sS '<CHAIN_ENDPOINT>' \
  -H "content-type: application/json" \
  -H "api-key: ${NOWNODES_API_KEY}" \
  --data '{"jsonrpc":"2.0","id":1,"method":"eth_blockNumber","params":[]}'
```

## Python Requests

```py
import os
import requests

api_key = os.environ["NOWNODES_API_KEY"]
response = requests.post(
    "<CHAIN_ENDPOINT>",
    headers={"api-key": api_key},
    json={"jsonrpc": "2.0", "id": 1, "method": "eth_blockNumber", "params": []},
    timeout=10,
)
```

## Ethers

Use a custom fetch layer or provider option that can send the `api-key` header. If the ethers version or transport wrapper cannot send custom headers cleanly, prefer a small JSON-RPC client wrapper or a documented provider configuration supported by that version.

## Viem

Use `custom` or `http` transport options that support custom fetch/headers in the selected viem version. Keep the API key outside the URL unless official docs require a query parameter.

## Logging

Redact secrets before logging request configuration:

```ts
const safeHeaders = { ...headers, "api-key": "<redacted>" };
```
