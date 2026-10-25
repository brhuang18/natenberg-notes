# Glossary

One line per term, in your own words. Link to the chapter where it is explained.

- **Spot (cash) transaction** - agree terms and swap money for goods immediately. [[chapters/01-financial-contracts]]
- **Forward contract** - agree terms now, swap money for goods at a later maturity date. [[concepts/01-financial-contracts/forwards-futures-and-options]]
- **Futures contract** - a forward traded on an exchange with standardised terms; the exchange guarantees it. [[concepts/01-financial-contracts/forwards-futures-and-options]]
- **Option contract** - gives one party the right, not the obligation, to decide later; the buyer pays a premium. [[concepts/01-financial-contracts/forwards-futures-and-options]]
- **Call option** - the right to buy at the exercise price.
- **Put option** - the right to sell at the exercise price.
- **Premium** - the price paid for an option; the seller keeps it regardless of what the buyer decides.
- **Derivative** - a contract whose value derives from an underlying asset (forwards, futures, options, swaps).
- **Swap** - an agreement to exchange cash flows, e.g. fixed for floating interest.
- **Maturity / expiration date** - the date a forward, futures or option contract ends.
- **Opening trade / closing trade** - the first trade creating a position / a later trade that reverses it.
- **Open interest** - number of contracts traded and not yet closed out.
- **Long / short (contract position)** - bought first / sold first.
- **Long / short (market position)** - wants the market to rise / fall. A long put is a short market position.
- **Notional value** - units times price (or index times point value) of the goods a contract covers; a measure of size, not cash paid.
- **Stock-type settlement** - pay in full now; profits unrealized until closed. [[concepts/01-financial-contracts/settlement-margin-and-variation]]
- **Futures-type (margin and variation) settlement** - small margin up front, daily cash transfers of profit and loss. [[concepts/01-financial-contracts/settlement-margin-and-variation]]
- **Margin** - a security deposit held by the exchange; still belongs to the trader.
- **Variation** - daily credit or debit from price changes on a futures position.
- **Unrealized / realized profit** - on paper only / locked in by closing the position.
- **Clearinghouse** - guarantees all exchange trades; becomes buyer to every seller and seller to every buyer. [[concepts/01-financial-contracts/clearinghouse-and-counterparty-risk]]
- **Clearing firm** - member of the clearinghouse that processes and guarantees its traders' trades.

<!-- Chapter 2 -->
- **Forward price** - the fair price today for buying at a future date: cash price plus costs of buying now minus benefits of buying now. [[concepts/02-forward-pricing/forward-price-cost-and-benefit]]
- **Costs of buying now** - what owning early costs you: interest on the price, storage, insurance, taxes.
- **Benefits of buying now** - what owning early pays you: dividends, coupons, rental or oil income, convenience yield.
- **Basis** - cash price minus forward price; usually negative.
- **Contango (normal market)** - forward prices above the cash price. [[concepts/02-forward-pricing/contango-backwardation-convenience-yield]]
- **Backwardation (backward market)** - cash price above forward prices.
- **Convenience yield** - the extra value of having a physical commodity immediately; inferred from prices, not quoted.
- **Forward rate** - an interest rate that starts at a future date, e.g. a $3 \times 9$ rate is a six-month rate starting in three months. [[concepts/02-forward-pricing/forward-price-by-instrument]]
- **FRA (forward-rate agreement)** - a contract to borrow or lend for a set period starting on a future date at a rate fixed today.
- **Arbitrage** - buying and selling the same or closely related things in different markets to profit from a mispricing. [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]]
- **Cash-and-carry arbitrage** - buy in the cash market, sell the forward, carry to maturity and deliver.
- **Carry trade** - borrowing a low-rate currency to hold a high-rate one; carries rate and exchange-rate risk, so not true arbitrage.
- **Implied value** - an input (rate, dividend, spot, later volatility) recovered by running a pricing formula backwards from a market price. [[concepts/02-forward-pricing/implied-values]]
- **Declared date** - day a company announces the dividend amount and payment date. [[concepts/02-forward-pricing/stock-dividends-and-key-dates]]
- **Ex-dividend date (ex-date)** - first day a stock trades without the right to the dividend.
- **Record date** - date you must officially own the stock to receive the dividend.
- **Payable date** - day the dividend is paid.
- **Short sale (of stock)** - selling stock you have borrowed, hoping to buy it back cheaper. [[concepts/02-forward-pricing/short-selling-and-borrowing-costs]]
- **Short-stock rebate (short rate $r_s$)** - the interest a short seller earns on the sale proceeds; lower than the long rate.
- **Long rate ($r_l$)** - the ordinary rate for borrowing and lending cash; also the rate used for option cash flows.
- **Borrowing cost ($r_{bc}$)** - long rate minus short rate.
- **Short-stock squeeze** - a stock so hard to borrow that shorting it is difficult or impossible.
- **OTC (over-the-counter)** - trading that is not done on an organised exchange.
- **Futures option** - an option whose underlying is one futures contract; its forward price is just the futures price.

