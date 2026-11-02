# DS3_ZONES_3_B73_GENERIC - is B73 (70% now, 30% after trade-through) a robust entry mode independent of zones? (ZL-3, V13X, 2026-11-02)
Research only, post-hoc, no PASS claim. Code l2vast/ds3/code/zl3/ (zl3lib.py: ZL_B73FIX, set_b73_delay; cells.py kind GB). Data /mnt/l2/l2vast/ds3_zones3_new/ZL-3/res_jobs_gb*_FIXall_0.pkl.

## 0. HEADLINE: a base defect, then no robust edge
**D7's B73 composition drops the TH-L2 loss cut (and take-line exits) whenever the cut second is before the second the resting 30% would fill** (`d7lib._compose_d7`: cand = kx > o[:,10]). The trade then runs on un-cut, the add fills after the cut time and the trade is credited with the later outcome. Example row 13940 (HM): the cut exits at -28 pts; the B73 version shows +51.7 pts (target). Correct treatment: an exit that precedes the add's fill cancels the add (70% leg only, cut applies to it). Fix implemented in my layer (`ZL_B73FIX`): add left unfilled when an injected exit precedes its fill.
* Generic B73 at d = 30 on every row, UNFIXED: total $7.06M vs base $2.23M (+216%, L6M cut +90..+100%): all artefact. FIXED: $1.86M (-17% vs the shipped split).
* **Impact on the SHIPPED base (OTE-62 B73 at D30, 145 rows affected):** lock=None total $2.234M -> $2.070M; L6M mean 26.9k -> 25.2k/wk; L6M maxDD 132.6k -> 136.8k; HOLD 132.6k -> 141.4k; PRE 178.4k -> 199.7k (cut -11.9%). Lock=12R: total $1.404M -> $1.231M; L6M mean 22.4k -> 18.3k/wk; L6M maxDD 73.9k -> 94.7k (-28%); PRE 252k -> 265k; MID/X' ~unchanged. So part of the shipped base's L6M performance (and the base lines everybody compares against) comes from this. Flagged to the lead; BASE-4 / d7lib owner to confirm and patch.
* The earlier FVG-zone B73 "leads" (section 19) and my G-series B73 cells were this artefact: re-run with the fix and against the FIXED base, FVG B73 gives lock=None L6M/HOLD/PRE/X' -2..+3 / +2..+7 / -12..+12 / -3..+1% with mean change -0.9k..+0.1k/wk (MDE 2.2-3.1k): nothing; lock=12 +2..+31% L6M but means 0 and not repeated in lock=None: LOCK-ONLY/noise.

