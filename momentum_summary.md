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

27 rebalance months (2024-04-01 .. 2026-06-01). Spread = winners - losers;
a positive, significant spread supports momentum, a negative one reversion.

| strategy | rebalances | n_eff | mean 3m spread | hit rate | IC autocorr | t (n_eff) | mean turnover | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| form1m | 27 | 13.253 | -2.9% | 37.0% | 0.342 | -1.817 | 80.9% | null |
| form3m | 25 | 5.094 | -6.4% | 16.0% | 0.661 | -1.738 | 50.4% | null |
| form6m | 22 | 3.213 | -2.7% | 22.7% | 0.745 | -0.962 | 38.2% | null |
| form6m_skip1 | 21 | 7.132 | 2.0% | 66.7% | 0.493 | 0.931 | 38.2% | null |

## Per-quintile monotonicity (pooled 3m hold return by formation quintile)

If momentum were real, the pooled mean hold return should rise monotonically from
Q1 (past losers) to Q5 (past winners); reversion would show the opposite ladder.
"Monotone steps" counts increasing adjacent pairs (out of 4); "rank
corr" is the correlation of quintile index with its pooled mean hold return
(+1 = perfect momentum ladder, -1 = perfect reversion ladder).

| strategy | Q1 (losers) | Q2 | Q3 | Q4 | Q5 (winners) | monotone steps | rank corr |
| --- | --- | --- | --- | --- | --- | --- | --- |
| form1m | 1.6% | 3.7% | 4.6% | 3.9% | -0.9% | 2/4 | -0.100 |
| form3m | 3.6% | 5.6% | 5.8% | 3.6% | -2.1% | 2/4 | -0.600 |
| form6m | 4.9% | 8.1% | 7.8% | 6.4% | 2.5% | 1/4 | -0.400 |
| form6m_skip1 | 3.8% | 6.8% | 8.3% | 6.8% | 5.9% | 2/4 | 0.300 |

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
independent data to distinguish anything. Of the 120 cells computed,
38 are graded insufficient.

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
| all cards | 491 | form1m | 27 | 373.667 | 74.733 | 13.253 | -2.9% | 37.0% | -1.817 | null |
| all cards | 491 | form1m_skip1 | 26 | 370.154 | 74.031 | 16.505 | -1.7% | 38.5% | -1.366 | null |
| all cards | 491 | form3m | 25 | 366.360 | 73.272 | 5.094 | -6.4% | 16.0% | -1.738 | null |
| all cards | 491 | form3m_skip1 | 24 | 362.250 | 72.450 | 11.436 | -3.9% | 16.7% | -1.794 | null |
| all cards | 491 | form6m | 22 | 354.409 | 70.882 | 3.213 | -2.7% | 22.7% | -0.962 | insufficient (n_eff<4) |
| all cards | 491 | form6m_skip1 | 21 | 350.286 | 70.057 | 7.132 | 2.0% | 66.7% | 0.931 | null |

_Era-blocked -- same cards, same dates, same n_eff machinery; only the RANKING
moves inside the era:_

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| within-era ranking | 491 | form1m | 27 | 373.667 | 74.733 | 21.159 | -5.4% | 7.4% | -5.607 | reversion |
| within-era ranking | 491 | form1m_skip1 | 26 | 370.154 | 74.031 | 18.101 | -3.7% | 19.2% | -3.607 | reversion |
| within-era ranking | 491 | form3m | 25 | 366.360 | 73.272 | 6.404 | -8.6% | 8.0% | -3.526 | reversion |
| within-era ranking | 491 | form3m_skip1 | 24 | 362.250 | 72.450 | 16.465 | -5.7% | 8.3% | -4.352 | reversion |
| within-era ranking | 491 | form6m | 22 | 354.409 | 70.882 | 3.742 | -5.0% | 18.2% | -1.885 | insufficient (n_eff<4) |
| within-era ranking | 491 | form6m_skip1 | 21 | 350.286 | 70.057 | 5.011 | 0.3% | 57.1% | 0.123 | null |

