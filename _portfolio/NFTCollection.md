---
title: "NFT-Collection"
excerpt: "Trustless NFT marketplace built on Solidity — list, buy, and cancel ERC-721 token listings with atomic payment and transfer. No funds or NFTs held by the contract at any point."
tagline: "Trustless NFT marketplace in Solidity. List, buy, or cancel any ERC-721 token — payment flows directly from buyer to seller and the NFT transfers atomically in the same transaction."
image: /images/projects/nft-collection-cover.png
github: https://github.com/sh4dex/NFT-Collection
collection: portfolio
---

<a href="https://github.com/sh4dex/NFT-Collection" class="btn btn--inverse btn--large" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>

---

NFT-Collection is a trustless NFT marketplace built in Solidity. Any ERC-721 token can be listed, bought, or delisted — the contract holds no funds or NFTs at any point. Payment flows directly from buyer to seller and the NFT transfers atomically in the same transaction.

Built using **Foundry** with **Solidity 0.8.34**, leveraging OpenZeppelin's ERC-721, ReentrancyGuard, and Ownable contracts.

## Architecture

![NFT-Collection Contract Architecture](/images/projects/nft-collection-cover.png)

## Functions

| Function | Access | Description |
|---|---|---|
| `listNft(nftAddress, tokenId, price)` | Public | List an ERC-721 token for sale at a given price |
| `buyNft(nftAddress, tokenId)` | Public | Buy a listed NFT by sending the exact price in ETH |
| `cancelListing(nftAddress, tokenId)` | Seller | Remove an active listing |

## Flow

```
User ──► listNft()       ── listings[nft][id] = Listing ──► NftListed(seller, nft, id, price)
User ──► buyNft()        ── delete listing ──► safeTransferFrom ──► ETH to seller ──► NftSold(...)
User ──► cancelListing() ── delete listing ──────────────────────────────────────────► CanceledListing(nft, id)
```

## Security

- **ReentrancyGuard** — all three state-changing functions are guarded by OpenZeppelin's `nonReentrant` modifier.
- **Checks-Effects-Interactions** — `buyNft` deletes the listing from storage before any external calls, providing a second layer of reentrancy protection.
- **Ownable** — deployer is set as owner via `Ownable(msg.sender)` for future administrative functions.

## Test Coverage

| File | % Lines | % Statements | % Branches | % Funcs |
|---|---|---|---|---|
| `src/NFTCollection.sol` | 100% | 100% | 91.67% | 100% |
| `test/NFTCollection.t.sol` | 100% | 100% | 100% | 100% |
