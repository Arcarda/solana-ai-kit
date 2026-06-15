# Extended Skills (opt-in, NOT installed by default)

Skills that COULD be added as submodules but are intentionally left out of the default install — niche, situational, or pending consolidation. Each carries a repo link, a one-line rationale, the exact `git submodule add` command, and a risk note. Snapshot: **2026-06**.

To install one, run its command from the repo root, then route it in `.claude/skills/SKILL.md` (and follow the Ripple Map in `CLAUDE.md`). Run the SAFETY SCRUTINY gate from [SKILL.md](../SKILL.md) first.

| Skill | Repo | Why opt-in (not default) |
|-------|------|--------------------------|
| Light Protocol | https://github.com/Lightprotocol/skills | ZK compression — niche; **likely to merge into Helius** soon, so vendoring now risks a near-term duplicate. Watch before adding. |
| Alchemy | https://github.com/alchemyplatform/skills | RPC/DAS/x402/SIWS — solid, but not our standard stack (we ship Helius as the RPC primary). |
| dflow-phantom | https://github.com/DFlowProtocol/dflow_phantom-connect-skill | DFlow + Phantom connect; the official Helius repo already ships dflow/phantom layers (`ext/helius/helius-skills/helius-dflow`, `helius-phantom`). |
| Octav | https://github.com/Octav-Labs/octav-api-skill | Portfolio/PnL API; overlaps sendai `wallet-analysis` (Zerion). |
| Quasar | https://github.com/blueshift-gg/quasar | Quasar zero-copy framework skill; we already route the quicknode-anchor `QUASAR.md` reference. Add the full skill only for deep Quasar work. |
| pnp-markets | https://github.com/pnp-protocol/solana-skill | Prediction markets protocol; single-protocol, low traction. |
| tenequm/skills | https://github.com/tenequm/skills | General Solana skills collection; verify scope vs `solana-dev` before adding. |
| Meteora SDK | https://github.com/MeteoraAg/meteora-sdk-skill | Meteora DLMM SDK; sendai already ships a `meteora` skill — add only if the SDK-level depth is needed. |

## Add commands
```bash
# Light Protocol (ZK compression) — verify it has not merged into Helius first
git submodule add https://github.com/Lightprotocol/skills .claude/skills/ext/light-protocol

# Alchemy (RPC/DAS/x402/SIWS)
git submodule add https://github.com/alchemyplatform/skills .claude/skills/ext/alchemy

# DFlow + Phantom connect
git submodule add https://github.com/DFlowProtocol/dflow_phantom-connect-skill .claude/skills/ext/dflow-phantom

# Octav (portfolio/PnL API)
git submodule add https://github.com/Octav-Labs/octav-api-skill .claude/skills/ext/octav

# Quasar (zero-copy framework)
git submodule add https://github.com/blueshift-gg/quasar .claude/skills/ext/quasar

# pnp-markets (prediction markets)
git submodule add https://github.com/pnp-protocol/solana-skill .claude/skills/ext/pnp-markets

# tenequm general skills
git submodule add https://github.com/tenequm/skills .claude/skills/ext/tenequm

# Meteora SDK skill
git submodule add https://github.com/MeteoraAg/meteora-sdk-skill .claude/skills/ext/meteora-sdk
```

## Risk notes
- **Light Protocol**: pending merge into Helius — adding now likely creates a duplicate within weeks. Prefer watchlist until the merge resolves.
- **Alchemy**: off our standard stack (Helius is the RPC primary). Adds a second, partly-overlapping RPC surface — only worth it for Alchemy-specific features (e.g. their x402 flow).
- **dflow-phantom / Meteora SDK**: overlap with already-vendored coverage (Helius dflow/phantom layers; sendai meteora). Confirm the delta is worth a separate submodule before adding.
- All others: low-traction / single-protocol. Clear the QUALITY BAR (>50★ or org-backed, push ≤2mo, license stated) before promoting from this list to a default.