### By era (sets.series)

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Scarlet & Violet | 247 | form1m | 27 | 199.222 | 39.844 | 22.242 | -5.7% | 25.9% | -4.116 | reversion |
| Scarlet & Violet | 247 | form1m_skip1 | 26 | 197.385 | 39.477 | 23.524 | -2.3% | 42.3% | -1.848 | null |
| Scarlet & Violet | 247 | form3m | 25 | 195.400 | 39.080 | 13.665 | -7.3% | 20.0% | -3.704 | reversion |
| Scarlet & Violet | 247 | form3m_skip1 | 24 | 193.250 | 38.650 | 14.917 | -2.8% | 20.8% | -1.392 | null |
| Scarlet & Violet | 247 | form6m | 22 | 188.364 | 37.673 | 8.162 | -1.6% | 50.0% | -0.630 | null |
| Scarlet & Violet | 247 | form6m_skip1 | 21 | 185.571 | 37.114 | 6.212 | 3.1% | 66.7% | 0.965 | null |
| Sword & Shield | 163 | form1m | 27 | 163.000 | 32.600 | 27.000 | -5.2% | 14.8% | -4.824 | reversion |
| Sword & Shield | 163 | form1m_skip1 | 26 | 163.000 | 32.600 | 10.441 | -4.6% | 26.9% | -2.098 | reversion |
| Sword & Shield | 163 | form3m | 25 | 163.000 | 32.600 | 4.852 | -9.9% | 4.0% | -2.890 | reversion |
| Sword & Shield | 163 | form3m_skip1 | 24 | 163.000 | 32.600 | 6.532 | -8.3% | 4.2% | -3.208 | reversion |
| Sword & Shield | 163 | form6m | 22 | 163.000 | 32.600 | 5.021 | -8.5% | 9.1% | -2.704 | reversion |
| Sword & Shield | 163 | form6m_skip1 | 21 | 163.000 | 32.600 | 7.781 | -2.6% | 42.9% | -1.028 | null |
| Mega Evolution | 81 | form1m | 8 | 38.625 | 7.725 | 8.000 | -3.3% | 37.5% | -0.627 | insufficient (leg<8) |
| Mega Evolution | 81 | form1m_skip1 | 7 | 36.286 | 7.257 | 7.000 | 2.1% | 57.1% | 0.488 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 81 | form3m | 6 | 33.167 | 6.633 | 6.000 | -4.1% | 33.3% | -0.974 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 81 | form3m_skip1 | 5 | 28.800 | 5.760 | 5.000 | 0.1% | 40.0% | 0.022 | insufficient (rebalances<8, leg<8) |
| Mega Evolution | 81 | form6m | 3 | 22.333 | 4.467 | 3.000 | 0.2% | 66.7% | 0.079 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution | 81 | form6m_skip1 | 2 | 18.000 | 3.600 | 2.000 | -0.6% | 50.0% | -0.205 | insufficient (rebalances<8, n_eff<4, leg<8) |

### By rarity tier (crosses eras, so not era-confounded)

`chase` is the top slot in each era (Special Illustration Rare / Hyper Rare /
Mega Hyper Rare / Rare Secret / Rare Rainbow); `wider full-art` is Ultra Rare +
Rare Ultra. Both tiers draw from both eras.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| wider full-art | 266 | form1m | 27 | 213.000 | 42.600 | 15.633 | -5.0% | 25.9% | -2.554 | reversion |
| wider full-art | 266 | form1m_skip1 | 26 | 211.577 | 42.315 | 26.000 | -1.6% | 30.8% | -1.339 | null |
| wider full-art | 266 | form3m | 25 | 210.040 | 42.008 | 5.608 | -6.9% | 20.0% | -1.726 | null |
| wider full-art | 266 | form3m_skip1 | 24 | 208.375 | 41.675 | 10.568 | -2.0% | 45.8% | -0.748 | null |
| wider full-art | 266 | form6m | 22 | 204.727 | 40.945 | 4.747 | -4.9% | 31.8% | -1.276 | null |
| wider full-art | 266 | form6m_skip1 | 21 | 202.714 | 40.543 | 6.028 | 0.3% | 47.6% | 0.089 | null |
| chase | 225 | form1m | 27 | 160.667 | 32.133 | 11.941 | 1.2% | 51.9% | 0.504 | null |
| chase | 225 | form1m_skip1 | 26 | 158.577 | 31.715 | 13.165 | -1.8% | 46.2% | -0.897 | null |
| chase | 225 | form3m | 25 | 156.320 | 31.264 | 11.496 | -4.8% | 24.0% | -1.812 | null |
| chase | 225 | form3m_skip1 | 24 | 153.875 | 30.775 | 19.337 | -5.4% | 25.0% | -2.845 | reversion |
| chase | 225 | form6m | 22 | 149.682 | 29.936 | 6.592 | -0.2% | 50.0% | -0.075 | null |
| chase | 225 | form6m_skip1 | 21 | 147.571 | 29.514 | 7.191 | 3.6% | 71.4% | 1.434 | null |

