# Are Elite Trainer Boxes going up, and is one worth holding?

The canonical ETB artifact. Everything below is computed live from
`price_history` and `data/output/etb_panel.csv` at write time -- no figure in
this document is typed by hand, and the per-product table behind every average
is published beside it as `data/output/etb_products.csv`.

Window **2024-03 .. 2026-10** (32 monthly observations, ONE regime) | **111 ETB
products** across **62 sets** | 2,831 product-months | headline index
**70.3%/yr**, HAC 95% CI [28.8%, 125.2%]

*This is measurement, not investment advice. Nothing here recommends buying,
holding or selling anything.*

---

## 1. The bottom line

**Yes, ETB prices went up a lot over 2024-03 .. 2026-10 -- about 70.3% a year,
an index multiple of 3.96x in 2.6 years. Four things immediately qualify that,
and each one is measured below rather than asserted.**

1. **The number is a construction choice.** Across the 15 defensible ways to
   build this index the answer spans 70.3% to 89.2%/yr -- a 18.9-point range.
   The headline above is the chained/geometric index over every product because
   that is the construction that admits the 43 products which entered
   mid-window. The higher numbers you will see quoted elsewhere -- including
   81.2%/yr -- come from a fixed basket that, by construction, can only contain
   products that already existed at the start AND survived to the end (section
   2.2).
2. **ETBs were not shown to beat the rest of sealed.** Against booster boxes
   over the same window with the same construction: +7.0pp/yr (t = 0.80).
   Against singles: +21.1pp/yr (t = 1.50). This repo's bar is |t| >= 2. "ETBs
   went up" is largely "the Pokemon market went up" (section 2.4).
3. **Older product has the higher point estimates, but none of the AGE contrasts
   is established.** Of 2 contrasts against the youngest on-sale cohort, none
   clears this repo's significance bar. Product 1-3 years past release grew
   84.1%/yr against 64.2%/yr for boxes under a year old and on sale (t = 1.28);
   the 3y+ cohort grew 66.9%/yr (t = 0.08), BELOW the 1-3y figure, so the
   monotone "older is better" reading is not supported either (section 4.4). An
   earlier version of this report pooled pre-release entrants into the youngest
   cohort and concluded the 1-3y contrast WAS established; section 7.4 records
   that correction. The launch-side evidence is separate, and it is a RELATIVE
   statement: from the first price at which a box could actually be bought the
   launch cohort's average path dips to 0.92x and is at 1.56x a year on, but
   only 0.78x of what the rest of the ETB market did over the same months -- the
   new box went up and the category went up more (section 4.3). **That is a
   statement about growth RATES, and it is not the answer to "older ETBs sell at
   higher prices, no?".** That question is about price LEVELS, it is a different
   quantity, and section 4.6 answers it -- **yes**: at 2026-10 mass-retail price
   rises with age at Spearman rho = 0.721 (p = 4.1e-12, n = 68), a median $114
   at <1yr (n = 6) against $806 at 8yr+ (n = 14). Two disclosures travel with it
   and are quoted in full in 4.6: within one calendar month age and release
   cohort are the SAME variable (R^2 = 1.000), so that rho ranks VINTAGES and
   cannot be read as an ageing curve; and only 56.0% of the same-era catalogue
   behind the oldest band is still priced at all, which puts that band's level
   somewhere in [$325.30, $1,800.00] rather than at its survivor median of
   $806.47 -- the bound is printed to the cent because rounding a
   distribution-free interval inwards makes it look tighter than it is. A level
   gradient is not a forecast: 4.6 publishes none.
4. **A holder does not keep the index.** Sales tax in, marketplace take out and
   shipping cost roughly 20.2% of the box plus $12.30 -- charged ONCE, which is
   why the answer is about time. At the measured growth rate a 3-month hold nets
   -42.8%/yr, a 12-month hold 32.1%/yr and a 24-month hold 51.3%/yr. In the
   realised data a 3-month flip lost money 80% of the time *during a boom*
   (section 6).

**So, is an ETB worth holding to sell later?** Stated as what this archive
measured rather than as advice: over this window a hold paid only when it ran
longer than 7 months (the point at which the one-time frictions amortise, at the
growth rate this window delivered), the box was retired rather than newly
released, and the market kept rising. That last condition did almost all of the
work and this data cannot speak to whether it repeats: the archive contains 32
months of a single boom whose deepest index drawdown was -2.7%. A fall of 50.8%
from here would erase the entire two-year edge over a savings account, and if
prices merely go FLAT a 12-month hold returns 0.75x -- a real loss, because the
frictions are charged anyway.

Two further answers, both negative, both worth having: the appreciation **cannot
be attributed to ageing** (age is collinear with calendar time by construction
here -- section 4.1), and **which** ETB will outperform **cannot be predicted**
at any horizon this archive can honestly test (section 5).

## 2. Did ETB prices go up?

### 2.1 The headline index

Chained, geometric, all products: base 100 at 2024-03 -> **395.9** at 2026-10,
i.e. **70.3%/yr**, HAC 95% CI [28.8%, 125.2%], t = 3.74 on 31 monthly log
returns with 3 Newey-West lags.

The standard error matters here. Monthly price levels in a boom are massively
autocorrelated, so an OLS standard error on a price trend is fiction; every
interval in this document is estimated on the mean monthly LOG RETURN with a HAC
covariance, which telescopes to exactly the endpoint growth rate but carries an
error bar that knows the months are not independent.

The median ETB was $66.75 in 2024-03 and $203.55 in 2026-10.

### 2.2 The headline moves a lot -- so the construction is the finding

| link | aggregator | survivorship | products | index end | CAGR | 95% lo | 95% hi |
| --- | --- | --- | --- | --- | --- | --- | --- |
| constant | geometric | all | 58 | 464.3 | 81.2%/yr | 36.0% | 141.4% |
| constant | arithmetic | all | 58 | 505.4 | 87.2%/yr | 36.0% | 157.8% |
| constant | value | all | 58 | 519.2 | 89.2%/yr | 45.1% | 146.7% |
| chained | geometric | all | 111 | 395.9 | 70.3%/yr | 28.8% | 125.2% |
| chained | arithmetic | all | 111 | 437.6 | 77.1%/yr | 32.9% | 136.0% |
| chained | value | all | 111 | 457.4 | 80.1%/yr | 40.5% | 130.9% |
| constant | geometric | exclude_delisted | 58 | 464.3 | 81.2%/yr | 36.0% | 141.4% |
| constant | arithmetic | exclude_delisted | 58 | 505.4 | 87.2%/yr | 36.0% | 157.8% |
| constant | value | exclude_delisted | 58 | 519.2 | 89.2%/yr | 45.1% | 146.7% |
| chained | geometric | exclude_delisted | 105 | 396.6 | 70.5%/yr | 28.1% | 126.9% |
| chained | arithmetic | exclude_delisted | 105 | 437.1 | 77.0%/yr | 32.0% | 137.3% |
| chained | value | exclude_delisted | 105 | 454.7 | 79.7%/yr | 39.6% | 131.4% |
| chained | geometric | full_history_only | 58 | 464.3 | 81.2%/yr | 36.0% | 141.4% |
| chained | arithmetic | full_history_only | 58 | 501.5 | 86.7%/yr | 39.1% | 150.6% |
| chained | value | full_history_only | 58 | 519.2 | 89.2%/yr | 45.1% | 146.7% |

Range: **70.3% to 89.2%/yr, 18.9 points apart**, median 81.2%. That spread is
not noise -- every cell is a defensible index -- so a single headline quoted
without its construction is unfalsifiable.

**Where the gap comes from, isolated cleanly:**

| construction | membership | products | CAGR |
| --- | --- | --- | --- |
| constant basket, geometric | full-history only (forced by construction) | 58 | 81.2%/yr |
| chained, geometric | full-history only (imposed) | 58 | 81.2%/yr |
| chained, geometric | every product (headline) | 111 | 70.3%/yr |

Rows 1 and 2 differ **only** by the linking method and they agree to 0.0e+00
percentage points, which is zero to machine precision -- on a balanced panel a
chained Jevons index equals the direct one exactly, and
`tests/test_etb_index.py` pins that identity. So the 10.8-point drop from row 2
to row 3 is **entirely** the 43 late-entering products, which compounded far
more slowly than the cohort that was already being priced in 2024-03.

That is a finding about the market, not a defect: a fixed basket cannot contain
a product that did not exist yet, so the high number is a survivor-cohort
number. It is also worth stating plainly that **the constant basket is identical
under the "all" and "exclude delisted" survivorship rules** -- it cannot measure
survivorship at all, because it has already excluded every non-survivor.

### 2.3 Robustness: does the result depend on how it was measured?

**The uncleaned universe.** A one-line `name LIKE '%elite trainer%'` query
returns 115 priced products, of which 62 span the window; its constant basket
grows 80.2%/yr and its chained index 70.0%/yr. The curated universe (which drops
multi-unit cases, "[Set of 2]" SKUs, code cards and the larger ETB Plus -- see
3.1) gives 81.2% and 70.3%: the cleaning moved the constant basket by +1.0pp and
the chained index by +0.3pp. **So the universe definition is not where the
headline comes from** -- which rules out the first thing a sceptic should check.

**A different price field.** Rebuilding on the cheapest live ask instead of the
trailing sales average:

| field | what it is | products | CAGR |
| --- | --- | --- | --- |
| `market` | TCGplayer market (trailing sales average) -- headline | 111 | 70.3%/yr |
| `low` | cheapest live ask | 111 | 77.6%/yr |

Same sign, same order of magnitude.

**Sub-periods.** The growth is not one early spike -- every sub-period below
rose:

| period | from | to | total | annualised |
| --- | --- | --- | --- | --- |
| full window | 2024-03 | 2026-10 | 295.9% | 70.3%/yr |
| first half | 2024-03 | 2025-07 | 118.2% | 79.5%/yr |
| second half | 2025-07 | 2026-10 | 81.4% | 61.1%/yr |
| trailing 12m | 2025-10 | 2026-10 | 36.4% | 36.4%/yr |
| trailing 6m | 2026-04 | 2026-10 | 14.0% | 30.0%/yr |

**Drawdown.** Worst peak-to-trough fall in the whole archive: **-2.7%** (2026-07
-> 2026-10), with 6 negative months out of 31 and a worst single month of -1.5%.
Read that as a warning, not comfort: an index that has never fallen more than
2.7% has not been tested.

**A second pipeline.** The pre-aggregated `sealed_index` table builds an ETB
series independently, at set level:

| source | unit | units | constant basket | chained | sets of this panel covered | share of panel sets |
| --- | --- | --- | --- | --- | --- | --- |
| price_history (this module) | product | 111 | 81.2%/yr | 70.3%/yr | 62 | 100% |
| sealed_index (pre-aggregated) | set | 62 | 77.9%/yr | 69.4%/yr | 62 | 100% |

They agree to 0.9 points on the chained index. The remaining difference is
composition -- one is 62 sets, the other 111 products -- not a pipeline defect.

**But do not read that agreement as a check on the whole index.** `sealed_index`
only carries a set-month when an ETB was actually priced there; it covers 62 of
this panel's 62 sets (100%). So the one available second pipeline remains
structurally partial, and quoting the agreement without this coverage share
would overstate how much of the index has actually been corroborated (section
2.6).

**Channel.** The largest arguable universe call is whether Pokemon Center
exclusives belong in an "ETB" index at all. Both are kept, with a flag, so it
can be re-run either way:

| channel | products | CAGR | 95% lo | 95% hi |
| --- | --- | --- | --- | --- |
| Pokemon Center exclusive | 37 | 71.1%/yr | 11.9% | 161.8% |
| Mass-retail | 74 | 70.9%/yr | 36.0% | 114.8% |

### 2.4 Against the rest of the market

Same window, same construction, and the difference is estimated on the PAIRED
monthly return difference so the common market tide cancels before the standard
error is formed. This is the decision-relevant statistic: not "did ETBs go up"
but "did ETBs beat the alternative".

| benchmark | units | its CAGR | ETB edge | t (HAC, paired) | clears \|t\| >= 2 |
| --- | --- | --- | --- | --- | --- |
| `booster_box` | 54 | 59.2%/yr | +7.0pp | 0.80 | no |
| `booster_bundle` | 27 | 62.5%/yr | +4.8pp | 0.55 | no |
| `singles` | 9,317 | 40.7%/yr | +21.1pp | 1.50 | no |

**Not one benchmark difference clears the bar** -- booster_box +7.0pp/yr at t =
0.80; booster_bundle +4.8pp/yr at t = 0.55; singles +21.1pp/yr at t = 1.50 -- so
ETBs are statistically indistinguishable from each of them over this window,
whatever the sign of the point estimate. The singles benchmark also deserves a
caveat in the other direction: it is an equal-weighted index of 9,317 cards
above a $1 floor, so it is dominated by cheap commons and probably understates
what a comparable singles portfolio did.

### 2.5 Dispersion -- what the average hides

Per-product growth, over the 97 products with enough history to annualise: p10
33.0%/yr, median 68.7%/yr, p90 116.2%/yr -- an interquartile range of 35 points.
2% of them went DOWN, and 70% have growth that clears |t| >= 2 on their own
error bar. The full table is section 7.3 and `etb_products.csv`.

### 2.6 The products are not independent observations

Every count above is a count of SKUs, and SKUs cluster inside sets: one release
can ship a regular box, a Pokemon Center box and two artwork variants, four
listings whose prices move together because they are the same cardboard. This
panel's 111 products are only 62 release events -- 1.79 SKUs per set. **Read "N
of 111 products rose" as at most 62 independent confirmations, not 111.** Any
cross-sectional share or count in this document -- including the 2-sigma count
just above -- inherits that inflation.

Re-running the index with ONE observation per set (the geometric mean of that
set's SKUs, so collapsing commutes with the geometric aggregator) is the
robustness cut:

| unit of observation | units | full-history units | of which rose | chained index | constant basket | worst full-history unit |
| --- | --- | --- | --- | --- | --- | --- |
| SKU (product) | 111 | 58 | 58 | 70.3%/yr | 81.2%/yr | 30.8%/yr |
| set (release event) | 62 | 34 | 34 | 70.4%/yr | 78.4%/yr | 30.8%/yr |

The index level barely moves (+0.0pp on the chained construction), so the
equal-weight-by-SKU choice is not what produced the headline. The floor does not
move either: the worst single SKU and the worst whole SET both grew 30.8%/yr --
the weakest release's SKUs moved together. Both are true; the SKU figure is the
honest answer to "what is the worst thing I could have bought" and the set
figure to "how many distinct releases went up". Every one of the 34 full-history
SETS rose, which is the version of "all of them rose" that survives clustering.

### 2.7 Is it still going, and is it ETBs?

Section 2.1 measures the whole window. A reader who wants to act on it is asking
something narrower -- *is this still true now* -- so the same index is re-read
on its trailing 12 months (2025-10 to 2026-10) and the benchmark null from 2.4
is re-run inside that sub-window.

**Still going, and not detectably slower.** The trailing 12 months compound at
36.4%/yr [-5.9%, 97.9%] against 70.3%/yr over the full window -- the same number
within its interval. Tested directly rather than eyeballed, a last-12-months
dummy on monthly log returns (Newey-West, 3 lags) gives -3.0pp/month, t = -1.31,
p = 0.19: **no detectable change in pace**. Read that as ruling out a collapse
and nothing more -- its standard error is 2.31pp/month against a mean of about
4.5pp, so it could only have caught roughly a halving. 6 of the archive's months
were negative and the worst drawdown inside the recent window was -2.7%.

**It is broad, not a handful of boxes.** 79 of 91 products priced at both ends
rose (87%), median 1.38x, and even the 10th percentile is 0.99x. Concentration
is mild: the top decile of movers carries 22% of the summed log rise, 2.22x its
even share. But breadth is narrowing -- on a cohort held fixed across both
halves, the share rising went 100% to 95%.

The 12 products that fell are named rather than averaged away: Mega Evolution
Pokemon Center Elite Trainer Box (Exclusive) [Mega Lucario] (0.76x); Temporal
Forces Pokemon Center Elite Trainer Box (Exclusive) [Walking Wake] (0.82x); Mega
Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Gardevoir] (0.84x);
Scarlet & Violet Pokemon Center Elite Trainer Box (Exclusive) [Koraidon]
(0.86x), and 8 more. Check release dates before reading that as a category
signal -- a box still inside its launch window is showing the cooldown measured
in section 4.3, not a market turn.

**Still not an ETB story.** The benchmark comparison from 2.4, recomputed inside
the recent window:

| window | vs | ETBs | them | gap | lo | hi | t | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| trailing 12m | Booster boxes | 36.4%/yr | 16.6%/yr | +17.0pp | -13.6pp | +58.5pp | 1.02 | no detectable difference |
| trailing 12m | Booster bundles | 36.4%/yr | 50.4%/yr | -9.3pp | -18.3pp | +0.7pp | -1.82 | no detectable difference |
| trailing 12m | Singles | 36.4%/yr | 67.6%/yr | -18.6pp | -34.2pp | +0.6pp | -1.90 | no detectable difference |
| full window (31m) | Booster boxes | 70.3%/yr | 59.2%/yr | +7.0pp | -9.3pp | +26.2pp | 0.80 | no detectable difference |
| full window (31m) | Booster bundles | 70.3%/yr | 62.5%/yr | +4.8pp | -11.3pp | +23.9pp | 0.55 | no detectable difference |
| full window (31m) | Singles | 70.3%/yr | 40.7%/yr | +21.1pp | -5.7pp | +55.3pp | 1.50 | no detectable difference |

0 of 6 judgeable comparisons differ from ETBs. The full-window null from section
2.4 therefore survives into the recent sub-window unchanged: **the recent rise
is a Pokemon-market rise, not an ETB one.** These are low-power nulls -- the
trailing-12-month intervals run roughly -13.6pp to +58.5pp -- so the honest
claim is "cannot be distinguished", not "they are the same".

9 shorter-window comparisons are computed and printed in
`etb_recent_benchmarks.csv` but excluded from every verdict above, because an
interval built on a handful of monthly observations is not one. That gate is
load-bearing rather than decorative: the most extreme of those excluded rows is
trailing 3m ETBs vs singles at t = -10.70 on 3 monthly returns, and quoting it
would have published a significant result off a window whose sign does not
survive to twelve months.

**The one split that does show a gap is channel, and it is the weakest inference
here.** Mass-retail boxes ran 1.54x against 1.08x for Pokemon Center exclusives
(42.4%, t = 9.05). Differencing two groups cancels the market-wide factor but
NOT a channel-specific one -- a Pokemon Center release calendar or a restock
decision leaves the within-channel residuals correlated -- so that t is an upper
bound on the evidence, not a clean test. Age bands are monotone in the recent
rise (`etb_recent_drivers_*.csv`).

## 3. Is that real? What the data can and cannot support

### 3.0 The headline, recomputed by a second implementation

Every figure in section 2 flows through one panel builder and one index
function, so unit tests on those functions cannot tell a reader whether the
number is a property of the market or of the code. `pokestat/model/etb_audit.py`
therefore recomputes the fixed-basket headline from `price_history` with its own
SQL, its own name matching, plain Python `math` instead of a pandas pivot, and
its longhand annualisation -- importing nothing from `etb_core` or `etb_index`
(a test enforces the non-import).

| | pipeline | independent rebuild |
|---|---|---|
| constant-basket geometric CAGR | 81.2%/yr | 81.2%/yr |
| full-history basket | -- | 58 products |
| of which rose | -- | 58 |
| worst / median member | -- | 30.8%/yr / 74.7%/yr |

The two **agree** to +0.0pp (tolerance +0.5pp). That is a check on the
ARITHMETIC only -- both sides compute the same defined quantity on the same
rows, so agreement rules out a join, pivot or double-counting bug and rules out
nothing about whether a fixed basket is the right object (it is not; see 2.2).
The construction spread in section 2.2 is the methodological check, this is the
implementation one.

### 3.1 What counts as an ETB, and what was thrown out

The universe is a set of tested rules, not a magic string, and the rule ORDER
matters (a "Code Card - ... Elite Trainer Box" is excluded as a code card before
anything else looks at it). Published verbatim so it is checkable:

| rule | catalogue rows | priced products | example |
| --- | --- | --- | --- |
| `INCLUDED` | 121 | 111 | Celebrations Elite Trainer Box |
| `NOT_A_BOX` | 115 | 0 | Code Card - Celebrations Elite Trainer Box |
| `MULTI_UNIT` | 80 | 0 | Celebrations Elite Trainer Box Case |
| `MIXED_LOT` | 3 | 0 | Costco Pokemon Evolving Skies Elite Trainer Box and Tin |
| `ETB_PLUS` | 4 | 4 | Pokemon GO Pokemon Center Elite Trainer Box Plus (Exclusive) |

The exclusions that actually cost priced products are the multi-unit SKUs (cases
and "[Set of 2]" listings, whose price level is not one box) and ETB Plus (a
physically different, larger product). Section 2.3 shows that putting them back
RAISES the naive headline rather than lowering it, so this cleaning is not what
produced the result.

