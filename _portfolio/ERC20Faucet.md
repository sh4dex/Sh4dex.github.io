---
title: "ERC20 Faucet"
excerpt: "Time-driven ERC20 token faucet implementation. Periodical token claims with cooldown and max claim limits."
tagline: "Time-driven ERC20 token faucet. Periodic token claims with cooldown enforcement and max claim limits. Deployed on Arbitrum Sepolia."
image: /images/projects/erc20-faucet-cover.png
github: https://github.com/sh4dex/ERC20-faucet
collection: portfolio
badge: "DEFI"
tech_tags: [Solidity, Foundry, OpenZeppelin, ERC-20, Arbitrum]
---

<a href="https://github.com/sh4dex/ERC20-faucet" class="btn btn--inverse btn--large" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>


## Overview

This project implements a simple ERC20 token and a faucet smart contract that allows users to claim tokens periodically with a cooldown and a maximum number of claims. Built using **Foundry** and **OpenZeppelin** as part of a Solidity learning and development workflow. An ERC20 token implementation built on top of OpenZeppelin.

Deployment script: `script/DeployTHXToken.s.sol`

## Deployed Contracts — Arbitrum Sepolia Testnet

| Contract | Address |
|---|---|
| TokenFaucet | `0x88E6277b1CfA68D47EB09d08F232d42A98A30942` |

🔗 [View on Arbiscan Sepolia](https://sepolia.arbiscan.io/address/0x88E6277b1CfA68D47EB09d08F232d42A98A30942)

## claim() Execution Flow

![Execution Flow](/images/projects/executionFlow.webp)

1. Check `block.timestamp - _lastClaim ≥ cooldown`
2. Check `balanceOf(this) ≥ _dripAmount`
3. Check `_timesClaimed[sender] < 20`
4. `_token.transfer(msg.sender, _dripAmount)`
5. Update `_lastClaim` + `_timesClaimed++`
6. Emit `tokensClaimed` event
