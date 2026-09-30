# Endpoint Guidance

NOWNodes endpoint availability can vary by chain, network, API type, plan, and time. This package does not maintain a complete catalog of all supported networks.

## Selection Flow

1. Identify the chain and network: for example Ethereum mainnet, Ethereum Sepolia, Bitcoin mainnet, Polygon mainnet, BNB Smart Chain, or Solana.
2. Identify the API surface:
   - JSON-RPC for EVM-style state reads and transaction broadcast.
   - REST for chains with native REST APIs or service-specific REST endpoints.
   - WebSocket for subscriptions and event streams.
   - Blockbook for indexed UTXO/address/block/transaction lookups where supported.
   - Trace/Debug or Archive for historical state and execution traces where supported by chain and plan.
   - MarketData for asset and market information.
3. Check chain-specific docs under `https://docs.nownodes.io/` before finalizing hostnames or unsupported capabilities.
4. Use placeholders in generated examples: `<CHAIN_ENDPOINT>`, `<WSS_ENDPOINT>`, `<BLOCKBOOK_ENDPOINT>`, `<ADDRESS>`, and `<NOWNODES_API_KEY>`.

## Common Placeholder Shapes

```text
https://<chain-or-service>.nownodes.io
wss://<chain-or-service>.nownodes.io
https://<blockbook-service>.nownodes.io
```

Always prefer the exact official endpoint from NOWNodes docs over inferred hostnames.