<!-- Chapter 3 -->
- **Exercise price (strike price)** - the price at which the underlying changes hands if the option is exercised; the call owner pays it, the put owner receives it. [[concepts/03-contract-specifications-and-option-terminology/option-contract-specifications]]
- **Underlying** - the security or commodity covered by an option; 100 shares for most stock options, one futures contract for futures options.
- **Round lot / odd lot** - 100 shares / fewer than 100 shares.
- **Flex option** - an exchange option whose terms (quantity, expiry, strike, style) buyer and seller negotiate.
- **Serial option** - an option expiry with no matching futures month; its underlying is the nearest futures contract after expiry.
- **Midcurve option** - a short-term option on a longer-term futures contract (one-, two- or five-year midcurve).
- **Expiration date (expiry)** - date the owner must make the final buy/sell decision; afterwards all rights and obligations end.
- **Last trading day** - last business day an option can be traded; usually the third Friday for stock options.
- **AM / PM expiration** - option value fixed from the opening price (many index contracts) / the closing price (stock options) on the last trading day.
- **Exercise style (European / American)** - exercisable only at expiration / on any business day until expiration. [[concepts/03-contract-specifications-and-option-terminology/european-vs-american-exercise]]
- **Exercise** - the buyer converts the option into a position in the underlying. [[concepts/03-contract-specifications-and-option-terminology/exercise-assignment-and-settlement]]
- **Assignment** - the seller is selected to take the other side of an exercise.
- **Exercise notice / do-not-exercise notice** - formal instruction to exercise / to not exercise an option that would be exercised automatically.
- **Automatic exercise** - exchange exercises in-the-money options at expiration if they are in the money by more than a threshold.
- **Physical / futures / cash settlement** - exercise delivers the underlying / a futures position at the exercise price / a cash payment.
- **Intrinsic value** - what an option would be worth if exercised now: $\max(0, S - X)$ for a call, $\max(0, X - S)$ for a put. [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]]
- **Time value (time premium, extrinsic value)** - premium minus intrinsic value.
- **Parity** - another name for intrinsic value; an option trading at parity has zero time value.
- **In the money (ITM)** - positive intrinsic value; **out of the money (OTM)** - zero intrinsic value; **at the money (ATM)** - exercise price equals (or, on an exchange, is closest to) the underlying price. [[concepts/03-contract-specifications-and-option-terminology/in-at-out-of-the-money]]
- **Risk-based margining (OCC, SPAN)** - option margin set by analysing a position's loss across a range of price and speed-of-change scenarios. [[concepts/03-contract-specifications-and-option-terminology/option-margining]]

<!-- Chapter 4 -->
- **Parity graph** - graph of an option position's value at expiration against the underlying price. [[concepts/04-expiration-profit-and-loss/parity-graphs]]
- **Hockey-stick diagrams** - nickname for the four basic parity graphs (long/short call, long/short put).
- **Slope (of a position graph)** - change in position value per 1 change in the underlying price. [[00-maths-refresher/slope-and-straight-lines]]
- **Slope method** - add contract slopes stretch by stretch to draw any position's graph. [[concepts/04-expiration-profit-and-loss/slope-method-for-combined-positions]]
- **Debit / credit** - cash paid out (buying options) / cash received (selling options).
- **Expiration P&L graph** - the parity graph shifted down by a debit or up by a credit. [[concepts/04-expiration-profit-and-loss/expiration-pnl-and-breakeven]]
- **Breakeven price** - the underlying price at which a position's P&L at expiration is zero.
- **Limited vs unlimited risk** - buyers can lose at most the premium; sellers of calls (and, practically, puts) can lose without limit.
- **Equivalent positions** - different combinations of options and underlying with the same graph, e.g. long call plus short put equals long underlying. [[concepts/04-expiration-profit-and-loss/equivalent-positions]]

