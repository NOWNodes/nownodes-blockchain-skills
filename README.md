# NOWNodes Blockchain Skills

`nownodes-blockchain-skills` is a Codex skill package for agents that build or troubleshoot integrations with [NOWNodes](https://nownodes.io/home) Blockchain API.

It helps agents choose between JSON-RPC, REST, WebSocket, Blockbook, Trace/Debug, Archive, and MarketData access; use `NOWNODES_API_KEY` safely; generate code examples; diagnose common `401`, `429`, and upstream errors; and keep transaction broadcasting separate from read-only calls.

## Install

From a public repository:

```bash
npx skills add https://github.com/NOWNodes/nownodes-blockchain-skills --skill nownodes-skill
```

From a local checkout:

```bash
npx skills add ./nownodes-blockchain-skills --skill nownodes-skill
```

## Use

After installation, invoke the skill in an agent prompt:

```text
Use $nownodes-skill to add a read-only Ethereum JSON-RPC smoke test using NOWNODES_API_KEY.
```

Example request:

```text
Use $nownodes-skill to migrate my ethers.js provider from Infura to NOWNodes. Keep it read-only and add clear handling for 401 and 429.
```

## Contents

- `skills/nownodes-skill/SKILL.md` is the short entrypoint and routing layer.
- `skills/nownodes-skill/PRODUCT_CATALOG.md` tracks NOWNodes product/API surfaces and coverage status.
- `skills/nownodes-skill/references/` contains focused guidance for auth, endpoint selection, request patterns, framework recipes, migrations, security, and evals.
- `ai-docs/` contains agent-facing overview files.
- `MAINTENANCE.md` explains the repository shape, why this package is intentionally smaller than the GetBlock reference, and which references are worth adding next.

## Safety Defaults

- No real API keys, private keys, mnemonic phrases, or signed payloads are included.
- Examples read API keys from `NOWNODES_API_KEY`.
- Live API calls are not performed by default.
- Transaction broadcast examples require explicit user confirmation before execution.

## Sources

The package points agents to official NOWNodes sources instead of copying full docs:

- NOWNodes docs: https://docs.nownodes.io/
- NOWNodes FAQ: https://nownodes.io/faq
- NOWNodes site: https://nownodes.io/home

When endpoint availability or limits matter, agents should verify current chain-specific documentation.
