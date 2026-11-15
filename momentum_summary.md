# Cross-sectional momentum vs. reversion study

NULL RESULT. At no formation horizon is the top-minus-bottom quintile 3m spread distinguishable from zero once the overlapping-hold autocorrelation is accounted for (|t(n_eff)| < 2 everywhere). The data supports NEITHER a tradeable momentum nor a tradeable reversion effect in this cross-section -- consistent with the forward model's near-zero momentum-only IC.

STRATIFIED RE-EXAMINATION (read this with the line above): the pooled null is partly a COMPOSITION artifact. Ranking the same cards inside their own era instead of across the whole cross-section turns 4 pooled horizon(s) directional, and reversion clears the sample-size gates in 2 of 3 eras. After the shared-endpoint (bid-ask-bounce) control, the era-level reversion that survives is Sword & Shield only; momentum survives nowhere (0 momentum cells). This is a POST-HOC subgroup finding on one calendar window with no trading costs applied -- it is not a tradeable signal and does not overturn the pooled null. Full tables, sample sizes and caveats below.

## Method

For each rebalance month T (monthly, expanding as the panel grows), the modeled
universe is ranked into quintiles by its trailing formation return and each card
is held for 3 months. The reported spread is the mean realized 3m log
return of the top (past-winner) quintile minus the bottom (past-loser) quintile.
MOMENTUM buys winners / sells losers; REVERSION is the exact mirror (spread
negated, legs swapped), so the verdict is driven by the SIGN and SIGNIFICANCE of
the momentum spread. Universe: the forward model's modeled cross-section
(build_dataset over MODEL_RARITIES, require_desirability=False). Rebalances with
fewer than 10 priced names, or too few distinct names to form full
quintiles, are dropped.

Formation windows: 1m, 3m, 6m trailing log return, plus a 6m SKIP-1 robustness
variant (form on T-7..T-1, skipping the most recent month to avoid 1-month
microstructure reversal contaminating the momentum signal). All formation
returns use only prices at/<= T; every hold window T -> T+3 is fully realized.

## Overlap-aware significance

Monthly rebalancing with a 3m hold makes consecutive spreads share 2 of 3 hold
months, so the per-rebalance spread series is positively autocorrelated and the
naive sqrt(n) t-stat overstates significance. Following forward.py, the effective
sample size is n_eff = n * (1 - rho) / (1 + rho) (rho = lag-1 autocorrelation of
the spread series, clipped so negative autocorrelation is not rewarded), and the
reported t-statistic is mean / std * sqrt(n_eff). A horizon is called MOMENTUM
only if t(n_eff) >= +2, REVERSION if <= -2,
else NULL.

## Top-minus-bottom quintile spread (momentum convention)

29 rebalance months (2024-04-01 .. 2026-08-01). Spread = winners - losers;
a positive, significant spread supports momentum, a negative one reversion.

| strategy | rebalances | n_eff | mean 3m spread | hit rate | IC autocorr | t (n_eff) | mean turnover | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| form1m | 29 | 12.401 | -2.2% | 41.4% | 0.401 | -1.182 | 80.7% | null |
| form3m | 27 | 6.159 | -5.8% | 18.5% | 0.629 | -1.670 | 50.2% | null |
| form6m | 24 | 5.288 | -2.9% | 25.0% | 0.639 | -1.282 | 37.9% | null |
| form6m_skip1 | 23 | 7.043 | 1.4% | 60.9% | 0.531 | 0.683 | 37.9% | null |

## Per-quintile monotonicity (pooled 3m hold return by formation quintile)

If momentum were real, the pooled mean hold return should rise monotonically from
Q1 (past losers) to Q5 (past winners); reversion would show the opposite ladder.
"Monotone steps" counts increasing adjacent pairs (out of 4); "rank
corr" is the correlation of quintile index with its pooled mean hold return
(+1 = perfect momentum ladder, -1 = perfect reversion ladder).

| strategy | Q1 (losers) | Q2 | Q3 | Q4 | Q5 (winners) | monotone steps | rank corr |
| --- | --- | --- | --- | --- | --- | --- | --- |
| form1m | 0.0% | 2.1% | 3.1% | 2.8% | -1.5% | 2/4 | -0.100 |
| form3m | 1.9% | 3.8% | 4.5% | 2.7% | -3.0% | 2/4 | -0.300 |
| form6m | 3.2% | 6.6% | 6.5% | 4.8% | 0.7% | 1/4 | -0.400 |
| form6m_skip1 | 2.1% | 5.3% | 7.2% | 5.3% | 3.6% | 2/4 | 0.100 |

