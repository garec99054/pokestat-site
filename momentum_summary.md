# Cross-sectional momentum vs. reversion study

NULL RESULT. At no formation horizon is the top-minus-bottom quintile 3m spread distinguishable from zero once the overlapping-hold autocorrelation is accounted for (|t(n_eff)| < 2 everywhere). The data supports NEITHER a tradeable momentum nor a tradeable reversion effect in this cross-section -- consistent with the forward model's near-zero momentum-only IC.

STRATIFIED RE-EXAMINATION (read this with the line above): the pooled null is partly a COMPOSITION artifact. Ranking the same cards inside their own era instead of across the whole cross-section turns 4 pooled horizon(s) directional, and reversion clears the sample-size gates in 2 of 3 eras. After the shared-endpoint (bid-ask-bounce) control, the era-level reversion that survives is Scarlet & Violet, Sword & Shield only; momentum survives nowhere (0 momentum cells). This is a POST-HOC subgroup finding on one calendar window with no trading costs applied -- it is not a tradeable signal and does not overturn the pooled null. Full tables, sample sizes and caveats below.

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

28 rebalance months (2024-04-01 .. 2026-07-01). Spread = winners - losers;
a positive, significant spread supports momentum, a negative one reversion.

| strategy | rebalances | n_eff | mean 3m spread | hit rate | IC autocorr | t (n_eff) | mean turnover | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| form1m | 28 | 14.098 | -2.5% | 39.3% | 0.330 | -1.464 | 80.9% | null |
| form3m | 26 | 5.233 | -6.4% | 15.4% | 0.665 | -1.793 | 50.2% | null |
| form6m | 23 | 3.366 | -3.2% | 21.7% | 0.745 | -1.139 | 37.9% | null |
| form6m_skip1 | 22 | 6.941 | 1.6% | 63.6% | 0.520 | 0.741 | 38.3% | null |

## Per-quintile monotonicity (pooled 3m hold return by formation quintile)

If momentum were real, the pooled mean hold return should rise monotonically from
Q1 (past losers) to Q5 (past winners); reversion would show the opposite ladder.
"Monotone steps" counts increasing adjacent pairs (out of 4); "rank
corr" is the correlation of quintile index with its pooled mean hold return
(+1 = perfect momentum ladder, -1 = perfect reversion ladder).

| strategy | Q1 (losers) | Q2 | Q3 | Q4 | Q5 (winners) | monotone steps | rank corr |
| --- | --- | --- | --- | --- | --- | --- | --- |
| form1m | 0.6% | 3.0% | 3.9% | 3.3% | -1.3% | 2/4 | -0.100 |
| form3m | 2.9% | 4.9% | 5.1% | 3.0% | -2.7% | 2/4 | -0.300 |
| form6m | 4.3% | 7.4% | 7.2% | 5.6% | 1.4% | 1/4 | -0.400 |
| form6m_skip1 | 3.0% | 6.1% | 7.7% | 6.0% | 4.7% | 2/4 | 0.100 |

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
43 are graded insufficient.

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
| all cards | 503 | form1m | 28 | 377.000 | 75.400 | 14.098 | -2.5% | 39.3% | -1.464 | null |
| all cards | 503 | form1m_skip1 | 27 | 373.259 | 74.652 | 17.563 | -1.7% | 37.0% | -1.457 | null |
| all cards | 503 | form3m | 26 | 369.731 | 73.946 | 5.233 | -6.4% | 15.4% | -1.793 | null |
| all cards | 503 | form3m_skip1 | 25 | 365.920 | 73.184 | 11.612 | -4.1% | 16.0% | -1.948 | null |
| all cards | 503 | form6m | 23 | 357.696 | 71.539 | 3.366 | -3.2% | 21.7% | -1.139 | insufficient (n_eff<4) |
| all cards | 503 | form6m_skip1 | 22 | 353.909 | 70.782 | 6.941 | 1.6% | 63.6% | 0.741 | null |

