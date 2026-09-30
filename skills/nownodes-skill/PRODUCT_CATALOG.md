# NOWNodes Skill Product Catalog

Maintenance source of truth for `nownodes-skill`. Product names and URLs should match current public NOWNodes product and documentation pages.

`coverage` values:

- `full`: routed from `SKILL.md` and covered by a dedicated or sufficiently detailed reference.
- `partial`: named and usable, but coverage is summary-level or depends heavily on current chain docs.
- `stub`: intentionally tracked, but not yet implemented deeply enough for agents to provision or integrate without checking official docs.

```yaml
last_verified: 2026-09-30
docs_root: https://docs.nownodes.io/
site_root: https://nownodes.io/

products:
  - name: API Keys
    slug: api-keys
    category: Platform
    docs_url: https://docs.nownodes.io/
    skill_section: Core Rules
    skill_reference: references/authentication.md
    coverage: full
    notes: "Default agent behavior is env var NOWNODES_API_KEY and api-key header. Chain-specific docs override this only when explicit."

  - name: Shared Nodes / Full Nodes
    slug: shared-full-nodes
    category: Node Access
    docs_url: https://docs.nownodes.io/
    skill_section: Endpoint Selection
    skill_reference: references/endpoint-selection.md
    coverage: full
    notes: "Default read/write node API surface. Use exact chain docs for hostnames, mainnet/testnet, and method support."

  - name: Dedicated Nodes aka Custom Nodes
    slug: dedicated-custom-nodes
    category: Node Access
    docs_url: https://docs.nownodes.io/
    skill_section: Endpoint Selection
    skill_reference: references/endpoint-selection.md
    coverage: partial
    notes: "Private hosted node offering. Agents should explain when it matters, but not promise provisioning from this skill."

  - name: Public Nodes
    slug: public-nodes
    category: Node Access
    docs_url: https://nownodes.io/faq
    skill_section: Endpoint Selection
    skill_reference: references/errors-and-limits.md
    coverage: partial
    notes: "Useful as a contrast with shared authenticated access. FAQ describes public nodes as free, overloaded, and low-limit."

  - name: Node APIs
    slug: node-apis
    category: Node Access
    docs_url: https://docs.nownodes.io/
    skill_section: Request Patterns
    skill_reference: references/request-patterns.md
    coverage: full
    notes: "JSON-RPC and chain-native REST patterns for reading state and broadcasting signed transactions."

  - name: WebSocket API
    slug: websocket-api
    category: Real-Time Data
    docs_url: https://docs.nownodes.io/
    skill_section: Request Patterns
    skill_reference: references/request-patterns.md
    coverage: partial
    notes: "Use only after checking WSS support for the selected chain. Header/query auth behavior must follow current docs."

  - name: Blockbook API
    slug: blockbook-api
    category: Indexed Data
    docs_url: https://nownodes.io/blockbook
    skill_section: Request Patterns
    skill_reference: references/request-patterns.md
    coverage: partial
    notes: "Read-optimized indexed API for balances, transactions, blocks, and address history. Dedicated reference is a good next addition."

  - name: Block Explorers
    slug: block-explorers
    category: Indexed Data
    docs_url: https://nownodes.io/blockbook
    skill_section: Overview
    skill_reference: references/overview.md
    coverage: stub
    notes: "Public explorer UI and explorer-style data should not be confused with raw node RPC."

  - name: Archive Nodes
    slug: archive-nodes
    category: Historical Data
    docs_url: https://docs.nownodes.io/
    skill_section: Endpoint Selection
    skill_reference: references/endpoint-selection.md
    coverage: partial
    notes: "Required for historical state beyond normal retention. Availability and plan requirements are chain-sensitive."

  - name: Trace & Debug API
    slug: trace-debug-api
    category: Historical Data
    docs_url: https://docs.nownodes.io/
    skill_section: Endpoint Selection
    skill_reference: references/endpoint-selection.md
    coverage: partial
    notes: "Use for step-level execution analysis. Must verify chain, client, method family, and plan support."

  - name: gRPC API
    slug: grpc-api
    category: Advanced Interfaces
    docs_url: https://docs.nownodes.io/
    skill_section: Overview
    skill_reference: references/overview.md
    coverage: stub
    notes: "Tracked as an advanced API surface. Add a dedicated reference before generating gRPC code."

  - name: MCP
    slug: mcp
    category: Agent Tooling
    docs_url: https://docs.nownodes.io/
    skill_section: Overview
    skill_reference: references/overview.md
    coverage: stub
    notes: "Tracked because NOWNodes docs expose MCP as an agent-facing surface. This skill currently does not provision MCP servers."

  - name: Monitoring
    slug: monitoring
    category: Operations
    docs_url: https://docs.nownodes.io/
    skill_section: Troubleshooting
    skill_reference: references/errors-and-limits.md
    coverage: stub
    notes: "Useful for production diagnostics and SLA discussions. Add a monitoring reference when concrete integration guidance is needed."

  - name: Team Access
    slug: team-access
    category: Account
    docs_url: https://docs.nownodes.io/
    skill_section: Security
    skill_reference: references/security-playbook.md
    coverage: partial
    notes: "Relevant to key ownership, least privilege, rotation, and incident response."

  - name: MarketData API
    slug: marketdata-api
    category: Market Data
    docs_url: https://docs.nownodes.io/nowmarket/
    skill_section: Examples
    skill_reference: references/examples.md
    coverage: partial
    notes: "Use for asset/market data instead of node RPC. Dedicated reference should cover rates, currencies, market-data, and price endpoints."

  - name: Webhooks
    slug: webhooks
    category: Notifications
    docs_url: https://nownodes.io/faq
    skill_section: null
    skill_reference: null
    coverage: stub
    notes: "FAQ lists Webhooks as a feature. Add a reference only after official endpoint docs are available and integration requests appear."
```

## Maintenance

When a product changes:

1. Update the most specific reference first.
2. Update `SKILL.md` only if routing or core safety behavior changes.
3. Update this catalog's `last_verified`, `coverage`, and notes.
4. Prefer `partial` or `stub` over invented details when official docs are unclear.
