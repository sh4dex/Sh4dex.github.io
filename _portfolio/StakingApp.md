---
title: "Staking App"
excerpt: "Decentralized staking protocol with flexible lock-in periods, dynamic yield rates, and reward distribution. Stake tokens to earn passive income with transparent on-chain settlement."
tagline: "Decentralized staking protocol with flexible lock-in periods and dynamic yield. Stake tokens to earn passive rewards with full transparency and on-chain settlement."
image: /images/projects/stakingApp.png
github: https://github.com/sh4dex/Staking-App
collection: portfolio
badge: "DEFI"
tech_tags: [Solidity, Foundry, Smart Contracts, Staking]
---

<a href="https://github.com/sh4dex/Staking-App" class="btn btn--inverse btn--large" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>

---

Staking App is a decentralized staking protocol that enables users to deposit tokens and earn passive rewards. The protocol features flexible lock-in periods, dynamic yield rates adjusted by market conditions, and transparent on-chain reward distribution with atomic settlement.

## Key Features

- **Flexible Staking** — choose lock-in periods matching your investment strategy
- **Dynamic Yields** — reward rates adjust based on total staked value and demand
- **Transparent Rewards** — all distributions calculated and verified on-chain
- **Atomic Settlement** — rewards distributed trustlessly without intermediaries

## Architecture

![Staking App Architecture](/images/projects/stakingApp.png)

## Staking Flow

```
User ──► deposit tokens ──► lock period starts ──► earn daily rewards ──► withdraw at maturity ──► tokens + rewards received
```

## Security

- **Non-custodial** — smart contract holds tokens, users maintain control via private keys
- **Automated Distribution** — reward calculations performed by contract logic, not external actors
- **Lock Enforcement** — time-lock mechanism prevents early withdrawal unless explicitly allowed
- **On-chain Transparency** — all stakes, yields, and withdrawals recorded on immutable ledger
