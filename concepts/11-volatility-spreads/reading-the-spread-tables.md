# Reading the spread evaluation tables (Figures 11-31 and 11-33)

**One-line definition:** the book's tables list each option's theoretical value, delta, gamma, theta, vega and rho, then build each example spread by multiplying by the quantity and adding up. The total row is the position's **cash flow** and its **Greeks**.

## How to rebuild one total (a worked example)
Option table (stock 100, 20%, 6%, April = 2 months; each entry per option):

| Option | Value | Delta | Gamma | Theta | Vega | Rho |
|---|---|---|---|---|---|---|
| April 110 call | 0.65 | 16 | 3.0 | $-0.019$ | 0.10 | 0.025 |
| April 105 call | 1.71 | 33 | 4.4 | $-0.030$ | 0.15 | 0.052 |

Position: $+20$ April 110 calls, $-10$ April 105 calls (call ratio spread, buy more).

**Rule:** for the Greeks, multiply each option's Greek by its quantity (plus for bought, minus for sold), then add. For the **cash flow**, buying costs money and selling brings money in, so the sign is **reversed**.

| | Cash flow | Delta | Gamma | Theta | Vega | Rho |
|---|---|---|---|---|---|---|
| $+20$ April 110 | $20 \times (-0.65) = -13.00$ | $20 \times 16 = +320$ | $+60.0$ | $-0.380$ | $+2.00$ | $+0.500$ |
| $-10$ April 105 | $10 \times (+1.71) = +17.10$ | $-10 \times 33 = -330$ | $-44.0$ | $+0.300$ | $-1.50$ | $-0.520$ |
| **Total** | **$+4.10$** | **$-10$** | **$+16.0$** | **$-0.080$** | **$+0.50$** | **$-0.020$** |

These match the book. The cash flow is the **theoretical value** of the spread: what it would cost or pay if everything traded at its theoretical price.

## Reading the cash flow
- **Negative** (a debit): you paid, so you are **long** the spread.
- **Positive** (a credit): you were paid, so you are **short** the spread.

Because no market prices are given in Figure 11-31, **no theoretical edge can be calculated**; the table only shows each spread's *characteristics*. Once the position exists, what helps or hurts it is set by its Greeks, not by the price at which you traded. As the book puts it, a trader's concern should be "not what happened yesterday but what can be done today".

