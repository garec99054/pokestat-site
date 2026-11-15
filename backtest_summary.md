# Historical backtest: undervalued vs overvalued forward returns

Question: do cards flagged "undervalued" at date T outperform "overvalued"
and unflagged ("fair") cards over the following ~90 days?

n = 5436 card-date observations across 8 snapshot dates.

## Pooled result (all snapshot dates combined)

| flag | n | mean_return | median_return |
| --- | --- | --- | --- |
| fair | 4693 | 8.6% | 6.7% |
| overvalued | 337 | 9.4% | 5.6% |
| undervalued | 406 | 10.2% | 8.2% |

**Spread (undervalued mean return minus overvalued mean return): +0.8%**

## Per-date result

| snapshot_date | flag | n | mean_return | median_return |
| --- | --- | --- | --- | --- |
| 2024-09-01 | fair | 509 | 2.8% | 2.4% |
| 2024-09-01 | overvalued | 36 | 1.8% | -2.4% |
| 2024-09-01 | undervalued | 51 | 1.9% | 0.0% |
| 2024-12-01 | fair | 521 | 21.1% | 14.8% |
| 2024-12-01 | overvalued | 39 | 31.8% | 24.3% |
| 2024-12-01 | undervalued | 47 | 30.0% | 27.3% |
| 2025-03-01 | fair | 558 | 5.1% | 5.6% |
| 2025-03-01 | overvalued | 46 | 4.4% | -8.9% |
| 2025-03-01 | undervalued | 48 | 10.1% | 7.7% |
| 2025-06-01 | fair | 577 | 6.9% | 5.1% |
| 2025-06-01 | overvalued | 44 | 13.9% | 14.8% |
| 2025-06-01 | undervalued | 48 | -1.1% | -4.5% |
| 2025-09-01 | fair | 602 | 5.8% | 6.5% |
| 2025-09-01 | overvalued | 41 | 11.0% | 9.4% |
| 2025-09-01 | undervalued | 53 | 5.9% | 7.5% |
| 2025-12-01 | fair | 622 | 5.8% | 3.8% |
| 2025-12-01 | overvalued | 42 | -0.5% | 1.1% |
| 2025-12-01 | undervalued | 50 | 9.3% | 8.2% |
| 2026-03-01 | fair | 655 | 17.3% | 12.9% |
| 2026-03-01 | overvalued | 43 | 11.0% | 5.3% |
| 2026-03-01 | undervalued | 53 | 16.6% | 14.2% |
| 2026-06-01 | fair | 649 | 3.9% | 4.7% |
| 2026-06-01 | overvalued | 46 | 3.1% | 3.9% |
| 2026-06-01 | undervalued | 56 | 10.0% | 9.4% |

## Skipped dates

(none)

## Archive dates

Each snapshot is fit on the nearest available tcgcsv archive to the requested
date and scored on the nearest to +90 days (search window ±5
days). tcgcsv withdrew its public archive on 2026-09-22, so only archives
already cached can be used; a shifted window below is that constraint showing.

- 2024-09-01: fit on 2024-09-01, forward 2024-11-30
- 2024-12-01: fit on 2024-12-01, forward 2025-03-01
- 2025-03-01: fit on 2025-03-01, forward 2025-05-30
- 2025-06-01: fit on 2025-06-01, forward 2025-08-30
- 2025-09-01: fit on 2025-09-01, forward 2025-11-30
- 2025-12-01: fit on 2025-12-01, forward 2026-03-01
- 2026-03-01: fit on 2026-03-01, forward 2026-05-30
- 2026-06-01: fit on 2026-06-01, forward 2026-08-30

## Look-ahead limitations (read before trusting these numbers)

- **Pageview look-ahead is now fixed.** Each snapshot's appeal is recomputed
  from the trailing 12 complete months of `feature_pageviews_history` (backfilled
  monthly Wikipedia pageviews, 2024-06..2026-06) ending at the last month before
  that snapshot's own month, log-scaled and percentile-normalized within that snapshot's cohort --
  the same transform `pokestat/features/pageviews.py` applies, just computed
  as of T instead of reused from 2026. 508 of 5440
  (snapshot, dex) appeal evaluations across all non-skipped snapshots
  (9.3%) had no pageview history in their trailing window (no
  Wikipedia article yet, or a gap in the backfill) and fell back to the
  as-of cohort median (neutral 5.5 if no dex had history); no 2026 value is used.
- **Character premium is now as-of-T (look-ahead removed).** The desirability
  input no longer uses the static 2026 `feature_character_premium.premium_10`; it
  is reconstructed at each snapshot date T from `price_history` via
  `pokestat.features.character_premium.compute_premium_asof` -- the per-dex mean
  price percentile within (rarity, series) peer groups, computed from ONLY the
  same-date (== T) price cross-section, which a trader at T could have computed.
  0 of 5440 (snapshot, dex) premium
  evaluations across all non-skipped snapshots (0.0%) had
  no as-of-T premium (too few priced peers that month) and fell back to that
  snapshot's own cohort MEDIAN premium -- a same-date quantity, so still
  leakage-free -- rather than the static 2026 value. price_history starts
  2024-03-01; every snapshot date here is later, so none lack as-of history
  entirely.
- **Modeled-card membership (rarity tiers: SIR / Hyper Rare / Mega Hyper Rare /
  Ultra Rare) is taken from the current DB**, not
  reconstructed as of T; a set's rarity taxonomy does not change after
  release, so this is low-risk, but it does mean sets added to `sets`/`cards`
  after these dates were ingested were not "discovered late" -- they are
  included as long as they pass the release-date-age filter. Snapshot
  *eligibility* is gated on a dex identity (plus artwork, an appeal fallback and
  a pull cost), NOT on the static 2026 character-premium table: admitting a card
  by whether its dex has a big-enough 2026 peer group would leak future
  peer-group sizes into an early-T selection. The premium VALUE used in the fit
  is always the as-of-T reconstruction (see the premium bullet above).
- **Archive date availability**: tcgcsv.com's archive starts 2024-02-08. When
  an exact snapshot or forward date 404s, the nearest available date within
  5 days is substituted (searching outward, nearest first); the
  actual dates used are in backtest_results.csv (`snapshot_date`,
  `forward_date` columns) alongside the originally `requested_date`. If a
  snapshot date so shifts off a canonical first-of-month, its as-of premium is
  reconstructed from the latest `price_history` snapshot on/before the shifted
  date (still <= it, hence leakage-free) instead of an empty same-date
  cross-section; every snapshot in the current run landed on a canonical date,
  so this path was not exercised here.
- **Small per-date samples**: some early dates have few chase cards old enough
  to pass the 30-day-release-age filter, and per-flag group sizes shrink
  further once split three ways. Read per-date means with that in mind; the
  pooled numbers pool across dates for more stable estimates but each card can
  appear in multiple snapshot dates, so pooled rows are not independent draws.
- **Not independent of the momentum/reversion study.** The "overvalued" cohort
  here overlaps disproportionately with the past-winner (top) quintile of the
  cross-sectional momentum study (momentum_summary.md) -- pronounced at the 6m
  formation window -- because a recent run-up is what lifts market above fair
  value. The "undervalued"/past-loser overlap stays near the ~1/5 random
  baseline, so the effect is asymmetric. Read the under-minus-over spread and the
  momentum reversion verdict as two views of the SAME recent-run-up population,
  not as independent confirmations.


Full per-card-per-date rows: backtest_results.csv (same directory).
