---
name: registry
description: Scout, vet, and track new Solana skills, repos, and MCP servers. Use when the user says "scout repos", "what new skills/MCPs", "registry", "trusted repos to monitor", "extended skills", "optional mcps", "vet this repo", or "should I add X". Provides a research methodology + curated, link-rich watchlists.
user-invocable: true
---

# Registry — Scouting & Monitoring

The methodology for finding, vetting, and tracking new Solana agent skills, clonable repos, and MCP servers — plus curated watchlists of what is worth monitoring. This skill is the home for opt-in things NOT installed by default (see `references/`).

Already-installed coverage (do not re-add): **18 ext submodules** under `.claude/skills/ext/` and the **MCP servers** in `.mcp.json`. Always dedupe against these before proposing anything.

## When to use
- "What new skills / repos / MCPs exist?" → survey via the SOURCES below + the curated `references/`.
- "Should I add X?" / "Is this repo trustworthy?" → run the QUALITY BAR + SAFETY SCRUTINY gates.
- "What should I monitor?" → point at `references/trusted-repos.md` + `references/watchlist.md`.

## Curated data (read these first — they hold the answers)
- [references/trusted-repos.md](references/trusted-repos.md) — high-signal repos worth monitoring/cloning.
- [references/extended-skills.md](references/extended-skills.md) — opt-in skills NOT installed by default, each with `git submodule add` command + risk note.
- [references/optional-mcps.md](references/optional-mcps.md) — MCPs that can be added, each with exact add command + RISK NOTE.
- [references/watchlist.md](references/watchlist.md) — young/unverified candidates to STUDY before promoting (date-stamped).

## Bulk source (the long tail)
solana-new vendors three catalogs — use them as the bulk corpus, then layer curation on top:
- [clonable-repos.json](../ext/solana-new/cli/data/clonable-repos.json) — **106 repos** (`repos` array).
- [solana-skills.json](../ext/solana-new/cli/data/solana-skills.json) — **15 official + 66 community = 81 skills** (`official_skills` / `community_skills`).
- [solana-mcps.json](../ext/solana-new/cli/data/solana-mcps.json) — **36 MCPs** (`mcps` array).

These are a Dec-2025/Jun-2026 snapshot — treat counts as a floor and re-fetch live before trusting freshness.

## SOURCES to sweep
1. **awesome-solana-ai** — [solana-foundation/awesome-solana-ai](https://github.com/solana-foundation/awesome-solana-ai): the README list **and its open PRs** (PRs surface what is landing next).
2. **Foundation skills page** — solana-foundation org repos (`*-skill`, `eth-to-sol-skill`, `solana-dev-skill`).
3. **GitHub org sweeps** — official orgs publish skills directly: `solana-foundation`, `sendaifun`, `helius-labs`, `jup-ag`, `metaplex-foundation`, `quiknode-labs`, `triton-one`, `anza-xyz`, `solana-mobile`, `colosseum`.
4. **MCP registries** — the public MCP registry/marketplaces; `npx`-installable servers; the vendored `solana-mcps.json`.
5. **npm** — `@<org>/...` skill/MCP packages (e.g. `helius-mcp`, `@phantom/mcp-server`).
6. **Hackathon winners** — Colosseum submissions often seed new tooling (cross-check with the colosseum skill).

## QUALITY BAR (a candidate must clear all three)
- **Provenance**: official / org-backed, OR strong traction (>50★).
- **Maintained**: last push ≤ 2 months.
- **License stated**: MIT / Apache-2.0 (or explicitly permissive). No license → watchlist only, never install.

## SAFETY SCRUTINY (mandatory before trusting — Read/Grep only, NEVER execute)
Grep the candidate for risk patterns before any add:
```
convex | telemetry | TEL_TIER | Preamble | curl .*\|.*sh | install\.sh | key custody | BIP-39 | PRIVATE_KEY
```
- **Telemetry / exfiltration** (e.g. `*.convex.cloud` beacons, "Preamble" bash blocks) → reject or quarantine; never route a self-exfiltrating SKILL.md.
- **`curl … | bash` / `curl … | sh` installers** → never execute; if the skill body is otherwise inert, route only its reference files (see the quicknode-anchor quarantine in the hub).
- **Key custody / signing** (MCPs that hold BIP-39 seeds or sign transactions, e.g. phantom, x402-proxy) → opt-in only, flagged with a ⚠ risk note; never a default.
- A benign local `install.sh` that only copies files to `~/.claude/skills` is acceptable, but we still do not route or execute it — we vendor as a submodule instead.

## DEDUPE
Before proposing an add, check it is not already covered:
- vs the 18 `ext/` submodules (an official primary may already supersede a community copy — e.g. official `jupiter`/`metaplex`/`helius` beat the sendai copies).
- vs the MCP servers in `.mcp.json`.
- vs the solana-new catalogs (avoid re-listing the long tail; cite the catalog entry instead).

## OUTPUT SHAPE (when recommending)
For each candidate, record: **name** · **repo link** · **one-line (why)** · **signal** (official/★/last-push) · **add command** (`git submodule add …` or MCP `claude mcp add …`) · **risk note**. Then file it into the matching `references/` data file:
- trustworthy repo to monitor → `trusted-repos.md`
- installable skill, opt-in → `extended-skills.md`
- installable MCP, opt-in → `optional-mcps.md`
- young/unverified → `watchlist.md` (date-stamp it; note "verify repo reachable + traction before promoting").

## Promotion path
watchlist → (clears QUALITY BAR + SAFETY SCRUTINY, traction confirmed) → extended-skills/optional-mcps (opt-in) → (used widely, official-grade) → propose as a default submodule/MCP via the Ripple Map in `CLAUDE.md`.
