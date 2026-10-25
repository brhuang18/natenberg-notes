# Formulas

Each formula: the equation, every symbol defined, and what it means in plain English.

## Template

$$\text{formula here}$$

- Symbols: ...
- Intuition: ...
- Source: [[chapters/chapter-template]]

---

## Chapter 1: Financial Contracts

**Notional value, physical commodity**

$$\text{notional value} = \text{units delivered} \times \text{unit price}$$

- Intuition: the size of the deal, not cash paid. Example: $1{,}000 \times \$75 = \$75{,}000$.
- Source: [[chapters/01-financial-contracts]]

**Notional value, cash-settled index**

$$\text{notional value} = \text{index price} \times \text{point value}$$

- Intuition: the exchange sets the point value so the contract is a sensible size to trade. Example: $825 \times \$200 = \$165{,}000$.
- Source: [[chapters/01-financial-contracts]]

**Futures variation**

$$\text{variation} = (P_{\text{new}} - P_{\text{old}}) \times \text{units per contract} \times \text{contracts}$$

- Symbols: $P$ is the futures price; contracts are positive for long and negative for short. Positive means credit, negative means debit.
- Intuition: the daily cash transfer that keeps the contract at its original agreed price. See [[concepts/settlement-margin-and-variation]].
- Source: [[chapters/01-financial-contracts]]
