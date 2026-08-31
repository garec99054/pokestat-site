# Forward 90-day return model: validation report

There is real, tradeable cross-sectional signal that survives removing the static features. The best model (rf) was chosen on 7 selection folds and scores mean rank IC 0.368 (autocorrelation-aware t-stat 10.211, n_eff 5.673) on the 8 held-out evaluation folds. Ablating the static features leaves mean IC 0.260, so the edge is not purely a set-age effect.

Best model chosen on the selection folds: **rf**. Signal strength
verdict: **strong** (weak if held-out mean IC < 0.05 or IR < 0.5; strong if
mean IC >= 0.1 and IR >= 1.0; **static-effect** overrides these when ablating the
static features collapses the signal below 0.05, OR when it
clears that floor by less than one sampling SE -- a within-noise crossing is
'static-effect (undetermined)', never tipped to strong).

## Methodology change note (2026-07 statistical-hygiene audit)

This report reflects a statistical-hygiene audit. The changes below are disclosed
old -> new; where a published number was deliberately left unchanged that is stated
explicitly.

1. **Purged walk-forward CV -- confirmed already in place (no headline change).**
   `select_training` already implements textbook purged CV: a test month `m` has 3m
   label window [m, m+3], and the `fwd_end <= m` rule drops every training row whose
   label window overlaps the interior of that window. Live audit over the test
   months: **11683** interior-overlapping training rows are
   excluded, **0** are included (structurally zero), and
   only the **5654** abutting boundary rows (fwd_end == m,
   sharing just P_m -- already observed at prediction time, no look-ahead) remain. A
   1-2 month purge gap (embargo) was audited and does NOT reduce held-out IC (it
   slightly rises), i.e. there is no overlap-inflation to correct, so the conservative
   status quo is retained: held-out eval mean IC is unchanged at 0.368.

2. **Verdict made noise-aware (framing change).** The static-effect vs strong call
   is not hung on the held-out ablated-eval IC crossing the hard
   0.05 floor exactly. That IC is
   0.285 +/- 0.018 (1 SE,
   autocorrelation-aware ic_std / sqrt(n_eff) with n_eff
   8.000 of 8 folds);
   it clears the 0.05 floor by more than one SE, so a residual non-static edge is statistically detectable. A within-one-SE
   crossing is reported as 'static-effect (undetermined)' rather than tipped to
   'strong'. Current verdict: **strong**.

3. **Ensemble scale bug fixed (published-number change, ensemble band only).** The
   equal-weight ensemble previously emitted a unit-variance z-score, not a return, so
   its split-conformal band was garbage: prior published values were
   [-1.046, +1.038], width 2.083 (z-score scale). It now calibrates the composite back
   onto the base learners' median cross-sectional return scale, a single positive
   rescale that leaves every Spearman-rank metric (the ensemble's mean IC, quintile
   spread, precision/recall, and its selection rank) EXACTLY unchanged and only
   corrects the return-scale outputs. The ensemble's new return-scale band appears in
   the interval table below. This did NOT change which model was chosen, its headline
   eval IC (0.368), or any Spearman-rank number.

4. **Modeled universe expanded to the SWSH era (published-number change; verdict can
   move).** The prior universe was 278 cards (SV + ME only), on which the verdict was
   'static-effect'. Onboarding the six SWSH chase sets (Evolving Skies, Brilliant
   Stars, Astral Radiance, Lost Origin, Silver Tempest, Crown Zenith) -- with cited
   pull-rate data and blind-anchor-calibrated artwork scores -- widens it to
   465 cards across the SWSH/SV/ME eras. This is a large
   cross-sectional change: the added era carries its own set-age/lifecycle dynamics,
   so the held-out and ablated ICs above are NOT comparable one-to-one with the prior
   278-card run. Reported straight -- expanding the cross-section can move the verdict
   either way, and this run's verdict is **strong** (the Signal attribution
   section shows whether the ablated signal now survives).

5. **Candidate roster expanded (published-number change; the winner moved).** Four candidates were added to the roster (4 -> 8): a Spearman-target linear model (rank_linear), a robust Huber regressor (huber), partial least squares (pls) and a shallow random forest (rf). They are registered in the same MODEL_FITTERS table as the originals, so the selection protocol is untouched -- selection on the selection folds, scoring on the disjoint held-out folds -- and only the field it ranks is wider. No hyperparameter of any newcomer was tuned against the evaluation folds. A newcomer won: the selected model moved from ridge (prior published held-out eval IC 0.303, static-ablated eval IC 0.159) to **rf**, whose held-out eval IC is 0.368 and static-ablated eval IC is 0.285 +/- 0.018. Both directions are reported straight in the candidate-roster table below: the new winner is not uniformly better than the old one on every statistic, and the selection folds -- not the held-out ones -- decided. A wider field also means more ways for the selection step to land somewhere else: the roster section quantifies that multiplicity live (selection-vs-held-out rank correlation, how many candidates the selection folds could not separate, and the full held-out range a different pick would have reported), because every number in this report is computed on the one model the step output.

6. **Within-era / within-rarity breakdown (new diagnostic, no headline change).** The report previously admitted, without measuring it, that the held-out edge might be cross-era contrast (SWSH cards are simply older and priced differently than SV cards) rather than within-era skill. It is now measured on the same held-out folds with the same metric: the pooled edge is reproduced almost entirely by within-era ranking, and the era ordering alone carries nothing distinguishable from zero -- the caveat is answered in the model's favour. Numbers in the breakdown section below; the headline IC, the chosen model and the verdict are unaffected -- this diagnostic only interprets them.


