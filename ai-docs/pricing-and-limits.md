# Pricing And Limits

NOWNodes plans, limits, supported methods, archive access, dedicated nodes, and rate limits may change. Treat pricing and quota information as live product data.

Agents should:

- Avoid claiming exact limits unless they were verified in current official docs or user-provided account data.
- Handle `429` with bounded retries and exponential backoff.
- Explain that `403` can indicate a plan/capability restriction, disabled endpoint, or forbidden method.
- Distinguish public/shared node access from dedicated node access when the user asks about latency, throughput, or custom limits.

Official sources:

- Pricing and product details: https://nownodes.io/home
- FAQ: https://nownodes.io/faq
- Docs: https://docs.nownodes.io/
