# Contango, backwardation and convenience yield

**One-line definition:** *contango* means forward prices are above the cash price, *backwardation* means the cash price is above forward prices, and *convenience yield* is the extra value the market puts on having a commodity right now.

## Intuition
Owning a physical commodity seems to have only costs: you pay interest, storage and insurance. So the forward price should always be above the cash price. That is the normal state of affairs, called **contango** (or a *normal* market).

But sometimes the cash price is *higher* than the forward price. That is **backwardation** (a *backward* market). Why would anyone pay more for the same goods today than for delivery later?

Because some users need the goods now. A factory that runs out of raw material may have to shut down, which could cost far more than any storage bill. If supplies are tight, buyers will pay a premium to get the commodity immediately. That premium is the **convenience yield**: a hidden benefit of holding the physical commodity.

## The maths
Contango and backwardation, using the basis from [[concepts/02-forward-pricing/forward-price-cost-and-benefit]]:

| Market | Cash vs forward | Basis ($\text{cash} - \text{forward}$) |
|---|---|---|
| Contango (normal) | forward > cash | negative |
| Backwardation | cash > forward | positive |

You cannot see the convenience yield directly, but if you know the other costs you can **infer** it. Work out what the cash price *should* be from the forward price using the commodity formula, and compare that to the actual cash price:

$$\text{convenience yield} = \text{actual cash price} - \text{cash price implied by the forward}$$

## Worked example (the book's)
Three-month forward $F = 77.40$, $r = 8\%$, storage $s = 3.00$, insurance $i = 0.60$, $t = 0.25$.

1. Implied cash price: $C = (77.40 - 3.60 \times 0.25) / (1 + 0.08 \times 0.25) = 76.50 / 1.02 = 75.00$.
2. Suppose the actual cash price is $76.25$.
3. Convenience yield $= 76.25 - 75.00 = 1.25$.

Users are paying an extra \$1.25 for the benefit of having the commodity immediately.

## A backwardation example (our own, same numbers)
If instead the actual cash price were $78.00$ while the three-month forward is still $77.40$:

- The basis is $78.00 - 77.40 = +0.60$ (cash above forward) so the market is in backwardation.
- Implied convenience yield $= 78.00 - 75.00 = 3.00$.

So the interest, storage and insurance costs are real, but the convenience yield of \$3.00 is larger than all of them put together.

## Common confusions
- Convenience yield is *inferred*, not quoted. It is whatever is left over after the known costs.
- Backwardation does not mean something is wrong. In the book's explanation it reflects scarcity today: buyers who need the commodity immediately will pay more for it than for later delivery.
- Do not confuse "normal" (contango) with "usual for every market". The book's own wording is that contango is the normal market for commodities.

## Related
- Chapter: [[chapters/02-forward-pricing]]
- See also: [[concepts/02-forward-pricing/forward-price-by-instrument]], [[concepts/02-forward-pricing/implied-values]], [[glossary]]
