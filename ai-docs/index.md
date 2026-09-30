# NOWNodes Skill AI Docs

This directory gives agents a compact, documentation-oriented view of the NOWNodes skill package.

Use the installable skill at `skills/nownodes-skill/` for task execution. Use these docs when preparing repository descriptions, external agent context, or `llms.txt` style discovery.

## Official Sources

- NOWNodes docs: https://docs.nownodes.io/
- NOWNodes FAQ: https://nownodes.io/faq
- NOWNodes home: https://nownodes.io/home

## Package Goals

- Help agents select JSON-RPC, REST, WSS, Blockbook, Trace/Debug, Archive, or MarketData access.
- Standardize safe API key usage through `NOWNODES_API_KEY`.
- Provide copyable integration patterns for TypeScript, JavaScript, Python, ethers, viem, and raw clients.
- Support troubleshooting for auth, rate limits, gateway failures, node upstream errors, and migration parity checks.

## Maintenance Rule

Update only the affected reference files and examples when official NOWNodes docs change. Do not rewrite the whole skill for localized endpoint or capability changes.