### Era x rarity tier

The only cut that can separate an era effect from a rarity-tier effect, because
each era contributes both tiers.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Scarlet & Violet / wider full-art | 125 | form1m | 27 | 103.815 | 20.763 | 27.000 | -9.3% | 14.8% | -4.873 | reversion |
| Scarlet & Violet / wider full-art | 125 | form1m_skip1 | 26 | 103.000 | 20.600 | 26.000 | -2.6% | 38.5% | -1.630 | null |
| Scarlet & Violet / wider full-art | 125 | form3m | 25 | 102.120 | 20.424 | 14.637 | -8.8% | 20.0% | -2.806 | reversion |
| Scarlet & Violet / wider full-art | 125 | form3m_skip1 | 24 | 101.167 | 20.233 | 14.541 | -0.5% | 54.2% | -0.188 | null |
| Scarlet & Violet / wider full-art | 125 | form6m | 22 | 99.000 | 19.800 | 7.010 | -3.9% | 40.9% | -1.123 | null |
| Scarlet & Violet / wider full-art | 125 | form6m_skip1 | 21 | 97.762 | 19.552 | 10.965 | -0.3% | 52.4% | -0.108 | null |
| Scarlet & Violet / chase | 122 | form1m | 27 | 95.407 | 19.081 | 12.015 | 0.3% | 44.4% | 0.095 | null |
| Scarlet & Violet / chase | 122 | form1m_skip1 | 26 | 94.385 | 18.877 | 13.647 | 0.0% | 38.5% | 0.006 | null |
| Scarlet & Violet / chase | 122 | form3m | 25 | 93.280 | 18.656 | 13.192 | -3.6% | 20.0% | -1.271 | null |
| Scarlet & Violet / chase | 122 | form3m_skip1 | 24 | 92.083 | 18.417 | 21.232 | -2.7% | 37.5% | -1.372 | null |
| Scarlet & Violet / chase | 122 | form6m | 22 | 89.364 | 17.873 | 5.164 | 4.0% | 54.5% | 0.783 | null |
| Scarlet & Violet / chase | 122 | form6m_skip1 | 21 | 87.810 | 17.562 | 4.945 | 7.4% | 66.7% | 1.327 | null |
| Sword & Shield / wider full-art | 104 | form1m | 27 | 104.000 | 20.800 | 27.000 | -5.8% | 25.9% | -3.818 | reversion |
| Sword & Shield / wider full-art | 104 | form1m_skip1 | 26 | 104.000 | 20.800 | 15.119 | -3.0% | 30.8% | -1.395 | null |
| Sword & Shield / wider full-art | 104 | form3m | 25 | 104.000 | 20.800 | 6.348 | -9.3% | 24.0% | -2.444 | reversion |
| Sword & Shield / wider full-art | 104 | form3m_skip1 | 24 | 104.000 | 20.800 | 7.159 | -6.8% | 29.2% | -2.739 | reversion |
| Sword & Shield / wider full-art | 104 | form6m | 22 | 104.000 | 20.800 | 7.571 | -8.7% | 18.2% | -2.705 | reversion |
| Sword & Shield / wider full-art | 104 | form6m_skip1 | 21 | 104.000 | 20.800 | 11.306 | -2.8% | 47.6% | -1.156 | null |
| Sword & Shield / chase | 59 | form1m | 27 | 59.000 | 11.800 | 23.654 | -3.1% | 25.9% | -2.891 | reversion |
| Sword & Shield / chase | 59 | form1m_skip1 | 26 | 59.000 | 11.800 | 9.485 | -6.6% | 15.4% | -2.204 | reversion |
| Sword & Shield / chase | 59 | form3m | 25 | 59.000 | 11.800 | 9.963 | -10.6% | 8.0% | -3.259 | reversion |
| Sword & Shield / chase | 59 | form3m_skip1 | 24 | 59.000 | 11.800 | 5.852 | -11.0% | 20.8% | -2.269 | reversion |
| Sword & Shield / chase | 59 | form6m | 22 | 59.000 | 11.800 | 5.474 | -8.4% | 13.6% | -2.262 | reversion |
| Sword & Shield / chase | 59 | form6m_skip1 | 21 | 59.000 | 11.800 | 8.763 | -3.5% | 38.1% | -1.388 | null |
| Mega Evolution / chase | 44 | form1m | 6 | 25.500 | 5.100 | 2.361 | 3.3% | 66.7% | 0.968 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 44 | form1m_skip1 | 5 | 23.800 | 4.760 | 5.000 | 8.2% | 60.0% | 1.366 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / chase | 44 | form3m | 4 | 21.250 | 4.250 | 1.000 | 10.0% | 75.0% | 0.720 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 44 | form3m_skip1 | 3 | 17.000 | 3.400 | 3.000 | 9.0% | 100.0% | 1.485 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 44 | form6m | 1 | 13.000 | 2.600 | 1.000 | 0.1% | 100.0% | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / chase | 44 | form6m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / wider full-art | 37 | form1m | 8 | 17.500 | 3.500 | 8.000 | -6.0% | 25.0% | -1.118 | insufficient (leg<8) |
| Mega Evolution / wider full-art | 37 | form1m_skip1 | 7 | 17.000 | 3.400 | 7.000 | -2.4% | 42.9% | -0.441 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form3m | 6 | 16.333 | 3.267 | 6.000 | -5.7% | 16.7% | -1.572 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form3m_skip1 | 5 | 15.400 | 3.080 | 5.000 | -1.4% | 40.0% | -0.236 | insufficient (rebalances<8, leg<8) |
| Mega Evolution / wider full-art | 37 | form6m | 3 | 12.667 | 2.533 | 3.000 | -3.8% | 33.3% | -0.694 | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Evolution / wider full-art | 37 | form6m_skip1 | 2 | 10.000 | 2.000 | 2.000 | -0.5% | 50.0% | -0.045 | insufficient (rebalances<8, n_eff<4, leg<8) |

