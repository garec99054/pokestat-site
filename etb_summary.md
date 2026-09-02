# Are Elite Trainer Boxes going up, and is one worth holding?

The canonical ETB artifact. Everything below is computed live from
`price_history` and `data/output/etb_panel.csv` at write time -- no figure in
this document is typed by hand, and the per-product table behind every average
is published beside it as `data/output/etb_products.csv`.

Window **2024-03 .. 2026-09** (31 monthly observations, ONE regime) | **108 ETB
products** across **60 sets** | 2,756 product-months | headline index
**59.1%/yr**, HAC 95% CI [22.2%, 107.2%]

*This is measurement, not investment advice. Nothing here recommends buying,
holding or selling anything.*

---

## 1. The bottom line

**Yes, ETB prices went up a lot over 2024-03 .. 2026-09 -- about 59.1% a year,
an index multiple of 3.19x in 2.5 years. Four things immediately qualify that,
and each one is measured below rather than asserted.**

1. **The number is a construction choice.** Across the 15 defensible ways to
   build this index the answer spans 58.8% to 90.5%/yr -- a 31.7-point range.
   The headline above is the chained/geometric index over every product because
   that is the construction that admits the 37 products which entered
   mid-window. The higher numbers you will see quoted elsewhere -- including
   81.7%/yr -- come from a fixed basket that, by construction, can only contain
   products that already existed at the start AND survived to the end (section
   2.2).
2. **ETBs did not beat the rest of sealed.** Against booster boxes over the same
   window with the same construction: -0.3pp/yr (t = -0.03). Against singles:
   +13.8pp/yr (t = 1.04), which does not clear this repo's |t| >= 2 bar. "ETBs
   went up" is largely "the Pokemon market went up" (section 2.4).
3. **Older product has the higher point estimates, but none of the AGE contrasts
   is established.** Of 3 contrasts against the youngest on-sale cohort, 1
   clears this repo's significance bar -- and the one that does is the
   PRE-RELEASE cohort, i.e. products bought at a pre-order quote, which is a
   statement about quotes rather than about age. Product 1-3 years past release
   grew 89.7%/yr against 64.5%/yr for boxes under a year old and on sale, but
   that difference does not clear the bar (t = 1.21); nor does the 3y+ one (t =
   0.12) at 68.9%/yr, which is BELOW the 1-3y figure, so the monotone "older is
   better" reading is not supported either (section 4.4). An earlier version of
   this report pooled pre-release entrants into the youngest cohort and
   concluded the 1-3y contrast WAS established; section 7.4 records that
   correction. The launch-side evidence is separate, and it is a RELATIVE
   statement rather than a negative one: from the first price at which a box
   could actually be bought the launch cohort's average path dips to 0.93x and
   reaches 1.68x a year on, but only 0.79x of what the rest of the ETB market
   did over the same months -- the new box went up and the category went up more
   (section 4.3). **That is a statement about growth RATES, and it is not the
   answer to "older ETBs sell at higher prices, no?".** That question is about
   price LEVELS, it is a different quantity, and section 4.6 answers it --
   **yes**: at 2026-09 mass-retail price rises with age at Spearman rho = 0.719
   (p = 6.9e-12, n = 67), a median $73 at <1yr (n = 5) against $831 at 8yr+ (n =
   15). Two disclosures travel with it and are quoted in full in 4.6: within one
   calendar month age and release cohort are the SAME variable (R^2 = 1.000), so
   that rho ranks VINTAGES and cannot be read as an ageing curve; and only 60.0%
   of the same-era catalogue behind the oldest band is still priced at all,
   which puts that band's level somewhere in [$421.79, $1,800.00] rather than at
   its survivor median of $830.82 -- the bound is printed to the cent because
   rounding a distribution-free interval inwards makes it look tighter than it
   is. A level gradient is not a forecast: 4.6 publishes none.
4. **A holder does not keep the index.** Sales tax in, marketplace take out and
   shipping cost roughly 20.2% of the box plus $12.30 -- charged ONCE, which is
   why the answer is about time. At the measured growth rate a 3-month hold nets
   -45.8%/yr, a 12-month hold 23.4%/yr and a 24-month hold 41.1%/yr. In the
   realised data a 3-month flip lost money 80% of the time *during a boom*
   (section 6).

**So, is an ETB worth holding to sell later?** Stated as what this archive
measured rather than as advice: over this window a hold paid only when it ran
longer than 8 months (the point at which the one-time frictions amortise, at the
growth rate this window delivered), the box was retired rather than newly
released, and the market kept rising. That last condition did almost all of the
work and this data cannot speak to whether it repeats: the archive contains 31
months of a single boom whose deepest index drawdown was -3.4%. A fall of 43.8%
from here would erase the entire two-year edge over a savings account, and if
prices merely go FLAT a 12-month hold returns 0.75x -- a real loss, because the
frictions are charged anyway.

Two further answers, both negative, both worth having: the appreciation **cannot
be attributed to ageing** (age is collinear with calendar time by construction
here -- section 4.1), and **which** ETB will outperform **cannot be predicted**
at any horizon this archive can honestly test (section 5).

## 2. Did ETB prices go up?

### 2.1 The headline index

Chained, geometric, all products: base 100 at 2024-03 -> **319.2** at 2026-09,
i.e. **59.1%/yr**, HAC 95% CI [22.2%, 107.2%], t = 3.45 on 30 monthly log
returns with 3 Newey-West lags.

The standard error matters here. Monthly price levels in a boom are massively
autocorrelated, so an OLS standard error on a price trend is fiction; every
interval in this document is estimated on the mean monthly LOG RETURN with a HAC
covariance, which telescopes to exactly the endpoint growth rate but carries an
error bar that knows the months are not independent.

The median ETB was $67.99 in 2024-03 and $218.37 in 2026-09.

### 2.2 The headline moves a lot -- so the construction is the finding

| link | aggregator | survivorship | products | index end | CAGR | 95% lo | 95% hi |
| --- | --- | --- | --- | --- | --- | --- | --- |
| constant | geometric | all | 62 | 445.3 | 81.7%/yr | 35.3% | 144.1% |
| constant | arithmetic | all | 62 | 496.2 | 89.8%/yr | 37.9% | 161.1% |
| constant | value | all | 62 | 500.8 | 90.5%/yr | 44.8% | 150.5% |
| chained | geometric | all | 108 | 319.2 | 59.1%/yr | 22.2% | 107.2% |
| chained | arithmetic | all | 108 | 374.6 | 69.6%/yr | 29.0% | 123.1% |
| chained | value | all | 108 | 375.5 | 69.8%/yr | 36.6% | 110.9% |
| constant | geometric | exclude_delisted | 62 | 445.3 | 81.7%/yr | 35.3% | 144.1% |
| constant | arithmetic | exclude_delisted | 62 | 496.2 | 89.8%/yr | 37.9% | 161.1% |
| constant | value | exclude_delisted | 62 | 500.8 | 90.5%/yr | 44.8% | 150.5% |
| chained | geometric | exclude_delisted | 103 | 317.8 | 58.8%/yr | 21.2% | 108.1% |
| chained | arithmetic | exclude_delisted | 103 | 372.4 | 69.2%/yr | 28.0% | 123.7% |
| chained | value | exclude_delisted | 103 | 362.9 | 67.5%/yr | 34.4% | 108.7% |
| chained | geometric | full_history_only | 62 | 445.3 | 81.7%/yr | 35.3% | 144.1% |
| chained | arithmetic | full_history_only | 62 | 483.1 | 87.8%/yr | 38.9% | 153.8% |
| chained | value | full_history_only | 62 | 500.8 | 90.5%/yr | 44.8% | 150.5% |

Range: **58.8% to 90.5%/yr, 31.7 points apart**, median 81.7%. That spread is
not noise -- every cell is a defensible index -- so a single headline quoted
without its construction is unfalsifiable.

**Where the gap comes from, isolated cleanly:**

| construction | membership | products | CAGR |
| --- | --- | --- | --- |
| constant basket, geometric | full-history only (forced by construction) | 62 | 81.7%/yr |
| chained, geometric | full-history only (imposed) | 62 | 81.7%/yr |
| chained, geometric | every product (headline) | 108 | 59.1%/yr |

Rows 1 and 2 differ **only** by the linking method and they agree to 2.8e-14
percentage points, which is zero to machine precision -- on a balanced panel a
chained Jevons index equals the direct one exactly, and
`tests/test_etb_index.py` pins that identity. So the 22.7-point drop from row 2
to row 3 is **entirely** the 37 late-entering products, which compounded far
more slowly than the cohort that was already being priced in 2024-03.

That is a finding about the market, not a defect: a fixed basket cannot contain
a product that did not exist yet, so the high number is a survivor-cohort
number. It is also worth stating plainly that **the constant basket is identical
under the "all" and "exclude delisted" survivorship rules** -- it cannot measure
survivorship at all, because it has already excluded every non-survivor.

### 2.3 Robustness: does the result depend on how it was measured?

**The uncleaned universe.** A one-line `name LIKE '%elite trainer%'` query
returns 120 priced products, of which 70 span the window; its constant basket
grows 80.7%/yr and its chained index 59.9%/yr. The curated universe (which drops
multi-unit cases, "[Set of 2]" SKUs, code cards and the larger ETB Plus -- see
3.1) gives 81.7% and 59.1%: the cleaning moved the constant basket by +1.1pp and
the chained index by -0.8pp. **So the universe definition is not where the
headline comes from** -- which rules out the first thing a sceptic should check.

**A different price field.** Rebuilding on the cheapest live ask instead of the
trailing sales average:

| field | what it is | products | CAGR |
| --- | --- | --- | --- |
| `market` | TCGplayer market (trailing sales average) -- headline | 108 | 59.1%/yr |
| `low` | cheapest live ask | 108 | 62.8%/yr |

Same sign, same order of magnitude.

**Sub-periods.** The growth is not one early spike:

