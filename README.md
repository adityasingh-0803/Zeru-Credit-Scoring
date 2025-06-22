# 💳 Zeru AIML Credit Scoring System

## 🔍 Project Overview

This project implements a **behavior-based credit scoring model** for Ethereum wallets interacting with the Compound V2 protocol. Using on-chain financial activity — such as deposits, borrows, and repayments — we compute a credit score ranging from **0 to 100** for each wallet.

The scoring is completely unsupervised and does not rely on any external credit history or labels — only behavioral features are used.

---

## 📦 Data Source

The data consists of Ethereum wallet transactions from the Compound V2 protocol, split across multiple JSON files. For this implementation, we used:

- `compoundV2_transactions_ethereum_chunk_0.json`
- `compoundV2_transactions_ethereum_chunk_1.json`
- `compoundV2_transactions_ethereum_chunk_2.json`

Each file contains 10,000 records for:
- `deposits`
- `borrows`
- `repays`
- `withdraws`
- `liquidations` *(none found in selected chunks)*

---

## 🧠 Feature Engineering

We processed the raw transaction logs into **wallet-level aggregates**:

| Feature Name | Description |
|--------------|-------------|
| `total_deposited_usd` | Total USD deposited |
| `total_borrowed_usd`  | Total USD borrowed |
| `total_repaid_usd`    | Total USD repaid |
| `total_withdrawn_usd` | Total USD withdrawn |
| `repay_ratio`         | `total_repaid_usd / total_borrowed_usd` |
| `deposit_to_borrow_ratio` | `total_deposited_usd / total_borrowed_usd` |
| `net_deposit`         | `total_deposited_usd - total_withdrawn_usd` |
| `num_liquidations`    | Count of liquidation events *(0 in our case)* |

---

## 🧮 Scoring Formula

We use a **custom scoring formula** to assign a credit score to each wallet:

```python
raw_score = (
    (repay_ratio * 40) +
    (deposit_to_borrow_ratio * 30) +
    (net_deposit * 0.001) -
    (num_liquidations * 10)
)
```
## 📈 Visualization
We plotted the credit score distribution using seaborn.histplot to visually analyze the spread of wallet health across the dataset.

📂 Folder Structure
```
Zeru-Credit-Scoring/
├── notebook/
│   └── zeru_credit_score.ipynb
├── output/
│   └── top_1000_wallets_final.csv
├── analysis/
│   └── wallet_behavior_summary.md
└── README.md
```
