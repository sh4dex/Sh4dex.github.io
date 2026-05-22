---
title: "CalculatorWeb3"
excerpt: "Solidity smart contract calculator with addition, subtraction, multiplication, division and power functions. Owner-restricted operations with on-chain event logging.<br/><img src='/images/projects/calculator.png'>"
collection: portfolio
---

<a href="https://github.com/sh4dex/CalculatorWeb3" class="btn btn--inverse btn--large" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>

---

CalculatorVW3 is a smart contract written in Solidity that performs main arithmetic operations while showcasing fundamental smart contract development concepts.

The contract keeps track of the most recent calculation result and emits an event for every operation executed. This enables off-chain applications and users to easily monitor contract activity.

This project was built using the **Foundry** smart contract development framework using core Solidity concepts and best practices including: Smart contract structure, Events, Enums, Modifiers, State variables, NatSpec documentation, Foundry project organization, and Unit testing.

Created using **Solidity version 0.8.33**

![CalculatorWeb3](/images/projects/calculator.png)

## Operations

| Operation | Function Name |
|---|---|
| Addition | `addition()` |
| Subtraction | `subtraction()` |
| Multiplication | `multiplication()` |
| Division | `division()` |
| Power | `power()` |

## Contract Structure

```solidity
/// @notice Stores operation types
enum Operation {
    ADDITION,
    SUBTRACTION,
    MULTIPLICATION,
    DIVISION,
    POWER
}
```