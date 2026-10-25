# Checking volatility against observed price changes

**One-line definition:** there is no "current volatility" you can read off a screen, so a trader checks whether recent price changes look like the ones the assumed volatility predicts.

## Intuition
A directional trade shows its result immediately: the price went up or it did not. Volatility is different. Nothing tells you "the volatility is 37%". You can only compare what you *expected* the price changes to look like with what actually happened.

If you used the wrong volatility, you used the wrong probabilities. Wrong probabilities give wrong theoretical values, which defeats the purpose of using a model.

## Worked example (the book's)
A stock at 45 is assumed to have 37% volatility. Over five days the settlement-to-settlement changes were

$$+0.98,\; -0.65,\; -0.70,\; +0.25,\; -0.85$$

1. One standard deviation daily: $45 \times 0.37 / 16 = 1.04$.
2. We expect a change **bigger** than 1.04 about 1 day in 3. In five days that means one or two such days.
3. Observed: none. The largest change was 0.98.
4. Conclusion: these changes do not look like 37% volatility.

What volatility *would* match? The book says 27.8%. Check with the steps in [[concepts/06-volatility/realized-volatility]]: standard deviation of the daily log changes, times 16. (In our notebook: 27.8%.)

## What to do about it
Before changing anything, ask whether something unusual happened:
- Was it a holiday week with abnormally little trading? Then 37% may still be fine.
- If there is no explanation, we may simply be using the wrong volatility, and a lower number fits the data better.

## How much data is enough?
Five days is a tiny sample. Coin analogy:
- 5 heads in 5 flips: not conclusive.
- 50 heads in 50 flips: something is wrong with the coin.

Traders prefer 20, 50 or 100 days of changes before drawing strong conclusions.

## What counts as a "price change"?
For exchange-traded contracts the usual choice is **settlement-to-settlement**: today's settlement price minus yesterday's. The high-low range or open-to-close change may be larger or smaller, but it is not what is used. (The book notes other estimators exist that use highs and lows, listed in its footnote.)

## Common confusions
- **A quiet week does not prove the volatility is lower.** The right test is a long sample.
- **A few big days do not prove it is higher.** Large moves do happen; see "unlikely is not impossible" in [[concepts/06-volatility/volatility-as-a-standard-deviation]].
- **Use the same kind of change throughout.** Mixing open-to-close with settlement-to-settlement is apples and oranges.

## Related
- Chapter: [[chapters/06-volatility]]
- Previous: [[concepts/06-volatility/scaling-volatility-for-time]]
- Next: [[concepts/06-volatility/interest-rate-products-and-rate-volatility]] (a special case), then [[concepts/06-volatility/realized-volatility]]
- Code: [[code/volatility.ipynb]]
- See also: [[glossary]]