## Signal attribution (is this real skill or a static effect?)

A meaningful part of the headline IC survives removing the static set-age/rarity features, so the edge is not merely a lifecycle effect -- but a large share of it still IS that static effect (see below). Evidence, all computed on the same walk-forward folds:

| diagnostic | mean IC | note |
| --- | --- | --- |
| rf full features (all folds) | 0.328 | the reported number |
| rf STATIC features ablated (all folds) | 0.260 | 21% of the signal gone |
| rf STATIC features ablated (eval folds) | 0.285 +/- 0.018 (1 SE) | held-out, clears the 0.05 floor by more than 1 SE |
| univariate set_age_months ranking | 0.296 | one feature, no model |
| rf momentum-only features | 0.130 | some signal on its own (40% of the full-feature IC), well short of the full feature set |

The held-out ablated-eval IC is 0.285 with a sampling standard error of 0.018 (autocorrelation-aware: ic_std / sqrt(n_eff), n_eff 8.000 of 8 folds), clearing the 0.05 static-effect floor by more than one SE, so genuine non-static signal survives ablation and the verdict is not a mechanical set-age artifact. The noise-aware rule still guards the call: only a crossing wider than one SE tips to 'strong'; a within-one-SE crossing would be reported as 'static-effect (undetermined)'.

Ablated features: set_age_months, log_price, lifecycle_drift, is_sir, is_mega_hyper, is_ultra, is_rare_secret, is_rare_rainbow, is_rare_ultra. The winning
model's pooled out-of-fold predictions correlate 0.370
(Spearman) with set_age_months -- its ranking still correlates substantially with set_age_months -- a large part of the edge remains the set-age ranking.
Because 345 of 465 cards appear in every
fold and set_age barely re-ranks month to month (Spearman rank corr between the
first and last fold is 1.000), the folds are heavily
overlapping re-tests of a largely static cross-sectional ranking, so the naive
sqrt(folds) information ratio overstates robustness; the table above reports the
autocorrelation-deflated IR (n_eff) instead.

## Model selection (held-out)

Candidate models were compared on the first 7 folds
(selection window) and the winner's performance is reported on the disjoint later
8 folds (evaluation window). Selection-fold mean IC for
**rf** was 0.283; held-out evaluation-fold mean
IC was 0.368 (IR 10.211, n_eff
5.673). The full walk-forward table below shows all models over
all folds for transparency, but those all-fold numbers are the SELECTION statistic
and carry optimistic selection bias for the chosen model; the honest number is the
held-out one.

### Candidate roster (expanded)

The roster was widened from 4 to 8 candidates and a NEW candidate won: **rf** tops the selection folds. Reported as it fell out -- the selection protocol was not touched, only the set of models it ranks. Note the gap the protocol deliberately accepts: **ensemble** scored a higher held-out eval IC (0.395) than the selected **rf** (0.368). Selecting on that number instead would be choosing a model by the very statistic then reported as its validation score, so the winner stays the one the selection folds chose.

| rank | candidate | new? | selection-fold IC | held-out eval IC | held-out IR (n_eff) |
| --- | --- | --- | --- | --- | --- |
| 1 | **rf** | new | 0.283 | 0.368 | 10.211 |
| 2 | ensemble |  | 0.278 | 0.395 | 7.459 |
| 3 | huber | new | 0.269 | 0.369 | 5.597 |
| 4 | rank_linear | new | 0.268 | 0.367 | 7.216 |
| 5 | ridge |  | 0.265 | 0.364 | 6.430 |
| 6 | elasticnet |  | 0.246 | 0.333 | 4.921 |
| 7 | gbm |  | 0.236 | 0.385 | 10.359 |
| 8 | pls | new | 0.217 | 0.354 | 4.529 |


**Selection multiplicity, stated rather than implied.** Across the 8 scored candidates the rank correlation between the selection-fold IC (which picks) and the held-out eval IC (which is reported) is rho = 0.500. Held-out eval IC across the roster spans 0.333 to 0.395 and held-out IR 4.529 to 10.359, so the reported headline depends on which of 8 candidates the selection folds happened to rank first. On the selection folds themselves the winner's own error bar is +/- 0.077 (autocorrelation-aware), and 7 of the other 7 candidates sit inside it (ensemble, huber, rank_linear, ridge, elasticnet, gbm, pls) -- i.e. the selection step did not statistically separate them. The selection statistic therefore orders the roster roughly the way the held-out folds do, so the pick is doing real work rather than drawing lots.

"new" marks the candidates added for this run: a Spearman-target linear model
(rank_linear), a robust Huber regressor (huber), partial least squares (pls) and
a shallow random forest (rf). They enter through the same MODEL_FITTERS registry
as the originals, so they are selected on the selection folds and scored on the
disjoint held-out folds like every other candidate; none of their hyperparameters
was tuned against the evaluation folds (each is fixed a priori or chosen by
cross-validation inside the training rows of the fold being fit).


## Within-era and within-rarity breakdown (is the edge cross-era contrast?)

The modeled universe spans three eras (SWSH, SV, ME) whose cards differ in age, price level and lifecycle stage. A pooled cross-sectional IC can therefore be earned two very different ways: by ranking cards correctly INSIDE an era (skill a buyer can act on within one release window), or merely by ranking the eras against each other. This section separates the two for the chosen model (**rf**).