| period | from | to | total | annualised |
| --- | --- | --- | --- | --- |
| full window | 2024-03 | 2026-09 | 219.2% | 59.1%/yr |
| first half | 2024-03 | 2025-06 | 88.2% | 65.8%/yr |
| second half | 2025-06 | 2026-09 | 69.6% | 52.6%/yr |
| trailing 12m | 2025-09 | 2026-09 | 41.9% | 41.9%/yr |
| trailing 6m | 2026-03 | 2026-09 | 23.1% | 51.6%/yr |

**Drawdown.** Worst peak-to-trough fall in the whole archive: **-3.4%** (2025-11
-> 2026-01), with 6 negative months out of 30 and a worst single month of -2.3%.
Read that as a warning, not comfort: an index that has never fallen more than
3.4% has not been tested.

**A second pipeline.** The pre-aggregated `sealed_index` table builds an ETB
series independently, at set level:

| source | unit | units | constant basket | chained | sets of this panel covered | share of panel sets |
| --- | --- | --- | --- | --- | --- | --- |
| price_history (this module) | product | 108 | 81.7%/yr | 59.1%/yr | 60 | 100% |
| sealed_index (pre-aggregated) | set | 60 | 80.1%/yr | 63.8%/yr | 60 | 100% |

They agree to a few points. The remaining difference is composition -- one is 60
sets, the other 108 products -- not a pipeline defect.

**But do not read that agreement as a check on the whole index.** `sealed_index`
only carries a set-month when an ETB was actually priced there; it covers 60 of
this panel's 60 sets (100%). So the one available second pipeline remains
structurally partial, and quoting the agreement without this coverage share
would overstate how much of the index has actually been corroborated (section
2.6).

**Channel.** The largest arguable universe call is whether Pokemon Center
exclusives belong in an "ETB" index at all. Both are kept, with a flag, so it
can be re-run either way:

| channel | products | CAGR | 95% lo | 95% hi |
| --- | --- | --- | --- | --- |
| Pokemon Center exclusive | 36 | 44.4%/yr | -4.3% | 118.0% |
| Mass-retail | 72 | 67.2%/yr | 35.2% | 106.8% |

### 2.4 Against the rest of the market

Same window, same construction, and the difference is estimated on the PAIRED
monthly return difference so the common market tide cancels before the standard
error is formed. This is the decision-relevant statistic: not "did ETBs go up"
but "did ETBs beat the alternative".

| benchmark | units | its CAGR | ETB edge | t (HAC, paired) | clears \|t\| >= 2 |
| --- | --- | --- | --- | --- | --- |
| `booster_box` | 54 | 59.6%/yr | -0.3pp | -0.03 | no |
| `booster_bundle` | 26 | 54.1%/yr | +3.2pp | 0.35 | no |
| `singles` | 9,209 | 39.8%/yr | +13.8pp | 1.04 | no |

**Not one benchmark difference clears the bar.** ETBs and booster boxes are
statistically indistinguishable over this window; the ~20-point edge over
singles has a t of about 1.0 and is not established. The singles benchmark also
deserves a caveat in the other direction: it is an equal-weighted index of 9,209
cards above a $1 floor, so it is dominated by cheap commons and probably
understates what a comparable singles portfolio did.

### 2.5 Dispersion -- what the average hides

Per-product growth, over the 98 products with enough history to annualise: p10
-2.8%/yr, median 63.9%/yr, p90 124.4%/yr -- an interquartile range of 51 points.
11% of them went DOWN, and 68% have growth that clears |t| >= 2 on their own
error bar. The full table is section 7.3 and `etb_products.csv`.

### 2.6 The products are not independent observations

Every count above is a count of SKUs, and SKUs cluster inside sets: one release
can ship a regular box, a Pokemon Center box and two artwork variants, four
listings whose prices move together because they are the same cardboard. This
panel's 108 products are only 60 release events -- 1.80 SKUs per set. **Read "N
of 108 products rose" as at most 60 independent confirmations, not 108.** Any
cross-sectional share or count in this document -- including the 2-sigma count
just above -- inherits that inflation.

Re-running the index with ONE observation per set (the geometric mean of that
set's SKUs, so collapsing commutes with the geometric aggregator) is the
robustness cut:

| unit of observation | units | full-history units | of which rose | chained index | constant basket | worst full-history unit |
| --- | --- | --- | --- | --- | --- | --- |
| SKU (product) | 108 | 62 | 62 | 59.1%/yr | 81.7%/yr | 11.6%/yr |
| set (release event) | 60 | 35 | 35 | 65.7%/yr | 81.0%/yr | 32.6%/yr |

The index level barely moves (+6.6pp on the chained construction), so the
equal-weight-by-SKU choice is not what produced the headline. What DOES move is
the floor: the worst single SKU fell to 11.6%/yr while the worst whole SET only
reached 32.6%/yr, because a set's weak variant is averaged against its strong
ones. Both are true; the SKU figure is the honest answer to "what is the worst
thing I could have bought" and the set figure to "how many distinct releases
went up". Every one of the 35 full-history SETS rose, which is the version of
"all of them rose" that survives clustering.

### 2.7 Is it still going, and is it ETBs?

Section 2.1 measures the whole window. A reader who wants to act on it is asking
something narrower -- *is this still true now* -- so the same index is re-read
on its trailing 12 months (2025-09 to 2026-09) and the benchmark null from 2.4
is re-run inside that sub-window.

**Still going, and not detectably slower.** The trailing 12 months compound at
41.9%/yr [0.3%, 100.6%] against 59.1%/yr over the full window -- the same number
within its interval. Tested directly rather than eyeballed, a last-12-months
dummy on monthly log returns (Newey-West, 3 lags) gives -1.6pp/month, t = -0.78,
p = 0.44: **no detectable change in pace**. Read that as ruling out a collapse
and nothing more -- its standard error is 2.04pp/month against a mean of about
3.9pp, so it could only have caught roughly a halving. 6 of the archive's months
were negative and the worst drawdown inside the recent window was -3.4%.

**It is broad, not a handful of boxes.** 88 of 91 products priced at both ends
rose (97%), median 1.55x, and even the 10th percentile is 1.17x. Concentration
is mild: the top decile of movers carries 20% of the summed log rise, 1.96x its
even share. Nor is breadth narrowing -- on a cohort held fixed across both
halves, the share rising went 97% to 98%.

The 3 products that fell are named rather than averaged away: Mega Evolution
Pokemon Center Elite Trainer Box (Exclusive) [Mega Gardevoir] (0.54x); Mega
Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Lucario] (0.62x);
Temporal Forces Pokemon Center Elite Trainer Box (Exclusive) [Walking Wake]
(0.95x). Check release dates before reading that as a category signal -- a box
still inside its launch window is showing the cooldown measured in section 4.3,
not a market turn.

**Still not an ETB story.** The benchmark comparison from 2.4, recomputed inside
the recent window:

| window | vs | ETBs | them | gap | lo | hi | t | verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| trailing 12m | Booster boxes | 41.9%/yr | 26.1%/yr | +12.5pp | -15.9pp | +50.4pp | 0.79 | no detectable difference |
| trailing 12m | Booster bundles | 41.9%/yr | 44.5%/yr | -1.9pp | -13.7pp | +11.6pp | -0.29 | no detectable difference |
| trailing 12m | Singles | 41.9%/yr | 73.5%/yr | -18.2pp | -36.4pp | +5.1pp | -1.57 | no detectable difference |
| full window (30m) | Booster boxes | 59.1%/yr | 59.6%/yr | -0.3pp | -17.0pp | +19.7pp | -0.03 | no detectable difference |
| full window (30m) | Booster bundles | 59.1%/yr | 54.1%/yr | +3.2pp | -13.4pp | +23.1pp | 0.35 | no detectable difference |
| full window (30m) | Singles | 59.1%/yr | 39.8%/yr | +13.8pp | -10.8pp | +45.2pp | 1.04 | no detectable difference |

0 of 6 judgeable comparisons differ from ETBs. The full-window null from section
2.4 therefore survives into the recent sub-window unchanged: **the recent rise
is a Pokemon-market rise, not an ETB one.** These are low-power nulls -- the
trailing-12-month intervals run roughly -15.9pp to +50.4pp -- so the honest
claim is "cannot be distinguished", not "they are the same".

9 shorter-window comparisons are computed and printed in
`etb_recent_benchmarks.csv` but excluded from every verdict above, because an
interval built on a handful of monthly observations is not one. That gate is
load-bearing rather than decorative: the most extreme of those excluded rows is
trailing 3m ETBs vs singles at t = -9.41 on 3 monthly returns, and quoting it
would have published a significant result off a window whose sign does not
survive to twelve months.

**The one split that does show a gap is channel, and it is the weakest inference
here.** Mass-retail boxes ran 1.69x against 1.28x for Pokemon Center exclusives
(31.5%, t = 5.11). Differencing two groups cancels the market-wide factor but
NOT a channel-specific one -- a Pokemon Center release calendar or a restock
decision leaves the within-channel residuals correlated -- so that t is an upper
bound on the evidence, not a clean test. Age bands and price quartiles show no
ordering at all (`etb_recent_drivers_*.csv`).

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
| constant-basket geometric CAGR | 81.7%/yr | 81.7%/yr |
| full-history basket | -- | 62 products |
| of which rose | -- | 62 |
| worst / median member | -- | 11.6%/yr / 77.5%/yr |

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
| `INCLUDED` | 121 | 108 | Celebrations Elite Trainer Box |
| `NOT_A_BOX` | 113 | 0 | Code Card - Celebrations Elite Trainer Box |
| `MULTI_UNIT` | 80 | 9 | Celebrations Elite Trainer Box Case |
| `MIXED_LOT` | 3 | 0 | Costco Pokemon Evolving Skies Elite Trainer Box and Tin |
| `ETB_PLUS` | 4 | 3 | Crown Zenith Pokemon Center Elite Trainer Box Plus |

The exclusions that actually cost priced products are the multi-unit SKUs (cases
and "[Set of 2]" listings, whose price level is not one box) and ETB Plus (a
physically different, larger product). Section 2.3 shows that putting them back
RAISES the naive headline rather than lowering it, so this cleaning is not what
produced the result.

### 3.2 Coverage, stated as a weakness