### By raw printed rarity (ERA-CONFOUNDED -- read with care)

Rarity is nested inside era in this universe: "Rare Ultra", "Rare Secret" and
"Rare Rainbow" occur only in Sword & Shield, and "Hyper Rare" only in Scarlet &
Violet. A directional cell here therefore cannot be attributed to rarity rather
than to its era. Reported for completeness only.

| stratum | cards | formation | rebalances | mean names/rebal | names per leg | n_eff | mean 3m spread | hit rate | t (n_eff) | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Ultra Rare | 162 | form1m | 27 | 109.000 | 21.800 | 27.000 | -7.4% | 22.2% | -3.550 | reversion |
| Ultra Rare | 162 | form1m_skip1 | 26 | 107.577 | 21.515 | 26.000 | -0.4% | 50.0% | -0.217 | null |
| Ultra Rare | 162 | form3m | 25 | 106.040 | 21.208 | 11.604 | -6.6% | 28.0% | -1.859 | null |
| Ultra Rare | 162 | form3m_skip1 | 24 | 104.375 | 20.875 | 22.193 | 1.2% | 62.5% | 0.594 | null |
| Ultra Rare | 162 | form6m | 22 | 100.727 | 20.145 | 7.280 | -2.8% | 40.9% | -0.877 | null |
| Ultra Rare | 162 | form6m_skip1 | 21 | 98.714 | 19.743 | 10.815 | 0.0% | 52.4% | 0.017 | null |
| Special Illustration Rare | 126 | form1m | 27 | 73.593 | 14.719 | 9.093 | 3.8% | 51.9% | 0.895 | null |
| Special Illustration Rare | 126 | form1m_skip1 | 26 | 71.885 | 14.377 | 9.889 | 1.0% | 53.8% | 0.269 | null |
| Special Illustration Rare | 126 | form3m | 25 | 70.040 | 14.008 | 12.693 | -1.5% | 44.0% | -0.387 | null |
| Special Illustration Rare | 126 | form3m_skip1 | 24 | 68.042 | 13.608 | 19.897 | -3.1% | 41.7% | -1.135 | null |
| Special Illustration Rare | 126 | form6m | 22 | 64.727 | 12.945 | 6.069 | 1.7% | 54.5% | 0.339 | null |
| Special Illustration Rare | 126 | form6m_skip1 | 21 | 63.095 | 12.619 | 7.530 | 5.1% | 61.9% | 1.166 | null |
| Rare Ultra | 104 | form1m | 27 | 104.000 | 20.800 | 27.000 | -5.8% | 25.9% | -3.818 | reversion |
| Rare Ultra | 104 | form1m_skip1 | 26 | 104.000 | 20.800 | 15.119 | -3.0% | 30.8% | -1.395 | null |
| Rare Ultra | 104 | form3m | 25 | 104.000 | 20.800 | 6.348 | -9.3% | 24.0% | -2.444 | reversion |
| Rare Ultra | 104 | form3m_skip1 | 24 | 104.000 | 20.800 | 7.159 | -6.8% | 29.2% | -2.739 | reversion |
| Rare Ultra | 104 | form6m | 22 | 104.000 | 20.800 | 7.571 | -8.7% | 18.2% | -2.705 | reversion |
| Rare Ultra | 104 | form6m_skip1 | 21 | 104.000 | 20.800 | 11.306 | -2.8% | 47.6% | -1.156 | null |
| Rare Rainbow | 44 | form1m | 27 | 44.000 | 8.800 | 18.677 | -2.7% | 37.0% | -1.664 | null |
| Rare Rainbow | 44 | form1m_skip1 | 26 | 44.000 | 8.800 | 11.961 | -5.9% | 30.8% | -1.931 | null |
| Rare Rainbow | 44 | form3m | 25 | 44.000 | 8.800 | 8.389 | -9.7% | 16.0% | -2.367 | reversion |
| Rare Rainbow | 44 | form3m_skip1 | 24 | 44.000 | 8.800 | 6.300 | -10.0% | 25.0% | -1.944 | null |
| Rare Rainbow | 44 | form6m | 22 | 44.000 | 8.800 | 11.603 | -6.8% | 18.2% | -2.948 | reversion |
| Rare Rainbow | 44 | form6m_skip1 | 21 | 44.000 | 8.800 | 9.132 | -2.2% | 33.3% | -0.717 | null |
| Hyper Rare | 33 | form1m | 27 | 27.000 | 5.400 | 14.575 | -0.4% | 48.1% | -0.105 | insufficient (leg<8) |
| Hyper Rare | 33 | form1m_skip1 | 26 | 26.769 | 5.354 | 18.831 | 4.6% | 61.5% | 1.771 | insufficient (leg<8) |
| Hyper Rare | 33 | form3m | 25 | 26.520 | 5.304 | 13.678 | -3.6% | 40.0% | -1.186 | insufficient (leg<8) |
| Hyper Rare | 33 | form3m_skip1 | 24 | 26.250 | 5.250 | 18.134 | -0.6% | 41.7% | -0.251 | insufficient (leg<8) |
| Hyper Rare | 33 | form6m | 22 | 25.636 | 5.127 | 7.028 | -2.3% | 40.9% | -0.545 | insufficient (leg<8) |
| Hyper Rare | 33 | form6m_skip1 | 21 | 25.286 | 5.057 | 9.041 | 2.1% | 38.1% | 0.523 | insufficient (leg<8) |
| Rare Secret | 15 | form1m | 27 | 15.000 | 3.000 | 27.000 | -6.8% | 37.0% | -1.801 | insufficient (leg<8) |
| Rare Secret | 15 | form1m_skip1 | 26 | 15.000 | 3.000 | 26.000 | -9.9% | 34.6% | -3.443 | insufficient (leg<8) |
| Rare Secret | 15 | form3m | 25 | 15.000 | 3.000 | 22.495 | -14.7% | 16.0% | -4.724 | insufficient (leg<8) |
| Rare Secret | 15 | form3m_skip1 | 24 | 15.000 | 3.000 | 19.719 | -10.9% | 20.8% | -2.740 | insufficient (leg<8) |
| Rare Secret | 15 | form6m | 22 | 15.000 | 3.000 | 16.874 | -13.0% | 18.2% | -3.164 | insufficient (leg<8) |
| Rare Secret | 15 | form6m_skip1 | 21 | 15.000 | 3.000 | 18.514 | -4.2% | 42.9% | -1.016 | insufficient (leg<8) |
| Mega Hyper Rare | 7 | form1m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form1m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form3m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form3m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form6m | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |
| Mega Hyper Rare | 7 | form6m_skip1 | 0 | n/a | n/a | 0.000 | n/a | n/a | n/a | insufficient (rebalances<8, n_eff<4, leg<8) |

