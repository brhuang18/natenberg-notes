# European vs American exercise style

**One-line definition:** a **European** option can be exercised only at expiration; an **American** option can be exercised on **any business day up to** expiration.

## Intuition
Same contract, different freedom. A European option is a ticket valid for one specific day. An American option is valid every day until the last one. In practice the holder of a European option makes the exercise decision on the last business day before expiration.

## Details from the book
- The names have **nothing to do with geography**. Many US options are European and many European options are American. (The first US-traded options had the right of early exercise, hence "American".)
- Rough pattern: options on **individual stocks** and on **futures** tend to be American. Options on **indexes** tend to be European.
- The style is part of the contract specification: [[concepts/03-contract-specifications-and-option-terminology/option-contract-specifications]].

## Why it matters
- An American holder can exercise early, so valuing American options is harder. Natenberg returns to early exercise in Chapter 16.
- The book notes that a *European* option can even have a **negative time value** (it can trade below its intrinsic value), see [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]].
- Our own reasoning (not stated in this chapter): since an American option gives all the rights of the European one plus extra, it should never be worth less than an otherwise identical European option.

## Common confusions
- "American" does not mean "traded in America".
- Being allowed to exercise early does not mean you *should*. Exercising early gives up the option's time value, a point the book develops later.

## Related
- Chapter: [[chapters/03-contract-specifications-and-option-terminology]]
- See also: [[glossary]]
