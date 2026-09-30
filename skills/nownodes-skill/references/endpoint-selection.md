# Endpoint Selection

Choose endpoints from the user's requested chain, network, and API surface. Do not infer final production hostnames when exact current docs matter; verify with official NOWNodes chain-specific docs.

## Steps

1. Identify chain and network: mainnet, testnet, or chain-specific test network.
2. Identify the required data or action.
3. Choose API type:
   - JSON-RPC for current node state, EVM methods, blocks, logs, gas, and broadcast.
   - REST for native chain or service REST endpoints.
   - WSS for live subscriptions.
   - Blockbook for indexed address/tx/block lookups on supported chains.
   - Trace/Debug for execution traces.
   - Archive for historical state reads.
   - MarketData for market and asset data.
4. Check `capability-matrix.md` for a quick route, then verify uncertain availability in official docs.
5. Generate code with endpoint placeholders if no exact endpoint is confirmed.

## Missing Or Unclear Capability

If the requested capability is missing or unclear:

- Say that capability needs verification in current NOWNodes docs.
- Offer a fallback API surface where possible.
- Avoid silently substituting a public RPC or another vendor unless the user asks for a fallback provider.

## Mainnet/Testnet

Do not switch between mainnet and testnet without naming it. Include chain id or a smoke test when useful:

- EVM: `eth_chainId`, `net_version`, `eth_blockNumber`.
- UTXO/Blockbook: block height, address summary, or transaction lookup.