### 3.2 Coverage, stated as a weakness

111 products x 32 months would be 3,552 observations; the panel has 2,831. The
shortfall is entirely structural. The obvious two-way framing -- "either it
started late or it was delisted" -- is wrong twice over here, so the split below
is mutually exclusive and exhaustive by construction and the code raises if the
buckets stop summing to 111:

| coverage shape | products | share | what it is |
| --- | --- | --- | --- |
| complete | 58 | 52% | priced in every month of the grid |
| late start only | 41 | 37% | a newer release; enters mid-window and never leaves |
| delisted only | 4 | 4% | priced from the start, then stops being listed |
| late start and delisted | 2 | 2% | enters mid-window AND stops before the end |
| interior gap only | 6 | 5% | spans the full window but is missing months inside it |

The two buckets a two-way split loses are the last two: products that start late
AND vanish before the end, and products that span the whole window with holes in
the middle. For the latter, "first price" and "last price" are not the ends of a
continuous series. Separately from all of this, 14 products are observed too
briefly to annualise at all and are published with a blank CAGR rather than an
annualised 3-month number, and 10 products have at least one interior hole, the
largest 18 months. The chained index never forms a return across a hole; it
simply drops that product from that month's link.

### 3.3 Survivorship bias runs the OPPOSITE way to the reflex

The reflex assumption is that dropping the products that vanished flatters an
index, because they were collapsing. In this archive they were not. Every
delisted product's trailing 3-month return before it stopped being priced:

| product | last priced | months observed | last $ | trailing 3m |
| --- | --- | --- | --- | --- |
| XY Roaring Skies Elite Trainer Box | 2026-06 | 11 | 4,899.99 | 6.5% |
| Ancient Origins Elite Trainer Box | 2025-10 | 13 | 2,625.00 | 43.2% |
| Elite Trainer Box [Mewtwo X] | 2026-06 | 16 | 900.00 | 0.0% |
| Fates Collide Elite Trainer Box | 2026-07 | 24 | 775.97 | -0.9% |
| Generations Elite Trainer Box | 2026-09 | 31 | 2,999.19 | 26.0% |
| Unbroken Bonds Elite Trainer Box | 2025-10 | 20 | 1,164.50 | 97.0% |

4 of 6 were still RISING when they disappeared and 1 were falling (median
16.3%). So a survivor-only basket is missing continued appreciation, not hiding
a collapse -- this particular bias makes the constant-basket number, if
anything, conservative. It is a different bias (missing the slow late entrants)
that inflates it, and section 2.2 quantifies that one at 10.8 points.

### 3.4 What the prices are, and are not

`market` is TCGplayer's trailing sales average. It is a quote, not an execution:
nobody transacted at the index, and section 6 is the correction for that. Two
specific things a reader should not assume:

* **There is no bid in this data.** `low`/`high` are the cheapest and dearest
  ASKS. Anything computed from `high - low` is a listing dispersion, not a
  spread -- the naive calculation gives a "spread" of 209% of the market price
  (section 6.6).
* **TCGplayer-Direct quotes do not exist for sealed product.** `direct_low` is
  NULL for every sealed row in the archive, so the direct-discount feature the
  singles models use is structurally unavailable here and was excluded rather
  than carried as an all-missing column.

### 3.5 The claim this study was asked to falsify

This study was commissioned around a preliminary headline: a constant-basket
geometric index on the raw catalogue query, with every full-history product
positive. **Both halves of that reproduce exactly, and neither should be the
headline.** Recomputed live on the uncleaned universe: **80.2%/yr**, over 62
full-history products of which **62 rose and 0 fell**.

It is not a calculation error. It is the wrong object, for the reason section
2.2 isolates -- it is a survivor-cohort index, and the "all positive" property
is true *by construction of which products get a full history*, not because ETBs
do not fall. The curated panel makes that visible: 9 of 111 products are down
over their own window, of which 9 are late entrants and 0 are full-history
products. A fixed basket cannot contain a single one of the fallers.

The honest headline is 70.3%/yr with a 95% interval of [28.8%, 125.2%], and even
that is one cell of a 18.9-point grid.

## 4. Why? The age story -- and why it mostly cannot be told

The natural explanation for section 2 is "boxes go up once they go out of
print". This section is where that explanation gets tested, and the honest
answer is that **the archive cannot identify an ageing effect at all**, while
the parts it CAN identify point away from the story a buyer of a new box would
want to be true.

### 4.1 The age effect is not weakly identified. It is not identified.

Every row of the panel satisfies `months_since_release = calendar month -
release month` exactly. So a product's age is a deterministic function of who it
is and what month it is: regressing age on product + calendar dummies gives
**R^2 = 1.000000**, and adding age to that design raises its rank by **zero**
(rank deficiency 2). "Do ETBs appreciate as they age" and "did the market rise"
are the same regressor over 32 months of one regime.

This is the classic age-period-cohort problem, and it is not fixable with more
cleverness -- a two-way fixed-effects age curve here would be reporting its own
normalisation, not a fact. What the lifecycle module publishes instead is the
FAN of answers you get from the three standard identifying restrictions, each of
which fits every observed price identically (largest fitted-price change across
the three restrictions: 7.1e-14, measured rather than asserted): a ten-year
ageing multiple anywhere from **0.87x to 744.27x** -- a **855x** span that is
pure assumption.

Anyone who tells you how much an ETB appreciates per year *because it aged* is
choosing one point in that fan.

### 4.2 What IS identified: the shape, not the slope

Slope CHANGES need no identifying assumption -- they survive the fixed effects.
Joint test that the age profile is linear: **chi2(5) = 30.9, p = 9.7e-06**. The
profile bends, decisively.

| age (months) | slope change (log/yr) | SE | t | significant | products crossing |
| --- | --- | --- | --- | --- | --- |
| 12 | 0.283 | 0.104 | 2.72 | yes | 38 |
| 24 | 0.053 | 0.102 | 0.52 | no | 34 |
| 36 | -0.217 | 0.063 | -3.45 | yes | 32 |
| 60 | -0.012 | 0.080 | -0.14 | no | 23 |
| 84 | 0.019 | 0.073 | 0.26 | no | 13 |

The normalisation-free contrast between the young band and the mature band
(12-24m -> 36-60m) is **-0.164 log/yr (t = -1.86)**: that contrast does not
clear the bar, so neither "it takes off once it is retired" nor its opposite is
established.

**Two caveats that cut the shape down, both published in
`etb_lifecycle_stability.csv`:**

1. The acceleration at 12 months **vanishes** once the launch cohort is
   excluded, so it is the launch cooldown ending, not a property of one-year-old
   boxes (-0.107, t = -0.62).
2. The deceleration is estimated almost entirely from the first calendar half;
   in the second half it is indistinguishable from zero (0.078, t = 1.15). Of 6
   subsamples tested, 2 are significant.

### 4.3 The decision-relevant result needs no assumption at all

Forget identifying the age curve. Ask the question a buyer actually faces: **buy
a box at release, hold it -- what happens?** That is a raw observed path, not a
model.

WHICH price counts as "at release" decides the answer, so it is worth saying
plainly. Prices in this archive are snapshots taken on the 1st of the month, and
no set in this cohort goes on sale on the 1st. So both a product's first quote
(usually one to two months before street date) and its release-month snapshot
are PRE-ORDER quotes on a box nobody can buy yet. Neither enters this panel
(CALCULATIONS 9.3b; `price_history` keeps them in `presale_quotes.csv`), and
they are not cheap: the last pre-street-date quote runs at a geometric mean of
**1.46x** of the first price the box actually opened at, above it for 92% of the
cohort and as high as 4.72x. The baseline below is therefore the first snapshot
dated on or after street date -- a real transactable price, taken a median of 10
days after the box went on sale (range 2-30 days).

> **Correction, 2026-07-25.** An earlier published version of this
> curve was wrong, not merely imprecise. It anchored k=0 on each product's first
> LISTED month, which for most of the cohort was then a pre-order quote on a box
> that had not shipped, and it counted k from that listing rather than from launch.
> The trough was published as
> 0.61x and is
> 0.92x; the 12-month figure was published as
> 1.00x and is
> 1.56x. Full ledger in section 7.4 and
> `etb_corrections.csv`.

For the 38 products whose first on-sale price is observed (26 of them with a
balanced 12-month window), the geometric mean path dips to **0.92x** by month 1
and is at **1.56x** a year later. That raw path is a boom reading, not a
lifecycle: measured as EXCESS over the rest of the ETB market it troughs at
0.76x and is still 0.78x at twelve months. The new box ended its first year
BEHIND the rest of the ETB market (0.76x at the trough, 0.78x at 12 months);
booster boxes (0.79x at the trough, 0.88x at 12 months) -- against those, buying
it was the worse of the two. It ended the year level with or AHEAD of singles
(0.87x at the trough, 1.05x at 12 months).

By channel -- the largest split in the study by point estimate, and small enough
on each side that the intervals are printed beside it:

| channel | products | trough month | trough (x launch) | at 12m (x launch) | 12m 95% lo | 12m 95% hi | products back at launch by 12m | worst product at 12m | best product at 12m | months for the MEAN to regain launch |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Pokemon Center exclusive | 13 | 3 | 0.88x | 1.46x | 1.15x | 1.85x | 10 | 0.76x | 3.06x | 6 |
| Mass-retail | 13 | 1 | 0.94x | 1.66x | 1.44x | 1.91x | 13 | 1.04x | 2.36x | 4 |

Pokemon Center exclusives -- allocated rather than stocked, so even their first
on-sale price is a queue price -- trough deeper, and take longer to get back
than mass-retail boxes on this run (trough 0.88x at month 3 against 0.94x at
month 1): the PC mean regains its launch price at month 6 against month 4 for
mass-retail. Read the last three columns before quoting any of that. Each side
is only 13 products; individually, 10 of the 13 Pokemon Center boxes ended at or
above the launch price at 12 months (best 3.06x, worst 0.76x) against 13 of 13
mass-retail boxes; and the two channels' 12-month confidence bands are [1.15x,
1.85x] and [1.44x, 1.91x]. Every one of those is a 13-product average measured
inside one boom, so none of it is a statement about every box or about any other
regime.

### 4.4 The index side: what survives a significance test, and what does not

Splitting the universe by how old each product was when it ENTERED the window
(an as-of fact, not one that depends on how the window ended) asks the same
question without any lifecycle machinery. Read the `t` column with the point
estimates: 0 of 2 contrasts against the youngest ON-SALE cohort clears this
repo's |t| >= 2 bar.

