# Are Elite Trainer Boxes going up, and is one worth holding?

The canonical ETB artifact. Everything below is computed live from
`price_history` and `data/output/etb_panel.csv` at write time -- no figure in
this document is typed by hand, and the per-product table behind every average
is published beside it as `data/output/etb_products.csv`.

Window **2024-03 .. 2026-11** (33 monthly observations, ONE regime) | **111 ETB
products** across **62 sets** | 2,940 product-months | headline index
**66.7%/yr**, HAC 95% CI [25.5%, 121.4%]

*This is measurement, not investment advice. Nothing here recommends buying,
holding or selling anything.*

---

## 1. The bottom line

**Yes, ETB prices went up a lot over 2024-03 .. 2026-11 -- about 66.7% a year,
an index multiple of 3.90x in 2.7 years. Four things immediately qualify that,
and each one is measured below rather than asserted.**

1. **The number is a construction choice.** Across the 15 defensible ways to
   build this index the answer spans 66.7% to 86.8%/yr -- a 20.1-point range.
   The headline above is the chained/geometric index over every product because
   that is the construction that admits the 43 products which entered
   mid-window. The higher numbers you will see quoted elsewhere -- including
   77.9%/yr -- come from a fixed basket that, by construction, can only contain
   products that already existed at the start AND survived to the end (section
   2.2).
2. **ETBs beat singles by a margin that clears the bar.** Against booster boxes
   over the same window with the same construction: +6.0pp/yr (t = 0.71).
   Against singles: +25.9pp/yr (t = 2.16). This repo's bar is |t| >= 2. See
   section 2.4 for the difference that clears the bar.
3. **Older product has the higher point estimates, but none of the AGE contrasts
   is established.** Of 2 contrasts against the youngest on-sale cohort, none
   clears this repo's significance bar. Product 1-3 years past release grew
   79.5%/yr against 59.6%/yr for boxes under a year old and on sale (t = 1.36);
   the 3y+ cohort grew 65.9%/yr (t = 0.19), BELOW the 1-3y figure, so the
   monotone "older is better" reading is not supported either (section 4.4). An
   earlier version of this report pooled pre-release entrants into the youngest
   cohort and concluded the 1-3y contrast WAS established; section 7.4 records
   that correction. The launch-side evidence is separate, and it is a RELATIVE
   statement: from the first price at which a box could actually be bought the
   launch cohort's average path dips to 0.92x and is at 1.56x a year on, but
   only 0.77x of what the rest of the ETB market did over the same months -- the
   new box went up and the category went up more (section 4.3). **That is a
   statement about growth RATES, and it is not the answer to "older ETBs sell at
   higher prices, no?".** That question is about price LEVELS, it is a different
   quantity, and section 4.6 answers it -- **yes**: at 2026-11 mass-retail price
   rises with age at Spearman rho = 0.805 (p = 2.7e-17, n = 71), a median $72 at
   <1yr (n = 5) against $877 at 8yr+ (n = 17). Two disclosures travel with it
   and are quoted in full in 4.6: within one calendar month age and release
   cohort are the SAME variable (R^2 = 1.000), so that rho ranks VINTAGES and
   cannot be read as an ageing curve; and only 65.4% of the same-era catalogue
   behind the oldest band is still priced at all, which puts that band's level
   somewhere in [$689.62, $1,800.00] rather than at its survivor median of
   $876.99 -- the bound is printed to the cent because rounding a
   distribution-free interval inwards makes it look tighter than it is. A level
   gradient is not a forecast: 4.6 publishes none.
4. **A holder does not keep the index.** Sales tax in, marketplace take out and
   shipping cost roughly 20.2% of the box plus $12.30 -- charged ONCE, which is
   why the answer is about time. At the measured growth rate a 3-month hold nets
   -43.6%/yr, a 12-month hold 29.3%/yr and a 24-month hold 48.0%/yr. In the
   realised data a 3-month flip lost money 81% of the time *during a boom*
   (section 6).

**So, is an ETB worth holding to sell later?** Stated as what this archive
measured rather than as advice: over this window a hold paid only when it ran
longer than 7 months (the point at which the one-time frictions amortise, at the
growth rate this window delivered), the box was retired rather than newly
released, and the market kept rising. That last condition did almost all of the
work and this data cannot speak to whether it repeats: the archive contains 33
months of a single boom whose deepest index drawdown was -4.1%. A fall of 48.7%
from here would erase the entire two-year edge over a savings account, and if
prices merely go FLAT a 12-month hold returns 0.75x -- a real loss, because the
frictions are charged anyway.

Two further answers, both negative, both worth having: the appreciation **cannot
be attributed to ageing** (age is collinear with calendar time by construction
here -- section 4.1), and **which** ETB will outperform **cannot be predicted**
at any horizon this archive can honestly test (section 5).

## 2. Did ETB prices go up?

### 2.1 The headline index

Chained, geometric, all products: base 100 at 2024-03 -> **390.4** at 2026-11,
i.e. **66.7%/yr**, HAC 95% CI [25.5%, 121.4%], t = 3.52 on 32 monthly log
returns with 3 Newey-West lags.

The standard error matters here. Monthly price levels in a boom are massively
autocorrelated, so an OLS standard error on a price trend is fiction; every
interval in this document is estimated on the mean monthly LOG RETURN with a HAC
covariance, which telescopes to exactly the endpoint growth rate but carries an
error bar that knows the months are not independent.

The median ETB was $66.75 in 2024-03 and $211.22 in 2026-11.

### 2.2 The headline moves a lot -- so the construction is the finding

| link | aggregator | survivorship | products | index end | CAGR | 95% lo | 95% hi |
| --- | --- | --- | --- | --- | --- | --- | --- |
| constant | geometric | all | 59 | 464.4 | 77.9%/yr | 33.5% | 137.0% |
| constant | arithmetic | all | 59 | 503.0 | 83.3%/yr | 33.0% | 152.6% |
| constant | value | all | 59 | 529.2 | 86.8%/yr | 43.6% | 143.0% |
| chained | geometric | all | 111 | 390.4 | 66.7%/yr | 25.5% | 121.4% |
| chained | arithmetic | all | 111 | 432.4 | 73.2%/yr | 29.3% | 131.9% |
| chained | value | all | 111 | 462.5 | 77.6%/yr | 38.6% | 127.6% |
| constant | geometric | exclude_delisted | 59 | 464.4 | 77.9%/yr | 33.5% | 137.0% |
| constant | arithmetic | exclude_delisted | 59 | 503.0 | 83.3%/yr | 33.0% | 152.6% |
| constant | value | exclude_delisted | 59 | 529.2 | 86.8%/yr | 43.6% | 143.0% |
| chained | geometric | exclude_delisted | 108 | 394.3 | 67.3%/yr | 25.5% | 123.0% |
| chained | arithmetic | exclude_delisted | 108 | 436.0 | 73.7%/yr | 29.3% | 133.3% |
| chained | value | exclude_delisted | 108 | 481.3 | 80.3%/yr | 39.6% | 132.7% |
| chained | geometric | full_history_only | 59 | 464.4 | 77.9%/yr | 33.5% | 137.0% |
| chained | arithmetic | full_history_only | 59 | 502.5 | 83.2%/yr | 36.5% | 145.9% |
| chained | value | full_history_only | 59 | 529.2 | 86.8%/yr | 43.6% | 143.0% |

Range: **66.7% to 86.8%/yr, 20.1 points apart**, median 77.9%. That spread is
not noise -- every cell is a defensible index -- so a single headline quoted
without its construction is unfalsifiable.

**Where the gap comes from, isolated cleanly:**

| construction | membership | products | CAGR |
| --- | --- | --- | --- |
| constant basket, geometric | full-history only (forced by construction) | 59 | 77.9%/yr |
| chained, geometric | full-history only (imposed) | 59 | 77.9%/yr |
| chained, geometric | every product (headline) | 111 | 66.7%/yr |

Rows 1 and 2 differ **only** by the linking method and they agree to 4.3e-14
percentage points, which is zero to machine precision -- on a balanced panel a
chained Jevons index equals the direct one exactly, and
`tests/test_etb_index.py` pins that identity. So the 11.2-point drop from row 2
to row 3 is **entirely** the 43 late-entering products, which compounded far
more slowly than the cohort that was already being priced in 2024-03.

That is a finding about the market, not a defect: a fixed basket cannot contain
a product that did not exist yet, so the high number is a survivor-cohort
number. It is also worth stating plainly that **the constant basket is identical
under the "all" and "exclude delisted" survivorship rules** -- it cannot measure
survivorship at all, because it has already excluded every non-survivor.

### 2.3 Robustness: does the result depend on how it was measured?

**The uncleaned universe.** A one-line `name LIKE '%elite trainer%'` query
returns 115 priced products, of which 63 span the window; its constant basket
grows 76.9%/yr and its chained index 66.4%/yr. The curated universe (which drops
multi-unit cases, "[Set of 2]" SKUs, code cards and the larger ETB Plus -- see
3.1) gives 77.9% and 66.7%: the cleaning moved the constant basket by +0.9pp and
the chained index by +0.3pp. **So the universe definition is not where the
headline comes from** -- which rules out the first thing a sceptic should check.