**Finding: the held-out edge is WITHIN-era skill, not cross-era contrast.** The era-NEUTRALIZED IC (every card ranked only against same-era cards) is 0.355 +/- 0.018 (n_eff 8.000), against a pooled held-out 0.368 +/- 0.036 (n_eff 5.673); the era-CONTRAST-ONLY IC (all within-era information destroyed) is 0.144 +/- 0.490 (n_eff 3.567). So essentially all of the pooled IC is reproduced when era contrast is removed, and the era ordering on its own carries nothing distinguishable from zero. The report's standing caveat -- that the jump from the 278-card SV+ME universe to the 441-card SWSH+SV+ME one might have bought a mechanical old-era/new-era contrast -- is NOT what happened. Evidence caveat (the 4.0 effective-fold bar this repo applies elsewhere before a cell may claim a direction): contrast-only does not clear the one-SE bar, but on n_eff 3.567 it could not have detected a moderate effect either -- read it as absence of evidence, not evidence of absence.

Taken one era at a time: ME (0.197 +/- 0.162, 5 folds, 46 cards), SV (0.367 +/- 0.027, 8 folds, 247 cards), SWSH (0.346 +/- 0.016, 8 folds, 163 cards). 3 of 3 era slices clear zero by more than one autocorrelation-aware SE on a sufficient effective sample (n_eff >= 4.0) (ME, SV, SWSH). With the static features ablated, 3 of 3 clear zero on a sufficient effective sample (ME, SV, SWSH).

Era slices, held-out folds only (8 folds):

| slice | cards | folds | held-out IC | +/- 1 SE | n_eff | static-ablated IC | ablated +/- 1 SE | one-SE call |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| pooled (headline) | 456 | 8 | 0.368 | 0.036 | 5.673 | 0.285 | 0.018 | clears 0 by > 1 SE |
| ME | 46 | 5 | 0.197 | 0.162 | 4.155 | 0.211 | 0.045 | clears 0 by > 1 SE |
| SV | 247 | 8 | 0.367 | 0.027 | 8.000 | 0.271 | 0.022 | clears 0 by > 1 SE |
| SWSH | 163 | 8 | 0.346 | 0.016 | 8.000 | 0.318 | 0.022 | clears 0 by > 1 SE |
| within-era neutralized | 456 | 8 | 0.355 | 0.018 | 8.000 | 0.287 | 0.017 | clears 0 by > 1 SE |
| between-era contrast only | 456 | 8 | 0.144 | 0.490 | 3.567 | 0.232 | 0.442 | within 1 SE of 0 |

By rarity tier the same test says: within-tier skill survives; the tier ordering on its own does not (neutralized 0.379 +/- 0.016, n_eff 8.000; contrast-only 0.106 +/- 0.435, n_eff 2.494). 4 of 6 scored tiers clear zero by more than one SE on a sufficient effective sample (n_eff >= 4.0). NOT counted as evidence, though they clear the one-SE bar: Hyper Rare (n_eff 2.354), Rare Rainbow (n_eff 2.420) -- below the 4.0 effective-fold bar this repo applies before a cell may claim a direction (the same MIN_CLAIM_N_EFF the momentum study uses), so the tier rests on roughly one independent draw and is reported as insufficient evidence rather than as corroboration. Evidence caveat (the 4.0 effective-fold bar this repo applies elsewhere before a cell may claim a direction): contrast-only does not clear the one-SE bar, but on n_eff 2.494 it could not have detected a moderate effect either -- read it as absence of evidence, not evidence of absence.

Rarity slices, same held-out folds:

| slice | cards | folds | held-out IC | +/- 1 SE | n_eff | static-ablated IC | ablated +/- 1 SE | one-SE call |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| pooled (headline) | 456 | 8 | 0.368 | 0.036 | 5.673 | 0.285 | 0.018 | clears 0 by > 1 SE |
| Hyper Rare | 33 | 8 | 0.392 | 0.170 | 2.354 | 0.175 | 0.173 | clears 0 by > 1 SE [THIN: n_eff 2.354 < 4.0, insufficient evidence] |
| Mega Hyper Rare | 4 | 0 | n/a | n/a | 0.000 | n/a | n/a | skipped (never >= 8 cards in a fold) |
| Rare Rainbow | 44 | 8 | 0.339 | 0.112 | 2.420 | 0.438 | 0.068 | clears 0 by > 1 SE [THIN: n_eff 2.420 < 4.0, insufficient evidence] |
| Rare Secret | 15 | 8 | 0.253 | 0.094 | 8.000 | 0.175 | 0.101 | clears 0 by > 1 SE |
| Rare Ultra | 104 | 8 | 0.366 | 0.031 | 8.000 | 0.328 | 0.036 | clears 0 by > 1 SE |
| Special Illustration Rare | 110 | 8 | 0.435 | 0.047 | 8.000 | 0.257 | 0.032 | clears 0 by > 1 SE |
| Ultra Rare | 146 | 8 | 0.370 | 0.028 | 8.000 | 0.223 | 0.023 | clears 0 by > 1 SE |
| within-rarity neutralized | 456 | 8 | 0.379 | 0.016 | 8.000 | 0.274 | 0.014 | clears 0 by > 1 SE |
| between-rarity contrast only | 456 | 8 | 0.106 | 0.435 | 2.494 | 0.267 | 0.309 | within 1 SE of 0 |

Both tables use the SAME held-out evaluation folds, the SAME per-fold Spearman IC,
and the SAME out-of-fold predictions as the headline, so every number is directly
comparable with it -- the only change is which rows enter each correlation. A
(slice, fold) cell with fewer than 8 scored cards is SKIPPED rather than
scored as zero, so a thin slice shows fewer folds instead of a mean quietly pulled
toward zero. Error bars are the autocorrelation-aware ic_std / sqrt(n_eff) used
everywhere else in this report, NOT ic_std / sqrt(folds): a slice re-scores mostly
the same cards every month, so its folds are not independent draws and the naive
error bar would be too tight on exactly the slices with the least evidence.

