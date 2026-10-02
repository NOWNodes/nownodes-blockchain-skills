# Eval: Bitcoin Blockbook

Prompt:

```text
Use $nownodes-skill to create a Python requests example that checks a Bitcoin address through a NOWNodes Blockbook endpoint.
```

Expected:

- Treats Blockbook as indexed explorer-style data, not generic JSON-RPC.
- Uses `<BLOCKBOOK_ENDPOINT>` and `<ADDRESS>` placeholders unless the endpoint is verified from current docs.
- Reads `NOWNODES_API_KEY` from environment.
- Sends the `api-key` header.
- Explains that Blockbook response shape differs from JSON-RPC.