## Turnover

Mean one-sided turnover is the fraction of the long (top) and short (bottom)
quintile membership that changes each rebalance (averaged over both legs and all
adjacent month pairs). Higher turnover means the past-return ranking reshuffles
quickly month to month, which both raises trading costs and shortens the shelf
life of any signal.

## Independence from the value backtest

The value backtest (backtest_summary.md) tags a card "overvalued" when its market
price sits well above the forward model's fair value. Those overvalued cards are
drawn disproportionately from THIS study's top (past-winner) quintile -- markedly
so at the longer (6m) formation window -- because a recent price run-up is exactly
what lifts market above fair value. The mirror is NOT symmetric: the "undervalued"
cohort's overlap with the past-loser (bottom) quintile stays close to the ~1/5
random baseline. So the backtest's under-minus-over spread and this
momentum/reversion result partly re-express the SAME recent-run-up cards; read the
"past winners look overvalued and subsequently lag" story as one phenomenon seen
through two lenses, NOT as two independent confirmations.

## Era- and tier-stratified re-examination

A pooled null has two very different explanations: no effect anywhere, or an
effect inside each stratum that pooling washes out. Pooling two eras that sit in
different lifecycle phases means the pooled quintile sort partly sorts cards on
ERA MEMBERSHIP rather than on their return relative to their own peers, which
attenuates the point estimate and inflates the spread series' variance and
autocorrelation (deflating n_eff). The tables below re-run the identical
estimator -- same formation windows, same as-of-T discipline, same overlap-aware
n_eff t-statistic -- inside strata, with quintiles formed WITHIN each stratum.

### How to not over-read a thin slice

A per-era slice of a 441-card panel is small. Every cell carries the sample size
behind it (cards in the stratum, rebalance months, mean priced names per
rebalance, names per quintile leg, and n_eff), and a cell is graded
`insufficient` -- NOT `null` -- unless it clears all three gates:
rebalances >= 8, n_eff >= 4, and
>= 8 names per quintile leg (a leg mean built from three
cards is noise amplification, not a portfolio). `null` means a measurable spread
indistinguishable from zero; `insufficient` means there is not enough
independent data to distinguish anything. Of the 126 cells computed,
41 are graded insufficient.

### Shared-endpoint (bid-ask-bounce) control

Each horizon is paired with a skip-1 twin. The price at T is BOTH the closing
endpoint of the formation return and the opening endpoint of the hold return, so
a measurement error e in P_T raises the formation return by e and lowers the hold
return by e -- mechanically manufacturing a negative, reversion-looking spread
out of pure noise (the classic Blume-Stambaugh / bid-ask-bounce bias). The skip-1
twin forms on T-1-w .. T-1, so its formation window never touches P_T. A
reversion result that survives skip-1 is not explained by the shared endpoint;
one that vanishes very likely is.

### Pooled baseline, and the same universe ranked within era

The second block is the BLOCKED estimator: identical universe, dates and
significance machinery, but cards are ranked inside their era and the per-era
spreads are then averaged (weighted by priced names). Comparing the two blocks
isolates how much of the pooled null is composition rather than absence of
effect.

_Unstratified pooled -- every card ranked against every other card (this is the
same estimator as the headline table above, extended with the skip-1 twins):_

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| all cards | 503 | form1m | 29 | 380.483 | 76.097 | 12.401 | -2.2% | 41.4% | -1.182 | null |
| all cards | 503 | form1m_skip1 | 28 | 377.000 | 75.400 | 19.303 | -1.2% | 39.3% | -0.912 | null |
| all cards | 503 | form3m | 27 | 373.259 | 74.652 | 6.159 | -5.8% | 18.5% | -1.670 | null |
| all cards | 503 | form3m_skip1 | 26 | 369.731 | 73.946 | 12.069 | -4.0% | 15.4% | -1.976 | null |
| all cards | 503 | form6m | 24 | 361.792 | 72.358 | 5.288 | -2.9% | 25.0% | -1.282 | null |
| all cards | 503 | form6m_skip1 | 23 | 357.696 | 71.539 | 7.043 | 1.4% | 60.9% | 0.683 | null |