## 1. Generic B73 on every row, FIXED (reference = the fixed base; windows L3M L6M HOLD MID PRE X'; lock=None first)
fill rule: the 30% is entered at the second after price trades 1 tick through the level d pts ahead (price of that second +1 tick), only if the stop has not been hit first, only if no injected exit (TH-L2 cut, take line) precedes it, and only before the signal's arm limit; **if it never fills the position stays at 70% for the whole trade (no later fill, no refund)**. The shipped dip leg (30% limit 3 pts better) is replaced by the B73 add. d >= target distance (60): the add can never fill (identical to d = 999).
| d (pts) | lock=None maxDD cut L3M / L6M / HOLD / MID / PRE / X' (%) | mean change L6M (MDE) $/wk | lock=12 cut L3M / L6M / HOLD / MID / PRE / X' |
|---|---|---|---|
| 10 | +7 / +16 / +19 / +49 / +24 / +46 | -3,386 (11,046) | +39 / +4 / +6 / +15 / -33 / -12 |
| 20 | +15 / +41 / +40 / +44 / +15 / +32 | -5,277 (13,361) | -24 / -1 / +3 / +7 / -53 / -11 |
| 30 | +26 / +46 / +36 / +50 / +4 / +35 | -6,716 (13,584) | -55 / -6 / +12 / +26 / -54 / -124 |
| 40 | +25 / +34 / +36 / +52 / +6 / +40 | -10,376 (14,200) | -8 / +22 / +37 / +41 / -89 / -3 |
| 50 | +37 / +33 / +35 / +52 / +11 / +47 | -10,676 (14,859) | +22 / +30 / +44 / +32 / -88 / +14 |
| 60 (= never fills) | +33 / +57 / +52 / +65 / +38 / +55 | -6,106 (13,653) | +17 / +41 / +51 / +26 / -8 / +20 |
| 25 / 50 / 75 % of target | = 15 pts / 30 pts / 45 pts | | |
| market entry, no split (nosplit) | +7 / +6 / +9 / +37 / +36 / +42 | +1,415 (10,908) | -10 / +8 / -7 / +12 / -2 / +16 |
WT (wait for trade-through, whole lot): lock=None L6M cut -315..-392% (d 20-40; worse), +100% at d = 60 (no fill = no trade). Not an option.
**Reading.** The lock=None cut grows to +33..+57% with the mean falling -3k..-10k/wk (all inside MDE 11-15k): the position is smaller (70%) whenever the add does not fill. That is a SIZE reduction, not an edge: the 'never fills' cell (d = 60) is the largest cut. Equal-risk (lots scaled until the worst-20 sum of ALL equals the base): lock=None d = 60 / 999: +43% L6M cut with mean +5.2k/wk (but lscale 1.55 moves integer min-1 lot rounding; treat with caution), d = 30: +41% and +0.2k; lock=12: d = 60 +47% with mean -3.1k, d = 30 +9% with -9.1k: **sign-unstable across frames, so no robust improvement.**

## 2. Placebos (fixed engine; descriptive, no rank <= 0.05 claim)
Same mechanics on a random share of rows (10 / 25 / 50 %; 3 seeds) at d = 30 / 60, lock=None: L6M cut -17..+40%, mean -7k..+0.7k (shares 10-25%: cut -27..+25%, inside the 0.31 noise band of Z3's table); distances SHUFFLED across rows (random draw from 20/30/40/60 per row, 3 seeds): cut +29..+35% L6M, +7..+21% PRE, mean -6.4k..-9.8k - the same as the fixed-d cell (d = 30: +46 / +4). So the distance carries no information; the cut is the volume of the missing 30%. Latency (1 s / 3 s delay on the resting 30% fill): identical to 0 s within a point or two (d = 30 lock=None L6M +50 / +47 vs +46; d = 60 no fills).

## 3. Versus the shipped entry split and OTE-62's own B73
The shipped split is the reference (base). 'nosplit' (100% market entry) is +6% L6M cut and +1.4k/wk in lock=None: the 70/30 split piece the SUM agent saw turning negative on the new L3M is roughly neutral on the L6M drawdown here. OTE-62's own B73 at D30 (145 rows with the defect) is slightly NEGATIVE once fixed (section 0): the piece should be re-judged on the fixed engine.

## 4. Per book x session (d = 30, lock=None, FIXED; L6M cut / mean)
K7 -5 / -0.8k, P7 +34 / -4.1k, U7 +3, H7 +12, M7 -2, A7 +5; Asia +21 / -6.4k, London -3, NY-AM -4, NY-PM +4. P7 (PE) and Asia carry the cut as in every other test; with a mean cost. d = 60: P7 +31, Asia +39 (never-fill = P7's 70% lots).

## 5. Episodes / noise band
Not separately computed for the generic cells: with the fix the cut is the size reduction and the mean falls; the carrying-week analysis is moot. Z3's noise band (assumed base, 5% rows) is 0.31 on L6M: the full-row cells (+33..+57%) exceed it but touch 100% of rows, outside the table's size range; the 50% share placebo gives +19..+40% with the same mean cost.

## 6. Verdict
**B73 as a generic entry mode is not an improvement independent of zones. The apparent effect was the injection-ordering defect; fixed, it is a 30% size reduction on trades where the add does not fill (mean down, drawdown down, frame-dependent at equal risk).** No flag for the lead beyond the base defect in section 0 (which IS the finding: the shipped OTE-62 B73 and every B73/WT cell scored on the unfixed engine are overstated).