108 products x 31 months would be 3,348 observations; the panel has 2,756. The
shortfall is entirely structural. The obvious two-way framing -- "either it
started late or it was delisted" -- is wrong twice over here, so the split below
is mutually exclusive and exhaustive by construction and the code raises if the
buckets stop summing to 108:

| coverage shape | products | share | what it is |
| --- | --- | --- | --- |
| complete | 62 | 57% | priced in every month of the grid |
| late start only | 35 | 32% | a newer release; enters mid-window and never leaves |
| delisted only | 3 | 3% | priced from the start, then stops being listed |
| late start and delisted | 2 | 2% | enters mid-window AND stops before the end |
| interior gap only | 6 | 6% | spans the full window but is missing months inside it |

The two buckets a two-way split loses are the last two: products that start late
AND vanish before the end, and products that span the whole window with holes in
the middle. For the latter, "first price" and "last price" are not the ends of a
continuous series. Separately from all of this, 10 products are observed too
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
| Unbroken Bonds Elite Trainer Box | 2025-10 | 20 | 1,164.50 | 97.0% |

3 of 5 were still RISING when they disappeared and 1 were falling (median 6.5%).
So a survivor-only basket is missing continued appreciation, not hiding a
collapse -- this particular bias makes the constant-basket number, if anything,
conservative. It is a different bias (missing the slow late entrants) that
inflates it, and section 2.2 quantifies that one at 22.7 points.

### 3.4 What the prices are, and are not

`market` is TCGplayer's trailing sales average. It is a quote, not an execution:
nobody transacted at the index, and section 6 is the correction for that. Two
specific things a reader should not assume:

* **There is no bid in this data.** `low`/`high` are the cheapest and dearest
  ASKS. Anything computed from `high - low` is a listing dispersion, not a
  spread -- the naive calculation gives a "spread" of 196% of the market price
  (section 6.6).
* **TCGplayer-Direct quotes do not exist for sealed product.** `direct_low` is
  NULL for every sealed row in the archive, so the direct-discount feature the
  singles models use is structurally unavailable here and was excluded rather
  than carried as an all-missing column.

### 3.5 The claim this study was asked to falsify

This study was commissioned around a preliminary headline: a constant-basket
geometric index on the raw catalogue query, with every full-history product
positive. **Both halves of that reproduce exactly, and neither should be the
headline.** Recomputed live on the uncleaned universe: **80.7%/yr**, over 70
full-history products of which **70 rose and 0 fell**.

It is not a calculation error. It is the wrong object, for the reason section
2.2 isolates -- it is a survivor-cohort index, and the "all positive" property
is true *by construction of which products get a full history*, not because ETBs
do not fall. The curated panel makes that visible: 17 of 108 products are down
over their own window, of which 17 are late entrants and 0 are full-history
products. A fixed basket cannot contain a single one of the fallers.

The honest headline is 59.1%/yr with a 95% interval of [22.2%, 107.2%], and even
that is one cell of a 31.7-point grid.

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
are the same regressor over 31 months of one regime.

This is the classic age-period-cohort problem, and it is not fixable with more
cleverness -- a two-way fixed-effects age curve here would be reporting its own
normalisation, not a fact. What the lifecycle module publishes instead is the
FAN of answers you get from the three standard identifying restrictions, each of
which fits every observed price identically (largest fitted-price change across
the three restrictions: 7.3e-14, measured rather than asserted): a ten-year
ageing multiple anywhere from **0.74x to 681.35x** -- a **920x** span that is
pure assumption.

Anyone who tells you how much an ETB appreciates per year *because it aged* is
choosing one point in that fan.

### 4.2 What IS identified: the shape, not the slope

Slope CHANGES need no identifying assumption -- they survive the fixed effects.
Joint test that the age profile is linear: **chi2(5) = 86.7, p = 3.3e-17**. The
profile bends, decisively.

| age (months) | slope change (log/yr) | SE | t | significant | products crossing |
| --- | --- | --- | --- | --- | --- |
| 12 | 0.640 | 0.098 | 6.53 | yes | 38 |
| 24 | -0.039 | 0.103 | -0.37 | no | 33 |
| 36 | -0.216 | 0.065 | -3.34 | yes | 31 |
| 60 | -0.013 | 0.082 | -0.16 | no | 21 |
| 84 | 0.012 | 0.076 | 0.16 | no | 13 |

The normalisation-free contrast between the young band and the mature band
(12-24m -> 36-60m) is **-0.254 log/yr (t = -2.84)**: mature boxes compounded at
a *lower* annual factor than young ones, which is the opposite of "it takes off
once it is retired".

**Two caveats that cut the shape down, both published in
`etb_lifecycle_stability.csv`:**

1. The acceleration at 12 months **vanishes** once the launch cohort is excluded
   (-0.120, t = -0.70). It is the launch cooldown ending, not a property of
   one-year-old boxes.
2. The deceleration is estimated almost entirely from the first calendar half;
   in the second half it is 0.002 (t = 0.02), i.e. indistinguishable from zero.
   Of 6 subsamples tested, 4 are significant.

### 4.3 The decision-relevant result needs no assumption at all

Forget identifying the age curve. Ask the question a buyer actually faces: **buy
a box at release, hold it -- what happens?** That is a raw observed path, not a
model.

WHICH price counts as "at release" decides the answer, so it is worth saying
plainly. Prices in this archive are snapshots taken on the 1st of the month, and
no set in this cohort goes on sale on the 1st. So both the month a listing first
appears (usually one to two months before street date) and the release month
itself are PRE-ORDER quotes on a box nobody can buy yet, and they are not cheap:
the last pre-street-date quote runs at a geometric mean of **1.47x** of the
first price the box actually opened at, above it for 92% of the cohort and as
high as 4.72x. The baseline below is therefore the first snapshot dated on or
after street date -- a real transactable price, taken a median of 10 days after
the box went on sale (range 2-30 days).

> **Correction, 2026-07-25.** An earlier published version of this
> curve was wrong, not merely imprecise. It anchored k=0 on each product's first
> LISTED month, which for most of the cohort is a pre-order quote on a box that
> had not shipped, and it counted k from that listing rather than from launch.
> The trough was published as
> 0.61x and is
> 0.93x; the 12-month figure was published as
> 1.00x and is
> 1.68x. Full ledger in section 7.4 and
> `etb_corrections.csv`.

For the 36 products whose first on-sale price is observed (22 of them with a
balanced 12-month window), the geometric mean path dips to **0.93x** by month 1
and is at **1.68x** a year later. That raw path is a boom reading, not a
lifecycle: measured as EXCESS over the rest of the ETB market it troughs at
0.75x and is still 0.79x at twelve months. So the box rose, and the rest of the
category rose MORE -- buying the new box was the worse of the two. The same
ordering holds against booster boxes (0.79x at the trough) and singles (0.91x).

By channel -- the largest split in the study by point estimate, and small enough
on each side that the intervals are printed beside it:

| channel | products | trough month | trough (x launch) | at 12m (x launch) | 12m 95% lo | 12m 95% hi | products back at launch by 12m | worst product at 12m | best product at 12m | months for the MEAN to regain launch |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Pokemon Center exclusive | 11 | 1 | 0.91x | 1.63x | 1.31x | 2.03x | 10 | 0.86x | 3.06x | 6 |
| Mass-retail | 11 | 1 | 0.95x | 1.73x | 1.48x | 2.02x | 11 | 1.04x | 2.36x | 3 |

Pokemon Center exclusives -- allocated rather than stocked, so even their first
on-sale price is a queue price -- trough deeper (0.91x at month 1) than
mass-retail boxes (0.95x at month 1), and take longer to get back: the PC mean
regains its launch price at month 6 against month 3 for mass-retail. Read the
last three columns before quoting any of that. Each side is only 11 products;
individually, 10 of the 11 Pokemon Center boxes ended at or above the launch
price at 12 months (best 3.06x, worst 0.86x) against 11 of 11 mass-retail boxes;
and the two channels' 12-month confidence bands are [1.31x, 2.03x] and [1.48x,
2.02x]. Every one of those is a 11-product average measured inside one boom, so
none of it is a statement about every box or about any other regime.

### 4.4 The index side: what survives a significance test, and what does not

Splitting the universe by how old each product was when it ENTERED the window
(an as-of fact, not one that depends on how the window ended) asks the same
question without any lifecycle machinery. Read the `t` column with the point
estimates: 1 of 3 contrasts against the youngest ON-SALE cohort clears this
repo's |t| >= 2 bar.

The first row is products whose first observed month PRECEDES their set's street
date -- their opening price is a pre-order quote, not a shelf price (section
4.3). They used to be pooled into the youngest cohort, which is what made that
cohort look flat; separated, they are the one contrast that does survive, and
what it establishes is a fact about pre-order quotes rather than about age.

| cohort (age at entry) | SKUs | sets | chained index | HAC 95% lo | HAC 95% hi | median product | share down over own window | vs youngest | t |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| pre-release at entry | 24 | 14 | -7.1%/yr | -37.6% | 38.2% | 2.0%/yr | 58% | -43.5pp | -2.55 |
| 0-12m old at entry | 24 | 12 | 64.5%/yr | 4.0% | 160.2% | 64.8%/yr | 12% | n/a | n/a |
| 1-3y old at entry | 26 | 11 | 89.7%/yr | 37.3% | 162.1% | 88.0%/yr | 0% | +15.3pp | 1.21 |
| 3y+ old at entry | 34 | 29 | 68.9%/yr | 34.5% | 112.3% | 62.6%/yr | 0% | +2.7pp | 0.12 |

Reading the rows against each other:

* Products first seen BEFORE their street date grew -7.1%/yr with 58% of them
  down over their own window, and their difference from the youngest on-sale
  cohort **clears the bar** (t = -2.55). Paying a pre-order quote is the one
  thing in this table that is reliably associated with a worse outcome.
* The youngest ON-SALE cohort's own index grew 64.5%/yr with t = 2.13 --
  **distinguishable from flat** at the same bar. 12% of those boxes are down
  over their own window.
* Product 1-3 years past release grew 89.7%/yr; its paired difference against
  the youngest on-sale cohort **does not clear the bar** (t = 1.21).