_Era-blocked -- same cards, same dates, same n_eff machinery; only the RANKING
moves inside the era:_

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| within-era ranking | 503 | form1m | 28 | 377.000 | 75.400 | 21.693 | -5.1% | 10.7% | -5.111 | reversion |
| within-era ranking | 503 | form1m_skip1 | 27 | 373.259 | 74.652 | 19.807 | -3.7% | 18.5% | -3.918 | reversion |
| within-era ranking | 503 | form3m | 26 | 369.731 | 73.946 | 6.531 | -8.7% | 7.7% | -3.652 | reversion |
| within-era ranking | 503 | form3m_skip1 | 25 | 365.920 | 73.184 | 16.445 | -5.9% | 8.0% | -4.596 | reversion |
| within-era ranking | 503 | form6m | 23 | 357.696 | 71.539 | 3.750 | -5.3% | 17.4% | -2.012 | insufficient (n_eff<4) |
| within-era ranking | 503 | form6m_skip1 | 22 | 353.909 | 70.782 | 4.938 | 0.1% | 54.5% | 0.034 | null |

### By era (sets.series)

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Scarlet & Violet | 247 | form1m | 28 | 200.536 | 40.107 | 24.085 | -5.3% | 32.1% | -3.775 | reversion |
| Scarlet & Violet | 247 | form1m_skip1 | 27 | 198.815 | 39.763 | 25.043 | -2.5% | 40.7% | -2.153 | reversion |
| Scarlet & Violet | 247 | form3m | 26 | 196.962 | 39.392 | 14.290 | -7.2% | 19.2% | -3.826 | reversion |
| Scarlet & Violet | 247 | form3m_skip1 | 25 | 194.960 | 38.992 | 14.458 | -3.1% | 20.0% | -1.540 | null |
| Scarlet & Violet | 247 | form6m | 23 | 190.435 | 38.087 | 7.612 | -2.1% | 43.5% | -0.806 | null |
| Scarlet & Violet | 247 | form6m_skip1 | 22 | 187.864 | 37.573 | 5.928 | 2.7% | 63.6% | 0.817 | null |
| Sword & Shield | 163 | form1m | 28 | 163.000 | 32.600 | 28.000 | -5.3% | 14.3% | -5.068 | reversion |
| Sword & Shield | 163 | form1m_skip1 | 27 | 163.000 | 32.600 | 10.843 | -4.6% | 25.9% | -2.178 | reversion |
| Sword & Shield | 163 | form3m | 26 | 163.000 | 32.600 | 5.272 | -9.9% | 3.8% | -3.094 | reversion |
| Sword & Shield | 163 | form3m_skip1 | 25 | 163.000 | 32.600 | 6.926 | -8.3% | 4.0% | -3.379 | reversion |
| Sword & Shield | 163 | form6m | 23 | 163.000 | 32.600 | 5.335 | -8.5% | 8.7% | -2.866 | reversion |
| Sword & Shield | 163 | form6m_skip1 | 22 | 163.000 | 32.600 | 8.141 | -2.5% | 40.9% | -1.060 | null |
| Mega Evolution | 93 | form1m | 9 | 41.889 | 8.378 | 9.000 | -0.6% | 44.4% | -0.102 | null |
| Mega Evolution | 93 | form1m_skip1 | 8 | 38.625 | 7.725 | 8.000 | 3.1% | 62.5% | 0.798 | insufficient (leg<8) |
| Mega Evolution | 93 | form3m | 7 | 36.286 | 7.257 | 5.090 | -6.6% | 28.6% | -1.296 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 93 | form3m_skip1 | 6 | 33.167 | 6.633 | 6.000 | -2.0% | 33.3% | -0.344 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 93 | form6m | 4 | 24.500 | 4.900 | 4.000 | -0.5% | 50.0% | -0.261 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 93 | form6m_skip1 | 3 | 22.333 | 4.467 | 3.000 | 0.1% | 66.7% | 0.072 | insufficient (rebalances<8, n_eff<4, leg<8) |