_Era-blocked -- same cards, same dates, same n_eff machinery; only the RANKING
moves inside the era:_

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| within-era ranking | 503 | form1m | 29 | 380.483 | 76.097 | 22.230 | -5.1% | 10.3% | -5.288 | reversion |
| within-era ranking | 503 | form1m_skip1 | 28 | 377.000 | 75.400 | 20.585 | -3.5% | 21.4% | -3.713 | reversion |
| within-era ranking | 503 | form3m | 27 | 373.259 | 74.652 | 7.358 | -8.4% | 7.4% | -3.735 | reversion |
| within-era ranking | 503 | form3m_skip1 | 26 | 369.731 | 73.946 | 16.768 | -6.0% | 7.7% | -4.793 | reversion |
| within-era ranking | 503 | form6m | 24 | 361.792 | 72.358 | 3.835 | -5.4% | 16.7% | -2.115 | insufficient (n_eff<4) |
| within-era ranking | 503 | form6m_skip1 | 23 | 357.696 | 71.539 | 4.990 | -0.1% | 52.2% | -0.040 | null |

### By era (sets.series)

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Scarlet & Violet | 247 | form1m | 29 | 202.138 | 40.428 | 24.612 | -5.3% | 31.0% | -3.857 | reversion |
| Scarlet & Violet | 247 | form1m_skip1 | 28 | 200.536 | 40.107 | 27.710 | -2.2% | 42.9% | -1.928 | null |
| Scarlet & Violet | 247 | form3m | 27 | 198.815 | 39.763 | 14.751 | -7.0% | 18.5% | -3.849 | reversion |
| Scarlet & Violet | 247 | form3m_skip1 | 26 | 196.962 | 39.392 | 15.011 | -3.1% | 19.2% | -1.625 | null |
| Scarlet & Violet | 247 | form6m | 24 | 192.792 | 38.558 | 7.707 | -2.3% | 41.7% | -0.904 | null |
| Scarlet & Violet | 247 | form6m_skip1 | 23 | 190.435 | 38.087 | 6.133 | 2.5% | 60.9% | 0.789 | null |
| Sword & Shield | 163 | form1m | 29 | 163.000 | 32.600 | 29.000 | -5.3% | 13.8% | -5.307 | reversion |
| Sword & Shield | 163 | form1m_skip1 | 28 | 163.000 | 32.600 | 11.275 | -4.5% | 25.0% | -2.246 | reversion |
| Sword & Shield | 163 | form3m | 27 | 163.000 | 32.600 | 5.533 | -9.8% | 3.7% | -3.199 | reversion |
| Sword & Shield | 163 | form3m_skip1 | 26 | 163.000 | 32.600 | 7.232 | -8.3% | 3.8% | -3.524 | reversion |
| Sword & Shield | 163 | form6m | 24 | 163.000 | 32.600 | 5.623 | -8.7% | 8.3% | -3.045 | reversion |
| Sword & Shield | 163 | form6m_skip1 | 23 | 163.000 | 32.600 | 8.647 | -2.7% | 39.1% | -1.176 | null |
| Mega Evolution | 93 | form1m | 10 | 44.500 | 8.900 | 10.000 | -0.7% | 50.0% | -0.143 | null |
| Mega Evolution | 93 | form1m_skip1 | 9 | 41.889 | 8.378 | 9.000 | 2.7% | 55.6% | 0.780 | null |
| Mega Evolution | 93 | form3m | 8 | 38.625 | 7.725 | 8.000 | -3.1% | 37.5% | -0.593 | insufficient (leg<8) |
| Mega Evolution | 93 | form3m_skip1 | 7 | 36.286 | 7.257 | 7.000 | -5.7% | 28.6% | -0.931 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 93 | form6m | 5 | 28.800 | 5.760 | 5.000 | -0.2% | 60.0% | -0.116 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 93 | form6m_skip1 | 4 | 24.500 | 4.900 | 4.000 | -4.4% | 50.0% | -1.007 | insufficient (rebalances<8, leg<8) |

### By rarity tier (crosses eras, so not era-confounded)