* Product 3+ years past release grew 68.9%/yr; its difference **does not clear
  the bar** (t = 0.12), and it sits BELOW the 1-3y cohort in point estimate, so
  this is not a monotone "older is better" effect even before the error bars are
  drawn.

**This corrects a previously published reading.** With pre-release entrants
pooled into the youngest cohort, that cohort's index came out at 39.1%/yr and
"not distinguishable from flat", and the 1-3y contrast against it cleared the
significance bar at t = 2.86 -- which is where the claim "the gains belong to
out-of-print product" came from. Separating the pre-order quotes moves the
youngest on-sale cohort to 64.5%/yr and leaves the 1-3y contrast at t = 1.21.
The ordering of the point estimates is broadly unchanged; what does not survive
is the claim that any of the AGEING contrasts was tested. See section 7.4.

Note also the sample these contrasts rest on: buckets of 24 to 34 SKUs, which
are only 11 to 29 distinct releases (the `sets` column above), all sharing ONE
31-month calendar window -- a post-hoc slice of a small panel, not an
experiment.

### 4.5 Reprints: the obvious mechanism, and why this data cannot test it

If "out of print" is the mechanism, a reprint should hurt. The lifecycle module
looked for that and **refuses to answer**: of 55 large idiosyncratic drops (<=
-20% after removing the month's cross-sectional mean), 50 are products under a
year old (launch cooldown) and only 5 are out-of-print product.
`reprint_analysis_supportable` returns **no**. In-print status is not a field in
this database at all; age is the only proxy, and it is labelled as one
everywhere.

What the shocks do show, for whatever it is worth on 55 events, is that they do
NOT mean-revert. The cumulative idiosyncratic return is -0.46 at impact and
-0.62 six months later. Whatever caused a big ETB drop in this window, the price
did not come back inside half a year.

### 4.6 Do older ETBs sell for more today? Yes -- and that is not an ageing curve

This is the owner's own observation, and it is correct as a statement about
today's shelf. It is also the single easiest number in this study to misread, so
the gradient and the reason it cannot be extrapolated are stated together
throughout: **at 2026-09, mass-retail ETB price rises with age at Spearman rho =
0.719 (p = 6.9e-12, n = 67) -- and within a single calendar month a product's
age IS its release cohort, with R^2 = 1.000, so that rho ranks vintages and
cannot separate "boxes gain value as they age" from "boxes made in 2016 are
scarcer than boxes made in 2026".** Neither half of that sentence is quotable
without the other.

Three things qualify it further, all measured.

**It is a mass-retail fact, not an ETB fact.** Pokemon Center exclusives give
rho = 0.417 (p = 0.01, n = 36) -- indistinguishable from zero, and no PC product
in the archive is older than about 5 years. The pooled rho = 0.559 is therefore
partly a statement about which channel happens to be old.

**The shape is not a trend, and this sample cannot order the bands.**

| age band | products | median price | lo | hi | sets |
| --- | --- | --- | --- | --- | --- |
| <1yr | 5 | $73 | $71 | $169 | 5 |
| 1-2yr | 9 | $140 | $118 | $167 | 7 |
| 2-3yr | 8 | $137 | $114 | $154 | 6 |
| 3-5yr | 12 | $207 | $152 | $327 | 11 |
| 5-8yr | 18 | $192 | $143 | $566 | 14 |
| 8yr+ | 15 | $831 | $636 | $1,256 | 13 |

Every row of that table is a different set of products bought in a different
decade -- it is a vintage ranking, printed by age because that is how the
question was asked. The medians do NOT rise monotonically: there are 2
inversions, the worst being 3-5yr -> 5-8yr at -7.2% -- the dip the owner
noticed. Of those 2 dips, 0 separate at the bootstrap median interval, and the
step up into the oldest band does separate either -- despite supplying 84% of
the whole top-to-bottom range by itself. With 67 products spread over 6 bands
and a long right tail, **the band ORDER above is not established by this
sample** -- neither the owner's dip nor the headline step. The point estimates
are what they are; their ordering is not. The counterweight is kept honestly the
other way too: dropping the vintage band entirely still leaves rho = 0.516 (p =
9.2e-05, n = 52) and a fitted 25.1%/yr against 27.6%/yr on the full sample, so
the gradient is not only the vintage tail.

**The oldest band is where the level lives and where the sample is worst.** Only
60.0% of same-era mass-retail vintage SKUs are still priced at all (15 of 25; 10
are absent, several with zero priced months anywhere in the archive), against
94-100% in every younger band. Assuming only that the absentees have *some*
price, the distribution-free bound on that band's median runs [$422, $1,800]
against a survivor median of $831 -- a 4.27x span from survivorship alone.
Trading is thin there too: 67% of vintage products have their market estimate
BELOW the cheapest live ask (0% in every band under 5 years) and 2 have one
listing. The obvious explanation -- smaller print runs -- is **unmeasurable
here**: no print-run figure exists anywhere in this database, and the
catalogue-breadth proxy comes out at 0.77, pointing AWAY from the scarcity story
rather than supporting it. That null is published rather than suppressed, and it
does not clear the confound: the proxy has no resolution at the 2016-vs-2026
distance.

#### Will a box bought today follow them up? The cross-section cannot say, and the panel says no

The gradient is a fact about products that already exist. Turning it into a
holding period requires that ageing CAUSES the gap, which is the one thing R^2 =
1.000 forbids. The panel answers the question the cross-section cannot, because
it watches the same box age.

Across 98 products with a full price path, mass-retail in-window appreciation
runs 67.8%/yr median with 6% negative. Its dependence on age is +2.1pp/yr per
year of age (t = 1.31) -- **no age dependence distinguishable from zero**.
Excluding products still inside their launch window it is -1.8pp/yr (t = -1.21):
older boxes appreciated more *slowly*, the opposite sign to what an ageing
reading of the cross-section predicts. The headline null is the conservative
statement and the one to quote; the excl-launch cut is a post-hoc slice of one
regime, published because its sign is decision-relevant, not because it
establishes that age is bad for a box.

Put on one scale: the cross-sectional gradient implies 83.8% over the median
observed span, while boxes actually returned 236.8%. The gradient can account
for at most 50% of the realised log move -- an upper bound, since it credits the
whole implied part to age. **The rest is calendar, and no box bought today can
assume it.** That ceiling is a bound on how much of the gradient an ageing story
could be carrying; it is not a finding that "50% of ETB appreciation is ageing".

The natural experiment settles the shape question the same way: 3 of 3
cross-sectional inversions are contradicted by the products that actually made
the crossing.

| channel | from | to | cross-section implies | boxes that crossed | they actually did | contradicted |
| --- | --- | --- | --- | --- | --- | --- |
| mass_retail | 1-2yr | 2-3yr | -2.5% | 6 | 369.3% | yes |
| mass_retail | 3-5yr | 5-8yr | -7.2% | 13 | 225.0% | yes |
| pokemon_center | 1-2yr | 2-3yr | -24.1% | 5 | 371.8% | yes |

The headline one is the owner's dip: mass retail 3-5yr -> 5-8yr implies -7.2%,
and the 13 boxes that genuinely aged past that boundary returned 225.0% median
[169.0%, 237.2%]. The cross-sectional dip is a fact about which sets are 5-8
years old, not about what happens to a box on its fifth birthday.

**No forecast follows.** `projection_support` reports `forecast_supported = no`
with a maximum measured horizon of 30 months. `etb_agevalue_illustrative.csv`
multiplies three readings of this same data out to 5 and 10 years with every row
flagged `is_measured = False`:

on a $73 box at 10 years -- *flat in nominal terms* -> 1.00x ($73); *today's box
walks the current cross-section* -> 14.65x ($1,063); *the 2024-2026 rate
continues* -> 176.47x ($12,803). Every one of those is an ASSUMPTION carried
forward, not a measurement, and they disagree by a factor of 176.

**The spread between them, from one dataset, is the finding** -- it is why this
study publishes no holding period.

## 5. Can it be predicted?

**No -- not at the horizon that matters, and the one horizon that looks
predictable is a measurement artefact.** This is a null result and it is
published as one.

The question is narrow and cross-sectional: standing at month T with only
information available at T, can we rank ETBs by which will beat the ETB basket
over the next H months? It is not "will ETBs go up" -- section 2 measures that.

| horizon (months) | purged folds | mean held-out IC | effective n | t | clears both gates |
| --- | --- | --- | --- | --- | --- |
| 1 | 24 | 0.271 | 10.37 | 3.57 | yes |
| 3 | 20 | -0.031 | 3.86 | -0.20 | no |
| 6 | 14 | -0.121 | 1.82 | -0.73 | no |
| 12 | 2 | -0.200 | 1.00 | -0.98 | no |

At the pre-registered primary horizon of 6 months the mean held-out rank
correlation is **-0.121** -- the point estimate is NEGATIVE -- on an effective
sample of 1.82 against the repo's 4.0 bar. At H = 12 there are **zero** usable
folds: a 31-month archive cannot test a one-year hold with a leakage-free design
at all, which is itself a finding about the data rather than about the model.

The binding constraint is structural, not statistical. With an H-month label
window, N monthly folds contain at most `(N-1)//H + 1` NON-OVERLAPPING label
windows -- two at H = 6. No autocorrelation estimate can see that, so the
effective sample used above is the MINIMUM of the autocorrelation-deflated n_eff
and that structural bound.

### 5.1 H = 1 clears the gates. It still is not a signal.

The one-month horizon does clear both gates, so it was chased down rather than
buried, and it does not survive three checks:

**Mechanism.** The strongest feature at every horizon is `mid_skew`, which
compares TCGplayer's TRAILING market average with the CURRENT book midpoint. If
it were demand, a high value should predict the book to keep rising. It does the
opposite:

| relationship | mean IC | t | effective n |
| --- | --- | --- | --- |
| mid_skew -> market | 0.271 | 4.36 | 10.34 |
| mid_skew -> book mid | -0.238 | -4.51 | 10.53 |
| mid_skew -> gap change | -0.449 | -16.68 | 24.00 |

A high skew predicts the market price RISING and the book midpoint FALLING, with
the gap between them closing hard. That is two measurements of one price
converging, not a forecast of value.

**Economics.** The top-quintile portfolio at H = 1 returns 169.8%/yr against the
basket's 98.8%/yr -- an edge of +71.0pp gross (t = 2.68). Twelve rebalances a
year at the round-trip cost from section 6 is a 85.8pp drag, so the NET edge is
-14.8pp. It loses to doing nothing.

**The model does not beat its own best single input.**

| horizon | best single feature | its IC | fitted model IC | which wins |
| --- | --- | --- | --- | --- |
| 1 | `mid_skew` | 0.271 | 0.271 | tie |
| 3 | `mid_skew` | 0.247 | -0.031 | the single feature |
| 6 | `mid_skew` | 0.284 | -0.121 | the single feature |
| 12 | `rel_spread` | -0.285 | -0.200 | model |

That is textbook small-sample overfitting, and it means the ML layer adds
nothing here that a one-line feature ranking does not. Full detail, including
the permutation nulls, purge audits and the selection-protocol contamination
flag, is in `data/output/etb_forward.md`.

## 6. What would a holder actually have earned?

An index is not money. This section converts it, using the cost model in
`pokestat/model/etb_hold.py`; the full treatment is
`data/output/etb_hold_summary.md`.

**Every cost constant below is a STATED ASSUMPTION, not a fetched fact.** This
project's permitted sources carry card prices and FX rates -- not TCGplayer's
fee schedule, not sales-tax rates, not Treasury yields. The marketplace take
(12.75%) is the single most influential one: sweeping it alone moves the
24-month answer by 16.4 points a year.

### 6.1 The frictions are a one-time toll, not a rate

Round trip: 7.5% sales tax in, 12.75% marketplace take out, $12.00 to ship a
heavy box. That is roughly **20.2% of the box price plus $12.30 fixed**, charged
once. Because it is charged once, it amortises -- which is the whole answer to
"how long should I hold".

At the measured gross index rate of 59.1%/yr, on a $218 box (the median ETB
price in 2026-09):

| hold (months) | gross | net | net rate | friction drag | gross growth needed to beat cash | beats cash |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | 1.12x | 0.86x | -45.8%/yr | 104.9pp/yr | 196.2%/yr | no |
| 6 | 1.26x | 0.97x | -6.2%/yr | 65.2pp/yr | 76.2%/yr | no |
| 12 | 1.59x | 1.23x | 23.4%/yr | 35.7pp/yr | 35.8%/yr | yes |
| 24 | 2.53x | 1.99x | 41.1%/yr | 18.0pp/yr | 19.3%/yr | yes |

**The minimum hold to beat a 4.5% savings account is 8 months** (9 months on a
cheap box, 7 on an expensive one -- shipping and the flat fee do not scale).
This is arithmetic about the fee structure and is the one conclusion in this
entire document that does not depend on the regime.

An OPTIMAL hold is a different matter and the study declines to name one: the
best observed horizon was 18 months at 66.8%/yr net, but a 30-month archive
contains exactly 1 non-overlapping window of that length. One window is an
anecdote.

### 6.2 What actually happened, box by box

37,442 realised holding periods across 108 products, all net of costs:

| hold | holding periods | independent windows | median net | 5th pct | 95th pct | share that lost money |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | 2,408 | 10 | 0.83x | 0.51x | 1.25x | 80% |
| 6 | 2,093 | 5 | 1.00x | 0.57x | 1.64x | 50% |
| 12 | 1,507 | 2 | 1.44x | 0.87x | 2.83x | 11% |
| 24 | 506 | 1 | 2.70x | 1.53x | 6.86x | 1% |

**A three-month flip lost money 80% of the time during a boom.** Six months was
a coin flip (50%). Twelve months lost 11% of the time. A product-clustered
bootstrap puts the median 12-month net rate at 44.3%/yr, 95% CI [37.1%, 53.7%]
over 96 products.

Note the two 12-month numbers in this document that DISAGREE: applying the
chained index rate uniformly gives 23.4%/yr, while the pooled realised holds
give 44.3%/yr. They are different objects -- pooling triples over-weights
long-history survivor products, and the middle of the window grew faster than
its ends. The gap is roughly the size of the entire friction drag, which is
itself a warning about how much of any of these numbers is a construction
choice.

### 6.3 One box is not the index

| products | 10th pct box | median box | 90th pct box | the basket | middle-50% spread | share worse than basket |
| --- | --- | --- | --- | --- | --- | --- |
| 96 | 0.98x | 1.44x | 2.45x | 1.30x | 73pp | 35% |

At twelve months the middle 50% of single-box outcomes spans about 73 annualised
points and 35% of picks did worse than simply owning the basket.

### 6.4 When you bought mattered more than how long you held

| bought when | holds | products | median net rate | share that lost money |
| --- | --- | --- | --- | --- |
| bought before release (pre-order quote) | 18 | 17 | -34.5%/yr | 72% |
| bought 0-6m after release | 138 | 32 | 24.9%/yr | 25% |
| bought 6-12m after release | 142 | 28 | 52.0%/yr | 11% |
| bought 1-3y after release | 473 | 47 | 60.1%/yr | 5% |
| bought 3y+ after release | 736 | 51 | 39.6%/yr | 10% |

Buying inside six months of release and holding a year lost money 25% of the
time; buying product already 1-3 years old lost 5% of the time. **The worst row
is the pre-order one**, and it is separated here for the first time: buys dated
before the set's street date -- pre-order quotes, not shelf prices -- returned
-34.5%/yr net over a year and lost money 72% of the time. They used to be
counted inside the "0-6m after release" bucket, which mislabelled them and made
buying a box at launch look worse than it was.

The mechanism is measured, not assumed -- but it is much smaller than this study
once published. Of 36 products with an observed first ON-SALE price, the median
trough over the following six months was 13.3% below it (IQR 3.4% to 22.0%) and
22% fell at least 25%. Measured at a fixed six-month endpoint rather than at a
minimum -- which is not selection-prone -- the median is -0.8%, i.e. the typical
box is **above** its launch price half a year on.

An earlier published version of this paragraph put those at 49.0% and 71%,
computed from each product's first LISTED price -- a pre-order quote for most of
the cohort, not a price anyone paid. Both arms are still computed here (the
superseded one under `naive_*`) so the size of the correction, 35.6 points on
the median, is a live number rather than a claim. See section 7.4.

### 6.5 The downside

Two numbers, both regime-facing:

* **Flat is not break-even.** If prices merely stop rising, a 12-month hold
  returns 0.75x -- a 24.6% annualised loss, because the frictions are charged
  anyway.
* **A fall of 43.8% from the terminal price erases the entire 24-month edge over
  a savings account**, and 48.3% turns it into a nominal loss. That is about 64%
  of the gain -- it does not require prices to return to where they started.

At 24 months the net answer keeps its sign under every sensitivity cell; at 6
months the same knobs move it across zero (-33.5% to 25.1%/yr), so short-horizon
verdicts are assumptions rather than measurements.

### 6.6 One brief the data contradicted

This study was briefed on a "~15-20% bid-ask on thin sealed listings". **The
archive does not support that**, and the obvious way to compute it is wrong.
`price_history` carries a LISTING book -- `low` is the cheapest ask, `high` the
dearest -- and no bid at all. Treating `high - low` as a spread gives a median
of 196% of the market price, because `high` has a median of 2.98x market. What
IS measurable: `low/market` has a median of 0.980, and a round trip executed at
`low` on both ends returned a median 1.006x of what a market-to-market round
trip returned, with only 46% of products worse off. The measurable spread very
nearly cancels. The holder's real loss is fees, tax and shipping -- which is why
the undercut constant defaults to zero and is swept to 15% anyway (worth 11.4
points a year), because "not measurable" is not "zero".

## 7. Limitations, and the data itself

### 7.1 The window is the finding's ceiling

**31 monthly observations, 2024-03 .. 2026-09, one regime.** Everything above
happened inside a historic Pokemon sealed boom. The index's worst peak-to-trough
fall in the entire archive is -3.4%. There is no bust in this data, so nothing
here measures what happens in one, and no interval printed above is a forecast
interval -- the HAC bands are sampling uncertainty WITHIN the boom. Statistical
uncertainty here is small; regime uncertainty is everything.

The archive does not go back further because it cannot: tcgcsv's price archive
begins in 2024-03, and the sources that would extend it (eBay, PriceCharting)
are excluded on terms-of-service grounds. "The last few years" means 2.5 years.

### 7.2 Everything else worth knowing before quoting a number

* **The headline is a construction choice.** The 15-cell grid spans 58.8% to
  90.5%/yr. Any single figure quoted without its construction is unfalsifiable.
* **Prices are TCGplayer quotes, not executions.** `market` is a trailing sales
  average; nobody transacted at the index. Section 6 is the correction, and its
  cost constants are stated assumptions, not fetched facts.
* **The age effect is unidentified** (section 4.1) and the ML layer is a null
  (section 5). Neither is a placeholder for a result that is coming later; both
  are the answer this data supports.
* **10 of 108 products are observed for fewer than the 12 months required to
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

108 products, sorted by annualised growth; blank CAGR means fewer than 12
observed months. The same rows, with every column, are in
**`data/output/etb_products.csv`**. Of these, 67 have a growth rate that clears
|t| >= 2 on their own Newey-West error bar and 17 are down over their observed
window. Those are SKU counts: 108 SKUs are 60 sets (1.80 per set), so divide by
roughly that before treating them as independent (section 2.6).

**Read the `total spans a gap?` column.** 2 rows carry `GAP`, meaning at least 6
months between the product's first and last observation have no price at all.
For those rows `total` compares two prices with a hole between them and the
terminal price may be a single illiquid relisting rather than a market move; the
blank-CAGR gate protects the ANNUALISED column but not this one.

| id | product | set | months | gaps | age at entry (m) | first $ | last $ | total | total spans a gap? | CAGR | t (HAC) | worst drawdown | PC | full | late | gone |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 501,999 | 151 Pokemon Center Elite Trainer Box (Exclusive) | sv3pt5 | 31 | 0 | 6 | 94.65 | 1,320.91 | 1,295.6% |  | 187.0%/yr | 3.56 | -14.0% | yes | yes | no | no |
| 528,040 | Paldean Fates Elite Trainer Box | sv4pt5 | 31 | 0 | 2 | 41.49 | 445.32 | 973.3% |  | 158.4%/yr | 3.23 | -21.7% | no | yes | no | no |
| 503,313 | 151 Elite Trainer Box | sv3pt5 | 31 | 0 | 6 | 53.31 | 569.14 | 967.6% |  | 157.8%/yr | 3.84 | -14.0% | no | yes | no | no |
| 501,266 | Obsidian Flames Pokemon Center Elite Trainer Box (Exclusive) | sv3 | 31 | 0 | 7 | 64.27 | 641.95 | 898.8% |  | 151.1%/yr | 2.30 | -25.8% | yes | yes | no | no |
| 528,039 | Paldean Fates Pokemon Center Elite Trainer Box (Exclusive) | sv4pt5 | 31 | 0 | 2 | 70.80 | 607.23 | 757.7% |  | 136.2%/yr | 2.33 | -21.7% | yes | yes | no | no |
| 247,673 | Fusion Strike Pokemon Center Elite Trainer Box (Exclusive) | swsh8 | 31 | 0 | 28 | 58.10 | 492.12 | 747.0% |  | 135.0%/yr | 2.92 | -9.6% | yes | yes | no | no |
| 247,671 | Fusion Strike Elite Trainer Box | swsh8 | 31 | 0 | 28 | 40.91 | 328.65 | 703.3% |  | 130.1%/yr | 4.05 | -10.2% | no | yes | no | no |
| 181,704 | Team Up Elite Trainer Box | sm9 | 31 | 0 | 61 | 506.90 | 4,000.00 | 689.1% |  | 128.5%/yr | 3.63 | -3.1% | no | yes | no | no |
| 453,470 | Crown Zenith Elite Trainer Box | swsh12pt5 | 31 | 0 | 14 | 42.75 | 325.56 | 661.5% |  | 125.3%/yr | 3.74 | -12.4% | no | yes | no | no |
| 501,264 | Obsidian Flames Elite Trainer Box | sv3 | 31 | 0 | 7 | 37.16 | 280.50 | 654.8% |  | 124.5%/yr | 2.93 | -12.1% | no | yes | no | no |
| 493,973 | Paldea Evolved Pokemon Center Elite Trainer Box (Exclusive) | sv2 | 31 | 0 | 9 | 79.88 | 602.85 | 654.7% |  | 124.4%/yr | 2.74 | -18.9% | yes | yes | no | no |
| 170,277 | Celestial Storm Elite Trainer Box | sm7 | 31 | 0 | 67 | 287.20 | 2,091.30 | 628.2% |  | 121.3%/yr | 3.58 | -6.8% | no | yes | no | no |
| 245,352 | Evolving Skies Pokemon Center Elite Trainer Box [Glaceon/Vaporeon/Sylveon/Espeon] (Exclusive) | swsh7 | 31 | 0 | 31 | 155.50 | 1,060.30 | 581.9% |  | 115.5%/yr | 4.92 | -2.1% | yes | yes | no | no |
| 493,974 | Paldea Evolved Elite Trainer Box | sv2 | 31 | 0 | 9 | 35.16 | 219.59 | 524.5% |  | 108.1%/yr | 3.06 | -12.6% | no | yes | no | no |
| 193,052 | Unified Minds Elite Trainer Box | sm11 | 31 | 0 | 55 | 291.86 | 1,813.25 | 521.3% |  | 107.6%/yr | 3.44 | -10.8% | no | yes | no | no |
| 242,443 | Evolving Skies Elite Trainer Box [Glaceon/Vaporeon/Sylveon/Espeon] | swsh7 | 31 | 0 | 31 | 82.74 | 509.27 | 515.5% |  | 106.9%/yr | 4.40 | -6.8% | no | yes | no | no |
| 277,336 | Lost Origin Pokemon Center Elite Trainer Box (Exclusive) | swsh11 | 31 | 0 | 18 | 63.87 | 386.41 | 505.0% |  | 105.4%/yr | 2.37 | -17.8% | yes | yes | no | no |
| 242,434 | Evolving Skies Elite Trainer Box [Flareon/Jolteon/Umbreon/Leafeon] | swsh7 | 31 | 0 | 31 | 95.48 | 570.59 | 497.6% |  | 104.4%/yr | 5.14 | -6.3% | no | yes | no | no |
| 185,719 | Unbroken Bonds Elite Trainer Box | sm10 | 20 | 0 | 58 | 376.23 | 1,164.50 | 209.5% |  | 104.1%/yr | 2.00 | -1.0% | no | no | no | yes |
| 245,376 | Evolving Skies Pokemon Center Elite Trainer Box [Jolteon/Flareon/Umbreon/Leafeon] (Exclusive) | swsh7 | 31 | 0 | 31 | 185.66 | 1,086.53 | 485.2% |  | 102.7%/yr | 4.63 | -0.9% | yes | yes | no | no |
| 277,335 | Lost Origin Elite Trainer Box | swsh11 | 31 | 0 | 18 | 35.08 | 194.55 | 454.6% |  | 98.4%/yr | 3.62 | -16.0% | no | yes | no | no |
| 251,199 | Celebrations Pokemon Center Elite Trainer Box (Exclusive) | cel25 | 31 | 0 | 29 | 110.31 | 568.24 | 415.1% |  | 92.6%/yr | 2.55 | -10.5% | yes | yes | no | no |
| 111,280 | XY BREAKpoint Elite Trainer Box | xy9 | 29 | 0 | 99 | 240.00 | 1,099.99 | 358.3% |  | 92.0%/yr | 2.40 | -3.3% | no | no | yes | no |
| 557,350 | Stellar Crown Elite Trainer Box | sv7 | 26 | 0 | -1 | 39.65 | 154.35 | 289.3% |  | 92.0%/yr | 2.49 | -14.9% | no | no | yes | no |
| 283,401 | Silver Tempest Elite Trainer Box | swsh12 | 31 | 0 | 16 | 30.50 | 155.70 | 410.5% |  | 92.0%/yr | 3.15 | -14.9% | no | yes | no | no |
| 107,107 | Elite Trainer Box [Mewtwo Y] | xy8 | 26 | 3 | 102 | 331.98 | 1,499.00 | 351.5% |  | 90.8%/yr | 2.33 | 0.0% | no | no | yes | no |
| 123,741 | Generations Elite Trainer Box | g1 | 31 | 0 | 97 | 602.32 | 2,999.19 | 397.9% |  | 90.1%/yr | 2.79 | -5.9% | no | yes | no | no |
| 199,308 | Cosmic Eclipse Elite Trainer Box | sm12 | 29 | 2 | 52 | 381.14 | 1,874.50 | 391.8% |  | 89.1%/yr | 2.89 | -2.6% | no | no | no | no |
| 285,860 | Silver Tempest Pokemon Center Elite Trainer Box (Exclusive) | swsh12 | 31 | 0 | 16 | 74.31 | 364.37 | 390.3% |  | 88.9%/yr | 3.19 | -5.4% | yes | yes | no | no |
| 256,140 | Brilliant Stars Pokemon Center Elite Trainer Box (Exclusive) | swsh9 | 31 | 0 | 25 | 51.25 | 248.23 | 384.4% |  | 88.0%/yr | 2.53 | -18.5% | yes | yes | no | no |
| 478,758 | Scarlet & Violet Pokemon Center Elite Trainer Box (Exclusive) [Koraidon] | sv1 | 31 | 0 | 12 | 61.50 | 290.17 | 371.8% |  | 86.0%/yr | 2.05 | -18.1% | yes | yes | no | no |
| 242,811 | Celebrations Elite Trainer Box | cel25 | 31 | 0 | 29 | 77.37 | 353.12 | 356.4% |  | 83.5%/yr | 2.51 | -29.1% | no | yes | no | no |
| 265,528 | Astral Radiance Pokemon Center Elite Trainer Box (Exclusive) | swsh10 | 31 | 0 | 22 | 49.11 | 220.38 | 348.7% |  | 82.3%/yr | 2.78 | -19.3% | yes | yes | no | no |
| 164,303 | Forbidden Light Elite Trainer Box | sm6 | 30 | 1 | 70 | 153.97 | 685.41 | 345.2% |  | 81.7%/yr | 3.11 | -9.6% | no | no | no | no |
| 256,138 | Brilliant Stars Elite Trainer Box | swsh9 | 31 | 0 | 25 | 37.38 | 160.76 | 330.1% |  | 79.2%/yr | 3.35 | -20.1% | no | yes | no | no |
| 265,527 | Astral Radiance Elite Trainer Box | swsh10 | 31 | 0 | 22 | 33.56 | 143.70 | 328.2% |  | 78.9%/yr | 2.82 | -10.8% | no | yes | no | no |
| 478,756 | Scarlet & Violet Pokemon Center Elite Trainer Box (Exclusive) [Miraidon] | sv1 | 31 | 0 | 12 | 74.94 | 317.06 | 323.1% |  | 78.1%/yr | 2.30 | -13.8% | yes | yes | no | no |
| 478,335 | Scarlet & Violet Elite Trainer Box [Koraidon] | sv1 | 31 | 0 | 12 | 32.52 | 135.58 | 316.9% |  | 77.0%/yr | 3.31 | -8.0% | no | yes | no | no |
| 512,813 | Paradox Rift Elite Trainer Box [Iron Valiant] | sv4 | 31 | 0 | 4 | 32.70 | 136.13 | 316.3% |  | 76.9%/yr | 3.07 | -10.1% | no | yes | no | no |
| 478,336 | Scarlet & Violet Elite Trainer Box [Miraidon] | sv1 | 31 | 0 | 12 | 35.95 | 148.18 | 312.2% |  | 76.2%/yr | 3.07 | -10.4% | no | yes | no | no |
| 129,890 | Guardians Rising Elite Trainer Box | sm2 | 28 | 3 | 82 | 105.41 | 421.79 | 300.1% |  | 74.1%/yr | 4.88 | -3.8% | no | no | no | no |
| 107,106 | Elite Trainer Box [Mewtwo X] | xy8 | 16 | 0 | 112 | 453.99 | 900.00 | 98.2% |  | 72.9%/yr | 2.11 | -2.3% | no | no | yes | yes |
| 512,815 | Paradox Rift Elite Trainer Box [Roaring Moon] | sv4 | 31 | 0 | 4 | 37.03 | 144.55 | 290.4% |  | 72.4%/yr | 2.95 | -13.7% | no | yes | no | no |
| 175,511 | Lost Thunder Elite Trainer Box | sm8 | 31 | 0 | 64 | 176.62 | 681.55 | 285.9% |  | 71.6%/yr | 2.68 | -3.6% | no | yes | no | no |
| 145,847 | Shining Legends Elite Trainer Box | sm35 | 31 | 0 | 77 | 266.92 | 1,016.29 | 280.7% |  | 70.7%/yr | 3.61 | -0.4% | no | yes | no | no |
| 123,447 | XY Evolutions Elite Trainer Box [Mega Charizard Y] | xy12 | 31 | 0 | 88 | 220.03 | 830.82 | 277.6% |  | 70.1%/yr | 3.33 | -12.0% | no | yes | no | no |
| 229,285 | Battle Styles Elite Trainer Box [Rapid Strike Urshifu] (Blue) | swsh5 | 31 | 0 | 36 | 36.47 | 134.30 | 268.2% |  | 68.4%/yr | 3.13 | -3.5% | no | yes | no | no |
| 120,697 | Steam Siege Elite Trainer Box | xy11 | 13 | 18 | 91 | 499.00 | 1,800.00 | 260.7% | GAP | 67.1%/yr | 1.73 | -18.2% | no | no | no | no |
| 512,809 | Paradox Rift Pokemon Center Elite Trainer Box (Exclusive) [Roaring Moon] | sv4 | 31 | 0 | 4 | 62.35 | 217.40 | 248.7% |  | 64.8%/yr | 2.16 | -12.7% | yes | yes | no | no |
| 552,999 | Shrouded Fable Elite Trainer Box | sv6pt5 | 27 | 0 | -1 | 39.48 | 113.74 | 188.1% |  | 63.0%/yr | 1.69 | -27.0% | no | no | yes | no |
| 229,284 | Battle Styles Elite Trainer Box [Single Strike Urshifu] (Red) | swsh5 | 31 | 0 | 36 | 37.64 | 126.94 | 237.2% |  | 62.6%/yr | 2.88 | -8.2% | no | yes | no | no |
| 216,856 | Darkness Ablaze Elite Trainer Box | swsh3 | 31 | 0 | 43 | 33.74 | 113.48 | 236.3% |  | 62.4%/yr | 2.49 | -16.9% | no | yes | no | no |
| 565,630 | Surging Sparks Elite Trainer Box | sv8 | 25 | 0 | -2 | 48.13 | 126.95 | 163.8% |  | 62.4%/yr | 1.26 | -37.8% | no | no | yes | no |
| 247,282 | Chilling Reign Pokemon Center Elite Trainer Box [Shadow Rider Calyrex] (Exclusive) | swsh6 | 31 | 0 | 33 | 56.98 | 191.21 | 235.6% |  | 62.3%/yr | 2.22 | -10.9% | yes | yes | no | no |
| 123,448 | XY Evolutions Elite Trainer Box [Mega Blastoise] | xy12 | 31 | 0 | 88 | 191.99 | 635.89 | 231.2% |  | 61.5%/yr | 3.83 | -4.6% | no | yes | no | no |
| 173,393 | Dragon Majesty Elite Trainer Box | sm75 | 31 | 0 | 66 | 381.99 | 1,256.49 | 228.9% |  | 61.0%/yr | 2.92 | -7.3% | no | yes | no | no |
| 133,776 | Burning Shadows Elite Trainer Box | sm3 | 31 | 0 | 79 | 98.56 | 323.35 | 228.1% |  | 60.8%/yr | 4.10 | -0.3% | no | yes | no | no |
| 221,752 | Vivid Voltage Elite Trainer Box | swsh4 | 31 | 0 | 40 | 41.61 | 135.94 | 226.7% |  | 60.6%/yr | 2.64 | -10.0% | no | yes | no | no |
| 236,261 | Chilling Reign Elite Trainer Box [Shadow Rider Calyrex] | swsh6 | 31 | 0 | 33 | 46.65 | 151.60 | 225.0% |  | 60.2%/yr | 3.23 | -1.6% | no | yes | no | no |
| 228,821 | Shining Fates Elite Trainer Box | swsh45 | 31 | 0 | 37 | 44.57 | 144.84 | 225.0% |  | 60.2%/yr | 3.33 | -8.4% | no | yes | no | no |
| 100,495 | Ancient Origins Elite Trainer Box | xy7 | 13 | 7 | 103 | 1,250.00 | 2,625.00 | 110.0% | GAP | 59.8%/yr | 1.90 | 0.0% | no | no | no | yes |
| 149,377 | Crimson Invasion Elite Trainer Box | sm4 | 31 | 0 | 76 | 67.99 | 218.27 | 221.0% |  | 59.4%/yr | 2.81 | -7.1% | no | yes | no | no |
| 194,729 | Hidden Fates Elite Trainer Box | sm115 | 31 | 0 | 55 | 176.31 | 560.90 | 218.1% |  | 58.9%/yr | 3.00 | -7.5% | no | yes | no | no |
| 155,664 | Ultra Prism Elite Trainer Box [Dusk Mane Necrozma] | sm5 | 30 | 1 | 73 | 230.32 | 728.97 | 216.5% |  | 58.5%/yr | 2.23 | -6.0% | no | no | no | no |
| 512,801 | Paradox Rift Pokemon Center Elite Trainer Box (Exclusive) [Iron Valiant] | sv4 | 31 | 0 | 4 | 60.33 | 189.74 | 214.5% |  | 58.1%/yr | 2.00 | -14.3% | yes | yes | no | no |
| 532,848 | Temporal Forces Elite Trainer Box [Iron Leaves ex] | sv5 | 31 | 0 | 0 | 40.05 | 125.91 | 214.4% |  | 58.1%/yr | 2.15 | -24.0% | no | yes | no | no |
| 532,845 | Temporal Forces Elite Trainer Box [Walking Wake] | sv5 | 31 | 0 | 0 | 44.29 | 136.96 | 209.2% |  | 57.1%/yr | 2.03 | -23.8% | no | yes | no | no |
| 247,281 | Chilling Reign Pokemon Center Elite Trainer Box [Ice Rider Calyrex] (Exclusive) | swsh6 | 31 | 0 | 33 | 65.50 | 200.47 | 206.1% |  | 56.4%/yr | 1.94 | -14.4% | yes | yes | no | no |
| 236,260 | Chilling Reign Elite Trainer Box [Ice Rider Calyrex] | swsh6 | 31 | 0 | 33 | 46.47 | 141.81 | 205.2% |  | 56.2%/yr | 3.17 | -5.9% | no | yes | no | no |
| 118,331 | Fates Collide Elite Trainer Box | xy10 | 24 | 5 | 94 | 275.22 | 775.97 | 181.9% |  | 55.9%/yr | 1.95 | -9.9% | no | no | no | yes |
| 155,663 | Ultra Prism Elite Trainer Box [Dawn Wings Necrozma] | sm5 | 29 | 2 | 73 | 263.49 | 711.99 | 170.2% |  | 48.8%/yr | 1.70 | -11.0% | no | no | no | no |
| 206,038 | Sword & Shield Elite Trainer Box [Zacian] | swsh1 | 31 | 0 | 49 | 61.65 | 165.86 | 169.0% |  | 48.6%/yr | 2.41 | -11.8% | no | yes | no | no |
| 206,039 | Sword & Shield Elite Trainer Box [Zamazenta] | swsh1 | 31 | 0 | 49 | 58.84 | 157.93 | 168.4% |  | 48.4%/yr | 3.07 | -3.7% | no | yes | no | no |
| 543,845 | Twilight Masquerade Elite Trainer Box | sv6 | 30 | 0 | -1 | 49.74 | 108.19 | 117.5% |  | 37.9%/yr | 1.07 | -29.6% | no | no | yes | no |
| 210,572 | Rebel Clash Elite Trainer Box | swsh2 | 31 | 0 | 46 | 148.37 | 326.83 | 120.3% |  | 37.1%/yr | 2.56 | -9.3% | no | yes | no | no |
| 565,632 | Surging Sparks Pokemon Center Elite Trainer Box (Exclusive) | sv8 | 24 | 0 | -1 | 149.99 | 270.98 | 80.7% |  | 36.2%/yr | 0.88 | -33.5% | yes | no | yes | no |
| 218,791 | Champion's Path Elite Trainer Box | swsh35 | 31 | 0 | 42 | 107.82 | 218.37 | 102.5% |  | 32.6%/yr | 2.21 | -13.4% | no | yes | no | no |
| 610,930 | Journey Together Elite Trainer Box | sv9 | 20 | 0 | -1 | 90.54 | 140.09 | 54.7% |  | 31.7%/yr | 0.95 | -26.9% | no | no | yes | no |
| 593,355 | Prismatic Evolutions Elite Trainer Box | sv8pt5 | 22 | 0 | -1 | 106.67 | 156.61 | 46.8% |  | 24.5%/yr | 0.80 | -22.6% | no | no | yes | no |
| 648,394 | Mega Evolution Elite Trainer Box [Mega Lucario] | me1 | 13 | 0 | 0 | 99.68 | 123.90 | 24.3% |  | 24.3%/yr | 0.64 | -22.7% | no | no | yes | no |
| 538,775 | Temporal Forces Pokemon Center Elite Trainer Box (Exclusive) [Walking Wake] | sv5 | 31 | 0 | 0 | 149.99 | 205.64 | 37.1% |  | 13.5%/yr | 0.27 | -54.5% | yes | yes | no | no |
| 532,853 | Temporal Forces Pokemon Center Elite Trainer Box (Exclusive) [Iron Leaves] | sv5 | 31 | 0 | 0 | 149.47 | 196.63 | 31.6% |  | 11.6%/yr | 0.27 | -58.0% | yes | yes | no | no |
| 543,844 | Twilight Masquerade Pokemon Center Elite Trainer Box (Exclusive) | sv6 | 29 | 0 | 0 | 149.98 | 190.93 | 27.3% |  | 10.9%/yr | 0.27 | -52.0% | yes | no | yes | no |
| 557,340 | Stellar Crown Pokemon Center Elite Trainer Box (Exclusive) | sv7 | 25 | 0 | 0 | 149.99 | 174.19 | 16.1% |  | 7.8%/yr | 0.15 | -47.6% | yes | no | yes | no |
| 593,324 | Prismatic Evolutions Pokemon Center Elite Trainer Box (Exclusive) | sv8pt5 | 22 | 0 | -1 | 383.32 | 432.02 | 12.7% |  | 7.1%/yr | 0.15 | -45.5% | yes | no | yes | no |
| 630,686 | Black Bolt Elite Trainer Box | zsv10pt5 | 16 | 0 | -1 | 158.92 | 167.22 | 5.2% |  | 4.2%/yr | 0.07 | -47.7% | no | no | yes | no |
| 552,998 | Shrouded Fable Pokemon Center Elite Trainer Box (Exclusive) | sv6pt5 | 27 | 0 | -1 | 159.99 | 166.87 | 4.3% |  | 2.0%/yr | 0.04 | -57.8% | yes | no | yes | no |
| 630,689 | White Flare Elite Trainer Box | rsv10pt5 | 16 | 0 | -1 | 158.44 | 154.59 | -2.4% |  | -1.9%/yr | -0.03 | -50.6% | no | no | yes | no |
| 654,136 | Phantasmal Flames Elite Trainer Box | me2 | 12 | 0 | -1 | 164.66 | 157.17 | -4.5% |  | -5.0%/yr | -0.05 | -53.3% | no | no | yes | no |
| 630,688 | White Flare Pokemon Center Elite Trainer Box (Exclusive) | rsv10pt5 | 16 | 0 | -1 | 299.99 | 239.64 | -20.1% |  | -16.4%/yr | -0.27 | -59.6% | yes | no | yes | no |
| 630,687 | Black Bolt Pokemon Center Elite Trainer Box (Exclusive) | zsv10pt5 | 16 | 0 | -1 | 363.99 | 276.21 | -24.1% |  | -19.8%/yr | -0.31 | -55.1% | yes | no | yes | no |
| 644,279 | Mega Evolution Elite Trainer Box [Mega Gardevoir] | me1 | 14 | 0 | -1 | 153.15 | 116.58 | -23.9% |  | -22.3%/yr | -0.41 | -51.2% | no | no | yes | no |
| 610,929 | Journey Together Pokemon Center Elite Trainer Box (Exclusive) | sv9 | 19 | 0 | 0 | 330.11 | 201.83 | -38.9% |  | -28.0%/yr | -0.42 | -66.0% | yes | no | yes | no |
| 624,676 | Destined Rivals Elite Trainer Box | sv10 | 18 | 0 | -1 | 192.15 | 118.02 | -38.6% |  | -29.1%/yr | -0.46 | -54.2% | no | no | yes | no |
| 644,282 | Mega Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Lucario] | me1 | 14 | 0 | -1 | 392.20 | 231.35 | -41.0% |  | -38.6%/yr | -0.59 | -57.7% | yes | no | yes | no |
| 648,415 | Mega Evolution Pokemon Center Elite Trainer Box (Exclusive) [Mega Gardevoir] | me1 | 13 | 0 | 0 | 369.32 | 200.09 | -45.8% |  | -45.8%/yr | -0.79 | -60.6% | yes | no | yes | no |
| 624,675 | Destined Rivals Pokemon Center Elite Trainer Box (Exclusive) | sv10 | 18 | 0 | -1 | 1,195.00 | 486.04 | -59.3% |  | -47.0%/yr | -0.46 | -84.7% | yes | no | yes | no |
| 654,135 | Phantasmal Flames Pokemon Center Elite Trainer Box (Exclusive) | me2 | 12 | 0 | -1 | 587.13 | 285.65 | -51.3% |  | -54.4%/yr | -0.57 | -68.7% | yes | no | yes | no |
| 98,028 | XY Roaring Skies Elite Trainer Box | xy6 | 11 | 1 | 122 | 1,597.50 | 4,899.99 | 206.7% |  | n/a | n/a | 0.0% | no | no | yes | yes |
| 670,607 | Prismatic Evolutions Elite Trainer Box (Dollar General Exclusive) | sv8pt5 | 9 | 0 | 12 | 127.95 | 200.65 | 56.8% |  | n/a | n/a | -2.4% | no | no | yes | no |
| 668,496 | Ascended Heroes Elite Trainer Box | me2pt5 | 9 | 0 | 0 | 132.60 | 168.98 | 27.4% |  | n/a | n/a | -33.1% | no | no | yes | no |
| 668,497 | Ascended Heroes Pokemon Center Elite Trainer Box (Exclusive) | me2pt5 | 9 | 0 | 0 | 386.33 | 409.27 | 5.9% |  | n/a | n/a | -22.1% | yes | no | yes | no |
| 692,947 | Pitch Black Elite Trainer Box | me5 | 4 | 0 | -1 | 124.95 | 70.66 | -43.4% |  | n/a | n/a | -43.4% | no | no | yes | no |
| 672,401 | Perfect Order Elite Trainer Box | me3 | 8 | 0 | -1 | 131.36 | 72.55 | -44.8% |  | n/a | n/a | -48.8% | no | no | yes | no |
| 684,450 | Chaos Rising Elite Trainer Box | me4 | 6 | 0 | -1 | 139.55 | 70.93 | -49.2% |  | n/a | n/a | -49.2% | no | no | yes | no |
| 672,404 | Perfect Order Pokemon Center Elite Trainer Box | me3 | 8 | 0 | -1 | 390.55 | 121.01 | -69.0% |  | n/a | n/a | -69.2% | yes | no | yes | no |
| 684,452 | Chaos Rising Pokemon Center Elite Trainer Box | me4 | 5 | 0 | 0 | 499.72 | 135.46 | -72.9% |  | n/a | n/a | -72.9% | yes | no | yes | no |
| 692,949 | Pitch Black Pokemon Center Elite Trainer Box (Exclusive) | me5 | 4 | 0 | -1 | 616.66 | 124.01 | -79.9% |  | n/a | n/a | -79.9% | yes | no | yes | no |