No cohort enters before its set's street date: pre-order quotes never enter this
panel (CALCULATIONS 9.3b), so every row below starts at a post-release price.

| cohort (age at entry) | SKUs | sets | chained index | HAC 95% lo | HAC 95% hi | median product | share down over own window | vs youngest | t |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0-12m old at entry | 50 | 22 | 64.2%/yr | 8.8% | 147.9% | 56.7%/yr | 18% | n/a | n/a |
| 1-3y old at entry | 27 | 12 | 84.1%/yr | 32.9% | 155.2% | 81.1%/yr | 0% | +12.1pp | 1.28 |
| 3y+ old at entry | 34 | 29 | 66.9%/yr | 33.6% | 108.6% | 61.4%/yr | 0% | +1.6pp | 0.08 |

Reading the rows against each other:

* The youngest ON-SALE cohort's own index grew 64.2%/yr with t = 2.36 --
  **distinguishable from flat** at the same bar. 18% of those boxes are down
  over their own window.
* Product 1-3 years past release grew 84.1%/yr; its paired difference against
  the youngest on-sale cohort **does not clear the bar** (t = 1.28).
* Product 3+ years past release grew 66.9%/yr; its difference **does not clear
  the bar** (t = 0.08), and it sits BELOW the 1-3y cohort in point estimate, so
  this is not a monotone "older is better" effect even before the error bars are
  drawn.

**This corrects a previously published reading.** With pre-release entrants
pooled into the youngest cohort, that cohort's index came out at 39.1%/yr and
"not distinguishable from flat", and the 1-3y contrast against it cleared the
significance bar at t = 2.86 -- which is where the claim "the gains belong to
out-of-print product" came from. Taking the pre-order quotes out (first as a
separate cohort, now at ingest, CALCULATIONS 9.3b) moves the youngest on-sale
cohort to 64.2%/yr and leaves the 1-3y contrast at t = 1.28. The 1-3y cohort
still has the higher point estimate; what does not survive is the claim that any
of the AGEING contrasts was tested. See section 7.4.

Note also the sample these contrasts rest on: buckets of 27 to 50 SKUs, which
are only 12 to 29 distinct releases (the `sets` column above), all sharing ONE
32-month calendar window -- a post-hoc slice of a small panel, not an
experiment.

### 4.5 Reprints: the obvious mechanism, and why this data cannot test it