`chase` is the top slot in each era (Special Illustration Rare / Hyper Rare /
Mega Hyper Rare / Rare Secret / Rare Rainbow); `wider full-art` is Ultra Rare +
Rare Ultra. Both tiers draw from both eras.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| wider full-art | 266 | form1m | 29 | 215.862 | 43.172 | 17.305 | -4.6% | 27.6% | -2.457 | reversion |
| wider full-art | 266 | form1m_skip1 | 28 | 214.357 | 42.871 | 28.000 | -1.3% | 28.6% | -1.152 | null |
| wider full-art | 266 | form3m | 27 | 212.741 | 42.548 | 5.561 | -6.4% | 25.9% | -1.616 | null |
| wider full-art | 266 | form3m_skip1 | 26 | 211.308 | 42.262 | 10.841 | -1.9% | 50.0% | -0.732 | null |
| wider full-art | 266 | form6m | 24 | 208.083 | 41.617 | 5.916 | -5.2% | 29.2% | -1.563 | null |
| wider full-art | 266 | form6m_skip1 | 23 | 206.261 | 41.252 | 6.551 | -0.2% | 43.5% | -0.058 | null |
| chase | 237 | form1m | 29 | 164.621 | 32.924 | 11.135 | 2.4% | 55.2% | 0.849 | null |
| chase | 237 | form1m_skip1 | 28 | 162.643 | 32.529 | 16.077 | -0.8% | 46.4% | -0.379 | null |
| chase | 237 | form3m | 27 | 160.519 | 32.104 | 15.520 | -3.8% | 25.9% | -1.475 | null |
| chase | 237 | form3m_skip1 | 26 | 158.423 | 31.685 | 19.987 | -4.9% | 26.9% | -2.758 | reversion |
| chase | 237 | form6m | 24 | 153.708 | 30.742 | 9.808 | 0.0% | 50.0% | 0.001 | null |
| chase | 237 | form6m_skip1 | 23 | 151.435 | 30.287 | 7.614 | 3.1% | 65.2% | 1.281 | null |

### Era x rarity tier

The only cut that can separate an era effect from a rarity-tier effect, because
each era contributes both tiers.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Scarlet & Violet / wider full-art | 125 | form1m | 29 | 105.034 | 21.007 | 29.000 | -8.8% | 17.2% | -4.809 | reversion |
| Scarlet & Violet / wider full-art | 125 | form1m_skip1 | 28 | 104.321 | 20.864 | 28.000 | -2.0% | 35.7% | -1.307 | null |
| Scarlet & Violet / wider full-art | 125 | form3m | 27 | 103.556 | 20.711 | 13.459 | -8.5% | 18.5% | -2.674 | reversion |
| Scarlet & Violet / wider full-art | 125 | form3m_skip1 | 26 | 102.731 | 20.546 | 16.165 | -0.3% | 53.8% | -0.110 | null |
| Scarlet & Violet / wider full-art | 125 | form6m | 24 | 100.875 | 20.175 | 7.309 | -4.8% | 37.5% | -1.445 | null |
| Scarlet & Violet / wider full-art | 125 | form6m_skip1 | 23 | 99.826 | 19.965 | 10.660 | -1.1% | 47.8% | -0.385 | null |
| Scarlet & Violet / chase | 122 | form1m | 29 | 97.103 | 19.421 | 13.501 | 0.7% | 48.3% | 0.211 | null |
| Scarlet & Violet / chase | 122 | form1m_skip1 | 28 | 96.214 | 19.243 | 16.229 | 0.1% | 39.3% | 0.050 | null |
| Scarlet & Violet / chase | 122 | form3m | 27 | 95.259 | 19.052 | 14.136 | -3.4% | 25.9% | -1.293 | null |
| Scarlet & Violet / chase | 122 | form3m_skip1 | 26 | 94.231 | 18.846 | 23.268 | -2.5% | 38.5% | -1.371 | null |
| Scarlet & Violet / chase | 122 | form6m | 24 | 91.917 | 18.383 | 5.748 | 3.5% | 54.2% | 0.737 | null |
| Scarlet & Violet / chase | 122 | form6m_skip1 | 23 | 90.609 | 18.122 | 5.266 | 6.8% | 65.2% | 1.299 | null |
| Sword & Shield / wider full-art | 104 | form1m | 29 | 104.000 | 20.800 | 29.000 | -6.1% | 24.1% | -4.277 | reversion |
| Sword & Shield / wider full-art | 104 | form1m_skip1 | 28 | 104.000 | 20.800 | 16.133 | -3.2% | 28.6% | -1.610 | null |
| Sword & Shield / wider full-art | 104 | form3m | 27 | 104.000 | 20.800 | 7.049 | -9.8% | 22.2% | -2.763 | reversion |
| Sword & Shield / wider full-art | 104 | form3m_skip1 | 26 | 104.000 | 20.800 | 8.121 | -7.1% | 26.9% | -3.143 | reversion |
| Sword & Shield / wider full-art | 104 | form6m | 24 | 104.000 | 20.800 | 8.088 | -9.1% | 16.7% | -3.019 | reversion |
| Sword & Shield / wider full-art | 104 | form6m_skip1 | 23 | 104.000 | 20.800 | 12.433 | -3.1% | 43.5% | -1.386 | null |
| Sword & Shield / chase | 59 | form1m | 29 | 59.000 | 11.800 | 25.883 | -3.0% | 27.6% | -3.028 | reversion |
| Sword & Shield / chase | 59 | form1m_skip1 | 28 | 59.000 | 11.800 | 9.853 | -6.1% | 17.9% | -2.105 | reversion |
| Sword & Shield / chase | 59 | form3m | 27 | 59.000 | 11.800 | 9.873 | -10.0% | 7.4% | -3.087 | reversion |
| Sword & Shield / chase | 59 | form3m_skip1 | 26 | 59.000 | 11.800 | 6.162 | -10.3% | 19.2% | -2.219 | reversion |
| Sword & Shield / chase | 59 | form6m | 24 | 59.000 | 11.800 | 5.986 | -8.3% | 12.5% | -2.417 | reversion |
| Sword & Shield / chase | 59 | form6m_skip1 | 23 | 59.000 | 11.800 | 10.000 | -3.6% | 34.8% | -1.574 | null |
| Mega Evolution / chase | 56 | form1m | 8 | 28.875 | 5.775 | 8.000 | 4.9% | 75.0% | 2.255 | insufficient (leg<8) |
| Mega Evolution / chase | 56 | form1m_skip1 | 7 | 27.429 | 5.486 | 7.000 | 5.9% | 57.1% | 1.349 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / chase | 56 | form3m | 6 | 25.500 | 5.100 | 1.354 | 6.3% | 66.7% | 0.570 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 56 | form3m_skip1 | 5 | 23.800 | 4.760 | 5.000 | 4.5% | 60.0% | 1.039 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / chase | 56 | form6m | 3 | 17.000 | 3.400 | 1.000 | 10.3% | 100.0% | 0.765 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 56 | form6m_skip1 | 2 | 13.000 | 2.600 | 2.000 | 6.5% | 100.0% | 3.026 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / wider full-art | 37 | form1m | 10 | 19.800 | 3.960 | 10.000 | -1.6% | 30.0% | -0.255 | insufficient (leg<8) |
| Mega Evolution / wider full-art | 37 | form1m_skip1 | 9 | 18.778 | 3.756 | 9.000 | -1.2% | 44.4% | -0.254 | insufficient (leg<8) |
| Mega Evolution / wider full-art | 37 | form3m | 8 | 17.500 | 3.500 | 8.000 | -4.5% | 25.0% | -1.554 | insufficient (leg<8) |
| Mega Evolution / wider full-art | 37 | form3m_skip1 | 7 | 17.000 | 3.400 | 7.000 | -0.3% | 42.9% | -0.062 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form6m | 5 | 15.400 | 3.080 | 5.000 | -6.5% | 20.0% | -1.430 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form6m_skip1 | 4 | 14.000 | 2.800 | 4.000 | -1.5% | 50.0% | -0.322 | insufficient (rebalances<8, leg<8) |

