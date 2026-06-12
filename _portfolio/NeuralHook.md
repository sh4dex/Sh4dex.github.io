---
title: "NeuralHook"
excerpt: "AI-powered impermanent loss protection for Uniswap v4 LPs — live on Unichain Sepolia."
tagline: "AI-powered impermanent loss protection for Uniswap v4 LPs. Three-node agent network predicts risk and autonomously adjusts pool fees. Live on Unichain Sepolia."
image: /images/projects/neuralhook-cover.png
github: https://github.com/Hijanhv/NeuralHook/tree/main
demo: https://neural-hook.vercel.app/
showcase: https://ethglobal.com/showcase/neuralhook-8gxzp
collection: portfolio
badge: "AI + WEB3"
tech_tags: [Solidity, Foundry, Uniswap v4, AI Agents, Unichain, Vercel]
---

<a href="https://github.com/Hijanhv/NeuralHook/tree/main" class="btn btn--inverse btn--large" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>&nbsp;&nbsp;<a href="https://neural-hook.vercel.app/" class="btn btn--primary btn--large" target="_blank"><i class="fas fa-rocket"></i> Live Demo</a>&nbsp;&nbsp;<a href="https://ethglobal.com/showcase/neuralhook-8gxzp" class="btn btn--warning btn--large" target="_blank"><i class="fas fa-trophy"></i> ETHGlobal Showcase</a>

---

> Built for the **Open Agents Async Hackathon 2026** — ETHGlobal · April 24 – May 6, 2026

## Overview

NeuralHook is a Uniswap v4 hook that uses a **three-node AI agent network** to predict impermanent loss risk before it happens. When risk rises, the pool fee surges automatically to compensate LPs.

Every fee change is cryptographically signed by the inference layer and verified atomically on-chain — **the AI cannot hallucinate a fee**.

When risk reaches **HIGH** or **CRITICAL**, agents call the Uniswap Trading API to get the optimal route, then autonomously execute a protective WETH → USDC rebalance swap on Base — closing the full protect → rebalance loop without human intervention.

## Stack

| Layer | Technology |
|---|---|
| 1️⃣ Smart Contracts | Uniswap v4 Hooks · Solidity |
| 2️⃣ AI Inference | 0G Sealed Inference |

## 💰 Dynamic Fee Tiers

Fees are adjusted autonomously based on the AI-predicted impermanent loss risk level:

| Risk Level | Behavior |
|---|---|
| LOW | Base fee |
| MEDIUM | Fee increases moderately |
| HIGH | Fee surges + rebalance triggered |
| CRITICAL | Maximum fee + autonomous WETH → USDC swap |

## Deployment

Live on **Unichain Sepolia** testnet.