<!-- Chapter 5 -->
- **Speed (of the market)** - how fast and how far the underlying price moves; an option buyer must be right about direction *and* speed. [[concepts/05-theoretical-pricing-models/direction-and-speed]]
- **Probability** - a number from 0 to 1 (or 0% to 100%) saying how likely an outcome is; probabilities of all outcomes add to 1. [[00-maths-refresher/probability-and-expected-value]]
- **Expected value** - the probability-weighted average payout, i.e. the long-run average result. [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- **Edge** - the difference between a proposition's price and its theoretical value; the long-run profit of the side that has it.
- **Theoretical value** - the price you would pay now to just break even in the long run; the present value of the expected value. [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- **Present value** - what a future amount is worth today after removing the interest it could earn, $E/(1 + rt)$. [[00-maths-refresher/present-value-and-discounting]]
- **Long run vs short run** - probabilities are reliable only over many repetitions; a trader must survive short-run bad luck to reach the long run.
- **Model** - a simplified, more manageable picture of the real world; only as good as its assumptions and inputs ("garbage in, garbage out"). [[concepts/05-theoretical-pricing-models/models-and-their-limits]]
- **Theoretical pricing model** - a formula that turns inputs into a theoretical option value. [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]]
- **At the forward** - an option whose exercise price equals the forward price (compare at the money: equals the current price).
- **Black-Scholes model** - the standard pricing model (1973); the Black (futures) and Garman-Kohlhagen (currency) versions are all called Black-Scholes by traders. [[concepts/05-theoretical-pricing-models/black-scholes-model-and-inputs]]
- **Model inputs** - exercise price, time to expiration, underlying price, interest rate, volatility (plus dividends for stocks). [[concepts/05-theoretical-pricing-models/choosing-the-inputs]]
- **Riskless hedge** - an opposite position in the underlying that cancels small price moves in an option position. [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]]
- **Hedge ratio** - the number of underlying contracts needed to hedge one option; developed later as the delta.
- **Risk-free rate** - the interest rate of the most creditworthy borrower, usually a government bill of the same maturity.
- **LIBOR** - London Interbank Offered Rate; a market interest rate traders used as a benchmark in the book.
- **Ex-dividend date** - the first date the stock trades without the right to the dividend; what option traders focus on.
- **Volatility** - the model input describing the speed of the underlying; discussed from Chapter 6.

<!-- Chapter 6 -->
- **Random walk** - a path of unpredictable steps, like a ball falling through a pinball maze; many walks form a bell curve. [[concepts/06-volatility/random-walks-and-normal-distributions]]
- **Normal distribution** - the symmetric bell-shaped curve, fully described by a mean and a standard deviation. [[concepts/06-volatility/random-walks-and-normal-distributions]]
- **Mean** - the average outcome; the centre (peak) of a normal distribution. [[concepts/06-volatility/mean-and-standard-deviation]]
- **Standard deviation** - how spread out outcomes are: about 68.3% fall within $\pm 1$, 95.4% within $\pm 2$, 99.7% within $\pm 3$ standard deviations. [[00-maths-refresher/standard-deviation-and-variance]]
- **Variance** - the standard deviation squared; variances of independent random steps add.
- **Z-score** - how many standard deviations a value is from the mean. [[00-maths-refresher/normal-distribution-and-z-scores]]
- **Volatility ($\sigma$)** - a trader's word for standard deviation: the one-standard-deviation price change, in percent, over a year. [[concepts/06-volatility/volatility-as-a-standard-deviation]]
- **Annualized** - expressed per year; volatility, like interest rates, is always quoted annually.
- **Square-root-of-time rule** - volatility over $t$ years is annual volatility times $\sqrt{t}$; daily $\approx$ annual $/ 16$, weekly $\approx$ annual $/ 7.2$. [[concepts/06-volatility/scaling-volatility-for-time]]
- **Settlement-to-settlement change** - price change from one day's settlement price to the next; the usual basis for volatility. [[concepts/06-volatility/checking-volatility-against-price-changes]]
- **Rate volatility / price volatility** - volatility of an interest rate (for contracts quoted as 100 minus the rate) vs of the contract price; yield volatility vs price volatility is the same idea for bonds. [[concepts/06-volatility/interest-rate-products-and-rate-volatility]]
- **Continuous compounding** - interest (or returns) compounded at every instant, $e^{rt}$. [[00-maths-refresher/exponentials-and-natural-logs]]
- **Lognormal distribution** - distribution of prices when percent changes are normal and compound continuously; floor at zero, skewed up. [[concepts/06-volatility/lognormal-distributions]]
- **Mode** - the peak of a distribution; equal to the mean for a normal distribution, left of the mean for a lognormal one.
- **Realized volatility** - annualized standard deviation of percent (log) price changes of the underlying. [[concepts/06-volatility/realized-volatility]]
- **Historical vs future realized volatility** - measured over a past period / what the underlying will do over the option's life (what the model needs).
- **Volatility forecast** - a model's estimate of future realized volatility.
- **Implied volatility** - the volatility that makes the model value equal the option's price; the market's consensus view. [[concepts/06-volatility/implied-volatility]]
- **Volatility points** - mispricing measured in volatility rather than price, e.g. 28.50% implied vs 25% estimate is 3.50 volatility points.
- **Premium (levels)** - an option's price; traders also use it loosely for implied volatility ("premium is high").
- **Volatility principles** - a volatility change affects at-the-money options most in points, out-of-the-money options most in percent, and long-dated options more than short-dated. [[concepts/06-volatility/volatility-and-option-values]]