### Shared-endpoint control, cell by cell

Only cells that clear the gates AND report a direction are listed -- they are the
only claims that need controlling.

| stratum | cards | horizon | base spread | base t(n_eff) | skip-1 spread | skip-1 t(n_eff) | abs ratio skip-1/base | reading |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| within-era ranking | 491 | 1m | -5.4% | -5.607 | -3.7% | -3.607 | 0.677 | SURVIVES the shared-endpoint control |
| within-era ranking | 491 | 3m | -8.6% | -3.526 | -5.7% | -4.352 | 0.666 | SURVIVES the shared-endpoint control |
| Scarlet & Violet | 247 | 1m | -5.7% | -4.116 | -2.3% | -1.848 | 0.408 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet | 247 | 3m | -7.3% | -3.704 | -2.8% | -1.392 | 0.390 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield | 163 | 1m | -5.2% | -4.824 | -4.6% | -2.098 | 0.884 | SURVIVES the shared-endpoint control |
| Sword & Shield | 163 | 3m | -9.9% | -2.890 | -8.3% | -3.208 | 0.841 | SURVIVES the shared-endpoint control |
| Sword & Shield | 163 | 6m | -8.5% | -2.704 | -2.6% | -1.028 | 0.304 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| wider full-art | 266 | 1m | -5.0% | -2.554 | -1.6% | -1.339 | 0.314 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet / wider full-art | 125 | 1m | -9.3% | -4.873 | -2.6% | -1.630 | 0.278 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Scarlet & Violet / wider full-art | 125 | 3m | -8.8% | -2.806 | -0.5% | -0.188 | 0.059 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / wider full-art | 104 | 1m | -5.8% | -3.818 | -3.0% | -1.395 | 0.510 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / wider full-art | 104 | 3m | -9.3% | -2.444 | -6.8% | -2.739 | 0.726 | SURVIVES the shared-endpoint control |
| Sword & Shield / wider full-art | 104 | 6m | -8.7% | -2.705 | -2.8% | -1.156 | 0.325 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Sword & Shield / chase | 59 | 1m | -3.1% | -2.891 | -6.6% | -2.204 | 2.149 | SURVIVES the shared-endpoint control |
| Sword & Shield / chase | 59 | 3m | -10.6% | -3.259 | -11.0% | -2.269 | 1.036 | SURVIVES the shared-endpoint control |
| Sword & Shield / chase | 59 | 6m | -8.4% | -2.262 | -3.5% | -1.388 | 0.415 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Ultra Rare | 162 | 1m | -7.4% | -3.550 | -0.4% | -0.217 | 0.052 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Ultra | 104 | 1m | -5.8% | -3.818 | -3.0% | -1.395 | 0.510 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Ultra | 104 | 3m | -9.3% | -2.444 | -6.8% | -2.739 | 0.726 | SURVIVES the shared-endpoint control |
| Rare Ultra | 104 | 6m | -8.7% | -2.705 | -2.8% | -1.156 | 0.325 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Rainbow | 44 | 3m | -9.7% | -2.367 | -10.0% | -1.944 | 1.032 | vanishes without P_T -- consistent with a shared-endpoint artifact |
| Rare Rainbow | 44 | 6m | -6.8% | -2.948 | -2.2% | -0.717 | 0.324 | vanishes without P_T -- consistent with a shared-endpoint artifact |

