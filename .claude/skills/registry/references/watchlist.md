# Watchlist — young / unverified candidates

Early-stage skills, repos, MCPs, and emerging standards worth STUDYING but NOT yet trustworthy enough to install. Each is date-stamped; **verify the repo is reachable + has real traction before promoting** any entry to [extended-skills.md](extended-skills.md) / [optional-mcps.md](optional-mcps.md). Snapshot: **2026-06**.

These have not cleared the QUALITY BAR (provenance / maintained ≤2mo / license stated) or the SAFETY SCRUTINY gate in [SKILL.md](../SKILL.md). Treat as research leads, not endorsements.

| Candidate | Link | What it claims | Status (2026-06) |
|-----------|------|----------------|------------------|
| gmem | https://github.com/yksanjo/gmem | Agent memory layer | Unverified — confirm maintenance + license before any use. |
| snap-protocol | https://github.com/agentzeny/snap-public | Snapshot/state protocol | Early; verify reachability + traction. |
| seeker-skills | https://github.com/Sarthib7/seeker-skills | Solana Seeker (mobile) skills | Niche mobile; cross-check vs `ext/solana-mobile` coverage. |
| SAID / SATI / AIP | https://github.com/cascade-protocol/sati | Agent-identity standards (SAID/SATI) + AIP | Emerging standard, not a skill yet; monitor for adoption. |
| token-rugcheck | https://github.com/AetherCore-Dev/token-rugcheck | Token rug/scam screening | Verify methodology + that it does not exfiltrate queried mints. |
| DeSide | (search: "DeSide Solana") repo unconfirmed | Decentralized side-data / intel | Repo link unconfirmed — locate canonical source first. |
| covenant | https://github.com/open-covenant/covenant-skill | Agent covenant / commitment skill | Early; verify license + scope. |
| prflght | (search: "prflght Solana") repo unconfirmed | Pre-flight tx checks | Repo link unconfirmed — find canonical source before trusting. |
| Noesis | https://noesisapi.dev/mcp | Hosted token-intelligence MCP | Listed as opt-in in [optional-mcps.md](optional-mcps.md); still hosted/unproven — verify provenance. |

## Explicit SKIPS (evaluated, not pursuing)
- **GOAT** — EVM-biased; not Solana-native enough to be a primary.
- **Eliza** — an agent *framework*, not a skill; out of scope for this registry.
- **Meteora-DLMM (private-key-in-env variants)** — any variant that puts a private key in an env var fails the custody bar; use the vendored sendai `meteora` skill instead.
- **dcSpark Jupiter** — superseded by the official `ext/jupiter` (jup-ag) skill.
- **sendaifun/solana-mcp** — stale; superseded by current MCP options.

## Promotion checklist (before moving an entry off this list)
1. Repo resolves and is real (not a placeholder/squat).
2. Clears the QUALITY BAR: official/org-backed OR >50★; last push ≤2 months; license stated.
3. Passes SAFETY SCRUTINY: no telemetry/exfiltration, no `curl|bash` installer in the routed body, no surprise key custody.
4. Not a duplicate of an existing submodule, `.mcp.json` entry, or [extended-skills.md](extended-skills.md) line.
5. Then file it into the appropriate reference with an add command + risk note, and date-stamp the promotion.
