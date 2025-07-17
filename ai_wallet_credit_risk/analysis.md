# Credit Score Analysis

## Overview

After processing and scoring DeFi user wallets using behavior-based features and a trained Random Forest model, we analyzed the distribution and patterns across the score spectrum.

---

## Score Distribution

The figure below shows the distribution of wallet credit scores and the top contributing features to the scoring model.

![Score Distribution and Feature Importances](output.png)

---

### Score Bucket Summary

| Score Range | Approx. Wallet Count |
|-------------|----------------------|
| 0–100       | Very few             |
| 100–200     | Very few             |
| 200–300     | Low                  |
| 300–400     | Low                  |
| 400–500     | Moderate             |
| 500–600     | High                 |
| 600–700     | Highest              |
| 700–800     | Moderate             |
| 800–900     | Low                  |
| 900–1000    | Noticeable spike     |

---

## Behavior Observations

### Wallets in the Lower Score Range (0–300):
- Rare deposit or repay activity
- Risky, irregular, or high-volatility transaction patterns
- Often include liquidated accounts
- Little diversity in DeFi interactions

### Wallets in the Higher Score Range (700–1000):
- High and regular repayments and deposits
- Excellent repay-to-borrow ratios
- High diversity in actions across DeFi protocols
- Stable, consistent transaction behavior

---

## Summary

The model effectively separates trustworthy wallets from risk-prone ones based on their DeFi interaction patterns. Most wallets scored between 600–800, suggesting moderate to good behavior. Feature importance indicates repayment behavior is the most powerful predictor.