### By rarity tier (crosses eras, so not era-confounded)

`chase` is the top slot in each era (Special Illustration Rare / Hyper Rare /
Mega Hyper Rare / Rare Secret / Rare Rainbow); `wider full-art` is Ultra Rare +
Rare Ultra. Both tiers draw from both eras.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| wider full-art | 266 | form1m | 28 | 214.357 | 42.871 | 17.038 | -4.6% | 28.6% | -2.386 | reversion |
| wider full-art | 266 | form1m_skip1 | 27 | 212.741 | 42.548 | 27.000 | -1.7% | 25.9% | -1.550 | null |
| wider full-art | 266 | form3m | 26 | 211.308 | 42.262 | 5.528 | -6.6% | 23.1% | -1.664 | null |
| wider full-art | 266 | form3m_skip1 | 25 | 209.760 | 41.952 | 10.639 | -2.1% | 48.0% | -0.836 | null |
| wider full-art | 266 | form6m | 23 | 206.261 | 41.252 | 5.450 | -5.3% | 30.4% | -1.498 | null |
| wider full-art | 266 | form6m_skip1 | 22 | 204.409 | 40.882 | 6.173 | -0.1% | 45.5% | -0.038 | null |
| chase | 237 | form1m | 28 | 162.643 | 32.529 | 12.768 | 1.7% | 53.6% | 0.702 | null |
| chase | 237 | form1m_skip1 | 27 | 160.519 | 32.104 | 14.461 | -1.7% | 44.4% | -0.895 | null |
| chase | 237 | form3m | 26 | 158.423 | 31.685 | 11.895 | -4.9% | 23.1% | -1.886 | null |
| chase | 237 | form3m_skip1 | 25 | 156.160 | 31.232 | 19.733 | -5.2% | 24.0% | -2.854 | reversion |
| chase | 237 | form6m | 23 | 151.435 | 30.287 | 6.855 | -0.6% | 47.8% | -0.225 | null |
| chase | 237 | form6m_skip1 | 22 | 149.500 | 29.900 | 7.567 | 3.3% | 68.2% | 1.349 | null |

### Era x rarity tier

