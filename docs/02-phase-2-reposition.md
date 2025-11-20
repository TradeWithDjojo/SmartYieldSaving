# Phase 2: Repositioning

Phase 2 is triggered when the market price moves beyond the active range of your **first Orca liquidity pool (Pool 1)**.

## Scenario A: Price Reaches MAX Price (Upward Breakout)
*Trigger: SOL price hits the upper limit of Pool 1.*

### 1. Create Second Orca Pool (Pool 2)
* **Range:** Use the **same percentage range** (Min% and Max%) as Pool 1.
* **Deposit:** The value must match the **original deposit value** of Pool 1.

### 2. Open Second Short Perpetual
Open a *new* additional short position with increased exposure to compensate for higher prices:
$$\text{Notional Value (Short 2)} = 1.1 \times \text{Notional Value of Phase 1}$$

### 3. Acquire Spot SOL
Swap USDC for SOL using this reduced ratio:
$$\text{SOL Swap} = (0.9 \times \text{Phase 1 SOL Quantity}) + \text{SOL Needed for Pool 2}$$

### Execution Order (Scenario A)
1.  [ ] Withdraw USDC from Earn (if applicable).
2.  [ ] **Swap USDC → SOL** (Calculated amount).
3.  [ ] **Open Short Perpetual 2** (Market order, adjusted notional).
4.  [ ] **Deposit into Orca** (Pool 2).

---

## Scenario B: Price Reaches MIN Price (Downward Breakout)
*Trigger: SOL price hits the lower limit of Pool 1.*

### 1. Create Second Orca Pool (Pool 2)
* **Range:** Use the **same percentage range** (Min% and Max%) as Pool 1.
* **Deposit:** The value must match the **original deposit value** of Pool 1.

### 2. Open Second Short Perpetual
Open a *new* additional short position with decreased exposure:
$$\text{Notional Value (Short 2)} = 0.9 \times \text{Notional Value of Phase 1}$$

### 3. Acquire Spot SOL
Swap USDC for SOL using this increased ratio to secure liquidity:
$$\text{SOL Swap} = (1.1 \times \text{Phase 1 SOL Quantity}) + \text{SOL Needed for Pool 2}$$

### Execution Order (Scenario B)
1.  [ ] Withdraw USDC from Earn (if applicable).
2.  [ ] **Swap USDC → SOL** (Calculated amount).
3.  [ ] **Open Short Perpetual 2** (Market order, adjusted notional).
4.  [ ] **Deposit into Orca** (Pool 2).

---

## Resulting Structure
After Phase 2, you will hold **two overlapping Orca pools**. This structure doubles yield efficiency during sideways markets (where ranges overlap) and stabilizes exposure.