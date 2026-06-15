# Optional MCP Servers (opt-in, NOT defaults)

MCP servers that can be added on demand. They are NOT in the default `.mcp.json` because they require key custody, transaction-signing capability, a paid key, or are situational. Each entry gives the exact add command and a RISK NOTE. Snapshot: **2026-06**.

For the 36-entry bulk corpus, read [solana-mcps.json](../../ext/solana-new/cli/data/solana-mcps.json) (`mcps` array). This file curates the highest-signal opt-ins on top of that. Always run the SAFETY SCRUTINY gate from [SKILL.md](../SKILL.md) before adding — especially for anything that holds keys or signs.

## Default MCPs already shipped (do NOT re-add — for dedupe)
See `.mcp.json`. The Solana-relevant defaults include Helius (on-chain data) and solana-dev (docs). This list is strictly the opt-in extras.

| MCP | Add | Risk note |
|-----|-----|-----------|
| jupiter-docs | remote, `https://dev.jup.ag/mcp` | ✅ Zero-key remote, official Jupiter docs server. Read-only. Lowest-risk add. |
| phantom | `@phantom/mcp-server` | ⚠ **Wallet signing capability** — can sign/submit transactions. Only add with explicit user consent; never in a default profile. |
| x402-proxy | `npx x402-proxy` | ⚠ **BIP-39 key custody** — holds a seed to make agent payments (x402). High-trust; opt-in only, isolate keys. |
| pyth-pro | paid key | 500+ price feeds, low latency. Requires a paid Pyth Pro API key. No custody risk, but billable. |
| chainstack | remote, `https://mcp.chainstack.com/mcp` | Unified multi-chain RPC. Hosted; check their data/retention policy. |
| noesis | remote, `https://noesisapi.dev/mcp` | Hosted token-intelligence. Third-party hosted — verify provenance/traction before trusting. |
| dexpaprika | `npx dexpaprika-mcp` | ✅ Free, no-key DEX market data. Low-risk read-only add. |

## Add commands
```bash
# jupiter-docs — official, zero-key remote (read-only)
claude mcp add --transport http jupiter-docs https://dev.jup.ag/mcp

# phantom — ⚠ signs transactions; explicit consent only
claude mcp add phantom -- npx -y @phantom/mcp-server

# x402-proxy — ⚠ BIP-39 key custody for agent payments
claude mcp add x402-proxy -- npx -y x402-proxy

# pyth-pro — paid key (500+ feeds); set PYTH_API_KEY
claude mcp add pyth-pro -- npx -y @pythnetwork/pyth-mcp

# chainstack — hosted unified RPC
claude mcp add --transport http chainstack https://mcp.chainstack.com/mcp

# noesis — hosted token intel
claude mcp add --transport http noesis https://noesisapi.dev/mcp

# dexpaprika — free, no-key DEX data
claude mcp add dexpaprika -- npx -y dexpaprika-mcp
```

Verify each `npx` package name and remote URL against the upstream before adding — package names drift. Exact `claude mcp add` syntax may vary by CLI version; treat the commands above as templates.

## Decision rules
- **Custody/signing MCPs (phantom, x402-proxy)**: never a default; require explicit user opt-in; keep their keys isolated from the rest of the agent.
- **Paid MCPs (pyth-pro)**: add only when the feed breadth is actually needed; surface the billing implication.
- **Hosted/remote (chainstack, noesis, jupiter-docs)**: prefer official (jupiter-docs) > established (chainstack) > newer (noesis); check data-retention before sending sensitive queries.
- **Free read-only (dexpaprika, jupiter-docs)**: safest extras; still dedupe vs Helius/solana-dev defaults.