The only cut that can separate an era effect from a rarity-tier effect, because
each era contributes both tiers.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Scarlet & Violet / wider full-art | 125 | form1m | 28 | 104.321 | 20.864 | 28.000 | -8.9% | 17.9% | -4.714 | reversion |
| Scarlet & Violet / wider full-art | 125 | form1m_skip1 | 27 | 103.556 | 20.711 | 27.000 | -2.5% | 37.0% | -1.674 | null |
| Scarlet & Violet / wider full-art | 125 | form3m | 26 | 102.731 | 20.546 | 13.474 | -8.9% | 15.4% | -2.807 | reversion |
| Scarlet & Violet / wider full-art | 125 | form3m_skip1 | 25 | 101.840 | 20.368 | 15.314 | -0.7% | 52.0% | -0.263 | null |
| Scarlet & Violet / wider full-art | 125 | form6m | 23 | 99.826 | 19.965 | 7.052 | -4.7% | 39.1% | -1.351 | null |
| Scarlet & Violet / wider full-art | 125 | form6m_skip1 | 22 | 98.682 | 19.736 | 10.086 | -1.1% | 50.0% | -0.362 | null |
| Scarlet & Violet / chase | 122 | form1m | 28 | 96.214 | 19.243 | 13.198 | 0.5% | 46.4% | 0.141 | null |
| Scarlet & Violet / chase | 122 | form1m_skip1 | 27 | 95.259 | 19.052 | 14.127 | -0.3% | 37.0% | -0.111 | null |
| Scarlet & Violet / chase | 122 | form3m | 26 | 94.231 | 18.846 | 13.470 | -3.6% | 23.1% | -1.314 | null |
| Scarlet & Violet / chase | 122 | form3m_skip1 | 25 | 93.120 | 18.624 | 21.931 | -2.9% | 36.0% | -1.520 | null |
| Scarlet & Violet / chase | 122 | form6m | 23 | 90.609 | 18.122 | 5.315 | 3.5% | 52.2% | 0.689 | null |
| Scarlet & Violet / chase | 122 | form6m_skip1 | 22 | 89.182 | 17.836 | 5.103 | 7.1% | 63.6% | 1.297 | null |
| Sword & Shield / wider full-art | 104 | form1m | 28 | 104.000 | 20.800 | 28.000 | -6.0% | 25.0% | -4.063 | reversion |
| Sword & Shield / wider full-art | 104 | form1m_skip1 | 27 | 104.000 | 20.800 | 15.492 | -3.2% | 29.6% | -1.533 | null |
| Sword & Shield / wider full-art | 104 | form3m | 26 | 104.000 | 20.800 | 6.921 | -9.6% | 23.1% | -2.655 | reversion |
| Sword & Shield / wider full-art | 104 | form3m_skip1 | 25 | 104.000 | 20.800 | 8.010 | -6.9% | 28.0% | -3.009 | reversion |
| Sword & Shield / wider full-art | 104 | form6m | 23 | 104.000 | 20.800 | 7.855 | -8.9% | 17.4% | -2.859 | reversion |
| Sword & Shield / wider full-art | 104 | form6m_skip1 | 22 | 104.000 | 20.800 | 12.000 | -2.9% | 45.5% | -1.260 | null |
| Sword & Shield / chase | 59 | form1m | 28 | 59.000 | 11.800 | 23.738 | -2.9% | 28.6% | -2.767 | reversion |
| Sword & Shield / chase | 59 | form1m_skip1 | 27 | 59.000 | 11.800 | 9.761 | -6.4% | 14.8% | -2.195 | reversion |
| Sword & Shield / chase | 59 | form3m | 26 | 59.000 | 11.800 | 9.869 | -10.3% | 7.7% | -3.155 | reversion |
| Sword & Shield / chase | 59 | form3m_skip1 | 25 | 59.000 | 11.800 | 6.085 | -10.7% | 20.0% | -2.280 | reversion |
| Sword & Shield / chase | 59 | form6m | 23 | 59.000 | 11.800 | 5.668 | -8.3% | 13.0% | -2.300 | reversion |
| Sword & Shield / chase | 59 | form6m_skip1 | 22 | 59.000 | 11.800 | 9.382 | -3.4% | 36.4% | -1.433 | null |
| Mega Evolution / chase | 56 | form1m | 7 | 27.429 | 5.486 | 7.000 | 5.0% | 71.4% | 2.010 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / chase | 56 | form1m_skip1 | 6 | 25.500 | 5.100 | 6.000 | 7.2% | 66.7% | 1.451 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / chase | 56 | form3m | 5 | 23.800 | 4.760 | 1.000 | 6.5% | 60.0% | 0.453 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 56 | form3m_skip1 | 4 | 21.250 | 4.250 | 4.000 | 5.7% | 75.0% | 1.059 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / chase | 56 | form6m | 2 | 13.000 | 2.600 | 2.000 | 2.8% | 100.0% | 1.022 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 56 | form6m_skip1 | 1 | 13.000 | 2.600 | 1.000 | 5.1% | 100.0% | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / wider full-art | 37 | form1m | 9 | 18.778 | 3.756 | 9.000 | -0.0% | 33.3% | -0.001 | insufficient (leg<8) |
| Mega Evolution / wider full-art | 37 | form1m_skip1 | 8 | 17.500 | 3.500 | 8.000 | -3.0% | 37.5% | -0.634 | insufficient (leg<8) |
| Mega Evolution / wider full-art | 37 | form3m | 7 | 17.000 | 3.400 | 7.000 | -4.8% | 28.6% | -1.486 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form3m_skip1 | 6 | 16.333 | 3.267 | 6.000 | -1.4% | 33.3% | -0.282 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form6m | 4 | 14.000 | 2.800 | 4.000 | -2.6% | 50.0% | -0.625 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form6m_skip1 | 3 | 12.667 | 2.533 | 3.000 | -2.4% | 33.3% | -0.377 | insufficient (rebalances<8, n_eff<4, leg<8) |

