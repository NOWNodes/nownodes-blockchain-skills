# Overview

NOWNodes is a Blockchain-as-a-Service provider for accessing full nodes, archive nodes, block explorers, WebSockets, Blockbook, Trace/Debug, gRPC, MCP-related integrations, team access, and MarketData APIs across many blockchain networks.

Official sources:

- Docs: https://docs.nownodes.io/
- FAQ: https://nownodes.io/faq
- Site: https://nownodes.io/home

## API Classes

- JSON-RPC: use for EVM-compatible reads, chain state, block data, gas estimates, logs, and transaction broadcast where supported.
- REST: use when the chain or NOWNodes service exposes native HTTP resources instead of JSON-RPC methods.
- WebSocket: use for subscriptions such as new block headers, logs, or pending transactions when the selected chain supports WSS.
- Blockbook: use for indexed UTXO/address/transaction/block lookups when Blockbook is available for the chain.
- Trace/Debug: use for execution tracing and debugging where methods and plan support exist.
- Archive: use for historical state at old block heights where an archive node is required.
- MarketData: use for asset, price, or market-oriented data exposed by NOWNodes MarketData docs.

## Decision Hints

- Wallet balance or current block height: JSON-RPC for EVM chains, Blockbook for UTXO address indexing where available.
- Indexer catch-up: JSON-RPC for blocks/logs, WSS for live tail, Archive for old state, Blockbook for indexed address/tx lookup.
- Transaction send: JSON-RPC broadcast after local signing. Keep signing outside NOWNodes unless the user's own app already owns that boundary.
- Debugging transaction execution: Trace/Debug or Archive only after checking support and plan access.
- Asset pricing: MarketData rather than node RPC.
