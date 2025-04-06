# Strategy Report: Adaptive Liquidity Threshold Maker

## Overview
The **Adaptive Liquidity Threshold Maker (ALT Maker)** strategy dynamically adjusts bid-ask spreads based on real-time liquidity conditions in the market order book. Unlike traditional market-making strategies, which rely purely on static spreads or simplistic volatility metrics, ALT Maker evaluates actual market depth and adapts accordingly. This ensures efficient operation under varying market conditions, capturing opportunities when liquidity fluctuates.

---

## Core Principles

### Liquidity-Based Adaptation
The cornerstone of ALT Maker is its **liquidity awareness**. By continuously monitoring the market order book—specifically, the total base asset volume within a small percentage band around the mid-price—the strategy categorizes market conditions into distinct liquidity tiers:
- **Low Liquidity**: Low order book volume triggers wider spreads, protecting the strategy from increased slippage and volatility.
- **Medium Liquidity**: Moderately tight spreads are used to balance profitability and risk.
- **High Liquidity**: Tightest spreads are employed, maximizing trade execution and capturing incremental profits from frequent, small price movements.

### Dynamic Inventory Management
ALT Maker incorporates **inventory management** by adjusting bid-ask spreads based on current portfolio composition relative to a target ratio:
- If the strategy holds more of the base asset than desired, it narrows sell-side spreads to facilitate selling.
- Conversely, holding too little base asset results in narrower buy-side spreads to encourage buying.

This proactive balancing reduces inventory risk and potential exposure to adverse price movements.

---

## Operational Mechanics

### Order Book Analysis
1. Fetch real-time order book data.
2. Calculate the liquidity score within ±1% of the mid-price.

### Spread Determination
1. Classify liquidity conditions (low, medium, high).
2. Set appropriate spreads based on the liquidity tier.

### Inventory Adjustment
1. Compute the current base-to-quote asset ratio.
2. Modify spreads slightly to drive the portfolio towards a predefined target ratio.

### Order Placement and Refreshing
1. Place limit orders at adjusted bid-ask prices.
2. Regularly refresh orders, adapting dynamically to changing market conditions.

---

## Profitability Rationale

### Exploiting Market Efficiency Gaps
Markets often experience brief liquidity shortages or surpluses due to large trades, rapid market moves, or external events. ALT Maker identifies these temporary inefficiencies by:
- Strategically widening spreads during uncertainty or illiquid periods to capture higher premiums.
- Narrowing spreads during stable, high-liquidity periods to ensure volume capture.

### Risk-Managed Execution
Adaptive inventory control ensures the portfolio remains balanced, mitigating directional risk:
- By continuously adjusting spreads based on current holdings, the strategy avoids excessive exposure to sustained market moves in any single direction.
- This enhances long-term stability and reduces drawdowns.

### Incremental Spread Capture
In high-liquidity environments, the strategy effectively capitalizes on tight spreads by executing numerous small trades:
- While each trade's profit margin might be thin, the cumulative effect of these frequent trades contributes substantially to overall profitability.

---

## Performance Metrics (Suggested for Analysis)
To evaluate the performance of ALT Maker effectively, consider tracking these metrics:
1. **Profit and Loss (PnL)**: Track cumulative gains or losses over various timeframes.
2. **Sharpe Ratio**: Measure returns relative to risk, aiming for consistency.
3. **Maximum Drawdown**: Monitor to ensure robust risk management.
4. **Liquidity Score Correlation**: Analyze the relationship between chosen liquidity tiers and profitability, validating the effectiveness of adaptive logic.

---

## Conclusion
The **Adaptive Liquidity Threshold Maker** strategy represents an innovative approach to market-making by intelligently adapting to real-time liquidity. Its dual emphasis on liquidity-driven spread adjustments and dynamic inventory management positions it well to profit from diverse market conditions. This provides a sophisticated tool for traders aiming to leverage market volatility and depth efficiently.

~ Utkarsh Dwivedi