### By raw printed rarity (ERA-CONFOUNDED -- read with care)

Rarity is nested inside era in this universe: "Rare Ultra", "Rare Secret" and
"Rare Rainbow" occur only in Sword & Shield, and "Hyper Rare" only in Scarlet &
Violet. A directional cell here therefore cannot be attributed to rarity rather
than to its era. Reported for completeness only.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Ultra Rare | 162 | form1m | 28 | 110.357 | 22.071 | 28.000 | -6.7% | 25.0% | -3.068 | reversion |
| Ultra Rare | 162 | form1m_skip1 | 27 | 108.741 | 21.748 | 27.000 | -0.5% | 44.4% | -0.309 | null |
| Ultra Rare | 162 | form3m | 26 | 107.308 | 21.462 | 10.183 | -6.7% | 26.9% | -1.809 | null |
| Ultra Rare | 162 | form3m_skip1 | 25 | 105.760 | 21.152 | 21.778 | 1.1% | 64.0% | 0.511 | null |
| Ultra Rare | 162 | form6m | 23 | 102.261 | 20.452 | 7.475 | -3.6% | 39.1% | -1.128 | null |
| Ultra Rare | 162 | form6m_skip1 | 22 | 100.409 | 20.082 | 10.600 | -0.6% | 50.0% | -0.222 | null |
| Special Illustration Rare | 136 | form1m | 28 | 75.179 | 15.036 | 9.483 | 4.3% | 53.6% | 1.019 | null |
| Special Illustration Rare | 136 | form1m_skip1 | 27 | 73.444 | 14.689 | 10.361 | 1.2% | 55.6% | 0.337 | null |
| Special Illustration Rare | 136 | form3m | 26 | 71.731 | 14.346 | 13.198 | -1.4% | 46.2% | -0.376 | null |
| Special Illustration Rare | 136 | form3m_skip1 | 25 | 69.880 | 13.976 | 20.438 | -3.0% | 44.0% | -1.117 | null |
| Special Illustration Rare | 136 | form6m | 23 | 66.043 | 13.209 | 6.423 | 1.5% | 56.5% | 0.316 | null |
| Special Illustration Rare | 136 | form6m_skip1 | 22 | 64.545 | 12.909 | 7.807 | 5.0% | 63.6% | 1.188 | null |
| Rare Ultra | 104 | form1m | 28 | 104.000 | 20.800 | 28.000 | -6.0% | 25.0% | -4.063 | reversion |
| Rare Ultra | 104 | form1m_skip1 | 27 | 104.000 | 20.800 | 15.492 | -3.2% | 29.6% | -1.533 | null |
| Rare Ultra | 104 | form3m | 26 | 104.000 | 20.800 | 6.921 | -9.6% | 23.1% | -2.655 | reversion |
| Rare Ultra | 104 | form3m_skip1 | 25 | 104.000 | 20.800 | 8.010 | -6.9% | 28.0% | -3.009 | reversion |
| Rare Ultra | 104 | form6m | 23 | 104.000 | 20.800 | 7.855 | -8.9% | 17.4% | -2.859 | reversion |
| Rare Ultra | 104 | form6m_skip1 | 22 | 104.000 | 20.800 | 12.000 | -2.9% | 45.5% | -1.260 | null |
| Rare Rainbow | 44 | form1m | 28 | 44.000 | 8.800 | 17.762 | -2.5% | 39.3% | -1.483 | null |
| Rare Rainbow | 44 | form1m_skip1 | 27 | 44.000 | 8.800 | 12.325 | -5.6% | 33.3% | -1.885 | null |
| Rare Rainbow | 44 | form3m | 26 | 44.000 | 8.800 | 8.064 | -9.2% | 19.2% | -2.182 | reversion |
| Rare Rainbow | 44 | form3m_skip1 | 25 | 44.000 | 8.800 | 6.509 | -9.8% | 24.0% | -1.971 | null |
| Rare Rainbow | 44 | form6m | 23 | 44.000 | 8.800 | 10.630 | -6.4% | 21.7% | -2.617 | reversion |
| Rare Rainbow | 44 | form6m_skip1 | 22 | 44.000 | 8.800 | 9.545 | -2.1% | 31.8% | -0.724 | null |
| Hyper Rare | 33 | form1m | 28 | 27.214 | 5.443 | 15.190 | -0.3% | 50.0% | -0.087 | insufficient (leg<8) |
| Hyper Rare | 33 | form1m_skip1 | 27 | 27.000 | 5.400 | 17.178 | 3.8% | 59.3% | 1.324 | insufficient (leg<8) |
| Hyper Rare | 33 | form3m | 26 | 26.769 | 5.354 | 14.096 | -3.8% | 38.5% | -1.296 | insufficient (leg<8) |
| Hyper Rare | 33 | form3m_skip1 | 25 | 26.520 | 5.304 | 18.286 | -0.8% | 40.0% | -0.348 | insufficient (leg<8) |
| Hyper Rare | 33 | form6m | 23 | 25.957 | 5.191 | 7.176 | -2.6% | 39.1% | -0.632 | insufficient (leg<8) |
| Hyper Rare | 33 | form6m_skip1 | 22 | 25.636 | 5.127 | 9.476 | 1.7% | 36.4% | 0.440 | insufficient (leg<8) |
| Rare Secret | 15 | form1m | 28 | 15.000 | 3.000 | 28.000 | -6.8% | 35.7% | -1.884 | insufficient (leg<8) |
| Rare Secret | 15 | form1m_skip1 | 27 | 15.000 | 3.000 | 27.000 | -9.3% | 37.0% | -3.271 | insufficient (leg<8) |
| Rare Secret | 15 | form3m | 26 | 15.000 | 3.000 | 24.094 | -14.5% | 15.4% | -4.917 | insufficient (leg<8) |
| Rare Secret | 15 | form3m_skip1 | 25 | 15.000 | 3.000 | 20.383 | -11.1% | 20.0% | -2.879 | insufficient (leg<8) |
| Rare Secret | 15 | form6m | 23 | 15.000 | 3.000 | 17.878 | -13.1% | 17.4% | -3.340 | insufficient (leg<8) |
| Rare Secret | 15 | form6m_skip1 | 22 | 15.000 | 3.000 | 19.355 | -4.2% | 40.9% | -1.081 | insufficient (leg<8) |
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
| within-era ranking | 503 | 1m | -5.1% | -5.111 | -3.7% | -3.918 | 0.724 | SURVIVES the shared-endpoint control |
| within-era ranking | 503 | 3m | -8.7% | -3.652 | -5.9% | -4.596 | 0.681 | SURVIVES the shared-endpoint control |
| Scarlet & Violet | 247 | 1m | -5.3% | -3.775 | -2.5% | -2.153 | 0.479 | SURVIVES the shared-endpoint control |
| Scarlet & Violet | 247 | 3m | -7.2% | -3.826 | -3.1% | -1.540 | 0.430 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield | 163 | 1m | -5.3% | -5.068 | -4.6% | -2.178 | 0.869 | SURVIVES the shared-endpoint control |
| Sword & Shield | 163 | 3m | -9.9% | -3.094 | -8.3% | -3.379 | 0.836 | SURVIVES the shared-endpoint control |
| Sword & Shield | 163 | 6m | -8.5% | -2.866 | -2.5% | -1.060 | 0.298 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| wider full-art | 266 | 1m | -4.6% | -2.386 | -1.7% | -1.550 | 0.380 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet / wider full-art | 125 | 1m | -8.9% | -4.714 | -2.5% | -1.674 | 0.284 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet / wider full-art | 125 | 3m | -8.9% | -2.807 | -0.7% | -0.263 | 0.079 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / wider full-art | 104 | 1m | -6.0% | -4.063 | -3.2% | -1.533 | 0.530 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / wider full-art | 104 | 3m | -9.6% | -2.655 | -6.9% | -3.009 | 0.719 | SURVIVES the shared-endpoint control |
| Sword & Shield / wider full-art | 104 | 6m | -8.9% | -2.859 | -2.9% | -1.260 | 0.331 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / chase | 59 | 1m | -2.9% | -2.767 | -6.4% | -2.195 | 2.193 | SURVIVES the shared-endpoint control |
| Sword & Shield / chase | 59 | 3m | -10.3% | -3.155 | -10.7% | -2.280 | 1.041 | SURVIVES the shared-endpoint control |
| Sword & Shield / chase | 59 | 6m | -8.3% | -2.300 | -3.4% | -1.433 | 0.413 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Ultra Rare | 162 | 1m | -6.7% | -3.068 | -0.5% | -0.309 | 0.080 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Ultra | 104 | 1m | -6.0% | -4.063 | -3.2% | -1.533 | 0.530 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Ultra | 104 | 3m | -9.6% | -2.655 | -6.9% | -3.009 | 0.719 | SURVIVES the shared-endpoint control |
| Rare Ultra | 104 | 6m | -8.9% | -2.859 | -2.9% | -1.260 | 0.331 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Rainbow | 44 | 3m | -9.2% | -2.182 | -9.8% | -1.971 | 1.069 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Rainbow | 44 | 6m | -6.4% | -2.617 | -2.1% | -0.724 | 0.334 | vanishes without P_T -- consistent with a shared-endpoint artifact |

