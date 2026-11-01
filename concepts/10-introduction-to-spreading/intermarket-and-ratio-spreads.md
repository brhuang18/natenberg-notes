# Intermarket and ratio spreads

**One-line definition:** an **intermarket spread** takes opposite positions in two different markets whose prices are related; a **ratio spread** uses unequal numbers of contracts on the two sides to match the relationship (3 of one against 1 of the other).

## Intuition
Cash-and-carry rests on an exact formula. Intermarket spreads rest on a **habit**: two prices that usually move together, or keep a rough ratio, and eventually return to it. Think of two friends who walk at roughly the same pace; if one gets too far ahead you bet that the gap will close. You do not know which friend will speed up or slow down, only that the gap is unusual.

Because the relationship is observed rather than guaranteed, these spreads are **less reliable and carry more risk**. If the relationship has really changed, you can lose even though you "spread".

## The examples, with the maths
### 1. Note over bond (NOB), a yield-curve spread (pages 161-162)
A 10-year Treasury note future at $116\tfrac{14}{32}$ and a 30-year bond future at $118\tfrac{27}{32}$ (quoted in 32nds, [[00-maths-refresher/ratios-and-32nds]]):

$$\text{spread} = 118\tfrac{27}{32} - 116\tfrac{14}{32} = 2\tfrac{13}{32}$$

Treasury prices move opposite to interest rates. If you think rates will rise and **long-term rates will rise faster than short-term**, the bond falls more than the note, so the spread narrows. You **sell the spread** (sell the bond, buy the note). Later the prices are $115\tfrac{10}{32}$ and $113\tfrac{7}{32}$:

$$\text{new spread} = 2\tfrac{3}{32}, \qquad \text{profit} = 2\tfrac{13}{32} - 2\tfrac{3}{32} = \tfrac{10}{32}$$

The spread depends on the **yield curve** (the relationship between short- and long-term interest rates). Traders call this the NOB spread: "notes over bonds".

### 2. A 3:1 ratio spread (page 162)
Suppose that over a long period Commodity B has traded at about three times Commodity A: $B = 3A$. Now A = 120 and B = 390, a ratio of $390/120 = 3.25$, above the usual 3. So B looks expensive compared with A. Two ways to read it:

- If B is right at 390, A "should" be $390 / 3 = 130$ (A looks cheap at 120).
- If A is right at 120, B "should" be $3 \times 120 = 360$ (B looks dear at 390).

We do not need to decide which one is wrong. We trade the *gap*: **buy three A and sell one B**, so the A side ($3 \times 120 = 360$) roughly matches the B side (390) in value.

| Leg | Cash flow |
|---|---|
| Buy 3 A at 120 | $-360$ |
| Sell 1 B at 390 | $+390$ |
| **Credit** | **+30** |

If the ratio returns to 3, then $B = 3A$ and closing costs nothing: selling the 3 A brings in $3A$ and buying back 1 B costs $3A$, net zero. So you keep the 30 **whatever the price level**: A = 50 and B = 150, or A = 200 and B = 600, all give +30.

*(The book's sentence reads "A ought to be trading at 360 (3 x 120) or B at 130 (390/3)". The two numbers are swapped: A would need to be 130, or B would need to be 360, as above. See the notes on the book's text in the chapter note.)*

### 3. The crack spread, three legs (page 163)
Refiners turn crude oil into gasoline and heating oil. The common ratio is **3:2:1**: 3 of crude yield 2 of gasoline and 1 of heating oil.

$$\text{crack} = 2 \times \text{gasoline} + 1 \times \text{heating oil} - 3 \times \text{crude}$$

The spread reflects refining costs and demand for the products. You **buy the spread** when you buy the products and sell crude (the products are worth more than the crude). If you think demand for the products will fall, sell the spread. (Our illustration, all prices in the same unit: gasoline 90, heating oil 95, crude 80 gives $180 + 95 - 240 = 35$.)

A similar three-leg spread in soybeans is the **crush spread**: soybeans against soybean oil and soybean meal.

### Other ratio spreads the book mentions
Gold against silver, corn against soybeans, the S&P 500 against the Dow Jones Industrial Average. In each pair the prices are very different in size, yet traders believe a relationship exists.

## What if the ratio does not return? (our check)
Your position is long 3 A and short 1 B, opened at A = 120, B = 390. At any later prices $A_1$ and $B_1$:

$$\text{P\&L} = 3(A_1 - 120) - (B_1 - 390) = 30 + (3A_1 - B_1)$$

Read the bracket as "how far B is *below* its 3:1 level". Writing the gap as $B - 3A$ (it starts at $390 - 360 = 30$):

$$\text{P\&L} = \text{starting gap} - \text{current gap} = 30 - (B_1 - 3A_1)$$

You earn money as the gap closes to 0, and you keep earning if it closes through zero in your favour.

- Ratio restored ($B_1 = 3A_1$): gap 0, P&L $= +30$.
- A stays at 120 and B falls to 360: gap 0, P&L $= +30$.
- A stays at 120 and B rises to 420: gap $420 - 360 = 60$, P&L $= 30 - 60 = -30$.

So the 30 is only safe **if** the relationship reverts. If the gap widens instead, you lose. That is the extra risk the book mentions.

## Common confusions
- **The ratio is in contracts, not dollars.** 3:1 means three contracts of one against one of the other; the *values* are roughly balanced.
- **"Profit independent of the price" holds only when the ratio is restored.** If A and B both rise by the same *percentage* but the ratio moves, you can still lose.
- **Intermarket spreads rely on the relationship, not on a formula.** Cash-and-carry has an exact answer; these do not.

## Related
- Chapter: [[chapters/10-introduction-to-spreading]]
- Previous: [[concepts/10-introduction-to-spreading/cash-and-carry-and-calendar-spreads]]
- Next: [[concepts/10-introduction-to-spreading/executing-a-spread]]
- Maths needed: [[00-maths-refresher/ratios-and-32nds]]
- See also: [[glossary]], [[formulas]]
