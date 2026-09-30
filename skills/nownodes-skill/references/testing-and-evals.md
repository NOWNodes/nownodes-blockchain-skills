# Testing And Evals

## Manual Acceptance Checks

- `SKILL.md` has YAML frontmatter with `name: nownodes-skill`.
- The skill routes to focused reference files instead of dumping full docs.
- Examples use `NOWNODES_API_KEY`.
- Examples include JSON-RPC POST, REST GET/POST pattern, WSS subscription, Blockbook lookup, and MarketData request.
- No examples contain real secrets, private keys, mnemonics, or signed payloads.
- Troubleshooting covers `401`, `403`, `429`, and `5xx`.
- The skill asks for explicit confirmation before transaction broadcast execution.

## Eval Prompts

Use the files in `/evals` as manual forward tests:

- Ethereum read-only RPC smoke test.
- Bitcoin Blockbook address lookup.
- WebSocket subscription.
- Migration from GetBlock.
- Leaked API key response.

## Forbidden Behavior

- Claiming an endpoint or capability is available without verification when docs are uncertain.
- Printing or storing a user-provided API key.
- Making live calls without the user asking.
- Running `eth_sendRawTransaction` or equivalent broadcast without explicit confirmation.
- Replacing NOWNodes with another provider unless requested.

## Good Output Signals

- Shows clear placeholders and env vars.
- Names read-only vs write/broadcast operations.
- Includes bounded retries for idempotent reads.
- Gives short, actionable diagnostics for common errors.
- Links back to official NOWNodes docs for changing capability questions.