**A different price field.** Rebuilding on the cheapest live ask instead of the
trailing sales average:

| field | what it is | products | CAGR |
| --- | --- | --- | --- |
| `market` | TCGplayer market (trailing sales average) -- headline | 111 | 66.7%/yr |
| `low` | cheapest live ask | 111 | 72.6%/yr |

Same sign, same order of magnitude.

**Sub-periods.** The growth is not one early spike -- every sub-period below
rose:

| period | from | to | total | annualised |
| --- | --- | --- | --- | --- |
| full window | 2024-03 | 2026-11 | 290.4% | 66.7%/yr |
| first half | 2024-03 | 2025-07 | 118.2% | 79.5%/yr |
| second half | 2025-07 | 2026-11 | 78.9% | 54.7%/yr |
| trailing 12m | 2025-11 | 2026-11 | 32.0% | 32.0%/yr |
| trailing 6m | 2026-05 | 2026-11 | 5.9% | 12.1%/yr |

**Drawdown.** Worst peak-to-trough fall in the whole archive: **-4.1%** (2026-07
-> 2026-11), with 7 negative months out of 32 and a worst single month of -1.5%.
Read that as a warning, not comfort: an index that has never fallen more than
4.1% has not been tested.

**A second pipeline.** The pre-aggregated `sealed_index` table builds an ETB
series independently, at set level:

| source | unit | units | constant basket | chained | sets of this panel covered | share of panel sets |
| --- | --- | --- | --- | --- | --- | --- |
| price_history (this module) | product | 111 | 77.9%/yr | 66.7%/yr | 62 | 100% |
| sealed_index (pre-aggregated) | set | 62 | 75.4%/yr | 66.3%/yr | 62 | 100% |

They agree to 0.4 points on the chained index. The remaining difference is
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
| Pokemon Center exclusive | 37 | 67.0%/yr | 9.3% | 155.3% |
| Mass-retail | 74 | 67.4%/yr | 32.4% | 111.8% |

### 2.4 Against the rest of the market

Same window, same construction, and the difference is estimated on the PAIRED
monthly return difference so the common market tide cancels before the standard
error is formed. This is the decision-relevant statistic: not "did ETBs go up"
but "did ETBs beat the alternative".

| benchmark | units | its CAGR | ETB edge | t (HAC, paired) | clears \|t\| >= 2 |
| --- | --- | --- | --- | --- | --- |
| `booster_box` | 54 | 57.2%/yr | +6.0pp | 0.71 | no |
| `booster_bundle` | 27 | 57.0%/yr | +6.1pp | 0.73 | no |
| `singles` | 6,913 | 32.4%/yr | +25.9pp | 2.16 | yes |

**1 of 3 benchmark differences clear the bar** (singles). The singles benchmark
also deserves a caveat in the other direction: it is an equal-weighted index of
6,913 cards above a $1 floor, so it is dominated by cheap commons and probably
understates what a comparable singles portfolio did.

### 2.5 Dispersion -- what the average hides

Per-product growth, over the 100 products with enough history to annualise: p10
28.3%/yr, median 64.5%/yr, p90 110.7%/yr -- an interquartile range of 32 points.
2% of them went DOWN, and 68% have growth that clears |t| >= 2 on their own
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
| SKU (product) | 111 | 59 | 59 | 66.7%/yr | 77.9%/yr | 28.4%/yr |
| set (release event) | 62 | 35 | 35 | 67.1%/yr | 75.8%/yr | 28.4%/yr |

The index level barely moves (+0.4pp on the chained construction), so the
equal-weight-by-SKU choice is not what produced the headline. The floor: the
worst single SKU grew 28.4%/yr, the worst whole SET 28.4%/yr. Both are true; the
SKU figure is the honest answer to "what is the worst thing I could have bought"
and the set figure to "how many distinct releases went up". Every one of the 35
full-history SETS rose, which is the version of "all of them rose" that survives
clustering.

### 2.7 Is it still going, and is it ETBs?

Section 2.1 measures the whole window. A reader who wants to act on it is asking
something narrower -- *is this still true now* -- so the same index is re-read
on its trailing 12 months (2025-11 to 2026-11) and the benchmark null from 2.4
is re-run inside that sub-window.

**Still going, and not detectably slower.** The trailing 12 months compound at
32.0%/yr [-11.1%, 96.1%] against 66.7%/yr over the full window -- the same
number within its interval. Tested directly rather than eyeballed, a
last-12-months dummy on monthly log returns (Newey-West, 3 lags) gives
-3.1pp/month, t = -1.36, p = 0.17: **no detectable change in pace**. Read that
as ruling out a collapse and nothing more -- its standard error is 2.28pp/month
against a mean of about 4.3pp, so it could only have caught roughly a halving. 7
of the archive's months were negative and the worst drawdown inside the recent
window was -4.1%.

**It is broad, not a handful of boxes.** 81 of 93 products priced at both ends
rose (87%), median 1.38x, and even the 10th percentile is 0.95x. Concentration
is mild: the top decile of movers carries 22% of the summed log rise, 2.25x its
even share. But breadth is narrowing -- on a cohort held fixed across both
halves, the share rising went 100% to 95%.

The 12 products that fell are named rather than averaged away: Scarlet & Violet
Pokemon Center Elite Trainer Box (Exclusive) [Koraidon] (0.84x); Mega Evolution
Pokemon Center Elite Trainer Box (Exclusive) [Mega Gardevoir] (0.87x); Temporal
Forces Pokemon Center Elite Trainer Box (Exclusive) [Walking Wake] (0.87x); Mega
Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Lucario] (0.88x),
and 8 more. Check release dates before reading that as a category signal -- a
box still inside its launch window is showing the cooldown measured in section
4.3, not a market turn.

**Still not an ETB story.** The benchmark comparison from 2.4, recomputed inside
the recent window:

| window | vs | ETBs | them | gap | lo | hi | t | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| trailing 12m | Booster boxes | 32.0%/yr | 18.0%/yr | +11.9pp | -19.2pp | +55.0pp | 0.68 | no detectable difference |
| trailing 12m | Booster bundles | 32.0%/yr | 45.4%/yr | -9.2pp | -18.3pp | +0.8pp | -1.80 | no detectable difference |
| trailing 12m | Singles | 32.0%/yr | 44.1%/yr | -8.4pp | -24.8pp | +11.7pp | -0.86 | no detectable difference |
| full window (32m) | Booster boxes | 66.7%/yr | 57.2%/yr | +6.0pp | -9.8pp | +24.6pp | 0.71 | no detectable difference |
| full window (32m) | Booster bundles | 66.7%/yr | 57.0%/yr | +6.1pp | -9.6pp | +24.7pp | 0.73 | no detectable difference |
| full window (32m) | Singles | 66.7%/yr | 32.4%/yr | +25.9pp | +2.2pp | +55.1pp | 2.16 | differs |

1 of 6 judgeable comparisons differ from ETBs. **So inside the recent window the
null from section 2.4 does NOT hold for every benchmark** -- read the rows that
differ before calling the recent rise a market-wide one. These are low-power
nulls -- the trailing-12-month intervals run roughly -19.2pp to +55.0pp -- so
the honest claim is "cannot be distinguished", not "they are the same".

9 shorter-window comparisons are computed and printed in
`etb_recent_benchmarks.csv` but excluded from every verdict above, because an
interval built on a handful of monthly observations is not one. That gate is
load-bearing rather than decorative: the most extreme of those excluded rows is
trailing 3m ETBs vs singles at t = -6.05 on 3 monthly returns, and quoting it
would have published a significant result off a window whose sign does not
survive to twelve months.