### By raw printed rarity (ERA-CONFOUNDED -- read with care)

Rarity is nested inside era in this universe: "Rare Ultra", "Rare Secret" and
"Rare Rainbow" occur only in Sword & Shield, and "Hyper Rare" only in Scarlet &
Violet. A directional cell here therefore cannot be attributed to rarity rather
than to its era. Reported for completeness only.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Ultra Rare | 162 | form1m | 29 | 111.862 | 22.372 | 28.513 | -6.6% | 24.1% | -3.145 | reversion |
| Ultra Rare | 162 | form1m_skip1 | 28 | 110.357 | 22.071 | 28.000 | 0.3% | 46.4% | 0.137 | null |
| Ultra Rare | 162 | form3m | 27 | 108.741 | 21.748 | 10.312 | -6.4% | 29.6% | -1.756 | null |
| Ultra Rare | 162 | form3m_skip1 | 26 | 107.308 | 21.462 | 22.761 | 1.5% | 65.4% | 0.744 | null |
| Ultra Rare | 162 | form6m | 24 | 104.083 | 20.817 | 8.651 | -3.5% | 41.7% | -1.177 | null |
| Ultra Rare | 162 | form6m_skip1 | 23 | 102.261 | 20.452 | 11.998 | -0.4% | 52.2% | -0.159 | null |
| Special Illustration Rare | 136 | form1m | 29 | 76.793 | 15.359 | 9.662 | 4.5% | 55.2% | 1.095 | null |
| Special Illustration Rare | 136 | form1m_skip1 | 28 | 75.179 | 15.036 | 11.304 | 2.0% | 57.1% | 0.558 | null |
| Special Illustration Rare | 136 | form3m | 27 | 73.444 | 14.689 | 13.800 | -0.7% | 48.1% | -0.183 | null |
| Special Illustration Rare | 136 | form3m_skip1 | 26 | 71.731 | 14.346 | 20.212 | -2.3% | 46.2% | -0.821 | null |
| Special Illustration Rare | 136 | form6m | 24 | 67.875 | 13.575 | 7.465 | 2.5% | 58.3% | 0.526 | null |
| Special Illustration Rare | 136 | form6m_skip1 | 23 | 66.043 | 13.209 | 8.229 | 5.2% | 65.2% | 1.292 | null |
| Rare Ultra | 104 | form1m | 29 | 104.000 | 20.800 | 29.000 | -6.1% | 24.1% | -4.277 | reversion |
| Rare Ultra | 104 | form1m_skip1 | 28 | 104.000 | 20.800 | 16.133 | -3.2% | 28.6% | -1.610 | null |
| Rare Ultra | 104 | form3m | 27 | 104.000 | 20.800 | 7.049 | -9.8% | 22.2% | -2.763 | reversion |
| Rare Ultra | 104 | form3m_skip1 | 26 | 104.000 | 20.800 | 8.121 | -7.1% | 26.9% | -3.143 | reversion |
| Rare Ultra | 104 | form6m | 24 | 104.000 | 20.800 | 8.088 | -9.1% | 16.7% | -3.019 | reversion |
| Rare Ultra | 104 | form6m_skip1 | 23 | 104.000 | 20.800 | 12.433 | -3.1% | 43.5% | -1.386 | null |
| Rare Rainbow | 44 | form1m | 29 | 44.000 | 8.800 | 20.079 | -2.7% | 37.9% | -1.724 | null |
| Rare Rainbow | 44 | form1m_skip1 | 28 | 44.000 | 8.800 | 12.560 | -5.4% | 32.1% | -1.875 | null |
| Rare Rainbow | 44 | form3m | 27 | 44.000 | 8.800 | 8.630 | -9.1% | 18.5% | -2.276 | reversion |
| Rare Rainbow | 44 | form3m_skip1 | 26 | 44.000 | 8.800 | 6.671 | -9.5% | 23.1% | -1.952 | null |
| Rare Rainbow | 44 | form6m | 24 | 44.000 | 8.800 | 11.944 | -6.5% | 20.8% | -2.870 | reversion |
| Rare Rainbow | 44 | form6m_skip1 | 23 | 44.000 | 8.800 | 9.996 | -2.2% | 30.4% | -0.764 | null |
| Hyper Rare | 33 | form1m | 29 | 27.414 | 5.483 | 15.689 | -0.0% | 51.7% | -0.012 | insufficient (leg<8) |
| Hyper Rare | 33 | form1m_skip1 | 28 | 27.214 | 5.443 | 18.473 | 3.8% | 60.7% | 1.390 | insufficient (leg<8) |
| Hyper Rare | 33 | form3m | 27 | 27.000 | 5.400 | 15.111 | -3.5% | 40.7% | -1.255 | insufficient (leg<8) |
| Hyper Rare | 33 | form3m_skip1 | 26 | 26.769 | 5.354 | 19.073 | -0.8% | 38.5% | -0.365 | insufficient (leg<8) |
| Hyper Rare | 33 | form6m | 24 | 26.250 | 5.250 | 7.293 | -3.1% | 37.5% | -0.746 | insufficient (leg<8) |
| Hyper Rare | 33 | form6m_skip1 | 23 | 25.957 | 5.191 | 9.395 | 1.0% | 34.8% | 0.258 | insufficient (leg<8) |
| Rare Secret | 15 | form1m | 29 | 15.000 | 3.000 | 29.000 | -6.4% | 37.9% | -1.838 | insufficient (leg<8) |
| Rare Secret | 15 | form1m_skip1 | 28 | 15.000 | 3.000 | 28.000 | -8.7% | 39.3% | -3.107 | insufficient (leg<8) |
| Rare Secret | 15 | form3m | 27 | 15.000 | 3.000 | 24.266 | -13.8% | 18.5% | -4.613 | insufficient (leg<8) |
| Rare Secret | 15 | form3m_skip1 | 26 | 15.000 | 3.000 | 21.576 | -10.5% | 23.1% | -2.823 | insufficient (leg<8) |
| Rare Secret | 15 | form6m | 24 | 15.000 | 3.000 | 18.645 | -13.5% | 16.7% | -3.573 | insufficient (leg<8) |
| Rare Secret | 15 | form6m_skip1 | 23 | 15.000 | 3.000 | 20.234 | -4.9% | 39.1% | -1.291 | insufficient (leg<8) |
| Mega Hyper Rare | 7 | form1m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form1m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form3m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form3m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form6m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form6m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Futuristic Rare | 2 | form1m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Futuristic Rare | 2 | form1m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Futuristic Rare | 2 | form3m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Futuristic Rare | 2 | form3m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Futuristic Rare | 2 | form6m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Futuristic Rare | 2 | form6m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |

