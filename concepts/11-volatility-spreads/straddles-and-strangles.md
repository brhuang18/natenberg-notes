# Straddles and strangles

**One-line definition:** a **straddle** is a call and a put with the **same** strike and expiration, both bought (long) or both sold (short). A **strangle** is a call and a put with the same expiration but **different** strikes.

## Intuition
A long straddle is a bet on **movement in either direction**. You pay for two options, but one of them will be worth something unless the underlying stays exactly at the strike.

- **Long straddle**: wins on a big move up or down (profit unlimited either way), loses a limited amount (the premiums) if the market sits still.
- **Short straddle**: the reverse: wins a limited amount if nothing happens, loses without limit if the market moves a long way.

A **strangle** does the same with options out of the money (cheaper, but the market has to move farther to pay off).

## Greeks
| Position | Gamma | Theta | Vega | Wants |
|---|---|---|---|---|
| Long straddle | $+$ | $-$ | $+$ | movement and rising implied volatility |
| Short straddle | $-$ | $+$ | $-$ | calm and falling implied volatility |
| Long strangle | $+$ | $-$ | $+$ | same as long straddle |
| Short strangle | $-$ | $+$ | $-$ | same as short straddle |

(The book's text on page 172 prints the short strangle as "+gamma/−theta/+vega", the same as the long. That is a slip: its own Figure 11-9 gives $-/+/-$, and the totals in Figure 11-33 confirm it.)

Example from the evaluation table (stock 100, April, volatility 20%): $+10$ April 100 calls and $+10$ April 100 puts (long straddle) cost 65.30 and give gamma $+96.0$, theta $-0.540$, vega $+3.20$; delta $= 10 \times 56 + 10 \times (-44) = +120$. A short straddle (here $-20$ April 105 calls and $-10$ April 105 puts) takes in 90.90 and has gamma $-132.0$, theta $+0.730$, vega $-4.50$.

## Straddles are normally 1:1, at the money
At the money, call delta is about 50 and put delta about $-50$, so one of each is roughly delta neutral. If the strike is not at the money, ratio the quantities.

**Ratio straddle** (page 171): underlying 100, buy the September 95 straddle. The call is in the money (delta 75), the put out of the money (delta $-25$). One of each gives $75 - 25 = +50$ deltas, a "bull straddle". To be delta neutral buy **3 puts per call**:

$$1 \times 75 + 3 \times (-25) = 0$$

It is still a straddle (same strike), but more precisely a **ratio straddle** because the numbers differ.

## Naming strangles (which options?)
A "March 90/110 strangle" could mean a 90 put plus 110 call, or a 90 call plus 110 put. By convention it means the **out-of-the-money** pair (90 put, 110 call if the market is at 100). The other version, made of in-the-money options, is called a **guts**. They have nearly the same payoff, but in-the-money options trade less actively, so the out-of-the-money version is what people mean.

## Why not just buy straddles all day?
New traders like long straddles: **limited risk, unlimited profit in both directions** sounds perfect. But losing money, even a limited amount, is painful, and the market not moving is a common outcome. The right question is not only "limited or unlimited?" but "how likely is each outcome?" That is why we use a theoretical pricing model ([[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]). Chapter 13 shows that straddles and strangles are often the *riskiest* of all spreads, even with a big theoretical edge.

## Common confusions
- **Straddle versus strangle:** same strike versus different strikes.
- **Short does not mean "sold the underlying".** Short straddle = sold both options.
- **A straddle is not automatically delta neutral** (the example above had $+120$ deltas). At the money, 1:1 is close; elsewhere you ratio.

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/hedging-with-other-options]]
- Next: [[concepts/11-volatility-spreads/butterflies-and-condors]]
- Earlier: [[concepts/04-expiration-profit-and-loss/equivalent-positions]]
- See also: [[glossary]], [[formulas]]
