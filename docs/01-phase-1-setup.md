# Phase 1: Strategic Setup

This document outlines the initial configuration for the Smart Yield Saving (SYS) strategy. The objective is to establish a balanced position that remains robust under both upward and downward price movements.

## 1. Orca Pool Configuration
**Pool:** SOL/USDC (0.04% Fee Tier)

### Step A: Identify Market Structure
Identify the **nearest Support** and **nearest Resistance** levels relative to the current SOL price. You must determine which level is **closer** to the current price; this will be your "Anchor."

### Step B: Set Price Range & Anchor
* **If Support is closer:**
    * Set **Min Price** = Support Level.
    * Look at the **Left-side percentage** in the Orca simulation graph.
* **If Resistance is closer:**
    * Set **Max Price** = Resistance Level.
    * Look at the **Right-side percentage** in the Orca simulation graph.

### Step C: Percentage Optimization Rules
The ideal operational range is **7% to 10%**. If your raw distance to support/resistance is higher, apply the following normalization mapping:

| Raw Distance to Support/Resistance | Final Applied Percentage |
| :--- | :--- |
| > 10% and ≤ 14% | **7%** |
| > 14% and ≤ 16% | **8%** |
| > 16% and ≤ 18% | **9%** |
| > 18% | **10%** |

**Input:** Enter the *Final Applied Percentage* into the "Custom Percentage" field in Orca (Use the left-side input if anchored to support, or right-side if anchored to resistance).

---

## 2. Jupiter Perpetuals (Short Position)
This position acts as a hedge against downward price movement.

### 2.1 Maximum Notional Value
The maximum allowable size for your short position is:
$$\text{Max Short Notional} = 0.5 \times (\text{USDC required for Orca Pool})$$

> **Note:** The USDC required for the Orca Pool is not equal to the total pool deposit.  
> In practice, it typically represents about 50% of the overall deposit amount.  
> Therefore, the Max Short Notional can be expressed as:  
> **Max Short Notional = 0.5 × (50% × Total Pool Deposit)**

### 2.2 Leverage Safety
* Set leverage such that the **Liquidation Price** is at least **25% away** (1.25x) from your entry price.
* *Note:* The "You're Paying" (Collateral) amount will change based on the leverage you select, but the **Notional Value** (Position Size) must remain fixed based on the formula above.

---

## 3. Spot SOL Acquisition
You must acquire enough SOL to cover the hedge reserve and the pool deposit.

**Formula:**
$$\text{Total SOL Buy} = (3 \times \text{Short Perp Notional}) + \text{SOL for Orca} + \text{Buffer Reserve}$$

* **Short Perp Notional:** The value calculated in Section 2.1.
* **Buffer Reserve:** Small amount ($0.5 - $1) for gas/fees.

---

## 4. Execution Order (Mandatory)
Execute strictly in this sequence:

1.  [ ] **Swap USDC → SOL**: Acquire the calculated Total SOL amount via Jupiter Swap.
2.  [ ] **Open Short Perpetual**:
    * Type: Market Order.
    * Input: "You're Paying" = USDC collateral.
    * Verify: Notional Value matches the calculation in Section 2.1.
3.  [ ] **Deposit into Orca**: Create the new position using the custom price range determined in Step 1.
4.  [ ] **(Optional) Jupiter Earn**: Deposit any remaining dust/idle USDC into the JLP/USDC vault.

> **Next Step:** Phase 2 is triggered when SOL price reaches the **Max Price** or **Min Price** of this pool.