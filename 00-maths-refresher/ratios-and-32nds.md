# Ratios, quotes in 32nds, and a spread as a signed sum

Needed for: [[chapters/10-introduction-to-spreading]]

## Ratios like 3:1
A ratio compares two quantities. "Commodity B trades at 3 times Commodity A" is written $B = 3A$, or "the ratio $B : A$ is $3 : 1$".

- To check a ratio today, divide: $390 \div 120 = 3.25$. That is more than 3, so B looks expensive against A.
- To trade the relationship, buy and sell in the *same proportion*: three A for each one B. In $3:2:1$ (crack spread), the numbers are the quantity of each leg: for every 3 of crude, 2 of gasoline and 1 of heating oil.
- A **ratio spread** is just a spread with unequal numbers of contracts on the two sides. Unequal *numbers* but roughly equal *value*: 3 A cost $3 \times 120 = 360$, close to one B at 390.

## Prices quoted in 32nds
US Treasury futures are quoted as points plus 32nds of a point. "$116\ 14/32$" means $116 + \tfrac{14}{32}$.

- To convert to a decimal: $\tfrac{14}{32} = 0.4375$, so $116\tfrac{14}{32} = 116.4375$.
- To subtract two quotes, subtract the points and the 32nds separately, borrowing 1 point (= 32/32) if needed.

Example, the book's first spread:

$$118\tfrac{27}{32} - 116\tfrac{14}{32} = (118 - 116) + \tfrac{27 - 14}{32} = 2\tfrac{13}{32}$$

Check with decimals: $118.84375 - 116.4375 = 2.40625$, and $\tfrac{13}{32} = 0.40625$.

A case that needs borrowing: $115\tfrac{10}{32} - 113\tfrac{7}{32} = 2\tfrac{3}{32}$ (no borrowing here, but $115\tfrac{3}{32} - 113\tfrac{7}{32}$ would be $1\tfrac{28}{32}$: borrow 1 point, $\tfrac{32+3-7}{32} = \tfrac{28}{32}$).

Profit from selling the spread at $2\tfrac{13}{32}$ and buying it back at $2\tfrac{3}{32}$: only the 32nds differ, $\tfrac{13 - 3}{32} = \tfrac{10}{32}$.

## A spread price is a signed sum
Use $+$ for a leg you buy and $-$ for a leg you sell, then add:

$$\text{spread price} = A - B - C \qquad \text{(buy } A\text{, sell } B \text{ and } C\text{)}$$

This is the same bookkeeping as in [[00-maths-refresher/signs-and-running-totals]]. Two consequences the chapter uses:

1. **Only the total matters.** Any set of leg prices that gives the same total is the same spread price: $129 - 47 - 68 = 131 - 48 - 69 = 200 - 86 - 100 = 14$.
2. **Buying and selling use different quotes.** To *buy* the spread you buy the bought legs at their asks and sell the sold legs at their bids. To *sell* it you reverse that. That is why a spread has its own bid and ask (see [[concepts/10-introduction-to-spreading/executing-a-spread]]).
