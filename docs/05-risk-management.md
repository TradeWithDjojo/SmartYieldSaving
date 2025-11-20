# Risk Factors and Mitigation Framework

Smart Yield Saving (SYS) utilizes concentrated liquidity and leverage. While designed to be robust, users must understand the inherent risks.

## Core Risk Categories

### 1. Impermanent Loss (IL)
**Cause:** Price diverts significantly from the liquidity range.
* *Scenario:* If SOL pumps significantly, your LP position converts entirely to USDC, causing you to miss out on the full upside of holding raw SOL.
* **Mitigation:** **Strategic Spot Accumulation.** SYS mandates holding Spot SOL alongside the LP position. The Spot SOL gains value exponentially during a pump, offsetting the relative underperformance of the LP.

### 2. Bearish Price Trend
**Cause:** SOL price weakens efficiently against USDC.
* *Risk:* The value of your SOL collateral drops.
* **Mitigation:** **Perpetual Short Hedging.** The short position generates positive PnL when prices fall. This profit creates a buffer that stabilizes the total portfolio value (Equity).

### 3. Lending Liquidation (Extreme Risk)
**Cause:** In Phase 3 (Bearish), SOL is used as collateral to borrow USDC. If SOL crashes violently, the LTV rises.
* *Risk:* Forced liquidation of collateral, leading to permanent loss of funds.
* **Mitigation:** **Defensive Collateral Management.**
    * Monitor LTV.
    * If the price approaches the liquidation threshold, immediately **Repay the Borrow** and **Withdraw Collateral**.
    * *Priority:* Preserving capital is more important than maintaining the strategy structure during a crash.

---

## Summary of Risk Controls

| Risk Type | Cause | Mitigation in SYS |
| :--- | :--- | :--- |
| **Impermanent Loss** | Price leaves LP range | Buy & Hold SOL (Spot exposure offset) |
| **SOL Bearish Trend** | Persistent price decline | Short Perpetual Hedge (Genereates +PnL) |
| **Lending Liquidation** | SOL falls below threshold | Early Repay + Withdraw Collateral |
| **Extreme Bearishness** | Multi-layer failure | Full De-Risk Procedure (Close all positions) |

---

## Disclaimer
> This documentation does not constitute financial advice. All users must conduct their own research (DYOR), understand the risks involved, and exercise independent judgment before participating in any strategy. Cryptocurrency markets are highly volatile, and users are fully responsible for their own assets, decisions, and potential losses.