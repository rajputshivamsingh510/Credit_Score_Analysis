# 📄 DeFi Credit Scoring Model – README

## 🔍 Overview
This project builds a credit score (0–1000 scale) for crypto wallet addresses based on their activity in decentralized finance (DeFi) protocols. Instead of using traditional credit history, this model uses public on-chain behavior to assess how responsibly a wallet interacts with DeFi systems.

The idea is to simulate a DeFi-native alternative to credit scoring — fair, data-driven, and permissionless.

---

## 🎯 How the Score Works

The score starts from a base value (500) and is adjusted based on wallet activity:

| Behavior / Feature          | Impact on Score                          |
|------------------------     |------------------------------------------|
| Regular deposits            | +20 points per deposit                   |
| Repaying borrowed funds     | +25 points per repay                     |
| High repay-to-borrow ratio  | Up to +100 points                        |
| Using many types of actions | +15 per unique action                    |
| Active usage                | +30 × log(1 + total transactions)        |
| Liquidations                | −150 points each                         |
| Large unpaid borrow amounts | −20 per extra borrowed unit              |
| Volatile amounts (e.g., frequent big swings) | −100 penalty            |
| Small noise added           | ±20 variation to simulate real-world     |

This scoring logic is used to generate a training target for a machine learning model. Final scores are clipped to stay between 0 and 1000.

---

## 🤖 ML Model Summary

- Features are aggregated per wallet from historical data.
- Scores are scaled using StandardScaler.
- A Random Forest Regressor learns patterns from features to generate predicted scores.

Model: `RandomForestRegressor(n_estimators=100, max_depth=10)`

Data is split 80/20 for training and testing.

---

## ⚙️ Why This Makes Sense

We reward:
- Consistent DeFi activity (e.g. deposits, repayments)
- Diversity in protocol usage
- Responsible borrowing behavior

We penalize:
- Risky actions like liquidation
- Failing to repay borrowed funds
- Extremely volatile transaction behavior

The model isn't perfect, but it's a solid starting point for making sense of DeFi reputation.

---

## 🔄 How You Can Extend This

This setup is easy to build on:
- Add new actions like staking, voting, or NFT transfers
- Include time-weighted behavior (e.g., more recent activity counts more)
- Try different ML models (e.g., XGBoost, neural nets)
- Bring in protocol-specific reputation (e.g., Lens, ENS)
