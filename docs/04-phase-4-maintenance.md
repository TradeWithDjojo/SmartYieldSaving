# Phase 4: Long-Term Maintenance

Phase 4 defines the long-term loop. The market may continue trending (creating Pool 4, 5, etc.) or reverse back into old ranges.

## Strategy Loop Principles
When price moves to a new range (Up or Down):
1.  **Withdraw Inactive Liquidity:** Pull ~98% liquidity from the pool that is furthest out of range.
2.  **Deploy New Pool:** Create a new position centered on the current price.
3.  **Hedge:** Execute the Short Perpetual and Spot Acquisition patterns defined in Phase 3.

## Scenario: Price Returns to Inactive Pool (Bounce Back)
If the price reverses and re-enters the range of a previously inactive pool (e.g., Pool 1 becomes active again):

1.  **Re-deposit Liquidity:** Put capital back into the specific pool that is now active. Use the exact same amount originally configured.
2.  **Funding the Deposit:**
    * Use available wallet balance.
    * If insufficient (due to Lending positions), execute a partial **Repay & Withdraw** on Jupiter Lend to unlock the necessary SOL.

## Execution Constraints (The "Rule of Two")
To maintain a leverage-neutral design, Phase 4 introduces limits on how many adjustments you can make in a row.

### 1. Scaling Perps
* You may adjust the size of a new short position (up or down) **only if shorting has been executed once so far**.
* **Constraint:** After **two** total perpetual shorts are open, no further scaling is allowed. You must wait until a position is closed.

### 2. Selling SOL / Closing Shorts
* **Short Perps:** Can only be closed (Take Profit / Stop Loss) after **two** short entries have been made.
* **Spot SOL:** Can only be sold (or used as collateral) after **two** spot purchases have been executed.

---

## Continuous Optimization
Regardless of market direction, the SYS system ensures:
* Inactive capital is always reclaimed.
* Active pools remain aligned with market structure.
* Hedge ratios are reset to stabilize Delta exposure.