If "out of print" is the mechanism, a reprint should hurt. The lifecycle module
looked for that and **refuses to answer**: of 24 large idiosyncratic drops (<=
-20% after removing the month's cross-sectional mean), 16 are products under a
year old (launch cooldown) and only 8 are out-of-print product.
`reprint_analysis_supportable` returns **no**. In-print status is not a field in
this database at all; age is the only proxy, and it is labelled as one
everywhere.

What the shocks do show, for whatever it is worth on 24 events, is that they do
NOT mean-revert. The cumulative idiosyncratic return is -0.30 at impact and
-0.35 six months later. Whatever caused a big ETB drop in this window, the price
did not come back inside half a year.

### 4.6 Do older ETBs sell for more today? Yes -- and that is not an ageing curve

This is the owner's own observation, and it is correct as a statement about
today's shelf. It is also the single easiest number in this study to misread, so
the gradient and the reason it cannot be extrapolated are stated together
throughout: **at 2026-10, mass-retail ETB price rises with age at Spearman rho =
0.721 (p = 4.1e-12, n = 68) -- and within a single calendar month a product's
age IS its release cohort, with R^2 = 1.000, so that rho ranks vintages and
cannot separate "boxes gain value as they age" from "boxes made in 2016 are
scarcer than boxes made in 2026".** Neither half of that sentence is quotable
without the other.

Three things qualify it further, all measured.

**It is strongest in mass retail.** Pokemon Center exclusives give rho = 0.402
(p = 0.01, n = 37) -- distinguishable from zero but weaker than mass-retail's,
and no PC product in the archive is older than about 5 years. The pooled rho =
0.553 is therefore partly a statement about which channel happens to be old.

**The shape is not a trend, and this sample cannot order the bands.**

| age band | products | median price | lo | hi | sets |
| --- | --- | --- | --- | --- | --- |
| <1yr | 6 | $114 | $70 | $158 | 6 |
| 1-2yr | 9 | $136 | $122 | $163 | 7 |
| 2-3yr | 8 | $136 | $113 | $157 | 6 |
| 3-5yr | 12 | $183 | $152 | $290 | 11 |
| 5-8yr | 19 | $216 | $141 | $565 | 15 |
| 8yr+ | 14 | $806 | $657 | $1,256 | 12 |

Every row of that table is a different set of products bought in a different
decade -- it is a vintage ranking, printed by age because that is how the
question was asked. The medians do rise monotonically: there are 0 inversions,
the worst being at n/a -- the dip the owner noticed. Of those 0 dips, 0 separate
at the bootstrap median interval, and the step up into the oldest band does
separate -- supplying 85% of the whole top-to-bottom range by itself. With 68
products spread over 6 bands and a long right tail, **the band ORDER above is
not established by this sample apart from the step into the oldest band** -- the
owner's dip included. The point estimates are what they are; their ordering is
not. The counterweight is kept honestly the other way too: dropping the vintage
band entirely still leaves rho = 0.535 (p = 3.1e-05, n = 54) and a fitted
24.5%/yr against 26.5%/yr on the full sample, so the gradient is not only the
vintage tail.

**The oldest band is where the level lives and where the sample is worst.** Only
56.0% of same-era mass-retail vintage SKUs are still priced at all (14 of 25; 11
are absent, several with zero priced months anywhere in the archive), against
95-100% in every younger band. Assuming only that the absentees have *some*
price, the distribution-free bound on that band's median runs [$325, $1,800]
against a survivor median of $806 -- a 5.53x span from survivorship alone.
Trading is thin there too: 64% of vintage products have their market estimate
BELOW the cheapest live ask (every band's share is in
`etb_agevalue_thinness.csv`) and 2 have one listing. The obvious explanation --
smaller print runs -- is **unmeasurable here**: no print-run figure exists
anywhere in this database, and the catalogue-breadth proxy comes out at 0.88,
pointing AWAY from the scarcity story rather than supporting it. That reading is
published rather than suppressed, and it does not clear the confound: the proxy
has no resolution at the 2016-vs-2026 distance.

#### Will a box bought today follow them up? The cross-section cannot say, and the panel says no

The gradient is a fact about products that already exist. Turning it into a
holding period requires that ageing CAUSES the gap, which is the one thing R^2 =
1.000 forbids. The panel answers the question the cross-section cannot, because
it watches the same box age.

Across 97 products with a full price path, mass-retail in-window appreciation
runs 69.5%/yr median with 0% negative. Its dependence on age is +0.0pp/yr per
year of age (t = 0.02) -- **no age dependence distinguishable from zero**.
Excluding products still inside their launch window it is -1.2pp/yr (t = -0.88):
older boxes appreciated more *slowly*, the opposite sign to what an ageing
reading of the cross-section predicts. The headline null is the conservative
statement and the one to quote; the excl-launch cut is a post-hoc slice of one
regime, published because its sign is decision-relevant, not because it
establishes that age is bad for a box.

Put on one scale: the cross-sectional gradient implies 83.4% over the median
observed span, while boxes actually returned 255.7%. The gradient can account
for at most 48% of the realised log move -- an upper bound, since it credits the
whole implied part to age. **The rest is calendar, and no box bought today can
assume it.** That ceiling is a bound on how much of the gradient an ageing story
could be carrying; it is not a finding that "48% of ETB appreciation is ageing".

The natural experiment settles the shape question the same way: 1 of 1
cross-sectional inversions are contradicted by the products that actually made
the crossing.

| channel | from | to | cross-section implies | boxes that crossed | they actually did | contradicted |
| --- | --- | --- | --- | --- | --- | --- |
| pokemon_center | 1-2yr | 2-3yr | -23.3% | 5 | 366.8% | yes |

The headline one is the owner's dip: mass retail implies n/a, and the n/a boxes
that genuinely aged past that boundary returned n/a median [n/a, n/a].

**No forecast follows.** `projection_support` reports `forecast_supported = no`
with a maximum measured horizon of 31 months. `etb_agevalue_illustrative.csv`
multiplies three readings of this same data out to 5 and 10 years with every row
flagged `is_measured = False`:

on a $114 box at 10 years -- *flat in nominal terms* -> 1.00x ($114); *today's
box walks the current cross-section* -> 8.60x ($982); *the 2024-2026 rate
continues* -> 195.72x ($22,355). Every one of those is an ASSUMPTION carried
forward, not a measurement, and they disagree by a factor of 196.

**The spread between them, from one dataset, is the finding** -- it is why this
study publishes no holding period.

## 5. Can it be predicted?

**No -- not at the horizon that matters, and the one shorter horizon that clears
the gates is chased down in 5.1.** This is a null result wherever the gates are
not cleared, and it is published as one.

The question is narrow and cross-sectional: standing at month T with only
information available at T, can we rank ETBs by which will beat the ETB basket
over the next H months? It is not "will ETBs go up" -- section 2 measures that.

| horizon (months) | purged folds | mean held-out IC | effective n | t | clears both gates |
| --- | --- | --- | --- | --- | --- |
| 1 | 25 | 0.274 | 8.30 | 3.11 | yes |
| 3 | 21 | 0.008 | 4.77 | 0.05 | no |
| 6 | 15 | -0.116 | 3.00 | -0.96 | no |
| 12 | 3 | -0.281 | 1.00 | -1.05 | no |

At the pre-registered primary horizon of 6 months the mean held-out rank
correlation is **-0.116** -- the point estimate is NEGATIVE -- on an effective
sample of 3.00 against the repo's 4.0 bar. At H = 12 there are only **3** usable
folds, holding at most 1 non-overlapping one-year windows: a 32-month archive
cannot test a one-year hold with any power, which is itself a finding about the
data rather than about the model.

The binding constraint is structural, not statistical. With an H-month label
window, N monthly folds contain at most `(N-1)//H + 1` NON-OVERLAPPING label
windows -- 3 at H = 6. No autocorrelation estimate can see that, so the
effective sample used above is the MINIMUM of the autocorrelation-deflated n_eff
and that structural bound.

### 5.1 H = 1 clears the gates. Is it a signal?

The one-month horizon does clear both gates, so it was chased down rather than
buried, through three checks:

**Mechanism.** The strongest feature at H = 1 is `mid_skew` (elsewhere: H = 12:
`rel_spread`). `mid_skew` compares TCGplayer's TRAILING market average with the
CURRENT book midpoint. If it were demand, a high value should predict the book
to keep rising. It does the opposite:

| relationship | mean IC | t | effective n |
| --- | --- | --- | --- |
| mid_skew -> market | 0.268 | 4.50 | 10.70 |
| mid_skew -> book mid | -0.234 | -4.53 | 11.24 |
| mid_skew -> gap change | -0.437 | -15.29 | 25.00 |

A high skew predicts the market price RISING and the book midpoint FALLING, with
the gap between them closing. That is two measurements of one price converging,
not a forecast of value.

**Economics.** The top-quintile portfolio at H = 1 returns 160.9%/yr against the
basket's 93.8%/yr -- an edge of +67.1pp gross (t = 2.65). Twelve rebalances a
year at the round-trip cost from section 6 is a 85.8pp drag, so the NET edge is
-18.7pp. It loses to doing nothing.

**The model beats its own best single input only at H = 12.**

| horizon | best single feature | its IC | fitted model IC | which wins |
| --- | --- | --- | --- | --- |
| 1 | `mid_skew` | 0.268 | 0.274 | tie |
| 3 | `mid_skew` | 0.260 | 0.008 | the single feature |
| 6 | `mid_skew` | 0.269 | -0.116 | the single feature |
| 12 | `rel_spread` | -0.359 | -0.281 | model |

Everywhere else it ties or loses to that one feature, so the ML layer adds
little that a one-line feature ranking does not. Full detail, including the
permutation nulls, purge audits and the selection-protocol contamination flag,
is in `data/output/etb_forward.md`.

## 6. What would a holder actually have earned?

An index is not money. This section converts it, using the cost model in
`pokestat/model/etb_hold.py`; the full treatment is
`data/output/etb_hold_summary.md`.

**Every cost constant below is a STATED ASSUMPTION, not a fetched fact.** This
project's permitted sources carry card prices and FX rates -- not TCGplayer's
fee schedule, not sales-tax rates, not Treasury yields. The marketplace take
rate is the single most influential one: sweeping it alone moves the 24-month
answer by 17.6 points a year.

### 6.1 The frictions are a one-time toll, not a rate

Round trip: 7.5% sales tax in, 12.75% marketplace take out, $12.00 to ship a
heavy box. That is roughly **20.2% of the box price plus $12.30 fixed**, charged
once. Because it is charged once, it amortises -- which is the whole answer to
"how long should I hold".

At the measured gross index rate of 70.3%/yr, on a $204 box (the median ETB
price in 2026-10):

| hold (months) | gross | net | net rate | friction drag | gross growth needed to beat cash | beats cash |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | 1.14x | 0.87x | -42.8%/yr | 113.1pp/yr | 200.5%/yr | no |
| 6 | 1.31x | 1.00x | 0.1%/yr | 70.3pp/yr | 77.5%/yr | no |
| 12 | 1.70x | 1.32x | 32.1%/yr | 38.3pp/yr | 36.4%/yr | yes |
| 24 | 2.90x | 2.29x | 51.3%/yr | 19.1pp/yr | 19.5%/yr | yes |

**The minimum hold to beat a 4.5% savings account is 7 months** (8 months on a
cheap box, 6 on an expensive one -- shipping and the flat fee do not scale). The
fee structure is regime-independent arithmetic; the floor it implies is not,
because it compounds the growth rate this window happened to deliver against
those fees (`etb_hold_summary.md` section 7 shows it across assumed rates).

An OPTIMAL hold is a different matter and the study declines to name one: the
best observed horizon was 18 months at 65.6%/yr net, but a 31-month archive
contains exactly 1 non-overlapping window of that length. One window is an
anecdote.

### 6.2 What actually happened, box by box

39,524 realised holding periods across 109 products, all net of costs:

| hold | holding periods | independent windows | median net | 5th pct | 95th pct | share that lost money |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | 2,478 | 10 | 0.83x | 0.55x | 1.23x | 80% |
| 6 | 2,162 | 5 | 0.99x | 0.61x | 1.63x | 51% |
| 12 | 1,573 | 2 | 1.43x | 0.88x | 2.80x | 11% |
| 24 | 571 | 1 | 2.73x | 1.62x | 6.62x | 0% |

**A three-month flip lost money 80% of the time during a boom.** Six months was
a coin flip (51%). Twelve months lost 11% of the time. A product-clustered
bootstrap puts the median 12-month net rate at 42.8%/yr, 95% CI [36.0%, 49.7%]
over 97 products.

Note the two 12-month numbers in this document that DISAGREE: applying the
chained index rate uniformly gives 32.1%/yr, while the pooled realised holds
give 42.8%/yr. They are different objects -- pooling triples over-weights
long-history products, and the index is spread evenly over a window that did not
grow evenly. The gap, 10.7 points, is 28% of the 38.3-point twelve-month
friction drag -- a warning about how much of any of these numbers is a
construction choice.

### 6.3 One box is not the index

| products | 10th pct box | median box | 90th pct box | the basket | middle-50% spread | share worse than basket |
| --- | --- | --- | --- | --- | --- | --- |
| 97 | 0.99x | 1.43x | 2.44x | 1.45x | 70pp | 50% |

At twelve months the middle 50% of single-box outcomes spans about 70 annualised
points and 50% of picks did worse than simply owning the basket.

### 6.4 When you bought: age at purchase

| bought when | holds | products | median net rate | share that lost money |
| --- | --- | --- | --- | --- |
| bought 0-6m after release | 122 | 32 | 27.7%/yr | 20% |
| bought 6-12m after release | 148 | 28 | 48.2%/yr | 14% |
| bought 1-3y after release | 518 | 48 | 55.8%/yr | 7% |
| bought 3y+ after release | 785 | 52 | 37.6%/yr | 11% |

Buying inside six months of release and holding a year lost money 20% of the
time; buying product already 1-3 years old lost 7% of the time. No row is dated
before a set's street date: pre-order quotes never enter this panel
(CALCULATIONS 9.3b), so every buy above is at a post-release price.

The mechanism is measured, not assumed. Of 36 products with an observed first
ON-SALE price, the median trough over the following six months was 13.3% below
it (IQR 3.6% to 22.0%) and 22% fell at least 25%. Measured at a fixed six-month
endpoint rather than at a minimum -- which is not selection-prone -- the median
is -0.8%, i.e. the typical box was above its first on-sale price at that
endpoint.

**This corrects a figure this study previously published.** The same statistic
measured from each product's first LISTED quote gives 49.2% at the trough and
45.8% at the endpoint, across 40 products -- a gap of 35.9 points on the median
(product-bootstrap 95% CI 19.8 to 43.6), and a change of SIGN at the endpoint.
That is the number this report used to carry. It was wrong: `price_history` is
snapshotted on the 1st and essentially no set ships on the 1st, so a product's
first listed quote is normally a pre-order ask on a box that has not shipped --
no longer part of the panel, and read back from `presale_quotes.csv` for this
comparison only -- and the old figure was largely that ask deflating rather than
a box losing value. Both arms are computed (first on-sale price vs first listed
price) so the comparison is auditable rather than asserted. A buyer who paid the
pre-order price ate the difference either way. See section 7.4.

### 6.5 The downside

Two numbers, both regime-facing:

* **Flat is not break-even.** If prices merely stop rising, a 12-month hold
  returns 0.75x -- a 25.0% annualised loss, because the frictions are charged
  anyway.
* **A fall of 50.8% from the terminal price erases the entire 24-month edge over
  a savings account**, and 54.7% turns it into a nominal loss. That is about 68%
  of the gain -- it does not require prices to return to where they started.

At 24 months the net answer keeps its sign under every sensitivity cell; at 6
months the same knobs move it across zero (-29.2% to 33.4%/yr), so short-horizon
verdicts are assumptions rather than measurements.

### 6.6 One brief the data contradicted

This study was briefed on a "~15-20% bid-ask on thin sealed listings". **The
archive does not support that**, and the obvious way to compute it is wrong.
`price_history` carries a LISTING book -- `low` is the cheapest ask, `high` the
dearest -- and no bid at all. Treating `high - low` as a spread gives a median
of 209% of the market price, because `high` has a median of 3.10x market. What
IS measurable: `low/market` has a median of 0.978, and a round trip executed at
`low` on both ends returned a median 1.051x of what a market-to-market round
trip returned, with only 35% of products worse off. The measurable spread very
nearly cancels. The holder's real loss is fees, tax and shipping -- which is why
the undercut constant defaults to zero and is swept to 15% anyway (worth 12.2
points a year), because "not measurable" is not "zero".

## 7. Limitations, and the data itself

### 7.1 The window is the finding's ceiling

**32 monthly observations, 2024-03 .. 2026-10, one regime.** Everything above
happened inside a historic Pokemon sealed boom. The index's worst peak-to-trough
fall in the entire archive is -2.7%. There is no bust in this data, so nothing
here measures what happens in one, and no interval printed above is a forecast
interval -- the HAC bands are sampling uncertainty WITHIN the boom. Statistical
uncertainty here is small; regime uncertainty is everything.

The archive does not go back further because it cannot: tcgcsv's price archive
begins in 2024-03, and the sources that would extend it (eBay, PriceCharting)
are excluded on terms-of-service grounds. "The last few years" means 2.6 years.

### 7.2 Everything else worth knowing before quoting a number

* **The headline is a construction choice.** The 15-cell grid spans 70.3% to
  89.2%/yr. Any single figure quoted without its construction is unfalsifiable.
* **Prices are TCGplayer quotes, not executions.** `market` is a trailing sales
  average; nobody transacted at the index. Section 6 is the correction, and its
  cost constants are stated assumptions, not fetched facts.
* **The age effect is unidentified** (section 4.1) and the ML layer is a null at
  the primary horizon (section 5). Neither is a placeholder for a result that is
  coming later; both are the answer this data supports.
* **14 of 111 products are observed for fewer than the 12 months required to
  annualise.** Their cumulative return is a fact and is published; their CAGR is
  blank rather than a number like -99.9%/yr, which is what annualising a 3-month
  window produces.
* **10 products have interior holes** in their series (a month with no priced
  listing); the largest is 18 months. The chained index never forms a return
  across a hole.
* **No liquidity, no time-to-sale, no condition risk.** The archive has no
  volume data. A box that takes four months to sell had a longer real holding
  period than the one priced here.
* **This is measurement, not investment advice.** Nothing here is a
  recommendation to buy, hold or sell anything.

### 7.3 Every ETB in the study

111 products, sorted by annualised growth; blank CAGR means fewer than 12
observed months. The same rows, with every column, are in
**`data/output/etb_products.csv`**. Of these, 68 have a growth rate that clears
|t| >= 2 on their own Newey-West error bar and 9 are down over their observed
window. Those are SKU counts: 111 SKUs are 62 sets (1.79 per set), so divide by
roughly that before treating them as independent (section 2.6).

**Read the `total spans a gap?` column.** 2 rows carry `GAP`, meaning at least 6
months between the product's first and last observation have no price at all.
For those rows `total` compares two prices with a hole between them and the
terminal price may be a single illiquid relisting rather than a market move; the
blank-CAGR gate protects the ANNUALISED column but not this one.

| id | product | set | months | gaps | age at entry (m) | first $ | last $ | total | total spans a gap? | CAGR | t (HAC) | worst drawdown | PC | full | late | gone |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 501,999 | 151 Pokemon Center Elite Trainer Box (Exclusive) | sv3pt5 | 32 | 0 | 6 | 94.65 | 1,264.45 | 1,235.9% |  | 172.8%/yr | 3.32 | -14.0% | yes | yes | no | no |
| 528,040 | Paldean Fates Elite Trainer Box | sv4pt5 | 32 | 0 | 2 | 41.49 | 433.14 | 944.0% |  | 147.9%/yr | 3.03 | -21.7% | no | yes | no | no |
| 501,266 | Obsidian Flames Pokemon Center Elite Trainer Box (Exclusive) | sv3 | 32 | 0 | 7 | 64.27 | 631.59 | 882.7% |  | 142.2%/yr | 2.23 | -25.8% | yes | yes | no | no |
| 503,313 | 151 Elite Trainer Box | sv3pt5 | 32 | 0 | 6 | 53.31 | 488.56 | 816.5% |  | 135.7%/yr | 3.06 | -24.2% | no | yes | no | no |
| 247,673 | Fusion Strike Pokemon Center Elite Trainer Box (Exclusive) | swsh8 | 32 | 0 | 28 | 58.10 | 476.75 | 720.6% |  | 125.9%/yr | 2.78 | -9.6% | yes | yes | no | no |
| 247,671 | Fusion Strike Elite Trainer Box | swsh8 | 32 | 0 | 28 | 40.91 | 327.93 | 701.6% |  | 123.8%/yr | 3.83 | -10.4% | no | yes | no | no |
| 528,039 | Paldean Fates Pokemon Center Elite Trainer Box (Exclusive) | sv4pt5 | 32 | 0 | 2 | 70.80 | 564.50 | 697.3% |  | 123.4%/yr | 2.18 | -21.7% | yes | yes | no | no |
| 181,704 | Team Up Elite Trainer Box | sm9 | 32 | 0 | 61 | 506.90 | 4,000.00 | 689.1% |  | 122.5%/yr | 3.62 | -3.1% | no | yes | no | no |
| 493,973 | Paldea Evolved Pokemon Center Elite Trainer Box (Exclusive) | sv2 | 32 | 0 | 9 | 79.88 | 614.08 | 668.8% |  | 120.2%/yr | 2.73 | -18.9% | yes | yes | no | no |
| 501,264 | Obsidian Flames Elite Trainer Box | sv3 | 32 | 0 | 7 | 37.16 | 275.31 | 640.9% |  | 117.1%/yr | 2.79 | -13.8% | no | yes | no | no |
| 170,277 | Celestial Storm Elite Trainer Box | sm7 | 32 | 0 | 67 | 287.20 | 2,091.30 | 628.2% |  | 115.7%/yr | 3.54 | -6.8% | no | yes | no | no |
| 453,470 | Crown Zenith Elite Trainer Box | swsh12pt5 | 32 | 0 | 14 | 42.75 | 305.11 | 613.7% |  | 114.0%/yr | 3.34 | -12.4% | no | yes | no | no |
| 245,352 | Evolving Skies Pokemon Center Elite Trainer Box [Glaceon/Vaporeon/Sylveon/Espeon] (Exclusive) | swsh7 | 32 | 0 | 31 | 155.50 | 1,045.99 | 572.7% |  | 109.1%/yr | 4.73 | -2.1% | yes | yes | no | no |
| 185,719 | Unbroken Bonds Elite Trainer Box | sm10 | 20 | 0 | 58 | 376.23 | 1,164.50 | 209.5% |  | 104.1%/yr | 2.00 | -1.0% | no | no | no | yes |
| 557,350 | Stellar Crown Elite Trainer Box | sv7 | 25 | 0 | 1 | 37.69 | 156.75 | 315.9% |  | 103.9%/yr | 2.81 | -7.6% | no | no | yes | no |
| 493,974 | Paldea Evolved Elite Trainer Box | sv2 | 32 | 0 | 9 | 35.16 | 217.76 | 519.3% |  | 102.6%/yr | 2.95 | -13.4% | no | yes | no | no |
| 242,443 | Evolving Skies Elite Trainer Box [Glaceon/Vaporeon/Sylveon/Espeon] | swsh7 | 32 | 0 | 31 | 82.74 | 497.10 | 500.8% |  | 100.2%/yr | 4.03 | -7.8% | no | yes | no | no |
| 242,434 | Evolving Skies Elite Trainer Box [Flareon/Jolteon/Umbreon/Leafeon] | swsh7 | 32 | 0 | 31 | 95.48 | 569.58 | 496.5% |  | 99.6%/yr | 4.77 | -6.3% | no | yes | no | no |
| 277,336 | Lost Origin Pokemon Center Elite Trainer Box (Exclusive) | swsh11 | 32 | 0 | 18 | 63.87 | 380.00 | 495.0% |  | 99.4%/yr | 2.32 | -17.8% | yes | yes | no | no |
| 193,052 | Unified Minds Elite Trainer Box | sm11 | 32 | 0 | 55 | 291.86 | 1,719.90 | 489.3% |  | 98.7%/yr | 3.14 | -10.8% | no | yes | no | no |
| 245,376 | Evolving Skies Pokemon Center Elite Trainer Box [Jolteon/Flareon/Umbreon/Leafeon] (Exclusive) | swsh7 | 32 | 0 | 31 | 185.66 | 1,060.06 | 471.0% |  | 96.3%/yr | 4.41 | -2.4% | yes | yes | no | no |
| 277,335 | Lost Origin Elite Trainer Box | swsh11 | 32 | 0 | 18 | 35.08 | 195.39 | 457.0% |  | 94.4%/yr | 3.44 | -16.0% | no | yes | no | no |
| 283,401 | Silver Tempest Elite Trainer Box | swsh12 | 32 | 0 | 16 | 30.50 | 163.86 | 437.2% |  | 91.7%/yr | 3.24 | -14.9% | no | yes | no | no |
| 285,860 | Silver Tempest Pokemon Center Elite Trainer Box (Exclusive) | swsh12 | 32 | 0 | 16 | 74.31 | 391.97 | 427.5% |  | 90.4%/yr | 3.35 | -5.4% | yes | yes | no | no |
| 123,741 | Generations Elite Trainer Box | g1 | 31 | 0 | 97 | 602.32 | 2,999.19 | 397.9% |  | 90.1%/yr | 2.79 | -5.9% | no | no | no | yes |
| 624,675 | Destined Rivals Pokemon Center Elite Trainer Box (Exclusive) | sv10 | 17 | 0 | 1 | 183.11 | 426.34 | 132.8% |  | 88.5%/yr | 1.20 | -23.9% | yes | no | yes | no |
| 111,280 | XY BREAKpoint Elite Trainer Box | xy9 | 30 | 0 | 99 | 240.00 | 1,099.99 | 358.3% |  | 87.8%/yr | 2.45 | -3.3% | no | no | yes | no |
| 107,107 | Elite Trainer Box [Mewtwo Y] | xy8 | 27 | 3 | 102 | 331.98 | 1,499.00 | 351.5% |  | 86.6%/yr | 2.40 | 0.0% | no | no | yes | no |
| 199,308 | Cosmic Eclipse Elite Trainer Box | sm12 | 30 | 2 | 52 | 381.14 | 1,874.50 | 391.8% |  | 85.3%/yr | 2.86 | -2.6% | no | no | no | no |
| 478,758 | Scarlet & Violet Pokemon Center Elite Trainer Box (Exclusive) [Koraidon] | sv1 | 32 | 0 | 12 | 61.50 | 287.06 | 366.8% |  | 81.6%/yr | 2.01 | -19.0% | yes | yes | no | no |
| 251,199 | Celebrations Pokemon Center Elite Trainer Box (Exclusive) | cel25 | 32 | 0 | 29 | 110.31 | 514.57 | 366.5% |  | 81.5%/yr | 2.27 | -10.5% | yes | yes | no | no |
| 242,811 | Celebrations Elite Trainer Box | cel25 | 32 | 0 | 29 | 77.37 | 356.84 | 361.2% |  | 80.7%/yr | 2.46 | -29.1% | no | yes | no | no |
| 164,303 | Forbidden Light Elite Trainer Box | sm6 | 31 | 1 | 70 | 153.97 | 686.16 | 345.6% |  | 78.3%/yr | 3.07 | -9.6% | no | no | no | no |
| 145,847 | Shining Legends Elite Trainer Box | sm35 | 32 | 0 | 77 | 266.92 | 1,183.16 | 343.3% |  | 78.0%/yr | 3.81 | -0.4% | no | yes | no | no |
| 256,140 | Brilliant Stars Pokemon Center Elite Trainer Box (Exclusive) | swsh9 | 32 | 0 | 25 | 51.25 | 227.17 | 343.3% |  | 78.0%/yr | 2.25 | -18.5% | yes | yes | no | no |
| 630,686 | Black Bolt Elite Trainer Box | zsv10pt5 | 15 | 0 | 1 | 84.46 | 162.67 | 92.6% |  | 75.4%/yr | 1.58 | -9.0% | no | no | yes | no |
| 256,138 | Brilliant Stars Elite Trainer Box | swsh9 | 32 | 0 | 25 | 37.38 | 159.18 | 325.8% |  | 75.2%/yr | 3.19 | -20.1% | no | yes | no | no |
| 129,890 | Guardians Rising Elite Trainer Box | sm2 | 29 | 3 | 82 | 105.41 | 446.54 | 323.6% |  | 74.9%/yr | 5.03 | -3.8% | no | no | no | no |
| 478,756 | Scarlet & Violet Pokemon Center Elite Trainer Box (Exclusive) [Miraidon] | sv1 | 32 | 0 | 12 | 74.94 | 317.06 | 323.1% |  | 74.8%/yr | 2.28 | -13.8% | yes | yes | no | no |
| 270,708 | Pokemon GO Elite Trainer Box | pgo | 32 | 0 | 20 | 40.25 | 169.91 | 322.1% |  | 74.6%/yr | 3.45 | -8.2% | no | yes | no | no |
| 265,527 | Astral Radiance Elite Trainer Box | swsh10 | 32 | 0 | 22 | 33.56 | 139.41 | 315.4% |  | 73.5%/yr | 2.65 | -10.8% | no | yes | no | no |
| 512,813 | Paradox Rift Elite Trainer Box [Iron Valiant] | sv4 | 32 | 0 | 4 | 32.70 | 135.18 | 313.4% |  | 73.2%/yr | 2.97 | -10.1% | no | yes | no | no |
| 107,106 | Elite Trainer Box [Mewtwo X] | xy8 | 16 | 0 | 112 | 453.99 | 900.00 | 98.2% |  | 72.9%/yr | 2.11 | -2.3% | no | no | yes | yes |
| 478,336 | Scarlet & Violet Elite Trainer Box [Miraidon] | sv1 | 32 | 0 | 12 | 35.95 | 144.73 | 302.6% |  | 71.5%/yr | 2.91 | -10.4% | no | yes | no | no |
| 478,335 | Scarlet & Violet Elite Trainer Box [Koraidon] | sv1 | 32 | 0 | 12 | 32.52 | 130.92 | 302.6% |  | 71.5%/yr | 3.06 | -8.0% | no | yes | no | no |
| 552,999 | Shrouded Fable Elite Trainer Box | sv6pt5 | 26 | 0 | 1 | 36.71 | 112.61 | 206.8% |  | 71.3%/yr | 1.96 | -21.1% | no | no | yes | no |
| 265,528 | Astral Radiance Pokemon Center Elite Trainer Box (Exclusive) | swsh10 | 32 | 0 | 22 | 49.11 | 195.65 | 298.4% |  | 70.8%/yr | 2.32 | -19.3% | yes | yes | no | no |
| 123,447 | XY Evolutions Elite Trainer Box [Mega Charizard Y] | xy12 | 32 | 0 | 88 | 220.03 | 870.98 | 295.8% |  | 70.3%/yr | 3.44 | -12.0% | no | yes | no | no |
| 175,511 | Lost Thunder Elite Trainer Box | sm8 | 32 | 0 | 64 | 176.62 | 681.55 | 285.9% |  | 68.7%/yr | 2.63 | -3.6% | no | yes | no | no |
| 512,815 | Paradox Rift Elite Trainer Box [Roaring Moon] | sv4 | 32 | 0 | 4 | 37.03 | 137.48 | 271.3% |  | 66.2%/yr | 2.64 | -13.7% | no | yes | no | no |
| 229,285 | Battle Styles Elite Trainer Box [Rapid Strike Urshifu] (Blue) | swsh5 | 32 | 0 | 36 | 36.47 | 134.13 | 267.8% |  | 65.6%/yr | 3.13 | -3.5% | no | yes | no | no |
| 532,845 | Temporal Forces Elite Trainer Box [Walking Wake] | sv5 | 31 | 0 | 1 | 39.91 | 140.00 | 250.8% |  | 65.2%/yr | 2.59 | -15.4% | no | no | yes | no |
| 630,689 | White Flare Elite Trainer Box | rsv10pt5 | 15 | 0 | 1 | 81.19 | 145.23 | 78.9% |  | 64.6%/yr | 1.73 | -6.1% | no | no | yes | no |
| 120,697 | Steam Siege Elite Trainer Box | xy11 | 14 | 18 | 91 | 499.00 | 1,800.00 | 260.7% | GAP | 64.3%/yr | 1.70 | -18.2% | no | no | no | no |
| 512,809 | Paradox Rift Pokemon Center Elite Trainer Box (Exclusive) [Roaring Moon] | sv4 | 32 | 0 | 4 | 62.35 | 222.52 | 256.9% |  | 63.6%/yr | 2.20 | -12.7% | yes | yes | no | no |
| 532,848 | Temporal Forces Elite Trainer Box [Iron Leaves ex] | sv5 | 31 | 0 | 1 | 36.85 | 123.59 | 235.4% |  | 62.3%/yr | 2.49 | -17.4% | no | no | yes | no |
| 216,856 | Darkness Ablaze Elite Trainer Box | swsh3 | 32 | 0 | 43 | 33.74 | 116.12 | 244.2% |  | 61.4%/yr | 2.50 | -16.9% | no | yes | no | no |
| 229,284 | Battle Styles Elite Trainer Box [Single Strike Urshifu] (Red) | swsh5 | 32 | 0 | 36 | 37.64 | 129.54 | 244.2% |  | 61.4%/yr | 2.93 | -8.2% | no | yes | no | no |
| 123,448 | XY Evolutions Elite Trainer Box [Mega Blastoise] | xy12 | 32 | 0 | 88 | 191.99 | 656.57 | 242.0% |  | 61.0%/yr | 3.94 | -4.6% | no | yes | no | no |
| 247,282 | Chilling Reign Pokemon Center Elite Trainer Box [Shadow Rider Calyrex] (Exclusive) | swsh6 | 32 | 0 | 33 | 56.98 | 191.56 | 236.2% |  | 59.9%/yr | 2.21 | -10.9% | yes | yes | no | no |
| 100,495 | Ancient Origins Elite Trainer Box | xy7 | 13 | 7 | 103 | 1,250.00 | 2,625.00 | 110.0% | GAP | 59.8%/yr | 1.90 | 0.0% | no | no | no | yes |
| 133,776 | Burning Shadows Elite Trainer Box | sm3 | 32 | 0 | 79 | 98.56 | 325.30 | 230.1% |  | 58.8%/yr | 4.02 | -0.3% | no | yes | no | no |
| 173,393 | Dragon Majesty Elite Trainer Box | sm75 | 32 | 0 | 66 | 381.99 | 1,256.49 | 228.9% |  | 58.6%/yr | 2.96 | -7.3% | no | yes | no | no |
| 149,377 | Crimson Invasion Elite Trainer Box | sm4 | 32 | 0 | 76 | 67.99 | 221.75 | 226.2% |  | 58.0%/yr | 2.84 | -7.1% | no | yes | no | no |
| 236,261 | Chilling Reign Elite Trainer Box [Shadow Rider Calyrex] | swsh6 | 32 | 0 | 33 | 46.65 | 152.04 | 225.9% |  | 58.0%/yr | 3.20 | -1.6% | no | yes | no | no |
| 155,664 | Ultra Prism Elite Trainer Box [Dusk Mane Necrozma] | sm5 | 31 | 1 | 73 | 230.32 | 741.96 | 222.1% |  | 57.3%/yr | 2.25 | -6.0% | no | no | no | no |
| 221,752 | Vivid Voltage Elite Trainer Box | swsh4 | 32 | 0 | 40 | 41.61 | 133.92 | 221.8% |  | 57.2%/yr | 2.52 | -10.0% | no | yes | no | no |
| 565,632 | Surging Sparks Pokemon Center Elite Trainer Box (Exclusive) | sv8 | 23 | 0 | 1 | 117.92 | 270.25 | 129.2% |  | 57.2%/yr | 1.29 | -33.5% | yes | no | yes | no |
| 194,729 | Hidden Fates Elite Trainer Box | sm115 | 32 | 0 | 55 | 176.31 | 564.69 | 220.3% |  | 56.9%/yr | 2.97 | -7.5% | no | yes | no | no |
| 512,801 | Paradox Rift Pokemon Center Elite Trainer Box (Exclusive) [Iron Valiant] | sv4 | 32 | 0 | 4 | 60.33 | 191.19 | 216.9% |  | 56.3%/yr | 2.00 | -14.3% | yes | yes | no | no |
| 118,331 | Fates Collide Elite Trainer Box | xy10 | 24 | 5 | 94 | 275.22 | 775.97 | 181.9% |  | 55.9%/yr | 1.95 | -9.9% | no | no | no | yes |
| 247,281 | Chilling Reign Pokemon Center Elite Trainer Box [Ice Rider Calyrex] (Exclusive) | swsh6 | 32 | 0 | 33 | 65.50 | 203.55 | 210.8% |  | 55.1%/yr | 1.96 | -14.4% | yes | yes | no | no |
| 543,845 | Twilight Masquerade Elite Trainer Box | sv6 | 29 | 0 | 1 | 37.85 | 104.86 | 177.0% |  | 54.8%/yr | 1.66 | -24.3% | no | no | yes | no |
| 228,821 | Shining Fates Elite Trainer Box | swsh45 | 32 | 0 | 37 | 44.57 | 136.37 | 206.0% |  | 54.2%/yr | 2.83 | -13.8% | no | yes | no | no |
| 236,260 | Chilling Reign Elite Trainer Box [Ice Rider Calyrex] | swsh6 | 32 | 0 | 33 | 46.47 | 140.67 | 202.7% |  | 53.5%/yr | 3.09 | -5.9% | no | yes | no | no |
| 206,039 | Sword & Shield Elite Trainer Box [Zamazenta] | swsh1 | 32 | 0 | 49 | 58.84 | 169.91 | 188.8% |  | 50.8%/yr | 3.23 | -3.7% | no | yes | no | no |
| 630,687 | Black Bolt Pokemon Center Elite Trainer Box (Exclusive) | zsv10pt5 | 15 | 0 | 1 | 166.85 | 268.87 | 61.1% |  | 50.5%/yr | 0.84 | -31.6% | yes | no | yes | no |
| 206,038 | Sword & Shield Elite Trainer Box [Zacian] | swsh1 | 32 | 0 | 49 | 61.65 | 171.89 | 178.8% |  | 48.7%/yr | 2.50 | -11.8% | no | yes | no | no |
| 155,663 | Ultra Prism Elite Trainer Box [Dawn Wings Necrozma] | sm5 | 30 | 2 | 73 | 263.49 | 711.99 | 170.2% |  | 46.9%/yr | 1.68 | -11.0% | no | no | no | no |
| 557,340 | Stellar Crown Pokemon Center Elite Trainer Box (Exclusive) | sv7 | 25 | 0 | 1 | 78.59 | 169.32 | 115.4% |  | 46.8%/yr | 1.01 | -44.5% | yes | no | yes | no |
| 532,853 | Temporal Forces Pokemon Center Elite Trainer Box (Exclusive) [Iron Leaves] | sv5 | 31 | 0 | 1 | 83.54 | 196.56 | 135.3% |  | 40.8%/yr | 1.40 | -24.9% | yes | no | yes | no |
| 610,930 | Journey Together Elite Trainer Box | sv9 | 19 | 0 | 1 | 81.14 | 135.53 | 67.0% |  | 40.8%/yr | 1.37 | -18.4% | no | no | yes | no |
| 630,688 | White Flare Pokemon Center Elite Trainer Box (Exclusive) | rsv10pt5 | 15 | 0 | 1 | 159.11 | 236.38 | 48.6% |  | 40.4%/yr | 0.78 | -31.0% | yes | no | yes | no |
| 648,394 | Mega Evolution Elite Trainer Box [Mega Lucario] | me1 | 13 | 0 | 1 | 92.52 | 127.30 | 37.6% |  | 37.6%/yr | 1.09 | -16.7% | no | no | yes | no |
| 565,630 | Surging Sparks Elite Trainer Box | sv8 | 23 | 0 | 1 | 69.00 | 121.54 | 76.1% |  | 36.2%/yr | 0.89 | -37.8% | no | no | yes | no |
| 210,572 | Rebel Clash Elite Trainer Box | swsh2 | 32 | 0 | 46 | 148.37 | 328.81 | 121.6% |  | 36.1%/yr | 2.60 | -9.3% | no | yes | no | no |
| 538,775 | Temporal Forces Pokemon Center Elite Trainer Box (Exclusive) [Walking Wake] | sv5 | 31 | 0 | 1 | 96.22 | 201.81 | 109.7% |  | 34.5%/yr | 0.78 | -29.1% | yes | no | yes | no |
| 593,324 | Prismatic Evolutions Pokemon Center Elite Trainer Box (Exclusive) | sv8pt5 | 21 | 0 | 1 | 262.31 | 410.57 | 56.5% |  | 30.8%/yr | 0.57 | -39.0% | yes | no | yes | no |
| 218,791 | Champion's Path Elite Trainer Box | swsh35 | 32 | 0 | 42 | 107.82 | 215.70 | 100.1% |  | 30.8%/yr | 2.11 | -13.4% | no | yes | no | no |
| 644,279 | Mega Evolution Elite Trainer Box [Mega Gardevoir] | me1 | 13 | 0 | 1 | 93.44 | 122.15 | 30.7% |  | 30.7%/yr | 0.79 | -20.0% | no | no | yes | no |
| 543,844 | Twilight Masquerade Pokemon Center Elite Trainer Box (Exclusive) | sv6 | 29 | 0 | 1 | 113.48 | 187.35 | 65.1% |  | 24.0%/yr | 0.71 | -36.5% | yes | no | yes | no |
| 593,355 | Prismatic Evolutions Elite Trainer Box | sv8pt5 | 21 | 0 | 1 | 101.63 | 138.55 | 36.3% |  | 20.4%/yr | 0.57 | -25.2% | no | no | yes | no |
| 624,676 | Destined Rivals Elite Trainer Box | sv10 | 17 | 0 | 1 | 94.78 | 116.12 | 22.5% |  | 16.5%/yr | 0.26 | -49.2% | no | no | yes | no |
| 610,929 | Journey Together Pokemon Center Elite Trainer Box (Exclusive) | sv9 | 19 | 0 | 1 | 156.12 | 194.57 | 24.6% |  | 15.8%/yr | 0.34 | -29.5% | yes | no | yes | no |
| 552,998 | Shrouded Fable Pokemon Center Elite Trainer Box (Exclusive) | sv6pt5 | 26 | 0 | 1 | 139.04 | 166.31 | 19.6% |  | 9.0%/yr | 0.20 | -51.4% | yes | no | yes | no |
| 648,415 | Mega Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Gardevoir] | me1 | 13 | 0 | 1 | 229.88 | 192.35 | -16.3% |  | -16.3%/yr | -0.33 | -36.8% | yes | no | yes | no |
| 644,282 | Mega Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Lucario] | me1 | 13 | 0 | 1 | 260.29 | 198.33 | -23.8% |  | -23.8%/yr | -0.35 | -40.8% | yes | no | yes | no |
| 98,028 | XY Roaring Skies Elite Trainer Box | xy6 | 11 | 1 | 122 | 1,597.50 | 4,899.99 | 206.7% |  | n/a | n/a | 0.0% | no | no | yes | yes |
| 654,136 | Phantasmal Flames Elite Trainer Box | me2 | 11 | 0 | 1 | 83.94 | 152.13 | 81.2% |  | n/a | n/a | -8.3% | no | no | yes | no |
| 670,607 | Prismatic Evolutions Elite Trainer Box (Dollar General Exclusive) | sv8pt5 | 10 | 0 | 12 | 127.95 | 199.49 | 55.9% |  | n/a | n/a | -2.4% | no | no | yes | no |
| 654,135 | Phantasmal Flames Pokemon Center Elite Trainer Box (Exclusive) | me2 | 11 | 0 | 1 | 192.67 | 287.82 | 49.4% |  | n/a | n/a | -16.6% | yes | no | yes | no |
| 668,497 | Ascended Heroes Pokemon Center Elite Trainer Box (Exclusive) | me2pt5 | 9 | 0 | 1 | 344.81 | 356.32 | 3.3% |  | n/a | n/a | -31.2% | yes | no | yes | no |
| 704,143 | 30th Celebration Elite Trainer Box | me55 | 1 | 0 | 1 | 162.45 | 162.45 | 0.0% |  | n/a | n/a | 0.0% | no | no | yes | no |
| 704,144 | 30th Celebration Pokemon Center Elite Trainer Box | me55 | 1 | 0 | 1 | 320.57 | 320.57 | 0.0% |  | n/a | n/a | 0.0% | yes | no | yes | no |
| 672,404 | Perfect Order Pokemon Center Elite Trainer Box | me3 | 7 | 0 | 1 | 123.45 | 122.85 | -0.5% |  | n/a | n/a | -16.3% | yes | no | yes | no |
| 692,947 | Pitch Black Elite Trainer Box | me5 | 3 | 0 | 1 | 78.81 | 76.31 | -3.2% |  | n/a | n/a | -10.3% | no | no | yes | no |
| 692,949 | Pitch Black Pokemon Center Elite Trainer Box (Exclusive) | me5 | 3 | 0 | 1 | 125.12 | 120.74 | -3.5% |  | n/a | n/a | -3.5% | yes | no | yes | no |
| 668,496 | Ascended Heroes Elite Trainer Box | me2pt5 | 9 | 0 | 1 | 161.94 | 153.64 | -5.1% |  | n/a | n/a | -33.1% | no | no | yes | no |
| 672,401 | Perfect Order Elite Trainer Box | me3 | 7 | 0 | 1 | 78.22 | 70.22 | -10.2% |  | n/a | n/a | -13.9% | no | no | yes | no |
| 684,450 | Chaos Rising Elite Trainer Box | me4 | 5 | 0 | 1 | 87.02 | 70.34 | -19.2% |  | n/a | n/a | -19.2% | no | no | yes | no |
| 684,452 | Chaos Rising Pokemon Center Elite Trainer Box | me4 | 5 | 0 | 1 | 212.33 | 125.92 | -40.7% |  | n/a | n/a | -40.7% | yes | no | yes | no |