## The April examples in one table (our rebuild)
Totals as in the book, from our notebook (each spread is from the book's Figure 11-33; see [[code/volatility_spreads.ipynb]]).

| Spread | Cash | Delta | Gamma | Theta | Vega |
|---|---|---|---|---|---|
| Long straddle: $+10$ 100 calls, $+10$ 100 puts | $-65.30$ | $+120$ | $+96.0$ | $-0.540$ | $+3.20$ |
| Short straddle: $-20$ 105 calls, $-10$ 105 puts | $+90.90$ | $+10$ | $-132.0$ | $+0.730$ | $-4.50$ |
| Long strangle: $+10$ 95 puts, $+10$ 110 calls | $-16.90$ | $-50$ | $+66.0$ | $-0.350$ | $+2.20$ |
| Short strangle: $-30$ 100 puts, $-40$ 105 calls | $+151.50$ | $0$ | $-320.0$ | $+1.770$ | $-10.80$ |
| Long butterfly: $+10$ 95, $-20$ 100, $+10$ 105 calls | $-11.70$ | $0$ | $-16.0$ | $+0.090$ | $-0.50$ |
| Short butterfly: $-10$ 100, $+20$ 105, $-10$ 110 puts | $+9.90$ | $-60$ | $+10.0$ | $-0.060$ | $+0.40$ |
| Long condor: $+10$ 90, $-10$ 95, $-10$ 105, $+10$ 110 calls | $-31.30$ | $-30$ | $-33.0$ | $+0.190$ | $-1.10$ |
| Short condor: $-10$ 90, $+10$ 95, $+10$ 100, $-10$ 105 puts | $+21.30$ | $+90$ | $+23.0$ | $-0.140$ | $+0.70$ |
| Call ratio, buy more: $+20$ 110, $-10$ 105 calls | $+4.10$ | $-10$ | $+16.0$ | $-0.080$ | $+0.50$ |
| Call ratio, sell more: $+20$ 95, $-30$ 100 calls | $-26.80$ | $-100$ | $-72.0$ | $+0.430$ | $-2.40$ |
| Put ratio, buy more: $+40$ 95, $-10$ 110 puts | $+54.00$ | $0$ | $+114.0$ | $-0.630$ | $+3.80$ |
| Put ratio, sell more: $+10$ 105, $-30$ 95 puts | $-25.50$ | $-40$ | $-64.0$ | $+0.350$ | $-2.10$ |
| Long call Christmas tree: $+10$ 100, $-10$ 105, $-10$ 110 | $-14.00$ | $+70$ | $-26.0$ | $+0.140$ | $-0.90$ |
| Short call Christmas tree: $-10$ 90, $+10$ 100, $+10$ 105 | $+57.00$ | $-40$ | $+75.0$ | $-0.420$ | $+2.50$ |
| Long put Christmas tree: $-10$ 95, $-10$ 100, $+10$ 105 | $-18.60$ | $-20$ | $-40.0$ | $+0.220$ | $-1.30$ |
| Short put Christmas tree: $+10$ 95, $+10$ 105, $-10$ 110 | $+28.50$ | $-40$ | $+50.0$ | $-0.280$ | $+1.70$ |
| Long calendar: $+10$ June 100, $-10$ April 100 calls | $-18.60$ | $+30$ | $-14.0$ | $+0.080$ | $+0.60$ |
| Short calendar: $+10$ April 105, $-10$ June 105 calls | $+16.50$ | $-90$ | $+10.0$ | $-0.050$ | $-0.80$ |

**Patterns to notice:**
- **Debit** (negative cash) goes with "long": long straddle, long strangle, long butterfly, long condor, long trees, long calendar.
- **Credit** goes with "short" and with the **backspreads**: both "buy more than sell" ratio spreads are credits (+4.10 and +54.00).
- **Gamma and theta have opposite signs in every row.**
- **Size of the Greeks:** short strangle gamma $-320$ versus long butterfly $-16$: the 20x spread between "largest" and "smallest" is the chapter's point.
- **Delta is not zero in every row.** The long straddle is $+120$, the short condor $+90$: "approximately neutral" is a judgement.

## Slips in the book's tables (found when recomputing)
None changes the ideas. We recomputed every spread from the option table and found these differences:

| Where | Book prints | We get | Comment |
|---|---|---|---|
| Short straddle (April), rho | $-0.170$ | $+0.170$ | $-20 \times 0.052 - 10 \times (-0.121) = -1.04 + 1.21 = +0.17$ |
| Long strangle (June), delta | $-20$ | $+20$ | $20 \times (-13) + 10 \times 28 = -260 + 280 = +20$ |
| Put ratio, sell more (June), theta | $+0.020$ | $+0.200$ | $30 \times (-0.008) - 40 \times (-0.011) = -0.24 + 0.44$ |
| Long put Christmas tree (April), gamma | $-30.0$ | $-40.0$ | the book multiplies the April 100 put by 3.8; the table says 4.8 |

Smaller: the short condor's cash line shows "$5.66$" for the April 105 put (the table says 5.67; the total 21.30 is right with 5.67). In our copy the **short condor (June)** lists the signs of a long call condor, but the totals match a short condor (sell 90 and 110, buy 95 and 105), which we used. Figure 11-18's last two labels read "sell more than sell" (a typo for "sell more than buy").

## Common confusions
- **Cash-flow signs are opposite to the Greek signs** for the same trade: buying is $-$ cash but $+$ delta.
- **Total rho is small** for all these; rho matters more for stock-option calendars ([[concepts/11-volatility-spreads/calendar-spreads-interest-rates-and-dividends]]).
- **Stock versus futures options:** the characteristics are the same except rho (page 198).

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/long-short-premium-and-the-four-categories]]
- Next: [[concepts/11-volatility-spreads/choosing-a-spread-by-implied-volatility]]
- Earlier: [[concepts/07-risk-measurement-i/reading-a-position-risk-table]]
- Maths needed: [[00-maths-refresher/signs-and-running-totals]]
- See also: [[glossary]], [[formulas]]
