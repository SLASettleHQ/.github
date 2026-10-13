<div align="center">

<img src="https://raw.githubusercontent.com/SLASettleHQ/.github/main/profile/assets/slasettle-org-banner.webp" alt="SLASettle" width="100%" />

# SLASettle

Open-source bonded SLA monitoring and settlement protocol on Stellar.

[Live App](https://slasettle-web.vercel.app) · [Documentation](https://slasettle-docs.vercel.app) · [Contracts](https://github.com/SLASettleHQ/slasettle-vault) · [Hub](https://github.com/SLASettleHQ/slasettle-hub) · [Testnet Deployment](https://slasettle-docs.vercel.app/testnet-deployment)

</div>

---

## Overview

SLASettle enables service providers to back service-level agreements with an on-chain token bond on Stellar. Registered, independent watchers monitor endpoint health round by round. When enough watchers report a confirmed downtime breach, permissionless settlement pays a configured penalty directly to the beneficiary from the deposited bond.

Settlement is permissionless once quorum is satisfied, but is not triggered automatically by either repository. In the current Testnet deployment, initial watcher addresses were registered by the maintainer for verification rather than by independent third-party operators.

## Repositories

| Repository | Purpose | Primary Stack | Current Status |
| --- | --- | --- | --- |
| [slasettle-vault](https://github.com/SLASettleHQ/slasettle-vault) | Soroban smart contracts (`watcher_registry` and `sla_vault`) for watcher management and bonded SLA settlement | Rust, Soroban SDK 28.0.0 | Testnet deployed |
| [slasettle-hub](https://github.com/SLASettleHQ/slasettle-hub) | Web dashboard, TypeScript SDK, hosted event indexer, Go watcher daemon, and documentation | Next.js, TypeScript, Go, Cloudflare Workers & D1 | Live Testnet application |

## Live Testnet Services

- **Web Application**: [slasettle-web.vercel.app](https://slasettle-web.vercel.app) (Hosted on Vercel)
- **Documentation**: [slasettle-docs.vercel.app](https://slasettle-docs.vercel.app) (Hosted on Vercel)
- **Hosted Indexer API**: [slasettle-indexer.slasettle-indexer.workers.dev](https://slasettle-indexer.slasettle-indexer.workers.dev) (Hosted on Cloudflare Workers, backed by Cloudflare D1)
- **SLA Vault Contract**: [`CDBFPYHJNYSIFXSMXF3BBDWPKHRS7SJFFEKMQ5WJXYTBMD4LFAG2CHLN`](https://stellar.expert/explorer/testnet/contract/CDBFPYHJNYSIFXSMXF3BBDWPKHRS7SJFFEKMQ5WJXYTBMD4LFAG2CHLN)
- **Watcher Registry Contract**: [`CDRNXUPCZTVZXKPWNBQZAYI6HYFNBDHRO2KNNJSMDVTEHFOM7LCMOYMF`](https://stellar.expert/explorer/testnet/contract/CDRNXUPCZTVZXKPWNBQZAYI6HYFNBDHRO2KNNJSMDVTEHFOM7LCMOYMF)
- **Target Network**: Stellar Testnet (`https://soroban-testnet.stellar.org`, Network Passphrase: `Test SDF Network ; September 2015`)

## Verification & Status

- **Network**: Stellar Testnet only. SLASettle is not deployed to Stellar Mainnet.
- **Contract Parity**: Local build artifacts match deployed Testnet WASM bytecode byte-for-byte (`watcher_registry`: `5478788e...`, `sla_vault`: `e177a76f...`).
- **Live Writes Verified**: Wallet-signed SLA creation, bond top-up, SLA cancellation, and bond withdrawal have been verified on Testnet with live transactions.
- **Settlement Verification**: Settlement payout logic is verified via contract tests and historical Testnet transaction evidence. Frontend-driven settlement was not live-submitted in Phase 7 because no genuine unsettled quorum-reached breach round existed on Testnet, and no artificial votes were fabricated.
- **Watcher Operation**: Watcher daemons are designed to run as standalone services operated by third parties; in the current deployment, test rounds were driven by the maintainer.
- **Security & Audit**: No independent third-party security audit has been performed on these smart contracts or off-chain components.
