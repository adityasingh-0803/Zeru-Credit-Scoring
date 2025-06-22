# 📊 Wallet Behavior Summary — Top vs Bottom Wallets

This report compares the highest- and lowest-scoring wallets from our behavior-based credit model built on Compound V2 transaction data.

---

## 🟢 Top 5 Wallets – Excellent Behavior

| Wallet Address | Score | Behavior Summary |
|----------------|-------|------------------|
| 0x2bF392Fb1127a3F20bC4a5Fd9A96Dd76E19a6942 | 100.00 | Repaid all borrowed funds, strong deposit-to-borrow ratio, zero withdrawals. |
| 0x69fbe8ea49350a8973bd08d7bc9e86b2e98f5da1 | 99.76  | High collateral deposits, steady repayment, low borrowing risk. |
| 0x0eb306df029d72af32d2baf9062546c790f5c600 | 98.59  | Near-perfect repay ratio, minimal borrowing, no liquidation. |
| 0xb6e39f70408704d04fbc949c2fe93644ea5d8d6d | 98.32  | Safe user profile with small loans and timely repayments. |
| 0xd325a3a48eb1bc4c0da40897ec7ed985d11ba2c8 | 97.77  | Excellent deposit-to-borrow balance and net positive deposits. |

✅ **Common traits:**
- High `repay_ratio` (≥ 0.9)
- `deposit_to_borrow_ratio` > 1
- Zero or low withdrawals
- No liquidations
- High net deposits

---

## 🔴 Bottom 5 Wallets – Risky Behavior

| Wallet Address | Score | Behavior Summary |
|----------------|-------|------------------|
| 0x9fd31424cfceab50218906bc1b3d87fe7778ca61 | 0.31 | Large borrow amount, near-zero repayment. Low deposit ratio. |
| 0x807de2f1e7df1299ecd3501f1d38878e871628a3 | 0.31 | Borrowed aggressively without repaying. Net withdrawal is high. |
| 0x02b435ba3f57fc391b11aa8a41b9275d4dbe33e8 | 0.32 | Deposited very little, withdrew all funds. No repay activity. |
| 0x189987bf96fcaab43a1f4c0c827d40a2d229f222 | 0.32 | Negative net deposit, poor repayment behavior. |
| 0xd999b256f1cd28983e84d7b71c87b3a2aa7115e3 | 0.33 | Imbalanced usage — borrowed more than deposited and did not repay. |

❌ **Common issues:**
- `repay_ratio` ≈ 0
- `deposit_to_borrow_ratio` < 0.5
- No repayment history
- Large withdrawals without deposits

---

## 📌 Creditworthiness Indicators

| Metric | Description | Impact |
|--------|-------------|--------|
| Repay Ratio | Repaid / Borrowed | +ve if near 1 |
| Deposit-to-Borrow Ratio | Deposited / Borrowed | +ve if >1 |
| Net Deposit | Deposited - Withdrawn | +ve indicates trust |
| Liquidations | Count | -ve impact (none in our chunks) |

---

## 🧠 Conclusion

This behavioral credit scoring approach highlights wallets with **strong on-chain financial discipline** — identifying both **low-risk candidates** and **risky actors**.

This can be used for:
- Lending limit assignment
- Borrowing rate adjustments
- On-chain financial identity scoring