## Honest stratified conclusion

THE POOLED NULL IS PARTLY A COMPOSITION ARTIFACT -- BUT WHAT SURVIVES IS NARROW AND POST-HOC. Every unstratified pooled horizon is null. Ranking the SAME 441 cards inside their own era and averaging the per-era spreads (the blocked estimator: identical universe, dates and n_eff machinery, only the ranking changes) is directional at form1m, form1m_skip1, form3m, form3m_skip1. form1m: pooled -2.5% (t -1.464, null) vs era-blocked -5.1% (t -5.111, reversion); form1m_skip1: pooled -1.7% (t -1.457, null) vs era-blocked -3.7% (t -3.918, reversion); form3m: pooled -6.4% (t -1.793, null) vs era-blocked -8.7% (t -3.652, reversion); form3m_skip1: pooled -4.1% (t -1.948, null) vs era-blocked -5.9% (t -4.596, reversion); form6m: pooled -3.2% (t -1.139, insufficient) vs era-blocked -5.3% (t -2.012, insufficient); form6m_skip1: pooled 1.6% (t 0.741, null) vs era-blocked 0.1% (t 0.034, null). So a large part of the pooled null was the pooled quintile sort ranking cards against a mixed-era field rather than against their own peers.

By era, reversion clears every sample-size gate in 2 of 3 eras (Scarlet & Violet, Sword & Shield): Scarlet & Violet @ form1m (-5.3%, t(n_eff) -3.775, 28 rebalances, n_eff 24.085, 247 cards); Scarlet & Violet @ form1m_skip1 (-2.5%, t(n_eff) -2.153, 27 rebalances, n_eff 25.043, 247 cards); Scarlet & Violet @ form3m (-7.2%, t(n_eff) -3.826, 26 rebalances, n_eff 14.290, 247 cards); Sword & Shield @ form1m (-5.3%, t(n_eff) -5.068, 28 rebalances, n_eff 28.000, 163 cards); Sword & Shield @ form1m_skip1 (-4.6%, t(n_eff) -2.178, 27 rebalances, n_eff 10.843, 163 cards); Sword & Shield @ form3m (-9.9%, t(n_eff) -3.094, 26 rebalances, n_eff 5.272, 163 cards); Sword & Shield @ form3m_skip1 (-8.3%, t(n_eff) -3.379, 25 rebalances, n_eff 6.926, 163 cards); Sword & Shield @ form6m (-8.5%, t(n_eff) -2.866, 23 rebalances, n_eff 5.335, 163 cards).