### Shared-endpoint control, cell by cell

Only cells that clear the gates AND report a direction are listed -- they are the
only claims that need controlling.

| stratum | cards | horizon | base spread | base t(n_eff) | skip-1 spread | skip-1 t(n_eff) | abs ratio skip-1/base | reading |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| within-era ranking | 503 | 1m | -5.1% | -5.288 | -3.5% | -3.713 | 0.686 | SURVIVES the shared-endpoint control |
| within-era ranking | 503 | 3m | -8.4% | -3.735 | -6.0% | -4.793 | 0.714 | SURVIVES the shared-endpoint control |
| Scarlet & Violet | 247 | 1m | -5.3% | -3.857 | -2.2% | -1.928 | 0.423 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet | 247 | 3m | -7.0% | -3.849 | -3.1% | -1.625 | 0.446 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield | 163 | 1m | -5.3% | -5.307 | -4.5% | -2.246 | 0.853 | SURVIVES the shared-endpoint control |
| Sword & Shield | 163 | 3m | -9.8% | -3.199 | -8.3% | -3.524 | 0.844 | SURVIVES the shared-endpoint control |
| Sword & Shield | 163 | 6m | -8.7% | -3.045 | -2.7% | -1.176 | 0.308 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| wider full-art | 266 | 1m | -4.6% | -2.457 | -1.3% | -1.152 | 0.294 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet / wider full-art | 125 | 1m | -8.8% | -4.809 | -2.0% | -1.307 | 0.231 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet / wider full-art | 125 | 3m | -8.5% | -2.674 | -0.3% | -0.110 | 0.034 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / wider full-art | 104 | 1m | -6.1% | -4.277 | -3.2% | -1.610 | 0.527 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / wider full-art | 104 | 3m | -9.8% | -2.763 | -7.1% | -3.143 | 0.731 | SURVIVES the shared-endpoint control |
| Sword & Shield / wider full-art | 104 | 6m | -9.1% | -3.019 | -3.1% | -1.386 | 0.342 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / chase | 59 | 1m | -3.0% | -3.028 | -6.1% | -2.105 | 2.002 | SURVIVES the shared-endpoint control |
| Sword & Shield / chase | 59 | 3m | -10.0% | -3.087 | -10.3% | -2.219 | 1.032 | SURVIVES the shared-endpoint control |
| Sword & Shield / chase | 59 | 6m | -8.3% | -2.417 | -3.6% | -1.574 | 0.431 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Ultra Rare | 162 | 1m | -6.6% | -3.145 | 0.3% | 0.137 | 0.038 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Ultra | 104 | 1m | -6.1% | -4.277 | -3.2% | -1.610 | 0.527 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Ultra | 104 | 3m | -9.8% | -2.763 | -7.1% | -3.143 | 0.731 | SURVIVES the shared-endpoint control |
| Rare Ultra | 104 | 6m | -9.1% | -3.019 | -3.1% | -1.386 | 0.342 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Rainbow | 44 | 3m | -9.1% | -2.276 | -9.5% | -1.952 | 1.042 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Rainbow | 44 | 6m | -6.5% | -2.870 | -2.2% | -0.764 | 0.331 | vanishes without P_T -- consistent with a shared-endpoint artifact |