**The one split that does show a gap is channel, and it is the weakest inference
here.** Mass-retail boxes ran 1.52x against 1.09x for Pokemon Center exclusives
(39.4%, t = 8.65). Differencing two groups cancels the market-wide factor but
NOT a channel-specific one -- a Pokemon Center release calendar or a restock
decision leaves the within-channel residuals correlated -- so that t is an upper
bound on the evidence, not a clean test. Age bands and price quartiles show no
monotone ordering (`etb_recent_drivers_*.csv`).

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
| constant-basket geometric CAGR | 77.9%/yr | 77.9%/yr |
| full-history basket | -- | 59 products |
| of which rose | -- | 59 |
| worst / median member | -- | 28.4%/yr / 70.6%/yr |

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
| `MIXED_LOT` | 4 | 0 | Ascended Heroes Elite Trainer Box and Pokeball (Sam's Club) |
| `ETB_PLUS` | 4 | 4 | Pokemon GO Pokemon Center Elite Trainer Box Plus (Exclusive) |

The exclusions that actually cost priced products are the multi-unit SKUs (cases
and "[Set of 2]" listings, whose price level is not one box) and ETB Plus (a
physically different, larger product). Section 2.3 shows that putting them back
RAISES the naive headline rather than lowering it, so this cleaning is not what
produced the result.

### 3.2 Coverage, stated as a weakness

111 products x 33 months would be 3,663 observations; the panel has 2,940. The
shortfall is entirely structural. The obvious two-way framing -- "either it
started late or it was delisted" -- is wrong twice over here, so the split below
is mutually exclusive and exhaustive by construction and the code raises if the
buckets stop summing to 111:

| coverage shape | products | share | what it is |
| --- | --- | --- | --- |
| complete | 59 | 53% | priced in every month of the grid |
| late start only | 42 | 38% | a newer release; enters mid-window and never leaves |
| delisted only | 2 | 2% | priced from the start, then stops being listed |
| late start and delisted | 1 | 1% | enters mid-window AND stops before the end |
| interior gap only | 7 | 6% | spans the full window but is missing months inside it |

The two buckets a two-way split loses are the last two: products that start late
AND vanish before the end, and products that span the whole window with holes in
the middle. For the latter, "first price" and "last price" are not the ends of a
continuous series. Separately from all of this, 11 products are observed too
briefly to annualise at all and are published with a blank CAGR rather than an
annualised 3-month number, and 11 products have at least one interior hole, the
largest 18 months. The chained index never forms a return across a hole; it
simply drops that product from that month's link.

### 3.3 Survivorship bias runs the OPPOSITE way to the reflex

The reflex assumption is that dropping the products that vanished flatters an
index, because they were collapsing. In this archive they were not. Every
delisted product's trailing 3-month return before it stopped being priced:

| product | last priced | months observed | last $ | trailing 3m |
| --- | --- | --- | --- | --- |
| Ancient Origins Elite Trainer Box | 2025-10 | 13 | 2,625.00 | 43.2% |
| Elite Trainer Box [Mewtwo X] | 2026-06 | 16 | 900.00 | 0.0% |
| Fates Collide Elite Trainer Box | 2026-07 | 24 | 775.97 | -0.9% |

1 of 3 were still RISING when they disappeared and 1 were falling (median 0.0%).
So a survivor-only basket is missing continued appreciation, not hiding a
collapse -- this particular bias makes the constant-basket number, if anything,
conservative. It is a different bias (missing the slow late entrants) that
inflates it, and section 2.2 quantifies that one at 11.2 points.

### 3.4 What the prices are, and are not

`market` is TCGplayer's trailing sales average. It is a quote, not an execution:
nobody transacted at the index, and section 6 is the correction for that. Two
specific things a reader should not assume:

* **There is no bid in this data.** `low`/`high` are the cheapest and dearest
  ASKS. Anything computed from `high - low` is a listing dispersion, not a
  spread -- the naive calculation gives a "spread" of 211% of the market price
  (section 6.6).
* **TCGplayer-Direct quotes do not exist for sealed product.** `direct_low` is
  NULL for every sealed row in the archive, so the direct-discount feature the
  singles models use is structurally unavailable here and was excluded rather
  than carried as an all-missing column.

### 3.5 The claim this study was asked to falsify

This study was commissioned around a preliminary headline: a constant-basket
geometric index on the raw catalogue query, with every full-history product
positive. **Both halves of that reproduce exactly, and neither should be the
headline.** Recomputed live on the uncleaned universe: **76.9%/yr**, over 63
full-history products of which **63 rose and 0 fell**.

It is not a calculation error. It is the wrong object, for the reason section
2.2 isolates -- it is a survivor-cohort index, and the "all positive" property
is true *by construction of which products get a full history*, not because ETBs
do not fall. The curated panel makes that visible: 12 of 111 products are down
over their own window, of which 12 are late entrants and 0 are full-history
products. A fixed basket cannot contain a single one of the fallers.

The honest headline is 66.7%/yr with a 95% interval of [25.5%, 121.4%], and even
that is one cell of a 20.1-point grid.

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
are the same regressor over 33 months of one regime.

This is the classic age-period-cohort problem, and it is not fixable with more
cleverness -- a two-way fixed-effects age curve here would be reporting its own
normalisation, not a fact. What the lifecycle module publishes instead is the
FAN of answers you get from the three standard identifying restrictions, each of
which fits every observed price identically (largest fitted-price change across
the three restrictions: 7.3e-14, measured rather than asserted): a ten-year
ageing multiple anywhere from **0.89x to 670.14x** -- a **757x** span that is
pure assumption.

Anyone who tells you how much an ETB appreciates per year *because it aged* is
choosing one point in that fan.

### 4.2 What IS identified: the shape, not the slope

Slope CHANGES need no identifying assumption -- they survive the fixed effects.
Joint test that the age profile is linear: **chi2(5) = 27.5, p = 4.6e-05**. The
profile bends, decisively.

| age (months) | slope change (log/yr) | SE | t | significant | products crossing |
| --- | --- | --- | --- | --- | --- |
| 12 | 0.275 | 0.101 | 2.71 | yes | 40 |
| 24 | 0.060 | 0.100 | 0.60 | no | 36 |
| 36 | -0.208 | 0.062 | -3.37 | yes | 36 |
| 60 | -0.009 | 0.076 | -0.12 | no | 25 |
| 84 | 0.033 | 0.070 | 0.48 | no | 15 |

The normalisation-free contrast between the young band and the mature band
(12-24m -> 36-60m) is **-0.148 log/yr (t = -1.71)**: that contrast does not
clear the bar, so neither "it takes off once it is retired" nor its opposite is
established.

**Two caveats that cut the shape down, both published in
`etb_lifecycle_stability.csv`:**

1. The acceleration at 12 months **vanishes** once the launch cohort is
   excluded, so it is the launch cooldown ending, not a property of one-year-old
   boxes (-0.102, t = -0.58).
2. The deceleration is estimated almost entirely from the first calendar half;
   in the second half it is indistinguishable from zero (0.080, t = 1.19). Of 6
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
**1.47x** of the first price the box actually opened at, above it for 92% of the
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
0.76x and is still 0.77x at twelve months. The new box ended its first year
BEHIND the rest of the ETB market (0.76x at the trough, 0.77x at 12 months);
booster boxes (0.79x at the trough, 0.88x at 12 months) -- against those, buying
it was the worse of the two. It ended the year level with or AHEAD of singles
(0.88x at the trough, 1.11x at 12 months).

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
| 0-12m old at entry | 50 | 22 | 59.6%/yr | 5.4% | 141.6% | 52.3%/yr | 24% | n/a | n/a |
| 1-3y old at entry | 27 | 12 | 79.5%/yr | 28.8% | 150.2% | 77.0%/yr | 0% | +12.5pp | 1.36 |
| 3y+ old at entry | 34 | 29 | 65.9%/yr | 33.5% | 106.1% | 63.0%/yr | 0% | +3.9pp | 0.19 |

Reading the rows against each other:

* The youngest ON-SALE cohort's own index grew 59.6%/yr with t = 2.21 --
  **distinguishable from flat** at the same bar. 24% of those boxes are down
  over their own window.
* Product 1-3 years past release grew 79.5%/yr; its paired difference against
  the youngest on-sale cohort **does not clear the bar** (t = 1.36).
* Product 3+ years past release grew 65.9%/yr; its difference **does not clear
  the bar** (t = 0.19), and it sits BELOW the 1-3y cohort in point estimate, so
  this is not a monotone "older is better" effect even before the error bars are
  drawn.

**This corrects a previously published reading.** With pre-release entrants
pooled into the youngest cohort, that cohort's index came out at 39.1%/yr and
"not distinguishable from flat", and the 1-3y contrast against it cleared the
significance bar at t = 2.86 -- which is where the claim "the gains belong to
out-of-print product" came from. Taking the pre-order quotes out (first as a
separate cohort, now at ingest, CALCULATIONS 9.3b) moves the youngest on-sale
cohort to 59.6%/yr and leaves the 1-3y contrast at t = 1.36. The 1-3y cohort
still has the higher point estimate; what does not survive is the claim that any
of the AGEING contrasts was tested. See section 7.4.

Note also the sample these contrasts rest on: buckets of 27 to 50 SKUs, which
are only 12 to 29 distinct releases (the `sets` column above), all sharing ONE
33-month calendar window -- a post-hoc slice of a small panel, not an
experiment.

### 4.5 Reprints: the obvious mechanism, and why this data cannot test it