Beyond the era cut, 28 of the 114 stratum cells report reversion and 0 report momentum after gating. Those cells are NOT independent of each other -- the era x tier and raw-rarity cells are subsets of the same cards as the era cells (raw rarity is nested inside era here), so counting them as separate confirmations would double-count the same months and the same cards.

SHARED-ENDPOINT CONTROL -- the decisive filter. 10 of the 32 directional cells form on a window that never touches the price at T, so they are not explainable by measurement error in the single price that is shared between the formation and hold returns. At the era level that is: Scarlet & Violet @ form1m_skip1 (-2.5%, t(n_eff) -2.153, 27 rebalances, n_eff 25.043, 247 cards); Sword & Shield @ form1m_skip1 (-4.6%, t(n_eff) -2.178, 27 rebalances, n_eff 10.843, 163 cards); Sword & Shield @ form3m_skip1 (-8.3%, t(n_eff) -3.379, 25 rebalances, n_eff 6.926, 163 cards). Every other directional cell has P_T as both the closing endpoint of its formation return and the opening endpoint of its hold return, where any error in that one monthly price mechanically manufactures a negative, reversion-looking spread (Blume-Stambaugh / bid-ask bounce).

NO stratum at any horizon supports MOMENTUM, at any formation window, with or without the endpoint control. Nothing here resurrects a tradeable-momentum claim; there is none.