## Honest stratified conclusion

THE POOLED NULL IS PARTLY A COMPOSITION ARTIFACT -- BUT WHAT SURVIVES IS NARROW AND POST-HOC. Every unstratified pooled horizon is null. Ranking the SAME 441 cards inside their own era and averaging the per-era spreads (the blocked estimator: identical universe, dates and n_eff machinery, only the ranking changes) is directional at form1m, form1m_skip1, form3m, form3m_skip1. form1m: pooled -2.9% (t -1.817, null) vs era-blocked -5.4% (t -5.607, reversion); form1m_skip1: pooled -1.7% (t -1.366, null) vs era-blocked -3.7% (t -3.607, reversion); form3m: pooled -6.4% (t -1.738, null) vs era-blocked -8.6% (t -3.526, reversion); form3m_skip1: pooled -3.9% (t -1.794, null) vs era-blocked -5.7% (t -4.352, reversion); form6m: pooled -2.7% (t -0.962, insufficient) vs era-blocked -5.0% (t -1.885, insufficient); form6m_skip1: pooled 2.0% (t 0.931, null) vs era-blocked 0.3% (t 0.123, null). So a large part of the pooled null was the pooled quintile sort ranking cards against a mixed-era field rather than against their own peers.

By era, reversion clears every sample-size gate in 2 of 3 eras (Scarlet & Violet, Sword & Shield): Scarlet & Violet @ form1m (-5.7%, t(n_eff) -4.116, 27 rebalances, n_eff 22.242, 247 cards); Scarlet & Violet @ form3m (-7.3%, t(n_eff) -3.704, 25 rebalances, n_eff 13.665, 247 cards); Sword & Shield @ form1m (-5.2%, t(n_eff) -4.824, 27 rebalances, n_eff 27.000, 163 cards); Sword & Shield @ form1m_skip1 (-4.6%, t(n_eff) -2.098, 26 rebalances, n_eff 10.441, 163 cards); Sword & Shield @ form3m (-9.9%, t(n_eff) -2.890, 25 rebalances, n_eff 4.852, 163 cards); Sword & Shield @ form3m_skip1 (-8.3%, t(n_eff) -3.208, 24 rebalances, n_eff 6.532, 163 cards); Sword & Shield @ form6m (-8.5%, t(n_eff) -2.704, 22 rebalances, n_eff 5.021, 163 cards).

