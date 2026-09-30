---
name: nownodes-skill
description: Build and troubleshoot integrations with NOWNodes blockchain APIs, including JSON-RPC, REST, WebSocket, Blockbook, Trace/Debug, Archive, and MarketData endpoints.
---

# NOWNodes Skill

Use this skill when a user is integrating, migrating to, testing, or debugging NOWNodes Blockchain API access in an application, script, indexer, wallet, exchange, analytics service, or agent workflow.

## Core Rules

- Prefer `NOWNODES_API_KEY` from the environment. Never hardcode API keys, private keys, mnemonic phrases, signed payloads, or user secrets.
- Default to the HTTP header `api-key: <NOWNODES_API_KEY>`, then check chain-specific NOWNodes docs before asserting unusual auth or endpoint variants.
- Do not make live NOWNodes API calls unless the user explicitly asks you to do so.
- Separate read-only requests from transaction signing or broadcasting. Ask for explicit confirmation before generating or running code that broadcasts a signed transaction.
- Treat the local capability matrix as a routing aid, not as a replacement for official NOWNodes docs. If availability, limits, endpoint hosts, or plan requirements matter, verify against current docs.
- Keep examples production-friendly: timeouts, status/error handling, retry/backoff for `429`, secret redaction in logs, and clear placeholders.

## Routing

Read only the references that match the task:

- Product surfaces, coverage status, and maintenance notes: [PRODUCT_CATALOG.md](PRODUCT_CATALOG.md).
- Product/API overview and official links: [references/overview.md](references/overview.md).
- API key handling and client setup: [references/authentication.md](references/authentication.md).
- Choosing chain, network, endpoint type, and capability: [references/endpoint-selection.md](references/endpoint-selection.md) and [references/capability-matrix.md](references/capability-matrix.md).
- JSON-RPC, REST, WSS, Blockbook, retry, and broadcast patterns: [references/request-patterns.md](references/request-patterns.md).
- HTTP/RPC errors, rate limits, and upstream failures: [references/errors-and-limits.md](references/errors-and-limits.md).
- Copyable TypeScript, curl, Python, ethers, viem, Blockbook, WSS, and MarketData snippets: [references/examples.md](references/examples.md).
- Framework-specific setup: [references/framework-recipes.md](references/framework-recipes.md).
- Migrations from GetBlock, Alchemy, Infura, QuickNode, public RPC, or self-hosted nodes: [references/migrations.md](references/migrations.md).
- Key leakage, rotation, CI/cloud secrets, and signing boundaries: [references/security-playbook.md](references/security-playbook.md).
- Skill QA, eval prompts, and forbidden behavior: [references/testing-and-evals.md](references/testing-and-evals.md).