Caveats that apply to every cell above. (1) POST-HOC: this stratification was run AFTER the pooled result came back null. A subgroup effect found that way is a materially weaker claim than a pre-registered one, and it is the correct reading that this is a hypothesis about where to look next, not a measured effect. (2) NOT INDEPENDENT REPLICATIONS: every stratum is cut from ONE panel over ONE calendar window, so two strata agreeing mostly tells you they lived through the same months. (3) ERA-CONFOUNDED RARITY: the SWSH rarity strings occur only in SWSH and the SV ones only in SV/ME, so a raw-rarity cell cannot be attributed to rarity rather than era; only the era x tier cross can separate them. (4) MULTIPLICITY: 83 cells cleared the gates and were read for significance; some directional cells are expected by chance, and because the cells overlap heavily no clean multiplicity correction exists. (5) NO COSTS: nothing here is net of fees, spread or shipping, and the quintile legs reshuffle most of their membership every month.

BOTTOM LINE: there is still NO tradeable momentum. The reversion that appears inside strata is real in the data but post-hoc, cost-free, endpoint-sensitive, and concentrated in the slices flagged above -- it is reported because it is what the data says, not because it is actionable.

Per-(dimension, stratum, strategy) detail with every sample-size column:
momentum_strata.csv (same directory).


## Honest conclusion (pooled)

NULL RESULT. At no formation horizon is the top-minus-bottom quintile 3m spread distinguishable from zero once the overlapping-hold autocorrelation is accounted for (|t(n_eff)| < 2 everywhere). The data supports NEITHER a tradeable momentum nor a tradeable reversion effect in this cross-section -- consistent with the forward model's near-zero momentum-only IC.

Per-(strategy, side, rebalance) detail: momentum_results.csv (same directory).
Reversion rows are the algebraic mirror of the momentum rows (spread negated,
long/short legs swapped) and are NOT independent evidence.
