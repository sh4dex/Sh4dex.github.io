---
title: "Debt Splitter"
excerpt: "Trustless on-chain expense splitter — no backend, no server. Expenses and debts live on Ethereum. A factory pattern deploys Group contracts that track balances, compute optimal debt settlements via a greedy algorithm, and handle ETH payouts atomically."
tagline: "Trustless on-chain expense splitter. Group expenses and debts live entirely on Ethereum — no backend, no server, no trusted third party."
image: /images/projects/splitter.png
github: https://github.com/Jeisson888/blockchain-splitwise/tree/contracts
collection: portfolio
badge: "BLOCKCHAIN"
tech_tags: [Solidity, Foundry]
---

<a href="https://github.com/Jeisson888/blockchain-splitwise/tree/contracts" class="btn btn--inverse btn--large" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>

---

Debt Splitter is a trustless expense-splitting protocol built entirely in Solidity. No backend, no server — expenses and debts live on-chain. A factory contract deploys per-group instances that track member balances, compute minimal-transfer debt settlements with a greedy two-pointer algorithm, and settle everything in ETH atomically.

## Highlights

- **Trustless** — no backend, no server; expenses and debts live on-chain
- **`RegistryGroups`** — factory that deploys and indexes `Group` contracts
- **`Group`** — tracks member balances, computes debts via a greedy algorithm, and handles ETH settlement

## Contract Architecture

```
RegistryGroups  (factory + global registry)
  ├── deploys Group instances
  └── holds a shared Utils instance

Group           (per-group logic)
  ├── addExpense(payer, amount)
  ├── split()
  ├── payAll()  { payable }
  └── V2 stubs: addMember, pay, leaveGroup, dissolveGroup

Utils           (stateless helpers, deployed once)
  ├── abs(int256) → uint256
  └── isSorted / isSortedDesc
```

## Balance Model

Each member holds an `int256` balance:

| Sign | Meaning |
|---|---|
| Positive | Creditor — is owed money |
| Negative | Debtor — owes money |
| Zero | Settled |

When `addExpense(payer, amount)` is called, the cost is split evenly among all members (`amount / totalMembers`). Integer-division remainder stays with the payer — no wei is ever trapped in the contract.

## Debt Algorithm (`split` → `getDebts`)

`split()` partitions members into debtors (balance < 0) and creditors (balance ≥ 0), then calls `getDebts()`, which applies a greedy two-pointer algorithm to minimise the number of transfers required. Sorting by absolute balance descending is done **off-chain** (caller's responsibility) to keep gas costs low.

## Settlement with `payAll`

`payAll()` is `payable` and requires `msg.value` to exactly equal the caller's total outstanding debt. It iterates over the debt array, transfers ETH directly to each creditor via `.call{value}()`, and updates all balances in the same block. Partial payments are not supported in V1.

## Flow

```
User ──► addExpense(payer, amount) ──► balances updated ──────────────────────► ExpenseAdded(...)
User ──► split()                   ──► getDebts() greedy ──► debts[] stored  ──► DebtsSplit(...)
User ──► payAll() { value }        ──► .call each creditor ──► balances reset ──► AllPaid(...)
```

## Test Coverage

| Contract | Lines | Statements | Branches | Functions |
|---|---|---|---|---|
| `Group.sol` | 92.59% | 98.95% | 82.61% | 58.33% |
| `RegistryGroups.sol` | 100.00% | 100.00% | 100.00% | 100.00% |
| `Utils.sol` | 27.27% | 17.65% | 25.00% | 33.33% |
| **Total** | **86.14%** | **87.70%** | **74.07%** | **58.82%** |