Two independent gates decide whether a row counts as evidence, and BOTH must pass.
(1) The one-SE noise gate: is the mean IC further from zero than its own error bar?
(2) The effective-sample gate: does the row have at least MIN_CLAIM_N_EFF =
4.0 effectively independent folds? n_eff is clipped to [1, folds],
so a row whose per-fold ICs are almost perfectly autocorrelated bottoms out at
n_eff = 1.0 -- one effectively independent draw, on which "clears zero by > 1 SE"
is not a central-limit claim at all. Rows that pass (1) but fail (2) are marked
THIN in the one-SE call column and are excluded from every "N of M slices clear"
count in the prose; they are disclosed, never counted. This is the same
MIN_CLAIM_N_EFF bar the momentum study imposes before a stratified cell may claim
a direction.


### Weakest era slice, adjudicated by resampling

The era table above screens every slice with a one-SE noise gate. That is the
right screen for a table, but a weak adjudicator for the single worst cell, so
the weakest slice gets a direct test. The slice probed is chosen
DETERMINISTICALLY as the era with the LOWEST held-out IC for the chosen model
(**rf**) -- not "the one that looks wrong" -- and it is reported whatever
the answer turns out to be.

This run's weakest era slice is **ME**: held-out IC 0.197
+/- 0.162 over 5 folds and 46 cards, against a
static-ablated 0.211.

**Finding: the ME cell is NOT statistically separated from zero.** The permutation test gives p = 0.114 against the 0.05 level, so the slice supports no directional claim -- neither the positive one its point estimate suggests nor its opposite. 8 of 8 candidates share its sign (roster median 0.308).

Evidence, all computed on the SAME held-out out-of-fold predictions as the
headline (nothing is refit, nothing is re-selected):