<!-- Chapter 7 -->
- **Risk measures (the Greeks)** - numbers a pricing model produces that say how an option's value changes when one input changes: delta, gamma, theta, vega, rho. Mathematically they are partial derivatives. [[chapters/07-risk-measurement-i]]
- **Delta ($\Delta$)** - change in option value per 1-point change in the underlying; 0 to 1 for calls, $-1$ to 0 for puts, 1 for the underlying. Also the hedge ratio (underlying per option $= 100/\Delta$), equivalent underlying position, and roughly the chance of finishing in the money. [[concepts/07-risk-measurement-i/delta]]
- **Whole-number delta** - the trader's convention of dropping the decimal: 0.56 is 56, the underlying is 100.
- **Delta neutral** - a position whose deltas add to 0: no preference for up or down moves (small moves only). [[concepts/07-risk-measurement-i/delta]]
- **Equivalent underlying position** - total deltas divided by 100: how many underlying contracts the directional risk resembles. [[concepts/07-risk-measurement-i/delta]]
- **Gamma ($\Gamma$, curvature)** - change in delta per 1-point change in the underlying; positive for all long options (calls and puts), negative for short. Measures speed or magnitude risk. [[concepts/07-risk-measurement-i/gamma]]
- **Long gamma / short gamma** - long gamma wants big, fast moves; short gamma wants the market to sit still. [[concepts/07-risk-measurement-i/gamma]]
- **Theta ($\Theta$, time decay)** - value an option loses per day as time passes, all else equal; written negative for long options. [[concepts/07-risk-measurement-i/theta]]
- **Negative time value** - when an option is worth less than its intrinsic value (a rare case: deep in the money, European, stock-type settlement), giving a positive theta. [[concepts/07-risk-measurement-i/theta]]
- **Vega (kappa $\kappa$, nu $\nu$)** - change in option value per 1 percentage point change in volatility; positive for all long options. [[concepts/07-risk-measurement-i/vega]]
- **Rho ($P$)** - change in option value per 1 percentage point change in the interest rate; sign depends on the underlying and settlement. Currency options have rho1 (domestic) and rho2 or phi (foreign). [[concepts/07-risk-measurement-i/rho]]
- **Theoretical edge** - quantity $\times$ (theoretical value $-$ price), summed over a position; zero for the underlying. [[concepts/07-risk-measurement-i/theoretical-edge]]
- **Implied volatility of a position (breakeven volatility)** - the volatility at which the position's theoretical profit is zero; roughly $\sigma_0 - E/\text{vega}$. [[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]]
- **Synthetic forward** - long call plus short put at the same strike and expiry; pays $S_T - K$. Its value gives $C - P = (F - K)/(1 + rt)$. [[concepts/07-risk-measurement-i/synthetic-forward-and-put-call-parity]]
- **Avoid short stock (rule)** - hedge with long stock when possible so one interest rate applies and borrowing and short-sale restrictions do not matter. [[concepts/07-risk-measurement-i/long-vs-short-stock-and-option-values]]

