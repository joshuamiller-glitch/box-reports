# PLAN_NP_LOG (W-PLAN-NP): per-book log of what was tried and why it failed. Research only; nothing live, nothing bought, nothing deleted.

## Scope facts found (2026-11-27 03:50-04:15Z)
- The 4 live NY PM books = MF1 L52359bf4.BRP30 (tm120 ATR-channel fade, 30/30), MF2 L8e0bf58c.BRS8U (anchored PDN + ZN breakout, 120/120), MF3 L4bdd521a.BRF80_40 (tm1800 + YM, 80 stop / 40 target), MF4 L2c6916a5.BRP60 (tm15 delta-divergence fade, 60/60); stack STKd893133bd8, pick JT241, same lots per book (2 at fit; file sizes 3/4/6) (D8_LAYER_KEYS_NYPM_4BOOK_JT241.md).
- NP-MACD and NP-CONF are NOT named anywhere in the box; the only text is the order. They are read as the two NY PM pool members that are coded (spec pages) but not in the live stack: NP-MACD = L6d238076.BRF90_30 (MACD 12/26/9 signal cross on vsess_50 bars, both sides, 90 stop / 30 target; D8_NYPM_SPEC_L6d238076.md), NP-CONF = L8dff280f.BRP90 (tm180 bars, 2-of-3 confluence squeeze fire / MACD cross / CCI zero cross, 90/90; D8_NYPM_SPEC_L8dff280f.md). READING, not confirmed: LEAD to confirm. Their event files (_brkt/ev) and bare engine sets (TL3_ALN_NP_L6d238076_R0BRF90_30, ..L8dff280f_R0BRP90) exist; exact in-mix rows (alone/mix variants TL3_DX_NP_*) do not exist yet for them.
- Live NY PM Trade Health: the 4-book JT241 pick has NO profit-side TH and no pulled-size TH: per-book layers CU (market cut on a closed second at k x stop), LK (lock at 80% of the TARGET, so inert without a fixed target), SHV (target shave); everything else is mix level (zones, BookLock, day limits, sizer). Reference row REFTH = fixed bracket + these per-book layers (quick-screen emulation, see fixed_rules_plan_np.json). Plans without a fixed target must use their own protective rules (handled: plans carry their own BE/trail, REFTH is only the yardstick).

## Round 1 (03:50-04:15Z wall) tried, count
- Tape-only attribution of leave-now signals: 6 books x 18 signals (17 + 1 control) = 108 tests, fit/hold split, matched null, day-block bootstrap, BH: 0 carry information (best raw: NP-MACD P_stall60 hold d=+0.036R p=0.002 but wrong sign on the fit half, BH q=0.16). So no tape-based "leave now" trigger enters any plan.
- Fixed-rule plans written before scoring (3): A bank-early, B half-runner, C three-targets: all worse than REF0/REFTH on income in 5 of 6 books and not shallower on drawdown except MF3-B and NPCONF-A.
- Structure grid 681 variants per book x 6 books x 2 fill labels = 8,172 simulated books: stop x0.5/0.75/1.0, single target 0.5-2T, trail-only, partial (0.33/0.5/0.67 at 0.5/0.75/1.0 T) + BE + runner trail (0.25/0.5/1.0 T) or second target (1.5/2/3 T), time stop 3600 s; WF re-pick 13/4/2 weeks; hold-out check; shared pick over the 4-book mix.
- Total variants counted this round: 108 + 3x6x(4 lots x 2) + 8,172 + 6 reference rows.

## Why each failed (what the trades do that the plan missed)
- MF1 (30/30 fade): winners are fast and tight; any partial before 30 pts or a stop at 0.5-0.75x loses more winners than it saves; fit-picks (s 0.75, t2 3T) hold-out income 6.4k vs 49.2k, DD deeper. The live layer LK8 helps the last 6 months (L6M 42.7k vs 38.2k, DD -3.6k vs -6.5k) but costs 30% income over all years.
- MF2 (120/120 breakout): large stop; a stop of 0.75x with BE and 3600 s time stop cuts drawdown a lot in the fit years (-8.0k vs -25.6k) and does not in hold (-38.5k vs -34.2k): 2025 is a bad year for every variant.
- MF3 (80/40): the one book where in-sample DD roughly halves with income kept (t2: partial 0.5T, rest 1.5T), but hold-out income is 21% of REF0 (the 2025/2026 trades want the 40 pt target taken whole).
- MF4 (60/60 delta fade): most fragile; every partial variant cuts income >60% in 2026, pessimistic fills turn the picks negative.
- NP-MACD (90/30): biggest structural lever (target 30 vs stop 90 leaves room: partial 0.5-0.75T and rest to 2T doubled fit income and halved DD) but hold-out income -34% and 2026 negative; WF step 4/2 gives DD 7 of 13 periods, income above REF0 in 5-6 of 13.
- NP-CONF (90/90): WF picks give shallower DD in 12 of 13 periods and equal worst week in 10 of 13, but income 31% lower (101k vs 148k); the STAGED t2 (a=1.0 f=0.33 b=2.0 be=1) is a hindsight row only: income 149.9k vs 148.2k, DD -13.9k vs -17.0k, L6M DD -7.2k vs -7.7k. This is the best candidate to carry into Round 2 (hindsight pick, must be re-tested forward).

## Next ideas (not yet run)
1. Book-state evidence needs MBO/10-level paths for NP entries: not extracted (x8/snap covers Asia + NY AM only). Count: 6 books ~ 21,000 entries; extractor ~8 s/day, 909 days = 2 h on one core per pass; needs approval of core use (box load 100 on 32 cores).
2. Import W-DYNC's X24 steering controller (not posted yet) to steer T2 (extend / pull in) and the runner trail on the structure that works in hindsight (t2 family): static row beside steered row.
3. Exact engine rows for the 3-4 surviving structures per book via dx_multi (stage port), after the quick-screen holds on a forward test.