If "out of print" is the mechanism, a reprint should hurt. The lifecycle module
looked for that and **refuses to answer**: of 26 large idiosyncratic drops (<=
-20% after removing the month's cross-sectional mean), 18 are products under a
year old (launch cooldown) and only 8 are out-of-print product.
`reprint_analysis_supportable` returns **no**. In-print status is not a field in
this database at all; age is the only proxy, and it is labelled as one
everywhere.

What the shocks do show, for whatever it is worth on 26 events, is that they do
NOT mean-revert. The cumulative idiosyncratic return is -0.29 at impact and
-0.35 six months later. Whatever caused a big ETB drop in this window, the price
did not come back inside half a year.

### 4.6 Do older ETBs sell for more today? Yes -- and that is not an ageing curve

This is the owner's own observation, and it is correct as a statement about
today's shelf. It is also the single easiest number in this study to misread, so
the gradient and the reason it cannot be extrapolated are stated together
throughout: **at 2026-11, mass-retail ETB price rises with age at Spearman rho =
0.805 (p = 2.7e-17, n = 71) -- and within a single calendar month a product's
age IS its release cohort, with R^2 = 1.000, so that rho ranks vintages and
cannot separate "boxes gain value as they age" from "boxes made in 2016 are
scarcer than boxes made in 2026".** Neither half of that sentence is quotable
without the other.

Three things qualify it further, all measured.

**It is strongest in mass retail.** Pokemon Center exclusives give rho = 0.408
(p = 0.01, n = 37) -- distinguishable from zero but weaker than mass-retail's,
and no PC product in the archive is older than about 5 years. The pooled rho =
0.620 is therefore partly a statement about which channel happens to be old.

**The shape is not a trend, and this sample cannot order the bands.**

| age band | products | median price | lo | hi | sets |
| --- | --- | --- | --- | --- | --- |
| <1yr | 5 | $72 | $69 | $120 | 5 |
| 1-2yr | 9 | $136 | $114 | $154 | 7 |
| 2-3yr | 7 | $128 | $113 | $161 | 6 |
| 3-5yr | 13 | $163 | $136 | $207 | 11 |
| 5-8yr | 20 | $265 | $145 | $502 | 16 |
| 8yr+ | 17 | $877 | $712 | $1,499 | 15 |

Every row of that table is a different set of products bought in a different
decade -- it is a vintage ranking, printed by age because that is how the
question was asked. The medians do NOT rise monotonically: there are 1
inversions, the worst being 1-2yr -> 2-3yr at -6.1% -- the dip the owner
noticed. Of those 1 dips, 0 separate at the bootstrap median interval, and the
step up into the oldest band does separate -- supplying 76% of the whole
top-to-bottom range by itself. With 71 products spread over 6 bands and a long
right tail, **the band ORDER above is not established by this sample apart from
the step into the oldest band** -- the owner's dip included. The point estimates
are what they are; their ordering is not. The counterweight is kept honestly the
other way too: dropping the vintage band entirely still leaves rho = 0.656 (p =
7.2e-08, n = 54) and a fitted 28.1%/yr against 31.8%/yr on the full sample, so
the gradient is not only the vintage tail.

**The oldest band is where the level lives and where the sample is worst.** Only
65.4% of same-era mass-retail vintage SKUs are still priced at all (17 of 26; 9
are absent, several with zero priced months anywhere in the archive), against
83-100% in every younger band. Assuming only that the absentees have *some*
price, the distribution-free bound on that band's median runs [$690, $1,800]
against a survivor median of $877 -- a 2.61x span from survivorship alone.
Trading is thin there too: 82% of vintage products have their market estimate
BELOW the cheapest live ask (every band's share is in
`etb_agevalue_thinness.csv`) and 3 have one listing. The obvious explanation --
smaller print runs -- is **unmeasurable here**: no print-run figure exists
anywhere in this database, and the catalogue-breadth proxy comes out at 0.96,
pointing AWAY from the scarcity story rather than supporting it. That reading is
published rather than suppressed, and it does not clear the confound: the proxy
has no resolution at the 2016-vs-2026 distance.

#### Will a box bought today follow them up? The cross-section cannot say, and the panel says no

The gradient is a fact about products that already exist. Turning it into a
holding period requires that ageing CAUSES the gap, which is the one thing R^2 =
1.000 forbids. The panel answers the question the cross-section cannot, because
it watches the same box age.

Across 100 products with a full price path, mass-retail in-window appreciation
runs 67.8%/yr median with 0% negative. Its dependence on age is +2.5pp/yr per
year of age (t = 1.87) -- **no age dependence distinguishable from zero**.
Excluding products still inside their launch window it is +2.7pp/yr (t = 1.48):
older boxes appreciated more *quickly*, the sign an ageing reading of the
cross-section predicts. The headline null is the conservative statement and the
one to quote; the excl-launch cut is a post-hoc slice of one regime, published
because its sign is decision-relevant, not because it establishes that age is
good for a box.

Put on one scale: the cross-sectional gradient implies 108.9% over the median
observed span, while boxes actually returned 266.9%. The gradient can account
for at most 57% of the realised log move -- an upper bound, since it credits the
whole implied part to age. **The rest is calendar, and no box bought today can
assume it.** That ceiling is a bound on how much of the gradient an ageing story
could be carrying; it is not a finding that "57% of ETB appreciation is ageing".

The natural experiment settles the shape question the same way: 2 of 2
cross-sectional inversions are contradicted by the products that actually made
the crossing.

| channel | from | to | cross-section implies | boxes that crossed | they actually did | contradicted |
| --- | --- | --- | --- | --- | --- | --- |
| mass_retail | 1-2yr | 2-3yr | -6.1% | 7 | 306.1% | yes |
| pokemon_center | 1-2yr | 2-3yr | -21.5% | 5 | 367.1% | yes |

The headline one is the owner's dip: mass retail 1-2yr -> 2-3yr implies -6.1%,
and the 7 boxes that genuinely aged past that boundary returned 306.1% median
[300.8%, 452.9%]. The cross-sectional dip is a fact about which sets sit in each
band today, not about what happens to a box that crosses 1-2yr -> 2-3yr.

**No forecast follows.** `projection_support` reports `forecast_supported = no`
with a maximum measured horizon of 32 months. `etb_agevalue_illustrative.csv`
multiplies three readings of this same data out to 5 and 10 years with every row
flagged `is_measured = False`:

on a $72 box at 10 years -- *flat in nominal terms* -> 1.00x ($72); *today's box
walks the current cross-section* -> 15.01x ($1,075); *the 2024-2026 rate
continues* -> 176.68x ($12,645). Every one of those is an ASSUMPTION carried
forward, not a measurement, and they disagree by a factor of 177.

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
| 1 | 26 | 0.273 | 8.77 | 3.26 | yes |
| 3 | 22 | 0.011 | 5.01 | 0.08 | no |
| 6 | 16 | -0.122 | 3.00 | -1.04 | no |
| 12 | 4 | -0.314 | 1.00 | -1.39 | no |

At the pre-registered primary horizon of 6 months the mean held-out rank
correlation is **-0.122** -- the point estimate is NEGATIVE -- on an effective
sample of 3.00 against the repo's 4.0 bar. At H = 12 there are only **4** usable
folds, holding at most 1 non-overlapping one-year windows: a 33-month archive
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
| mid_skew -> market | 0.265 | 4.57 | 10.96 |
| mid_skew -> book mid | -0.233 | -4.67 | 11.61 |
| mid_skew -> gap change | -0.435 | -16.06 | 26.00 |

A high skew predicts the market price RISING and the book midpoint FALLING, with
the gap between them closing. That is two measurements of one price converging,
not a forecast of value.

**Economics.** The top-quintile portfolio at H = 1 returns 152.1%/yr against the
basket's 88.1%/yr -- an edge of +64.0pp gross (t = 2.72). Twelve rebalances a
year at the round-trip cost from section 6 is a 85.8pp drag, so the NET edge is
-21.8pp. It loses to doing nothing.

**The model beats its own best single input only at H = 12.**

| horizon | best single feature | its IC | fitted model IC | which wins |
| --- | --- | --- | --- | --- |
| 1 | `mid_skew` | 0.265 | 0.273 | tie |
| 3 | `mid_skew` | 0.270 | 0.011 | the single feature |
| 6 | `mid_skew` | 0.270 | -0.122 | the single feature |
| 12 | `rel_spread` | -0.383 | -0.314 | model |

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
answer by 17.2 points a year.

### 6.1 The frictions are a one-time toll, not a rate

Round trip: 7.5% sales tax in, 12.75% marketplace take out, $12.00 to ship a
heavy box. That is roughly **20.2% of the box price plus $12.30 fixed**, charged
once. Because it is charged once, it amortises -- which is the whole answer to
"how long should I hold".

At the measured gross index rate of 66.7%/yr, on a $211 box (the median ETB
price in 2026-11):

| hold (months) | gross | net | net rate | friction drag | gross growth needed to beat cash | beats cash |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | 1.14x | 0.87x | -43.6%/yr | 110.2pp/yr | 198.2%/yr | no |
| 6 | 1.29x | 0.99x | -1.8%/yr | 68.5pp/yr | 76.8%/yr | no |
| 12 | 1.67x | 1.29x | 29.3%/yr | 37.3pp/yr | 36.1%/yr | yes |
| 24 | 2.78x | 2.19x | 48.0%/yr | 18.7pp/yr | 19.4%/yr | yes |

**The minimum hold to beat a 4.5% savings account is 7 months** (8 months on a
cheap box, 6 on an expensive one -- shipping and the flat fee do not scale). The
fee structure is regime-independent arithmetic; the floor it implies is not,
because it compounds the growth rate this window happened to deliver against
those fees (`etb_hold_summary.md` section 7 shows it across assumed rates).

An OPTIMAL hold is a different matter and the study declines to name one: the
best observed horizon was 24 months at 65.4%/yr net, but a 32-month archive
contains exactly 1 non-overlapping window of that length. One window is an
anecdote.

### 6.2 What actually happened, box by box

42,334 realised holding periods across 111 products, all net of costs:

| hold | holding periods | independent windows | median net | 5th pct | 95th pct | share that lost money |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | 2,583 | 10 | 0.82x | 0.55x | 1.23x | 81% |
| 6 | 2,263 | 5 | 0.98x | 0.61x | 1.62x | 52% |
| 12 | 1,667 | 2 | 1.39x | 0.85x | 2.76x | 12% |
| 24 | 648 | 1 | 2.73x | 1.63x | 6.36x | 0% |

**A three-month flip lost money 81% of the time during a boom.** Six months was
a coin flip (52%). Twelve months lost 12% of the time. A product-clustered
bootstrap puts the median 12-month net rate at 39.4%/yr, 95% CI [34.2%, 47.1%]
over 98 products.

Note the two 12-month numbers in this document that DISAGREE: applying the
chained index rate uniformly gives 29.3%/yr, while the pooled realised holds
give 39.4%/yr. They are different objects -- pooling triples over-weights
long-history products, and the index is spread evenly over a window that did not
grow evenly. The gap, 10.0 points, is 27% of the 37.3-point twelve-month
friction drag -- a warning about how much of any of these numbers is a
construction choice.

### 6.3 One box is not the index

| products | 10th pct box | median box | 90th pct box | the basket | middle-50% spread | share worse than basket |
| --- | --- | --- | --- | --- | --- | --- |
| 98 | 0.97x | 1.39x | 2.42x | 1.44x | 70pp | 49% |

At twelve months the middle 50% of single-box outcomes spans about 70 annualised
points and 49% of picks did worse than simply owning the basket.

### 6.4 When you bought: age at purchase

| bought when | holds | products | median net rate | share that lost money |
| --- | --- | --- | --- | --- |
| bought 0-6m after release | 130 | 32 | 26.6%/yr | 21% |
| bought 6-12m after release | 154 | 30 | 47.2%/yr | 16% |
| bought 1-3y after release | 547 | 50 | 50.7%/yr | 10% |
| bought 3y+ after release | 836 | 55 | 35.2%/yr | 12% |

Buying inside six months of release and holding a year lost money 21% of the
time; buying product already 1-3 years old lost 10% of the time. No row is dated
before a set's street date: pre-order quotes never enter this panel
(CALCULATIONS 9.3b), so every buy above is at a post-release price.

The mechanism is measured, not assumed. Of 38 products with an observed first
ON-SALE price, the median trough over the following six months was 13.6% below
it (IQR 4.3% to 24.0%) and 24% fell at least 25%. Measured at a fixed six-month
endpoint rather than at a minimum -- which is not selection-prone -- the median
is 0.4%, i.e. the typical box was 0.4% below its first on-sale price at that
endpoint.

**This corrects a figure this study previously published.** The same statistic
measured from each product's first LISTED quote gives 49.9% at the trough and
46.0% at the endpoint, across 40 products -- a gap of 36.3 points on the median
(product-bootstrap 95% CI 19.8 to 43.4). That is the number this report used to
carry. It was wrong: `price_history` is snapshotted on the 1st and essentially
no set ships on the 1st, so a product's first listed quote is normally a
pre-order ask on a box that has not shipped -- no longer part of the panel, and
read back from `presale_quotes.csv` for this comparison only -- and the old
figure was largely that ask deflating rather than a box losing value. Both arms
are computed (first on-sale price vs first listed price) so the comparison is
auditable rather than asserted. A buyer who paid the pre-order price ate the
difference either way. See section 7.4.

### 6.5 The downside

Two numbers, both regime-facing:

* **Flat is not break-even.** If prices merely stop rising, a 12-month hold
  returns 0.75x -- a 24.8% annualised loss, because the frictions are charged
  anyway.
* **A fall of 48.7% from the terminal price erases the entire 24-month edge over
  a savings account**, and 52.8% turns it into a nominal loss. That is about 65%
  of the gain -- it does not require prices to return to where they started.

At 24 months the net answer keeps its sign under every sensitivity cell; at 6
months the same knobs move it across zero (-30.5% to 30.9%/yr), so short-horizon
verdicts are assumptions rather than measurements.

### 6.6 One brief the data contradicted

This study was briefed on a "~15-20% bid-ask on thin sealed listings". **The
archive does not support that**, and the obvious way to compute it is wrong.
`price_history` carries a LISTING book -- `low` is the cheapest ask, `high` the
dearest -- and no bid at all. Treating `high - low` as a spread gives a median
of 211% of the market price, because `high` has a median of 3.13x market. What
IS measurable: `low/market` has a median of 0.977, and a round trip executed at
`low` on both ends returned a median 1.028x of what a market-to-market round
trip returned, with only 33% of products worse off. The measurable spread very
nearly cancels. The holder's real loss is fees, tax and shipping -- which is why
the undercut constant defaults to zero and is swept to 15% anyway (worth 11.9
points a year), because "not measurable" is not "zero".

## 7. Limitations, and the data itself

### 7.1 The window is the finding's ceiling

**33 monthly observations, 2024-03 .. 2026-11, one regime.** Everything above
happened inside a historic Pokemon sealed boom. The index's worst peak-to-trough
fall in the entire archive is -4.1%. There is no bust in this data, so nothing
here measures what happens in one, and no interval printed above is a forecast
interval -- the HAC bands are sampling uncertainty WITHIN the boom. Statistical
uncertainty here is small; regime uncertainty is everything.

The archive does not go back further because it cannot: tcgcsv's price archive
begins in 2024-03, and the sources that would extend it (eBay, PriceCharting)
are excluded on terms-of-service grounds. "The last few years" means 2.7 years.

### 7.2 Everything else worth knowing before quoting a number

* **The headline is a construction choice.** The 15-cell grid spans 66.7% to
  86.8%/yr. Any single figure quoted without its construction is unfalsifiable.
* **Prices are TCGplayer quotes, not executions.** `market` is a trailing sales
  average; nobody transacted at the index. Section 6 is the correction, and its
  cost constants are stated assumptions, not fetched facts.
* **The age effect is unidentified** (section 4.1) and the ML layer is a null at
  the primary horizon (section 5). Neither is a placeholder for a result that is
  coming later; both are the answer this data supports.
* **11 of 111 products are observed for fewer than the 12 months required to
  annualise.** Their cumulative return is a fact and is published; their CAGR is
  blank rather than a number like -99.9%/yr, which is what annualising a 3-month
  window produces.
* **11 products have interior holes** in their series (a month with no priced
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
|t| >= 2 on their own Newey-West error bar and 12 are down over their observed
window. Those are SKU counts: 111 SKUs are 62 sets (1.79 per set), so divide by
roughly that before treating them as independent (section 2.6).

**Read the `total spans a gap?` column.** 3 rows carry `GAP`, meaning at least 6
months between the product's first and last observation have no price at all.
For those rows `total` compares two prices with a hole between them and the
terminal price may be a single illiquid relisting rather than a market move; the
blank-CAGR gate protects the ANNUALISED column but not this one.

| id | product | set | months | gaps | age at entry (m) | first $ | last $ | total | total spans a gap? | CAGR | t (HAC) | worst drawdown | PC | full | late | gone |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 98,028 | XY Roaring Skies Elite Trainer Box | xy6 | 12 | 5 | 122 | 1,597.50 | 7,899.99 | 394.5% |  | 231.6%/yr | 5.78 | 0.0% | no | no | yes | no |
| 501,999 | 151 Pokemon Center Elite Trainer Box (Exclusive) | sv3pt5 | 33 | 0 | 6 | 94.65 | 1,173.14 | 1,139.5% |  | 157.0%/yr | 3.02 | -15.9% | yes | yes | no | no |
| 528,040 | Paldean Fates Elite Trainer Box | sv4pt5 | 33 | 0 | 2 | 41.49 | 435.34 | 949.3% |  | 141.5%/yr | 2.97 | -21.7% | no | yes | no | no |
| 501,266 | Obsidian Flames Pokemon Center Elite Trainer Box (Exclusive) | sv3 | 33 | 0 | 7 | 64.27 | 614.08 | 855.5% |  | 133.1%/yr | 2.16 | -25.8% | yes | yes | no | no |
| 503,313 | 151 Elite Trainer Box | sv3pt5 | 33 | 0 | 6 | 53.31 | 493.84 | 826.4% |  | 130.4%/yr | 2.98 | -23.7% | no | yes | no | no |
| 247,671 | Fusion Strike Elite Trainer Box | swsh8 | 33 | 0 | 28 | 40.91 | 338.29 | 726.9% |  | 120.8%/yr | 3.81 | -10.2% | no | yes | no | no |
| 247,673 | Fusion Strike Pokemon Center Elite Trainer Box (Exclusive) | swsh8 | 33 | 0 | 28 | 58.10 | 462.36 | 695.8% |  | 117.7%/yr | 2.65 | -9.6% | yes | yes | no | no |
| 181,704 | Team Up Elite Trainer Box | sm9 | 33 | 0 | 61 | 506.90 | 4,000.00 | 689.1% |  | 117.0%/yr | 3.56 | -3.1% | no | yes | no | no |
| 528,039 | Paldean Fates Pokemon Center Elite Trainer Box (Exclusive) | sv4pt5 | 33 | 0 | 2 | 70.80 | 542.15 | 665.7% |  | 114.6%/yr | 2.08 | -21.7% | yes | yes | no | no |
| 493,973 | Paldea Evolved Pokemon Center Elite Trainer Box (Exclusive) | sv2 | 33 | 0 | 9 | 79.88 | 594.28 | 644.0% |  | 112.2%/yr | 2.63 | -18.9% | yes | yes | no | no |
| 170,277 | Celestial Storm Elite Trainer Box | sm7 | 33 | 0 | 67 | 287.20 | 2,091.30 | 628.2% |  | 110.5%/yr | 3.49 | -6.8% | no | yes | no | no |
| 501,264 | Obsidian Flames Elite Trainer Box | sv3 | 33 | 0 | 7 | 37.16 | 266.98 | 618.5% |  | 109.5%/yr | 2.63 | -16.4% | no | yes | no | no |
| 245,352 | Evolving Skies Pokemon Center Elite Trainer Box [Glaceon/Vaporeon/Sylveon/Espeon] (Exclusive) | swsh7 | 33 | 0 | 31 | 155.50 | 1,115.49 | 617.4% |  | 109.4%/yr | 4.91 | -2.1% | yes | yes | no | no |
| 453,470 | Crown Zenith Elite Trainer Box | swsh12pt5 | 33 | 0 | 14 | 42.75 | 302.73 | 608.1% |  | 108.4%/yr | 3.20 | -12.4% | no | yes | no | no |
| 557,350 | Stellar Crown Elite Trainer Box | sv7 | 26 | 0 | 1 | 37.69 | 161.28 | 327.9% |  | 100.9%/yr | 2.84 | -7.6% | no | no | yes | no |
| 123,741 | Generations Elite Trainer Box | g1 | 33 | 0 | 97 | 602.32 | 3,833.33 | 536.4% |  | 100.2%/yr | 3.12 | -5.9% | no | yes | no | no |
| 493,974 | Paldea Evolved Elite Trainer Box | sv2 | 33 | 0 | 9 | 35.16 | 207.31 | 489.6% |  | 94.5%/yr | 2.71 | -17.5% | no | yes | no | no |
| 193,052 | Unified Minds Elite Trainer Box | sm11 | 33 | 0 | 55 | 291.86 | 1,719.90 | 489.3% |  | 94.5%/yr | 3.06 | -10.8% | no | yes | no | no |
| 245,376 | Evolving Skies Pokemon Center Elite Trainer Box [Jolteon/Flareon/Umbreon/Leafeon] (Exclusive) | swsh7 | 33 | 0 | 31 | 185.66 | 1,087.99 | 486.0% |  | 94.1%/yr | 4.41 | -1.0% | yes | yes | no | no |
| 277,336 | Lost Origin Pokemon Center Elite Trainer Box (Exclusive) | swsh11 | 33 | 0 | 18 | 63.87 | 372.19 | 482.7% |  | 93.7%/yr | 2.25 | -17.8% | yes | yes | no | no |
| 242,434 | Evolving Skies Elite Trainer Box [Flareon/Jolteon/Umbreon/Leafeon] | swsh7 | 33 | 0 | 31 | 95.48 | 550.57 | 476.6% |  | 92.9%/yr | 4.24 | -8.5% | no | yes | no | no |
| 277,335 | Lost Origin Elite Trainer Box | swsh11 | 33 | 0 | 18 | 35.08 | 193.96 | 452.9% |  | 89.9%/yr | 3.27 | -16.3% | no | yes | no | no |
| 242,443 | Evolving Skies Elite Trainer Box [Glaceon/Vaporeon/Sylveon/Espeon] | swsh7 | 33 | 0 | 31 | 82.74 | 456.18 | 451.3% |  | 89.7%/yr | 3.38 | -15.4% | no | yes | no | no |
| 654,136 | Phantasmal Flames Elite Trainer Box | me2 | 12 | 0 | 1 | 83.94 | 147.31 | 75.5% |  | 84.7%/yr | 1.39 | -8.3% | no | no | yes | no |
| 283,401 | Silver Tempest Elite Trainer Box | swsh12 | 33 | 0 | 16 | 30.50 | 156.10 | 411.8% |  | 84.5%/yr | 3.00 | -14.9% | no | yes | no | no |
| 285,860 | Silver Tempest Pokemon Center Elite Trainer Box (Exclusive) | swsh12 | 33 | 0 | 16 | 74.31 | 377.92 | 408.6% |  | 84.0%/yr | 3.22 | -5.4% | yes | yes | no | no |
| 111,280 | XY BREAKpoint Elite Trainer Box | xy9 | 31 | 0 | 99 | 240.00 | 1,099.99 | 358.3% |  | 83.9%/yr | 2.47 | -3.3% | no | no | yes | no |
| 185,719 | Unbroken Bonds Elite Trainer Box | sm10 | 21 | 12 | 58 | 376.23 | 1,899.99 | 405.0% | GAP | 83.5%/yr | 2.83 | -1.0% | no | no | no | no |
| 107,107 | Elite Trainer Box [Mewtwo Y] | xy8 | 28 | 3 | 102 | 331.98 | 1,499.00 | 351.5% |  | 82.8%/yr | 2.44 | 0.0% | no | no | yes | no |
| 199,308 | Cosmic Eclipse Elite Trainer Box | sm12 | 31 | 2 | 52 | 381.14 | 1,874.50 | 391.8% |  | 81.7%/yr | 2.82 | -2.6% | no | no | no | no |
| 256,140 | Brilliant Stars Pokemon Center Elite Trainer Box (Exclusive) | swsh9 | 33 | 0 | 25 | 51.25 | 241.50 | 371.2% |  | 78.8%/yr | 2.35 | -18.5% | yes | yes | no | no |
| 478,758 | Scarlet & Violet Pokemon Center Elite Trainer Box (Exclusive) [Koraidon] | sv1 | 33 | 0 | 12 | 61.50 | 287.26 | 367.1% |  | 78.2%/yr | 1.99 | -19.0% | yes | yes | no | no |
| 145,847 | Shining Legends Elite Trainer Box | sm35 | 33 | 0 | 77 | 266.92 | 1,199.66 | 349.4% |  | 75.7%/yr | 3.91 | -0.4% | no | yes | no | no |
| 256,138 | Brilliant Stars Elite Trainer Box | swsh9 | 33 | 0 | 25 | 37.38 | 167.90 | 349.2% |  | 75.7%/yr | 3.31 | -20.1% | no | yes | no | no |
| 164,303 | Forbidden Light Elite Trainer Box | sm6 | 32 | 1 | 70 | 153.97 | 689.62 | 347.9% |  | 75.5%/yr | 3.04 | -9.6% | no | no | no | no |
| 624,675 | Destined Rivals Pokemon Center Elite Trainer Box (Exclusive) | sv10 | 18 | 0 | 1 | 183.11 | 403.76 | 120.5% |  | 74.7%/yr | 1.07 | -27.9% | yes | no | yes | no |
| 129,890 | Guardians Rising Elite Trainer Box | sm2 | 30 | 3 | 82 | 105.41 | 461.86 | 338.2% |  | 74.0%/yr | 5.15 | -3.8% | no | no | no | no |
| 107,106 | Elite Trainer Box [Mewtwo X] | xy8 | 16 | 0 | 112 | 453.99 | 900.00 | 98.2% |  | 72.9%/yr | 2.11 | -2.3% | no | no | yes | yes |
| 251,199 | Celebrations Pokemon Center Elite Trainer Box (Exclusive) | cel25 | 33 | 0 | 29 | 110.31 | 471.21 | 327.2% |  | 72.4%/yr | 2.00 | -17.8% | yes | yes | no | no |
| 478,756 | Scarlet & Violet Pokemon Center Elite Trainer Box (Exclusive) [Miraidon] | sv1 | 33 | 0 | 12 | 74.94 | 315.77 | 321.4% |  | 71.5%/yr | 2.25 | -13.8% | yes | yes | no | no |
| 512,813 | Paradox Rift Elite Trainer Box [Iron Valiant] | sv4 | 33 | 0 | 4 | 32.70 | 135.87 | 315.5% |  | 70.6%/yr | 2.92 | -10.1% | no | yes | no | no |
| 175,511 | Lost Thunder Elite Trainer Box | sm8 | 33 | 0 | 64 | 176.62 | 729.80 | 313.2% |  | 70.2%/yr | 2.79 | -3.6% | no | yes | no | no |
| 242,811 | Celebrations Elite Trainer Box | cel25 | 33 | 0 | 29 | 77.37 | 319.67 | 313.2% |  | 70.2%/yr | 2.05 | -35.8% | no | yes | no | no |
| 270,708 | Pokemon GO Elite Trainer Box | pgo | 33 | 0 | 20 | 40.25 | 163.46 | 306.1% |  | 69.1%/yr | 3.21 | -8.2% | no | yes | no | no |
| 478,335 | Scarlet & Violet Elite Trainer Box [Koraidon] | sv1 | 33 | 0 | 12 | 32.52 | 132.00 | 305.9% |  | 69.1%/yr | 3.01 | -8.0% | no | yes | no | no |
| 478,336 | Scarlet & Violet Elite Trainer Box [Miraidon] | sv1 | 33 | 0 | 12 | 35.95 | 144.10 | 300.8% |  | 68.3%/yr | 2.84 | -10.4% | no | yes | no | no |
| 123,447 | XY Evolutions Elite Trainer Box [Mega Charizard Y] | xy12 | 33 | 0 | 88 | 220.03 | 876.99 | 298.6% |  | 68.0%/yr | 3.48 | -12.0% | no | yes | no | no |
| 552,999 | Shrouded Fable Elite Trainer Box | sv6pt5 | 27 | 0 | 1 | 36.71 | 112.69 | 207.0% |  | 67.8%/yr | 1.94 | -21.1% | no | no | yes | no |
| 123,448 | XY Evolutions Elite Trainer Box [Mega Blastoise] | xy12 | 33 | 0 | 88 | 191.99 | 762.56 | 297.2% |  | 67.7%/yr | 4.12 | -4.6% | no | yes | no | no |
| 532,845 | Temporal Forces Elite Trainer Box [Walking Wake] | sv5 | 32 | 0 | 1 | 39.91 | 145.26 | 264.0% |  | 64.9%/yr | 2.67 | -15.4% | no | no | yes | no |
| 216,856 | Darkness Ablaze Elite Trainer Box | swsh3 | 33 | 0 | 43 | 33.74 | 126.48 | 274.9% |  | 64.1%/yr | 2.74 | -16.9% | no | yes | no | no |
| 265,528 | Astral Radiance Pokemon Center Elite Trainer Box (Exclusive) | swsh10 | 33 | 0 | 22 | 49.11 | 181.61 | 269.8% |  | 63.3%/yr | 2.03 | -24.0% | yes | yes | no | no |
| 265,527 | Astral Radiance Elite Trainer Box | swsh10 | 33 | 0 | 22 | 33.56 | 124.10 | 269.8% |  | 63.3%/yr | 2.20 | -19.1% | no | yes | no | no |
| 630,686 | Black Bolt Elite Trainer Box | zsv10pt5 | 16 | 0 | 1 | 84.46 | 154.37 | 82.8% |  | 62.0%/yr | 1.35 | -13.7% | no | no | yes | no |
| 120,697 | Steam Siege Elite Trainer Box | xy11 | 15 | 18 | 91 | 499.00 | 1,800.00 | 260.7% | GAP | 61.8%/yr | 1.67 | -18.2% | no | no | no | no |
| 512,815 | Paradox Rift Elite Trainer Box [Roaring Moon] | sv4 | 33 | 0 | 4 | 37.03 | 133.50 | 260.5% |  | 61.8%/yr | 2.45 | -14.4% | no | yes | no | no |
| 532,848 | Temporal Forces Elite Trainer Box [Iron Leaves ex] | sv5 | 32 | 0 | 1 | 36.85 | 127.56 | 246.2% |  | 61.7%/yr | 2.54 | -17.4% | no | no | yes | no |
| 229,284 | Battle Styles Elite Trainer Box [Single Strike Urshifu] (Red) | swsh5 | 33 | 0 | 36 | 37.64 | 132.77 | 252.7% |  | 60.4%/yr | 2.99 | -8.2% | no | yes | no | no |
| 229,285 | Battle Styles Elite Trainer Box [Rapid Strike Urshifu] (Blue) | swsh5 | 33 | 0 | 36 | 36.47 | 128.34 | 251.9% |  | 60.3%/yr | 2.91 | -4.4% | no | yes | no | no |
| 133,776 | Burning Shadows Elite Trainer Box | sm3 | 33 | 0 | 79 | 98.56 | 346.28 | 251.3% |  | 60.2%/yr | 4.28 | -0.3% | no | yes | no | no |
| 100,495 | Ancient Origins Elite Trainer Box | xy7 | 13 | 7 | 103 | 1,250.00 | 2,625.00 | 110.0% | GAP | 59.8%/yr | 1.90 | 0.0% | no | no | no | yes |
| 512,809 | Paradox Rift Pokemon Center Elite Trainer Box (Exclusive) [Roaring Moon] | sv4 | 33 | 0 | 4 | 62.35 | 215.44 | 245.5% |  | 59.2%/yr | 2.11 | -12.7% | yes | yes | no | no |
| 221,752 | Vivid Voltage Elite Trainer Box | swsh4 | 33 | 0 | 40 | 41.61 | 142.16 | 241.6% |  | 58.5%/yr | 2.67 | -10.0% | no | yes | no | no |
| 247,282 | Chilling Reign Pokemon Center Elite Trainer Box [Shadow Rider Calyrex] (Exclusive) | swsh6 | 33 | 0 | 33 | 56.98 | 191.93 | 236.8% |  | 57.7%/yr | 2.19 | -10.9% | yes | yes | no | no |
| 155,664 | Ultra Prism Elite Trainer Box [Dusk Mane Necrozma] | sm5 | 32 | 1 | 73 | 230.32 | 760.77 | 230.3% |  | 56.5%/yr | 2.30 | -6.0% | no | no | no | no |
| 149,377 | Crimson Invasion Elite Trainer Box | sm4 | 33 | 0 | 76 | 67.99 | 224.48 | 230.2% |  | 56.5%/yr | 2.85 | -7.1% | no | yes | no | no |
| 118,331 | Fates Collide Elite Trainer Box | xy10 | 24 | 5 | 94 | 275.22 | 775.97 | 181.9% |  | 55.9%/yr | 1.95 | -9.9% | no | no | no | yes |
| 173,393 | Dragon Majesty Elite Trainer Box | sm75 | 33 | 0 | 66 | 381.99 | 1,228.24 | 221.5% |  | 55.0%/yr | 2.91 | -7.3% | no | yes | no | no |
| 247,281 | Chilling Reign Pokemon Center Elite Trainer Box [Ice Rider Calyrex] (Exclusive) | swsh6 | 33 | 0 | 33 | 65.50 | 209.26 | 219.5% |  | 54.6%/yr | 2.00 | -14.4% | yes | yes | no | no |
| 228,821 | Shining Fates Elite Trainer Box | swsh45 | 33 | 0 | 37 | 44.57 | 142.09 | 218.8% |  | 54.5%/yr | 2.95 | -13.9% | no | yes | no | no |
| 236,261 | Chilling Reign Elite Trainer Box [Shadow Rider Calyrex] | swsh6 | 33 | 0 | 33 | 46.65 | 148.60 | 218.5% |  | 54.4%/yr | 3.03 | -2.3% | no | yes | no | no |
| 512,801 | Paradox Rift Pokemon Center Elite Trainer Box (Exclusive) [Iron Valiant] | sv4 | 33 | 0 | 4 | 60.33 | 189.46 | 214.0% |  | 53.6%/yr | 1.97 | -14.3% | yes | yes | no | no |
| 630,689 | White Flare Elite Trainer Box | rsv10pt5 | 16 | 0 | 1 | 81.19 | 138.46 | 70.5% |  | 53.3%/yr | 1.44 | -10.4% | no | no | yes | no |
| 194,729 | Hidden Fates Elite Trainer Box | sm115 | 33 | 0 | 55 | 176.31 | 547.35 | 210.4% |  | 52.9%/yr | 2.78 | -7.5% | no | yes | no | no |
| 236,260 | Chilling Reign Elite Trainer Box [Ice Rider Calyrex] | swsh6 | 33 | 0 | 33 | 46.47 | 142.00 | 205.6% |  | 52.0%/yr | 3.07 | -5.9% | no | yes | no | no |
| 543,845 | Twilight Masquerade Elite Trainer Box | sv6 | 30 | 0 | 1 | 37.85 | 103.13 | 172.5% |  | 51.4%/yr | 1.61 | -24.3% | no | no | yes | no |
| 206,039 | Sword & Shield Elite Trainer Box [Zamazenta] | swsh1 | 33 | 0 | 49 | 58.84 | 173.84 | 195.4% |  | 50.1%/yr | 3.32 | -3.7% | no | yes | no | no |
| 206,038 | Sword & Shield Elite Trainer Box [Zacian] | swsh1 | 33 | 0 | 49 | 61.65 | 179.10 | 190.5% |  | 49.2%/yr | 2.60 | -11.8% | no | yes | no | no |
| 557,340 | Stellar Crown Pokemon Center Elite Trainer Box (Exclusive) | sv7 | 26 | 0 | 1 | 78.59 | 180.74 | 130.0% |  | 49.1%/yr | 1.10 | -44.5% | yes | no | yes | no |
| 654,135 | Phantasmal Flames Pokemon Center Elite Trainer Box (Exclusive) | me2 | 12 | 0 | 1 | 192.67 | 276.89 | 43.7% |  | 48.5%/yr | 0.72 | -19.2% | yes | no | yes | no |
| 565,632 | Surging Sparks Pokemon Center Elite Trainer Box (Exclusive) | sv8 | 24 | 0 | 1 | 117.92 | 245.36 | 108.1% |  | 46.6%/yr | 1.10 | -33.5% | yes | no | yes | no |
| 155,663 | Ultra Prism Elite Trainer Box [Dawn Wings Necrozma] | sm5 | 31 | 2 | 73 | 263.49 | 711.99 | 170.2% |  | 45.2%/yr | 1.66 | -11.0% | no | no | no | no |
| 630,687 | Black Bolt Pokemon Center Elite Trainer Box (Exclusive) | zsv10pt5 | 16 | 0 | 1 | 166.85 | 261.26 | 56.6% |  | 43.2%/yr | 0.77 | -31.6% | yes | no | yes | no |
| 630,688 | White Flare Pokemon Center Elite Trainer Box (Exclusive) | rsv10pt5 | 16 | 0 | 1 | 159.11 | 241.76 | 51.9% |  | 39.7%/yr | 0.83 | -31.0% | yes | no | yes | no |
| 532,853 | Temporal Forces Pokemon Center Elite Trainer Box (Exclusive) [Iron Leaves] | sv5 | 32 | 0 | 1 | 83.54 | 197.48 | 136.4% |  | 39.5%/yr | 1.40 | -24.9% | yes | no | yes | no |
| 610,930 | Journey Together Elite Trainer Box | sv9 | 20 | 0 | 1 | 81.14 | 135.89 | 67.5% |  | 38.5%/yr | 1.36 | -18.4% | no | no | yes | no |
| 538,775 | Temporal Forces Pokemon Center Elite Trainer Box (Exclusive) [Walking Wake] | sv5 | 32 | 0 | 1 | 96.22 | 212.25 | 120.6% |  | 35.8%/yr | 0.83 | -29.1% | yes | no | yes | no |
| 210,572 | Rebel Clash Elite Trainer Box | swsh2 | 33 | 0 | 46 | 148.37 | 323.19 | 117.8% |  | 33.9%/yr | 2.52 | -9.3% | no | yes | no | no |
| 565,630 | Surging Sparks Elite Trainer Box | sv8 | 24 | 0 | 1 | 69.00 | 119.87 | 73.7% |  | 33.4%/yr | 0.87 | -37.8% | no | no | yes | no |
| 218,791 | Champion's Path Elite Trainer Box | swsh35 | 33 | 0 | 42 | 107.82 | 210.19 | 94.9% |  | 28.4%/yr | 1.97 | -14.0% | no | yes | no | no |
| 648,394 | Mega Evolution Elite Trainer Box [Mega Lucario] | me1 | 14 | 0 | 1 | 92.52 | 119.54 | 29.2% |  | 26.7%/yr | 0.83 | -16.7% | no | no | yes | no |
| 593,324 | Prismatic Evolutions Pokemon Center Elite Trainer Box (Exclusive) | sv8pt5 | 22 | 0 | 1 | 262.31 | 385.39 | 46.9% |  | 24.6%/yr | 0.48 | -39.0% | yes | no | yes | no |
| 543,844 | Twilight Masquerade Pokemon Center Elite Trainer Box (Exclusive) | sv6 | 30 | 0 | 1 | 113.48 | 185.52 | 63.5% |  | 22.6%/yr | 0.69 | -36.5% | yes | no | yes | no |
| 644,279 | Mega Evolution Elite Trainer Box [Mega Gardevoir] | me1 | 14 | 0 | 1 | 93.44 | 114.50 | 22.5% |  | 20.6%/yr | 0.58 | -20.0% | no | no | yes | no |
| 610,929 | Journey Together Pokemon Center Elite Trainer Box (Exclusive) | sv9 | 20 | 0 | 1 | 156.12 | 193.45 | 23.9% |  | 14.5%/yr | 0.33 | -29.5% | yes | no | yes | no |
| 593,355 | Prismatic Evolutions Elite Trainer Box | sv8pt5 | 22 | 0 | 1 | 101.63 | 120.72 | 18.8% |  | 10.3%/yr | 0.29 | -34.8% | no | no | yes | no |
| 624,676 | Destined Rivals Elite Trainer Box | sv10 | 18 | 0 | 1 | 94.78 | 107.31 | 13.2% |  | 9.2%/yr | 0.15 | -53.1% | no | no | yes | no |
| 552,998 | Shrouded Fable Pokemon Center Elite Trainer Box (Exclusive) | sv6pt5 | 27 | 0 | 1 | 139.04 | 163.22 | 17.4% |  | 7.7%/yr | 0.18 | -51.4% | yes | no | yes | no |
| 648,415 | Mega Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Gardevoir] | me1 | 14 | 0 | 1 | 229.88 | 191.63 | -16.6% |  | -15.5%/yr | -0.34 | -36.8% | yes | no | yes | no |
| 644,282 | Mega Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Lucario] | me1 | 14 | 0 | 1 | 260.29 | 201.14 | -22.7% |  | -21.2%/yr | -0.34 | -40.8% | yes | no | yes | no |
| 670,607 | Prismatic Evolutions Elite Trainer Box (Dollar General Exclusive) | sv8pt5 | 11 | 0 | 12 | 127.95 | 196.23 | 53.4% |  | n/a | n/a | -3.0% | no | no | yes | no |
| 672,404 | Perfect Order Pokemon Center Elite Trainer Box | me3 | 8 | 0 | 1 | 123.45 | 122.02 | -1.2% |  | n/a | n/a | -16.3% | yes | no | yes | no |
| 692,949 | Pitch Black Pokemon Center Elite Trainer Box (Exclusive) | me5 | 4 | 0 | 1 | 125.12 | 119.77 | -4.3% |  | n/a | n/a | -4.3% | yes | no | yes | no |
| 668,497 | Ascended Heroes Pokemon Center Elite Trainer Box (Exclusive) | me2pt5 | 10 | 0 | 1 | 344.81 | 326.75 | -5.2% |  | n/a | n/a | -36.9% | yes | no | yes | no |
| 672,401 | Perfect Order Elite Trainer Box | me3 | 8 | 0 | 1 | 78.22 | 71.57 | -8.5% |  | n/a | n/a | -13.9% | no | no | yes | no |
| 692,947 | Pitch Black Elite Trainer Box | me5 | 4 | 0 | 1 | 78.81 | 70.87 | -10.1% |  | n/a | n/a | -10.3% | no | no | yes | no |
| 704,144 | 30th Celebration Pokemon Center Elite Trainer Box | me55 | 2 | 0 | 1 | 319.60 | 277.19 | -13.3% |  | n/a | n/a | -13.3% | yes | no | yes | no |
| 684,450 | Chaos Rising Elite Trainer Box | me4 | 6 | 0 | 1 | 87.02 | 69.03 | -20.7% |  | n/a | n/a | -20.7% | no | no | yes | no |
| 704,143 | 30th Celebration Elite Trainer Box | me55 | 2 | 0 | 1 | 158.18 | 117.82 | -25.5% |  | n/a | n/a | -25.5% | no | no | yes | no |
| 668,496 | Ascended Heroes Elite Trainer Box | me2pt5 | 10 | 0 | 1 | 161.94 | 120.37 | -25.7% |  | n/a | n/a | -33.1% | no | no | yes | no |
| 684,452 | Chaos Rising Pokemon Center Elite Trainer Box | me4 | 6 | 0 | 1 | 212.33 | 120.18 | -43.4% |  | n/a | n/a | -43.4% | yes | no | yes | no |

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
| launch cohort excess over the rest of the ETB market at 12 months | 0.47x | 0.77x | revised up | etb_summary.md 4.3, etb.html |
| post-launch median trough, as a fall from the launch price | 47.2% | 13.6% | revised down | etb_summary.md 6.4, etb_hold_summary.md |
| post-launch drop at a fixed 6-month endpoint | 38.1% | 0.4% | revised down | etb_hold_summary.md |
| share of launch-cohort products falling at least 25% | 66% | 24% | revised down | etb_summary.md 6.4, etb_hold_summary.md |
| 12-month net rate for "bought 0-6m after release" | 20.9% | 26.6% | revised up | etb_summary.md 6.4, etb_hold_summary.md 5 |
| share losing money, "bought 0-6m after release", 12-month hold | 30% | 21% | revised down | etb_summary.md 6.4, etb_hold_summary.md 5 |
| chained index of the "0-12m old at entry" cohort | 39.1% | 59.6% | revised up | etb_summary.md 1 and 4.4, etb.html |
| share of the "0-12m old at entry" cohort down over its own window | 35% | 24% | revised down | etb_summary.md 1 and 4.4 |
| t of the 1-3y cohort's difference from the youngest cohort | t = 2.86 | t = 1.36 | revised down | etb_summary.md 1 and 4.4, etb.html, etb_hold_summary.md 5 |

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

None of these corrections reverses the sign of the published claim on this
build; each one only resizes it. The pre-order quotes the corrected baseline
refuses to use are themselves published -- 66 of them, across 38 products, in
`etb_lifecycle_pre_order_premium.csv`, read from price_history's
`presale_quotes.csv` now that the panel no longer holds them -- because how far
a pre-order sits above the shelf price that follows is a finding in its own
right.