## Honest stratified conclusion

THE POOLED NULL IS PARTLY A COMPOSITION ARTIFACT -- BUT WHAT SURVIVES IS NARROW AND POST-HOC. Every unstratified pooled horizon is null. Ranking the SAME 441 cards inside their own era and averaging the per-era spreads (the blocked estimator: identical universe, dates and n_eff machinery, only the ranking changes) is directional at form1m, form1m_skip1, form3m, form3m_skip1. form1m: pooled -2.2% (t -1.182, null) vs era-blocked -5.1% (t -5.288, reversion); form1m_skip1: pooled -1.2% (t -0.912, null) vs era-blocked -3.5% (t -3.713, reversion); form3m: pooled -5.8% (t -1.670, null) vs era-blocked -8.4% (t -3.735, reversion); form3m_skip1: pooled -4.0% (t -1.976, null) vs era-blocked -6.0% (t -4.793, reversion); form6m: pooled -2.9% (t -1.282, null) vs era-blocked -5.4% (t -2.115, insufficient); form6m_skip1: pooled 1.4% (t 0.683, null) vs era-blocked -0.1% (t -0.040, null). So a large part of the pooled null was the pooled quintile sort ranking cards against a mixed-era field rather than against their own peers.

By era, reversion clears every sample-size gate in 2 of 3 eras (Scarlet & Violet, Sword & Shield): Scarlet & Violet @ form1m (-5.3%, t(n_eff) -3.857, 29 rebalances, n_eff 24.612, 247 cards); Scarlet & Violet @ form3m (-7.0%, t(n_eff) -3.849, 27 rebalances, n_eff 14.751, 247 cards); Sword & Shield @ form1m (-5.3%, t(n_eff) -5.307, 29 rebalances, n_eff 29.000, 163 cards); Sword & Shield @ form1m_skip1 (-4.5%, t(n_eff) -2.246, 28 rebalances, n_eff 11.275, 163 cards); Sword & Shield @ form3m (-9.8%, t(n_eff) -3.199, 27 rebalances, n_eff 5.533, 163 cards); Sword & Shield @ form3m_skip1 (-8.3%, t(n_eff) -3.524, 26 rebalances, n_eff 7.232, 163 cards); Sword & Shield @ form6m (-8.7%, t(n_eff) -3.045, 24 rebalances, n_eff 5.623, 163 cards).