### 7.4 Corrections to previously published figures

This repo discloses corrections rather than silently overwriting them. 14
figures below were published in earlier versions of `etb_summary.md`,
`etb_hold_summary.md` and `etb.html` and are **wrong**. They are recorded here,
machine-readably in `etb_corrections.csv`, with the live replacement resolved
from this build rather than stored -- so if a number moves again, this table
moves with it. Corrected 2026-07-25.

| figure | published (wrong) | corrected | moved | appeared in |
| --- | --- | --- | --- | --- |
| launch cohort, pooled trough (multiple of launch price) | 0.61x | 0.92x | revised up | etb_summary.md 4.3, etb.html |
| launch cohort at 12 months (multiple of launch price) | 1.00x | 1.56x | revised up | etb_summary.md 4.3, etb.html |
| share of the cohort below launch at month 2 | 100% | 62% | revised down | etb_summary.md 4.3 |
| mass-retail launch cohort at 12 months | 1.28x | 1.66x | revised up | etb_summary.md 4.3, etb.html |
| Pokemon Center launch cohort at 12 months | 0.78x | 1.46x | revised up | etb_summary.md 4.3, etb.html |
| launch cohort excess over the rest of the ETB market at 12 months | 0.47x | 0.78x | revised up | etb_summary.md 4.3, etb.html |
| post-launch median trough, as a fall from the launch price | 47.2% | 13.3% | revised down | etb_summary.md 6.4, etb_hold_summary.md |
| post-launch drop at a fixed 6-month endpoint | 38.1% | -0.8% | sign reversed | etb_hold_summary.md |
| share of launch-cohort products falling at least 25% | 66% | 22% | revised down | etb_summary.md 6.4, etb_hold_summary.md |
| 12-month net rate for "bought 0-6m after release" | 20.9% | 27.7% | revised up | etb_summary.md 6.4, etb_hold_summary.md 5 |
| share losing money, "bought 0-6m after release", 12-month hold | 30% | 20% | revised down | etb_summary.md 6.4, etb_hold_summary.md 5 |
| chained index of the "0-12m old at entry" cohort | 39.1% | 64.2% | revised up | etb_summary.md 1 and 4.4, etb.html |
| share of the "0-12m old at entry" cohort down over its own window | 35% | 18% | revised down | etb_summary.md 1 and 4.4 |
| t of the 1-3y cohort's difference from the youngest cohort | t = 2.86 | t = 1.28 | revised down | etb_summary.md 1 and 4.4, etb.html, etb_hold_summary.md 5 |

