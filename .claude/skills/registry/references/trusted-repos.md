# Trusted Repos to Monitor

High-signal repos worth watching for new skills, patterns, and tooling. Snapshot: **2026-06**. For the long tail (106 repos), read [clonable-repos.json](../../ext/solana-new/cli/data/clonable-repos.json) (`repos` array) — this file curates the highest-signal entries plus our own additions on top of that bulk.

Re-verify last-push freshness before relying on any entry; treat dates as a floor.

## Already vendored as submodules (do NOT re-add — listed for dedupe)
These 18 are installed under `.claude/skills/ext/`:
`solana-dev`, `sendai`, `solana-game`, `cloudflare`, `trailofbits`, `qedgen`, `solana-mobile`, `colosseum`, `safe-solana-builder`, `vercel`, `solana-new`, `ghostsecurity`, `defending-code`, `jupiter`, `metaplex`, `helius`, `quicknode-anchor`, `eth-to-sol`.

## Official / Foundation orgs (sweep these for new `*-skill` repos)
| Org | Link | Why monitor |
|-----|------|-------------|
| Solana Foundation | https://github.com/solana-foundation | Source of `solana-dev-skill`, `eth-to-sol-skill`, awesome-solana-ai; first-party patterns |
| Anza | https://github.com/anza-xyz | Agave validator, Solana core; SVM internals truth |
| SendAI | https://github.com/sendaifun | `skills` (DeFi), `solana-new` (idea→launch); fast-moving protocol coverage |
| Helius Labs | https://github.com/helius-labs | `core-ai` (skill + MCP + SVM); RPC/DAS/streaming |
| Jupiter | https://github.com/jup-ag | `agent-skills`; canonical swap/lend/perps integration |
| Metaplex | https://github.com/metaplex-foundation | `skill`; NFT/Core/Bubblegum/Candy Machine standard |
| QuickNode | https://github.com/quiknode-labs | `solana-anchor-claude-skill`; Anchor/Quasar/financial-math refs |
| Triton One | https://github.com/rpcpool | Yellowstone gRPC / Geyser; high-perf data |
| Solana Mobile | https://github.com/solana-mobile | MWA, Seeker/Saga, SKR |
| Colosseum | https://github.com/ColosseumOrg | Hackathon tooling + copilot |

## Curated high-signal lists (meta-sources)
| Repo | Link | Why |
|------|------|-----|
| awesome-solana-ai | https://github.com/solana-foundation/awesome-solana-ai | The canonical index; watch the README **and open PRs** for what is landing next |
| solana-new catalogs | [clonable-repos.json](../../ext/solana-new/cli/data/clonable-repos.json) | 106-repo vendored corpus; bulk source for the long tail |

## How to use
1. Sweep the orgs above for new `*-skill` / `agent-skills` repos and the awesome-solana-ai PR queue.
2. Run the QUALITY BAR + SAFETY SCRUTINY gates from [SKILL.md](../SKILL.md).
3. Dedupe against the 18 submodules + `.mcp.json` + the catalog above.
4. File the survivor into [extended-skills.md](extended-skills.md) (skill), [optional-mcps.md](optional-mcps.md) (MCP), or [watchlist.md](watchlist.md) (unverified).