Beyond the era cut, 27 of the 114 stratum cells report reversion and 0 report momentum after gating. Those cells are NOT independent of each other -- the era x tier and raw-rarity cells are subsets of the same cards as the era cells (raw rarity is nested inside era here), so counting them as separate confirmations would double-count the same months and the same cards.

SHARED-ENDPOINT CONTROL -- the decisive filter. 9 of the 31 directional cells form on a window that never touches the price at T, so they are not explainable by measurement error in the single price that is shared between the formation and hold returns. At the era level that is: Sword & Shield @ form1m_skip1 (-4.5%, t(n_eff) -2.246, 28 rebalances, n_eff 11.275, 163 cards); Sword & Shield @ form3m_skip1 (-8.3%, t(n_eff) -3.524, 26 rebalances, n_eff 7.232, 163 cards). Every other directional cell has P_T as both the closing endpoint of its formation return and the opening endpoint of its hold return, where any error in that one monthly price mechanically manufactures a negative, reversion-looking spread (Blume-Stambaugh / bid-ask bounce).

NO stratum at any horizon supports MOMENTUM, at any formation window, with or without the endpoint control. Nothing here resurrects a tradeable-momentum claim; there is none.

Caveats that apply to every cell above. (1) POST-HOC: this stratification was run AFTER the pooled result came back null. A subgroup effect found that way is a materially weaker claim than a pre-registered one, and it is the correct reading that this is a hypothesis about where to look next, not a measured effect. (2) NOT INDEPENDENT REPLICATIONS: every stratum is cut from ONE panel over ONE calendar window, so two strata agreeing mostly tells you they lived through the same months. (3) ERA-CONFOUNDED RARITY: the SWSH rarity strings occur only in SWSH and the SV ones only in SV/ME, so a raw-rarity cell cannot be attributed to rarity rather than era; only the era x tier cross can separate them. (4) MULTIPLICITY: 85 cells cleared the gates and were read for significance; some directional cells are expected by chance, and because the cells overlap heavily no clean multiplicity correction exists. (5) NO COSTS: nothing here is net of fees, spread or shipping, and the quintile legs reshuffle most of their membership every month.

BOTTOM LINE: there is still NO tradeable momentum. The reversion that appears inside strata is real in the data but post-hoc, cost-free, endpoint-sensitive, and concentrated in the slices flagged above -- it is reported because it is what the data says, not because it is actionable.

Per-(dimension, stratum, strategy) detail with every sample-size column:
momentum_strata.csv (same directory).


## Honest conclusion (pooled)

NULL RESULT. At no formation horizon is the top-minus-bottom quintile 3m spread distinguishable from zero once the overlapping-hold autocorrelation is accounted for (|t(n_eff)| < 2 everywhere). The data supports NEITHER a tradeable momentum nor a tradeable reversion effect in this cross-section -- consistent with the forward model's near-zero momentum-only IC.

Per-(strategy, side, rebalance) detail: momentum_results.csv (same directory).
Reversion rows are the algebraic mirror of the momentum rows (spread negated,
long/short legs swapped) and are NOT independent evidence.