**One misunderstanding, 4 independent modules.** Every row traces to the same
wrong assumption: that a product's first priced row is a price somebody could
have paid. `price_history` is a snapshot taken on the 1st of each month and
essentially no Pokemon set ships on the 1st, so the month a product's listing
first appeared was normally a **pre-order quote on a box that had not shipped**
-- and those quotes are not cheap. (Since CALCULATIONS 9.3b they no longer enter
the panel at all: `price_history` drops every quote taken before the set's
release date.) Where a figure above is a ratio to that baseline the error did
not add noise, it moved the whole curve one way; where it is a bucket edge, it
silently mixed pre-order quotes in with shelf prices and made the group they
landed in look worse than it was. The launch-curve study, the holding study and
the cohort split each made the mistake separately, which is why the rule now
lives in one shared module (`etb_launch_anchor`) instead of being re-derived in
each.

A second, independent defect rode along in the launch curve: its x-axis counted
months since the listing first appeared rather than since launch, so a single
"month 2" pooled products at three different ages.

1 of these corrections **reversed the sign** of the published claim rather than
merely resizing it, which is the reason this table exists at all. The pre-order
quotes the corrected baseline refuses to use are themselves published -- 66 of
them, across 38 products, in `etb_lifecycle_pre_order_premium.csv`, read from
price_history's `presale_quotes.csv` now that the panel no longer holds them --
because how far a pre-order sits above the shelf price that follows is a finding
in its own right.
