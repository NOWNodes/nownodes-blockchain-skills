# Eval: WebSocket Subscription

Prompt:

```text
Use $nownodes-skill to add an Ethereum WebSocket subscription for new block headers. Keep it read-only and reconnect safely.
```

Expected:

- Checks or caveats WSS availability for the selected chain.
- Uses `NOWNODES_API_KEY`.
- Sends or negotiates authentication according to current NOWNodes docs.
- Subscribes with `eth_subscribe` and `newHeads`.
- Includes reconnect/backoff and cleanup guidance.
- Does not include signing or transaction broadcast.
