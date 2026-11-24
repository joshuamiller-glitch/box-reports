# CARRYOVER_SE_STATUS (read-only status, 2026-11-24 04:40Z, W-STATUS; nothing queued, nothing changed)

Counts come from pending_sr_fit.txt and the other pending files (deduped set/month), the DONE markers in _th_sz/ijk/exact/runs_rf, and the leases in _s2/leases. BF1/BF4 rows were parked at 17:36Z Nov 23 (2 lots only), so only BF2 rows count below.

## Rows (BF2 = the 2-lot rows that still matter)
| family | landed (DONE) | running (lease, not DONE) | unstarted (queued) | note |
|---|---|---|---|---|
| XS (bare base carry) | 233 | 58 | 94 | 5 BF1/BF4 rows also landed earlier |
| XF (delivered-pick base carry) | 33 | 115 | 47 | |
| XD (sub-sets of XS/XF, the daily-loss thresholds) | inside XS/XF above | | | pending_sr_fit.txt: 330 lines total, all XS/XF |
| SE (session-end, run-vs-flatten) | 299 BF2 + 7 BF1 | 0 | 0 | all 59 sets DONE except 5 short identity/firing sets (1-5 months by design) |
| SK (SE skid variant, tagged _SK_ inside SE sets) | included in SE (26 sets, 13 settings x 2 sessions) | 0 | 0 | no queued rows |
Unstarted XS+XF = 141. Running = 173 leases. SE is fully landed.

## Queue position and rank (code/lead_watchdog/meter_shares.py _rank)
- XS/XF XD carry-over sets: rank 4.5 (+0.001 per pair, ASNY, ASLO, LONY, NYNP, ANY); XA/XB/XC reference rows: 4.55. Level with the DL/SE/TW/NW screens, behind rank 0 (Asia re-run, Asia daily-loss screen, NP joint JT1-80 at 0.001, STC-free NP JT2xx at 0.002), behind ordered NY AM / London / NY PM fits (1/2/3).
- They ride the 'stack' head (declared share 0.15, fall-through to idle capacity, 0.35-0.50 while many rows queue). Asia-first plan (DIRECTIVE_ONE_SESSION_ASIA_FIRST_20261123_2135Z) keeps them behind Asia.
- Leases for XS/XF were written 03:xxZ-04:xxZ today (381 in 2 h), so they are being fed now as fall-through.

## ETA
At ~4k rows/h: 141 unstarted + 173 running = ~314 rows is ~0.1 h of the whole fleet rate, so the exact rows should land within about 1-2 h of 04:40Z if the head keeps feeding them (assumption: nothing at rank <4.5 re-fills the stack head; the other stack files were not measured). The exact score page XSESS_EXACT.md then needs one scoring run (code/th_xsess/xs_score.py); not yet triggered and I did not run it. Prior years and the best-of-many null are NOT part of that screen by its own header, and no job for them is queued.

## Results so far
### Carry-over (XS / XF)
- Exact: no scored result yet. autopilot/XSESS_EXACT.md (last written 2026-11-23 09:39Z) reads for each of three sets: "base L6M months not all DONE yet"; it predates the 2-lot switch and the XF sets. Why: sets not all DONE and the scorer was last run before they landed.
- Identity (rules off, 2026-10), W-XSESS 17:44Z: merged 15-book 2-lot sets reproduce the separate sets trade for trade (bare 947 vs 947, net 235905.08 both; fitted 968 vs 968, net 130102.74 both).
- PROXY only (closed-P&L path, truly bare; autopilot/XSESS_CARRY_PROXY.md, 2026-11-23 17:24Z), quoted exactly from its "Best return-per-ulcer (fired >= 3 days)" section:
  - "1 lot AS+NY+LO AS>LO+NY_skip_6000: x1.29, ulcer -21%, $/wk +2%, fired 5 days"
  - "2 lot AS+NY AS>NY_skip_6000: x1.21, ulcer -16%, $/wk +1%, fired 3 days"
  - 1 lot AS+NY row "AS>NY_skip_4000 | 10 | -13% | -19% | -4% | x1.11 | -20% / -2% | -9% / -6% / +1%" (days fired, L6M ulcer, max DD, $/wk, return-per-ulcer, L3M ulcer / $/wk, prior years 23/24/25 $/wk).
  - "AS>NY_skip_6000 | 3 | -18% | -19% | +1% | x1.24 | -24% / +1% | +0% / -1% / +4%" (L3M ulcer -24%, $/wk +1%; prior years +0% / -1% / +4%). Only 3 days fired: thin.
  - AS>LO and LO>NY, NY>NP show 0 days fired at 1 lot (no effect); at 4 lots AS>LO fires 22 days at -3% ulcer, -1% $/wk.
  - Read: the skip lowers ulcer in L6M and L3M, costs a little $/wk, prior years mostly negative to flat at low thresholds. A proxy; no luck test (date-shift null) exists for it.
- Luck test: none yet for carry-over.

### Session end (SE)
- Exact rows: landed (all BF2 SE and SK sets, Asia pick TL3_SR_AS_STKd8106b26ef_BF2_JT19 and NY AM pick TL3_SR_NY_STKd8b76ecd35_BF2_JT68, 13 settings x 6 months each). Identity passed 2026-10: Asia 396 vs 396 trades, net 53434.58 both (202608: 296 vs 296, 34625.18); NY AM 302 vs 302, net 24620.36 (202608: 204 vs 204, 21374.78).
- Scored verdict: no scored result yet. No SE result page exists in autopilot/ (only the order DIRECTIVE_SESSION_END_20261123_0645Z.md); code/th_sessend/se_cmp.py exists but no output of it was found. Why: the rows landed but the compare/score step, prior years, walk-forward and null were not run (the order ranks it fall-through behind fits, Asia first). Not verified: whether a scorer cron is set to run it.

## Could not verify
- Whether anything at rank <4.5 will refill the stack head before XS/XF finish (ETA above is the optimistic path).
- Whether leases counted as running are all live processes (ps shows 1 process line naming TL3_SR_XS/XF; the workers may be named differently).
- SE scorer schedule.
