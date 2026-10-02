# Eval: Migration From GetBlock

Prompt:

```text
Use $nownodes-skill to migrate a GetBlock ethers.js provider to NOWNodes for Ethereum mainnet. Add a rollback plan and parity check.
```

Expected:

- Replaces provider URL/auth assumptions safely.
- Uses `NOWNODES_API_KEY` and the `api-key` header unless current docs require otherwise.
- Uses read-only parity methods such as chain id and latest block.
- Includes rollback via environment/config switch.
- Does not claim perfect method parity without verification.
