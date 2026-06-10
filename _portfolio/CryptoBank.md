---
title: "CryptoBank"
excerpt: "Solidity Ether bank contract with deposit, withdrawal, and peer-to-peer transfer. Reentrancy-protected with owner-configurable deposit limits and on-chain event logging."
tagline: "Solidity Ether bank contract with deposit, withdrawal, and peer-to-peer transfer. Reentrancy-protected with owner-configurable deposit limits."
image: /images/projects/CryptoBank.sol.png
github: https://github.com/sh4dex/CryptoBank
collection: portfolio
badge: "BLOCKCHAIN"
tech_tags: [Solidity, Foundry, OpenZeppelin, ReentrancyGuard]
---

<a href="https://github.com/sh4dex/CryptoBank" class="btn btn--inverse btn--large" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>

---

CryptoBank is a Solidity smart contract that acts as an on-chain Ether bank. Users can deposit ETH, withdraw their balance, and send ETH directly to other addresses — all guarded against reentrancy attacks. The contract owner can adjust the maximum deposit limit at any time.

Built using **Foundry** as part of a Solidity security and smart contract development workflow.

## Architecture

![CryptoBank Contract Architecture](/images/projects/CryptoBank.sol.png)

## Functions

| Function | Access | Description |
|---|---|---|
| `depositEther()` | Public | Deposit ETH into the bank; updates `Balances[msg.sender]` |
| `withdrawEther(amount)` | Public | Withdraw ETH to caller; protected with `nonReentrant` |
| `sendEth(amount, to)` | Public | Transfer ETH to another address; protected with `nonReentrant` |
| `modifyMaxLimit(n)` | Owner | Update the `depositLimit` state variable |

## State Variables & Events

| Name | Type | Description |
|---|---|---|
| `Balances` | `mapping(address => uint)` | Tracks each user's ETH balance |
| `depositLimit` | `uint` | Maximum ETH a user can deposit |

| Event | Emitted When |
|---|---|
| `EtherDeposited` | Successful deposit |
| `EtherWithdrawn` | Successful withdrawal |
| `EtherSent` | Successful peer-to-peer transfer |
| `MaxBalanceEdited` | Owner changes the deposit limit |

## Security

- `withdrawEther` and `sendEth` use a **`nonReentrant` modifier** to prevent reentrancy attacks.
- Balance checks are performed before any ETH transfer.
- Owner-only access control is applied to administrative functions.