No claim is made for Mega Evolution: every horizon there fails a sample-size gate (too few rebalance months, too little effective sample after the overlap deflation, or too few names per quintile leg). A thin slice is not weak evidence, it is no evidence.

Beyond the era cut, 27 of the 108 stratum cells report reversion and 0 report momentum after gating. Those cells are NOT independent of each other -- the era x tier and raw-rarity cells are subsets of the same cards as the era cells (raw rarity is nested inside era here), so counting them as separate confirmations would double-count the same months and the same cards.

SHARED-ENDPOINT CONTROL -- the decisive filter. 9 of the 31 directional cells form on a window that never touches the price at T, so they are not explainable by measurement error in the single price that is shared between the formation and hold returns. At the era level that is: Sword & Shield @ form1m_skip1 (-4.6%, t(n_eff) -2.098, 26 rebalances, n_eff 10.441, 163 cards); Sword & Shield @ form3m_skip1 (-8.3%, t(n_eff) -3.208, 24 rebalances, n_eff 6.532, 163 cards). Every other directional cell has P_T as both the closing endpoint of its formation return and the opening endpoint of its hold return, where any error in that one monthly price mechanically manufactures a negative, reversion-looking spread (Blume-Stambaugh / bid-ask bounce).

NO stratum at any horizon supports MOMENTUM, at any formation window, with or without the endpoint control. Nothing here resurrects a tradeable-momentum claim; there is none.

Caveats that apply to every cell above. (1) POST-HOC: this stratification was run AFTER the pooled result came back null. A subgroup effect found that way is a materially weaker claim than a pre-registered one, and it is the correct reading that this is a hypothesis about where to look next, not a measured effect. (2) NOT INDEPENDENT REPLICATIONS: every stratum is cut from ONE panel over ONE calendar window, so two strata agreeing mostly tells you they lived through the same months. (3) ERA-CONFOUNDED RARITY: the SWSH rarity strings occur only in SWSH and the SV ones only in SV/ME, so a raw-rarity cell cannot be attributed to rarity rather than era; only the era x tier cross can separate them. (4) MULTIPLICITY: 82 cells cleared the gates and were read for significance; some directional cells are expected by chance, and because the cells overlap heavily no clean multiplicity correction exists. (5) NO COSTS: nothing here is net of fees, spread or shipping, and the quintile legs reshuffle most of their membership every month.

BOTTOM LINE: there is still NO tradeable momentum. The reversion that appears inside strata is real in the data but post-hoc, cost-free, endpoint-sensitive, and concentrated in the slices flagged above -- it is reported because it is what the data says, not because it is actionable.

Per-(dimension, stratum, strategy) detail with every sample-size column:
momentum_strata.csv (same directory).


## Honest conclusion (pooled)

NULL RESULT. At no formation horizon is the top-minus-bottom quintile 3m spread distinguishable from zero once the overlapping-hold autocorrelation is accounted for (|t(n_eff)| < 2 everywhere). The data supports NEITHER a tradeable momentum nor a tradeable reversion effect in this cross-section -- consistent with the forward model's near-zero momentum-only IC.

Per-(strategy, side, rebalance) detail: momentum_results.csv (same directory).
Reversion rows are the algebraic mirror of the momentum rows (spread negated,
long/short legs swapped) and are NOT independent evidence.