### 7.4 Corrections to previously published figures

This repo discloses corrections rather than silently overwriting them. 14
figures below were published in earlier versions of `etb_summary.md`,
`etb_hold_summary.md` and `etb.html` and are **wrong**. They are recorded here,
machine-readably in `etb_corrections.csv`, with the live replacement resolved
from this build rather than stored -- so if a number moves again, this table
moves with it. Corrected 2026-07-25.

| figure | published (wrong) | corrected | moved | appeared in |
| --- | --- | --- | --- | --- |
| launch cohort, pooled trough (multiple of launch price) | 0.61x | 0.93x | revised up | etb_summary.md 4.3, etb.html |
| launch cohort at 12 months (multiple of launch price) | 1.00x | 1.68x | revised up | etb_summary.md 4.3, etb.html |
| share of the cohort below launch at month 2 | 100% | 55% | revised down | etb_summary.md 4.3 |
| mass-retail launch cohort at 12 months | 1.28x | 1.73x | revised up | etb_summary.md 4.3, etb.html |
| Pokemon Center launch cohort at 12 months | 0.78x | 1.63x | revised up | etb_summary.md 4.3, etb.html |
| launch cohort excess over the rest of the ETB market at 12 months | 0.47x | 0.79x | revised up | etb_summary.md 4.3, etb.html |
| post-launch median trough, as a fall from the launch price | 47.2% | 13.3% | revised down | etb_summary.md 6.4, etb_hold_summary.md |
| post-launch drop at a fixed 6-month endpoint | 38.1% | -0.8% | sign reversed | etb_hold_summary.md |
| share of launch-cohort products falling at least 25% | 66% | 22% | revised down | etb_summary.md 6.4, etb_hold_summary.md |
| 12-month net rate for "bought 0-6m after release" | 20.9% | 24.9% | revised up | etb_summary.md 6.4, etb_hold_summary.md 5 |
| share losing money, "bought 0-6m after release", 12-month hold | 30% | 25% | revised down | etb_summary.md 6.4, etb_hold_summary.md 5 |
| chained index of the "0-12m old at entry" cohort | 39.1% | 64.5% | revised up | etb_summary.md 1 and 4.4, etb.html |
| share of the "0-12m old at entry" cohort down over its own window | 35% | 12% | revised down | etb_summary.md 1 and 4.4 |
| t of the 1-3y cohort's difference from the youngest cohort | t = 2.86 | t = 1.21 | revised down | etb_summary.md 1 and 4.4, etb.html, etb_hold_summary.md 5 |

**One misunderstanding, 4 independent modules.** Every row traces to the same
wrong assumption: that a product's first priced row is a price somebody could
have paid. `price_history` is a snapshot taken on the 1st of each month and
essentially no Pokemon set ships on the 1st, so the month a product's listing
first appears is normally a **pre-order quote on a box that has not shipped** --
and those quotes are not cheap. Where a figure above is a ratio to that baseline
the error did not add noise, it moved the whole curve one way; where it is a
bucket edge, it silently mixed pre-order quotes in with shelf prices and made
the group they landed in look worse than it was. The launch-curve study, the
holding study and the cohort split each made the mistake separately, which is
why the rule now lives in one shared module (`etb_launch_anchor`) instead of
being re-derived in each.

A second, independent defect rode along in the launch curve: its x-axis counted
months since the listing first appeared rather than since launch, so a single
"month 2" pooled products at three different ages.

1 of these corrections **reversed the sign** of the published claim rather than
merely resizing it, which is the reason this table exists at all. The pre-order
quotes the corrected baseline refuses to use are themselves published, in
`etb_lifecycle_pre_order_premium.csv`, rather than dropped -- how far a
pre-order sits above the shelf price that follows is a finding in its own right.