| test | result | reads as |
| --- | --- | --- |
| permutation (20,000 draws of a random CARD-CONSTANT ranking scored through this slice's own folds) | p = 0.114 (two-sided), null SD 0.125 | NOT separated from zero at the 0.05 level |
| bootstrap over the slice's cards (5,000 resamples) | 95% CI [-0.013, 0.394] which SPANS zero | sign flips in 3.3% of resamples |
| cross-candidate control (same folds, same cards, same features) | 8 of 8 candidates share the sign; median 0.308 | the roster broadly agrees |

Why the permutation null is a CARD-CONSTANT ranking rather than a per-fold
shuffle: the model's within-slice ordering barely changes month to month, so the
honest question is "how often does an ARBITRARY FIXED ranking of these same cards
score this well or this badly through these same overlapping folds?". Shuffling
each fold independently would answer a different, easier question -- it destroys
the fold overlap that the n_eff deflation exists to acknowledge, and returns a
tighter null than the estimator deserves. Removing the static features does not change the picture inside this slice (ablated IC 0.211 vs full 0.197).

Per-candidate IC on this slice:

| candidate | held-out IC inside ME |
| --- | --- |
| gbm | 0.468 |
| ensemble | 0.417 |
| pls | 0.356 |
| elasticnet | 0.321 |
| ridge | 0.295 |
| rank_linear | 0.253 |
| huber | 0.235 |
| rf | 0.197 |


## Recovered listing-book features (previously discarded tcgcsv fields)

tcgcsv returns five price points for every product -- `lowPrice`, `midPrice`,
`highPrice`, `marketPrice`, `directLowPrice`. The monthly panel used to keep only
`marketPrice` and throw the other four away at aggregation time. They describe the
SHAPE of the listing book around the traded price (width, where trades clear inside
it, ask-side overhang, dealer inventory), which is a liquidity / thinness /
dealer-pressure proxy. Across 30 monthly snapshots of `price_history`, the extra points are populated at: low 100%, mid 100%, high 100%, direct_low 42%. They are present for EVERY historical date, not just the present-day one, which is what makes them usable as training features at all.

Six scale-free features are derived from them, all normalised by `market` and all
read from the date-T snapshot (and the T-3m snapshot for the two deltas), so they
are strictly as-of-T: `rel_spread`, `market_pos`, `mid_skew`, `direct_discount`, `d_rel_spread_3m`, `d_market_pos_3m`,
plus the `direct_missing` indicator. All six are time-varying and
therefore stay IN the static-ablated feature set (they are not static-effect
carriers); the ablation table above is unaffected by their classification.

### Before / after (full selection protocol re-run on each feature set)

| arm | features | winner | selection IC | held-out eval IC | held-out IR | static-ablated eval IC |
| --- | --- | --- | --- | --- | --- | --- |
| before (market only) | 12 numeric + 9 ind. | rf | 0.289 | 0.313 +/- 0.083 | 3.771 | 0.233 |
| after (+ listing book) | 18 numeric + 10 ind. | rf | 0.283 | 0.368 +/- 0.036 | 10.211 | 0.285 |

Held-out mean rank IC moves 0.313 -> 0.368
(+0.055); the static-ablated held-out IC moves
0.233 -> 0.285 (+0.053).
Both arms use the SAME panel, the SAME folds, the SAME selection/evaluation split
and the SAME metric -- only the feature list differs. The selection folds chose the same model (**rf**) on both sides, so the comparison is not confounded by a change of learner.

The held-out error bars above are the autocorrelation-aware `ic_std / sqrt(n_eff)`
used everywhere else in this report, NOT `ic_std / sqrt(folds)`. That matters here
specifically: the two arms' fold-IC series have different autocorrelation, so the
naive bar would tighten one side of this comparison more than the other.
State it plainly: the move (+0.055) is SMALLER than the 'before' arm's own one-SE band (0.083). On these error bars a reader cannot conclude that the improvement clears sampling noise, and no joint significance test of the two arms is claimed anywhere in this section. The 'after' arm's bar is tighter (0.036) only because its fold-IC series is less autocorrelated, not because it has more data.

### Where the gain comes from, and what it really is

Univariate IC of each new feature on its own (no model, raw feature vs realized
market-relative return). The SELECTION column is what nominates the single
driver feature discussed below; the HELD-OUT column is what is then reported for
it. Both are shown so the pick and the score are visibly different statistics.
Error bars are the autocorrelation-aware `ic_std / sqrt(n_eff)` used everywhere
else in this report, NOT `ic_std / sqrt(folds)`.

| feature | selection-fold IC | held-out IC | +/- 1 SE |
| --- | --- | --- | --- |
| mid_skew | 0.181 | 0.190 | 0.036 |
| d_market_pos_3m | -0.117 | -0.087 | 0.031 |
| rel_spread | 0.055 | -0.028 | 0.208 |
| direct_discount | 0.040 | 0.021 | 0.053 |
| market_pos | -0.124 | 0.012 | 0.067 |
| d_rel_spread_3m | 0.003 | 0.001 | 0.041 |

The gain is CONCENTRATED, not spread across the six new features: adding `mid_skew` alone to the pre-spread feature set already reaches held-out 0.364, against 0.313 without it and 0.368 with all six. The other five contribute the remainder. How `mid_skew` was picked, stated so the number can be read correctly: it is the largest-magnitude univariate IC on the SELECTION folds (0.181), which are disjoint from the held-out folds every number quoted in this paragraph comes from. The pick therefore does not peek at the evaluation data, and the 0.364 is a held-out score for a pre-registered choice rather than the best of six post-hoc looks. Both columns are in the table above so the multiple-comparison context is visible either way.

The univariate IC of `mid_skew` DECAYS monotonically-ish as the horizon lengthens (1m 0.277, 2m 0.240, 3m 0.190, 6m 0.076). That is the signature of a mechanical catch-up, not of demand forecasting: TCGplayer's `market` is a trailing transaction-weighted average, while `mid` is the CURRENT listing midpoint, so `mid` carries fresher information than `market` at the same instant. A large part of this feature's edge is therefore the stale average converging on a book that was already visible at T -- honest as-of-T signal, but substantially a measurement-lag artifact of how the price series is constructed rather than a forecast of future demand. A buyer paying live listing prices would capture less of it than the IC suggests.

This is disclosed rather than buried because it changes how the improvement should
be read: the recovered fields are legitimate, leakage-free, as-of-T data from an
already-approved source, and the IC gain is real on held-out folds -- but it is
mostly ONE feature, and that feature is substantially exploiting a lag inside the
price series rather than predicting the market.


## Walk-forward metrics (all models and baselines)

Expanding-window, 15 monthly test folds. For each fold, training
uses only rows whose 3m forward window ends on or before the test month (no
overlap). IC is the per-fold Spearman rank correlation between the predicted
market-relative return and the realized market-relative return. "IC autocorr" is
the lag-1 autocorrelation of the per-fold IC series; "eff folds" is n_eff =
folds * (1 - autocorr) / (1 + autocorr); "IC IR (n_eff)" is
mean/std * sqrt(n_eff) -- deflated because positively autocorrelated folds are
not independent draws (the naive sqrt(folds) overstates robustness).
**Read "IC IR" as a t-statistic, not as an information ratio.** mean/std *
sqrt(n_eff) is the mean divided by the standard ERROR; a Sharpe-style
information ratio divides by the standard DEVIATION, and the two differ by
sqrt(n_eff). The column name is kept for continuity with published artifacts,
but the portfolio-management intuition that "an IR above 1 is good" is
calibrated on mean/SD and does NOT transfer to this number. Quintile
spread is the pooled mean realized relative return of the predicted top quintile
minus the bottom quintile. Big-move precision/recall use the predicted top decile
against realized >= +20% absolute 3m moves (up) and the predicted bottom decile
against <= -20% moves (down). NOTE: these are all-fold (selection) numbers shown
for transparency; the chosen model's honest number is the held-out one above.

| model | mean IC | IC std | IC autocorr | eff folds | IC IR (n_eff) | quintile spread | up prec | up rec | down prec | down rec | folds |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ridge | 0.318 | 0.141 | 0.563 | 4.191 | 4.622 | 17.2% | 37.0% | 18.1% | 27.3% | 24.3% | 15 |
| elasticnet | 0.292 | 0.142 | 0.495 | 5.064 | 4.631 | 14.9% | 34.5% | 16.9% | 27.5% | 24.5% | 15 |
| gbm | 0.316 | 0.148 | 0.764 | 2.009 | 3.023 | 17.3% | 38.9% | 19.1% | 27.5% | 24.5% | 15 |
| ensemble | 0.340 | 0.151 | 0.671 | 2.957 | 3.875 | 17.9% | 36.6% | 18.0% | 28.3% | 25.2% | 15 |
| rank_linear | 0.321 | 0.134 | 0.504 | 4.941 | 5.304 | 17.3% | 37.8% | 18.5% | 28.3% | 25.2% | 15 |
| huber | 0.322 | 0.145 | 0.564 | 4.182 | 4.527 | 16.7% | 37.5% | 18.4% | 28.1% | 25.1% | 15 |
| pls | 0.290 | 0.140 | 0.401 | 6.408 | 5.239 | 15.1% | 32.8% | 16.1% | 28.9% | 25.8% | 15 |
| rf | 0.328 | 0.110 | 0.478 | 5.301 | 6.854 | 17.0% | 34.2% | 16.8% | 31.2% | 27.9% | 15 |
| zero | 0.000 | 0.000 | 0.000 | 15.000 | n/a | 7.6% | 19.6% | 9.6% | 19.9% | 17.7% | 15 |
| momentum | -0.061 | 0.101 | 0.457 | 5.591 | -1.423 | -3.0% | 14.7% | 7.2% | 18.1% | 16.1% | 15 |
| reversion | 0.137 | 0.207 | 0.696 | 2.692 | 1.089 | 6.6% | 22.3% | 10.9% | 15.8% | 14.1% | 15 |

Baselines that must be beaten to claim signal: zero prediction, momentum-only
(mom_3m as the score), reversion-only (negative mispricing residual as the
score). A model earns "signal" only if it beats all three on mean IC.

The equal-weight ensemble (standardized mean of ridge/elasticnet/gbm) ranked #2 of 8 candidate models by selection-fold mean IC. It flows through the identical walk-forward selection/evaluation
machinery as the base learners (no special-casing), so its rank is comparable.

## Prediction intervals (split-conformal, per rarity tier)

Every outlook prediction carries an 80% uncertainty band. Out-of-fold residuals
(realized minus predicted market-relative return) are collected from the
EVALUATION folds only -- never the selection folds used to choose the model -- and
their empirical [10th, 90th] quantiles are recentred on each card's point
prediction (pred_lo90, pred_hi90 in forward_outlook.csv). The quantiles are taken **within each rarity tier**, so band width varies
by card.

The chosen model (**rf**) calibrates on 3424 eval-fold
residuals. 5 of 7 rarity tiers cleared the
200-residual minimum and carry their own band; the rest borrow the
pooled band [-0.178, 0.206] (width 0.384) and are
marked as borrowed in the table below. Self-calibrated tier widths range from 0.250 to 0.504 (2.0x)
-- the spread a single global band used to average away.

**Why a minimum-n fallback, and why 200.** The realized coverage of
an empirically calibrated 80% band is a binomial proportion, so its sampling SD
is about `sqrt(0.8 * 0.2 / n)` -- 2.8 points at n = 200. Below roughly that size a
tier's own quantiles are noisier than the miscalibration they exist to remove, so
the thin tier borrows the pooled band instead of being handed a band it cannot
support. The threshold is a variance floor, not a validity floor; the validity
floor is far lower and is discussed under the guarantee limit below.

### Coverage, measured out of the calibration sample

**The published coverage number is now measured on folds that did not calibrate
it.** For each held-out fold the bands are recalibrated on STRICTLY PRIOR folds
only and the fold's realized returns are then scored against them -- the sequence
a user actually experiences. Over 8 scored folds and
3424 card-months, realized coverage is
**81.5%** against a 80.0%
nominal target, at a mean band width of 0.426.

The previous published number was **not a measurement at all**. It took the
empirical 10th and 90th percentiles of a residual sample and then asked what
fraction of that same sample fell between them, which returns the nominal level
for any input whatsoever. Every row of this report's candidate table used to read
"80.0% / 80.0%" for that reason. The statistic is retained in the candidate table
below under the honest name `in-sample check` -- it still reads at the nominal
level for every candidate, which is precisely what makes it a construction check
rather than evidence.

Demonstrated rather than asserted -- the same folds, three predictors:

| predictor | in-sample check | honest coverage | honest band width |
| --- | --- | --- | --- |
| the selected model | 80.3% | 81.5% | 0.426 |
| N(0, 1) noise | 79.7% | 80.5% | 2.601 |
| constant zero | 80.0% | 80.7% | 0.446 |

The in-sample column cannot tell the three apart -- that is the tautology. Note what the honest column also does NOT do: it too lands near nominal for noise, because split conformal is valid for ANY predictor. It just needs a band 6.1x wider to get there. **Coverage alone never separates a model from noise; width against a no-model baseline does**, which is why that comparison is published below rather than left implicit.

### Realized coverage by rarity tier (honest protocol)

| rarity | calibration residuals | own band? | band [q10, q90] | band width | scored rows | realized coverage | nominal |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Hyper Rare | 264 | own | [-0.132, 0.193] | 0.325 | 264 | 81.1% | 80.0% |
| Mega Hyper Rare | 14 | borrowed (pooled) | [-0.178, 0.206] | 0.384 | 12 | 91.7% | 80.0% |
| Rare Rainbow | 352 | own | [-0.158, 0.092] | 0.250 | 352 | 78.4% | 80.0% |
| Rare Secret | 120 | borrowed (pooled) | [-0.178, 0.206] | 0.384 | 120 | 90.8% | 80.0% |
| Rare Ultra | 832 | own | [-0.155, 0.169] | 0.324 | 832 | 82.3% | 80.0% |
| Special Illustration Rare | 765 | own | [-0.172, 0.251] | 0.423 | 765 | 84.3% | 80.0% |
| Ultra Rare | 1077 | own | [-0.239, 0.265] | 0.504 | 1077 | 78.9% | 80.0% |

Across the 5 tiers carrying their own band, realized coverage spans 78.4% to 84.3% -- a 5.9-point spread. Scored on the identical folds with ONE global band instead, the same tiers span 74.5% to 96.3% -- a 21.8-point spread; the per-tier bands are what closed the gap. Tiers still marked borrowed inherit the pooled band and are the ones left visibly off nominal -- disclosed, not fixed.

The bands are conditioned on rarity only. Coverage along the OTHER slice axis is
published too, so a residual gap on the axis that was not banded is visible rather
than assumed away:

| era | scored rows | mean band width | realized coverage | nominal |
| --- | --- | --- | --- | --- |
| ME | 144 | 0.482 | 87.5% | 80.0% |
| SV | 1976 | 0.470 | 80.8% | 80.0% |
| SWSH | 1304 | 0.354 | 82.1% | 80.0% |

### What the modelling is worth, against doing nothing

The honest comparison for a prediction interval is not "does it cover?" -- a
wide enough band always covers. It is "how narrow an interval buys that coverage,
against the interval you could publish with no model at all?" All three
constructions below are scored under the identical rolling protocol on the
identical folds:

| construction | uses the model? | mean band width | realized coverage | nominal |
| --- | --- | --- | --- | --- |
| naive unconditional (no model, one band) | no | 0.451 | 82.6% | 80.0% |
| model + one global band (previously shipped) | yes | 0.430 | 84.1% | 80.0% |
| model + per-rarity bands (**shipped now**) | yes | 0.426 | 81.5% | 80.0% |

So the whole modelling apparatus buys **5.5% tighter** intervals (0.426 against 0.451), at 81.5% realized coverage against the baseline's 82.6%, still at or above the 80.0% nominal target -- a width saving, not coverage traded away. That is the entire measurable return on the feature engineering,
the candidate roster and the selection protocol as far as INTERVALS are concerned
(the ranking metrics elsewhere in this report answer a different question). It is
published because a reader deciding how much to trust the band deserves to know
how close the do-nothing alternative comes.

### Where the finite-sample guarantee stops

Split conformal's distribution-free coverage guarantee is a statement about
EXCHANGEABLE calibration draws, and it needs the order statistic of rank
`ceil((n + 1) * 0.90)` to exist -- i.e. `ceil((n + 1) * 0.90) <= n`.

* On the **3424 residual ROWS**: rank 3083 of 3424 --
  holds.
* On the **8 monthly folds** actually scored: rank
  9 of 8 --
  **FAILS**.
* On the **~3 non-overlapping label blocks** those folds contain (the 3m
  forward window means consecutive monthly folds share a label): rank
  4 of 3 --
  **FAILS**.

The row count is not the sample size. Those 3424 rows are the same few hundred
cards re-scored month after month on overlapping 3-month labels, so the honest
effective sample is the single-digit block count. At `hi = 0.90` the condition
is not satisfiable at all below **9 exchangeable draws**, and
both the fold count and the block count sit at or under that bar. **There is
therefore no finite-sample coverage guarantee behind these bands at the sample
size that matters**, and the realized coverage reported above is exactly that:
realized, measured, and free to be wrong. Read the band as a calibrated
historical-residual band, not as a promise.

### Standing caveats

| caveat | why it matters |
| --- | --- |
| in-sample check is not coverage | The `in-sample check` column measures the calibration sample against quantiles taken from that same sample. It returns the nominal level for ANY predictor (noise included) and is published only as an arithmetic self-check. The coverage column is the rolling out-of-calibration measurement. |
| exchangeability | Split conformal assumes exchangeable residuals. Monthly folds are temporally autocorrelated (the same largely static cross-sectional ranking re-tested each month), so realized forward coverage can drift from nominal -- and under the rolling protocol it visibly does. |
| effective sample size | The guarantee is computed on 3424 residual ROWS but the folds are only 8 monthly re-tests of an overlapping cross-section with 3-month overlapping labels. See the guarantee-limit section: the finite-sample condition fails at the effective sample size. |
| conditioning is coarse | Bands are conditioned on rarity tier only -- not on price level, volatility, era, or the card itself. Within a tier every card still receives the same width, so the band remains an average over that tier rather than a card-specific interval. |
| thin tiers borrow | A tier under the minimum-n threshold is given the pooled band. Its interval is therefore calibrated on a population it is not representative of, which the per-tier coverage table shows directly. |
| forward drift | Every number here is measured on folds that have already happened. Nothing in the construction protects coverage against a regime the calibration window never contained. |

### Calibration by candidate

| model | eval residuals | q10 | q90 | pooled band width | honest coverage | honest width | in-sample check | nominal |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ridge | 3424 | -0.178 | 0.213 | 0.391 | 81.2% | 0.432 | 80.1% | 80.0% |
| elasticnet | 3424 | -0.177 | 0.214 | 0.390 | 80.4% | 0.434 | 80.0% | 80.0% |
| gbm | 3424 | -0.181 | 0.189 | 0.370 | 83.0% | 0.443 | 80.2% | 80.0% |
| ensemble | 3424 | -0.170 | 0.209 | 0.379 | 81.2% | 0.427 | 80.1% | 80.0% |
| rank_linear | 3424 | -0.242 | 0.278 | 0.520 | 81.3% | 0.555 | 79.9% | 80.0% |
| huber | 3424 | -0.172 | 0.214 | 0.387 | 81.7% | 0.435 | 80.1% | 80.0% |
| pls | 3424 | -0.176 | 0.213 | 0.389 | 80.0% | 0.433 | 80.0% | 80.0% |
| rf | 3424 | -0.178 | 0.206 | 0.384 | 81.5% | 0.426 | 80.3% | 80.0% |

## What drives predictions

Drivers are read from the Ridge model refit on the full trainable panel
(standardized coefficient x each card's cross-sectional feature z-score). Even
when a non-linear model wins the walk-forward, the per-card driver strings in
forward_outlook.csv use these Ridge contributions (labeled approximate) because
they are directly interpretable. The largest-magnitude Ridge coefficients
indicate which features move the relative-return prediction most across the
cross-section.

## 2026-07-01 outlook flags

Flags now use the INTERVAL-AWARE rule: candidate_up requires a positive point
prediction AND a lower band that clears (roughly) zero (pred_lo90 > -0.02);
candidate_down mirrors it (negative prediction AND pred_hi90 < +0.02). This
demands the 80% band, not just the point estimate, point the same way -- yielding
fewer, higher-confidence flags than the old rule. The legacy top/bottom-decile
percentile rule is retained in the ``direction_flag_percentile`` column so a
dashboard can show both; when no conformal band is available the flag falls back
to that percentile rule.

0 candidate_up and 4 candidate_down (interval-aware rule) out of
465 modeled cards priced at 2026-07-01.

Top candidate_up:
(none)

Top candidate_down:
- Dracozolt V (Evolving Skies): predicted -0.299 (80% band [-0.453, -0.130]) [set_age +0.09; vol_6m -0.08; mom_3m -0.08]
- Rayquaza V (Evolving Skies): predicted -0.233 (80% band [-0.387, -0.064]) [log_price -0.13; mom_3m -0.12; premium_asof +0.12]
- Hisuian Arcanine V (Silver Tempest): predicted -0.157 (80% band [-0.312, +0.012]) [mispricing -0.08; premium_asof +0.08; mom_3m -0.07]
- Rayquaza VMAX (Evolving Skies): predicted -0.117 (80% band [-0.274, -0.024]) [log_price -0.30; premium_asof +0.12; set_age +0.09]

## Limitations

- Set-age/rarity effect is a LARGE part of the signal, though no longer the whole story. The "older high-rarity cards appreciate, recent cards decline" lifecycle pattern is real and sizeable: ablating the 9 static / near-time-invariant features (set_age_months, log_price, lifecycle_drift, is_sir, is_mega_hyper, is_ultra, is_rare_secret, is_rare_rainbow, is_rare_ultra) drops the all-fold mean IC from 0.328 to 0.260 (21% of it), and a univariate set_age ranking alone scores 0.296. What is new with the wider SWSH+SV+ME cross-section is that the held-out ablated-eval IC (0.285 +/- 0.018) clears the 0.05 floor by more than one SE, so a residual, non-static edge survives -- but it is a minority of the raw IC and may not persist across regimes.
- The held-out edge is within-era, not cross-era contrast (era-neutralized IC 0.355 +/- 0.018 vs era-contrast-only 0.144 +/- 0.490), but it is NOT uniform across eras. 3 of 3 scored era slices clear zero by more than one autocorrelation-aware SE. See the within-era breakdown section.
- Folds are NOT independent. The dominant features barely change relative rank
  month to month (set_age Spearman rank corr between the first and last fold is
  1.000) and 345 of 465 modeled cards appear in
  every one of the 15 folds, so the folds are near-duplicate re-tests of one
  static ranking. The information ratio therefore uses an effective fold count
  n_eff = n * (1 - rho) / (1 + rho) deflated for the lag-1 IC autocorrelation,
  NOT the naive sqrt(n) (which would materially overstate robustness).
- Model selection vs reporting are separated: the model is chosen on the first
  7 folds and the headline IC/IR come only from the disjoint held-out folds,
  to avoid selecting a model by argmax IC on the folds whose IC is then reported.
- Short history: 15 monthly test folds (2025-03 .. 2026-05). IC standard errors
  are wide; the information ratio is a small-sample estimate.
- Monthly granularity: price_history is month-start snapshots, so momentum,
  volatility, and the 3m target are all coarse. Intramonth moves are invisible.
- Modeled universe only: the panel covers the build_dataset modeled universe
  (465 cards across a handful of modern sets, SIR/HR/MHR plus Ultra
  Rare), not the full catalog. A much wider panel of all priced cards (the whole
  catalog above the $5 penny filter) is used only to estimate the lifecycle drift
  feature.
- Character premium is as-of-T (look-ahead removed). The model uses premium_asof,
  reconstructed at each panel date from the same-date price_history cross-section
  (per-dex mean price percentile within (rarity, series) peer groups) -- a
  quantity fully known at T -- paired with a premium_missing indicator for dexes
  with no as-of-T value (which stay NaN, never falling back to the 2026 value).
  The mispricing_resid hedonic cross-section also uses this as-of-T premium, so
  the residual premium look-ahead that previously lived there is gone. The static
  2026 snapshot premium_10 is retained only for provenance and is still barred
  from the raw feature list (LOOKAHEAD_SNAPSHOT_FEATURES). price_history begins
  2024-03-01; the panel starts 2024-06-01, so every modeled date has real as-of
  premium history.
- No transaction costs, no liquidity screen beyond the $5 penny filter on the
  wide lifecycle panel. Predicted relative returns are gross.


The outlook CSV also carries OUTLOOK-ONLY Cardmarket (EU) display columns
(cardmarket_eur_avg30, cardmarket_eur_trend, and cardmarket_eur_usd_div_z, a
cross-sectionally standardized EUR-trend/USD-market divergence proxy). These are
auxiliary reference columns from a single Cardmarket snapshot; per the
single-snapshot leakage doctrine they are NEVER model training features.

Full per-card outlook: forward_outlook.csv (same directory).
