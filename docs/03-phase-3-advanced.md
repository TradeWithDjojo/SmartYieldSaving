# Phase 3: Advanced Rotation & Lending

Phase 3 is triggered when price movement extends beyond the range of **Pool 2**. At this stage, Pool 1 is likely far out of range. We will partially unwind Pool 1 to fund Pool 3.

## Scenario A: Price Reaches MAX Price of Pool 2 (Bullish)

### 1. Withdraw from Pool 1
Since Pool 1 is inactive (composed entirely of USDC due to upward move):
* **Harvest Yield.**
* **Withdraw 98% of Liquidity** from Pool 1 (USDC portion). Do not close the pool completely.

### 2. Reset Short Perpetual (Stop Loss) and Sell SOL (Take Profit)
* **Close Previous Short & Sell SOL:** The existing short is acting as a stop loss, but the SOL position is in profit. Close it and Swap the SOL back to USDC to make a small profit.
* **Open New Short:** Re-establish the baseline hedge.
    $$\text{Notional Value (Short 3)} = \text{Notional Value of Phase 1}$$

### 3. Create Pool 3
* **Buy Spot SOL:** Quantity = Same quantity used in Phase 1.
* **Deposit Pool 3:** Use the same Min-Max percentage range and deposit amount as Phase 1.

---

## Execution Checklist (Bullish Scenario)
1.  [ ] Harvest Pool 1 & Withdraw 98% Liquidity (USDC).
2.  [ ] **Swap USDC → SOL** (Phase 1 Amount).
3.  [ ] **Open New Short Perp** (Phase 1 Notional).
4.  [ ] **Deposit into Orca** (Pool 3).

---

## Scenario B: Price Reaches MIN Price of Pool 2 (Bearish)

### 1. Withdraw from Pool 1
Since Pool 1 is inactive (composed entirely of SOL due to downward move):
* **Harvest Yield.**
* **Withdraw 98% of Liquidity** from Pool 1 (SOL portion). The released SOL will be used for the lending strategy below.

### 2. Close Short Perpetual (Take Profit)
* Close the previous short position to realize profit. 

### 3. Supply-Borrow Strategy (Jupiter Lend)
To increase capital efficiency without over-leveraging:
1.  **Supply:** Deposit **All SOL** (keep 1% for gas) into Jupiter Lend.
2.  **Borrow:** Borrow **USDC** (Max LTV 50%).

### 4. Create Pool 3
* **Open New Short:** Reset the hedge ($\text{Notional} = \text{Phase 1 Value}$).
* **Buy Spot SOL:** Swap borrowed USDC for SOL (Phase 1 Quantity).
* **Deposit Pool 3:** Same range and amount as Phase 1.

---

## Execution Checklist (Bearish Scenario)
1.  [ ] Harvest Pool 1 & Withdraw 98% Liquidity (SOL).
2.  [ ] **Supply SOL** to Jupiter Lend (Leave 1% for gas).
3.  [ ] **Borrow USDC** (Max 50% LTV).
4.  [ ] **Swap USDC → SOL** (Phase 1 Amount).
5.  [ ] **Open New Short Perp** (Phase 1 Notional).
6.  [ ] **Deposit into Orca** (Pool 3).

> [!WARNING]
> **Lending Risk:** When borrowing USDC against SOL collateral, monitor your LTV closely. If SOL price crashes further, you must Repay and Withdraw before liquidation occurs.