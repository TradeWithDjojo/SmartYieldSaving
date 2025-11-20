# Smart Yield Saving - Technical Documentation

Welcome to the technical documentation for **Smart Yield Saving (SYS)**. This repository outlines a structured DeFi strategy combining **Orca Concentrated Liquidity**, **Jupiter Perpetuals**, and **Spot SOL acquisition** to create a balanced, yield-optimized position.

This documentation is divided into phases to guide you through the lifecycle of the strategy, from initial setup to long-term maintenance.

## 📚 Documentation Index

### [1. Phase 1: Strategic Setup](./01-phase-1-setup.md)
**Start here.** Learn how to configure the initial liquidity pool, calculate the correct price range based on market structure, and set up the initial hedge.
* *Key Concepts:* Anchor prices, Percentage optimization, Initial allocation.

### [2. Phase 2: Repositioning](./02-phase-2-reposition.md)
Triggers when the price exits the range of your first pool.
* *Scenarios:* Price reaches Max Price (Bullish) or Min Price (Bearish).
* *Action:* Adding a second pool and adjusting the hedge ratio.

### [3. Phase 3: Advanced Rotation & Lending](./03-phase-3-advanced.md)
Triggers when the price exits the range of your second pool. Introduces capital rotation and borrowing mechanics.
* *Action:* Withdrawing inactive liquidity, resetting hedges, and using **Jupiter Lend** (Supply/Borrow) for bearish protection.

### [4. Phase 4: Long-Term Maintenance](./04-phase-4-maintenance.md)
The infinite loop. How to manage the strategy indefinitely, handle market reversals (bounces), and reactivate old pools.

### [5. Risk Management & Mitigation](./05-risk-management.md)
A detailed breakdown of risks (Impermanent Loss, Liquidation) and the specific mitigation layers embedded in the SYS architecture.

---

## 🔗 Reference Links (Core dApps)
*Always verify URLs before connecting your wallet.*

* **Liquidity Provision:** [Orca SOL/USDC Pool](https://www.orca.so/pools/Czfq3xZZDmsdGdUyrNLtRhGc47cXcZtLG4crryfu44zE)
* **Hedging:** [Jupiter Perpetuals (Short SOL/USDC)](https://jup.ag/perps/short/USDC-SOL)
* **Spot Swap:** [Jupiter Swap](https://jup.ag/swap)
* **Passive Yield (Idle Assets):** [Jupiter Earn (USDC Vault)](https://jup.ag/lend/earn/USDC/deposit)
* **Lending/Borrowing:** [Jupiter Lend](https://jup.ag/lend/borrow/1/nfts/5304/actions/deposit-borrow)

> **Disclaimer:** This documentation is for educational purposes only. Cryptocurrency markets are volatile. Please review the [Risk Management](./05-risk-management.md) section carefully.