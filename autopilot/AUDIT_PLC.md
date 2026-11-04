# AUDIT-PLC: time-shifted trigger placebos that keep the signal's side (BASE-4, 2026-11-04 ~23:50Z; $0; read-only on others' outputs; no PASS claims)

## The flaw
A placebo that moves every signal by a random +-minutes and KEEPS THE SIDE places entries BEFORE the real signal with a side that the later price path produced (look-ahead). Direction of the error: for continuation / momentum sides the placebo is inflated (it knows where price went), so the real cell looks worse than it is (CONSERVATIVE leak, false nulls); for fade / counter-move sides an earlier entry runs against the path that created the signal, so the placebo is deflated and the real cell is FLATTERED. Causal reference = delay-only (entry never earlier than the real signal), which is what the shared harness `shift5` placebo already does (`make_placebo(kind, rng, forward_only=True)`, delay 5..120 min in 5-min steps inside the same session and label day; same in the pre-gate_v3 harness).

## Reruns (delay-only, 5..120 min, no random sign; 100 draws each; new seeds; ZL-2's code copied with ONE line changed; originals untouched)
Scripts and outputs: scratchpad q9_stage2_fwd.py, q9_stage2b_fwd.py, q10_stage2_fwd.py, q12_plc_fwd.py (pickles *_fwd.pkl). Q12's original shift is +-30..300 SECONDS (dshift is in seconds), rerun as +30..300 s. 100 draws means p floors at 0.01 and sampling noise of about +-0.05 near p 0.1; only moves across .10 are treated as informative.

### Q9 (12 entry cells top-t + 6 overlay cells), p of the shifted-trigger placebo (L6M mean / HOLD stack gain), old -> delay-only
| cell | old | delay-only |
|--|--|--|
| LNR L_rev&A_wide S1 (the one tolerant cell) | .01 / .10 | .01 / .14 |
| LR A_won S2 | .01 / .24 | .01 / .52 |
| LR A_wide&A_ER_high S2 | .05 / .29 | .05 / .50 |
| LR A_wide S2 | .01 / .26 | .01 / .35 |
| LNR A_ER_high S1 | .01 / .15 | .01 / .39 |
| LNR L_rev S1 | .02 / .29 | .02 / .59 |
| LR A_ER_high S2 | .04 / .36 | .06 / .53 |
| LF A_wide&A_ER_high S2 | .02 / .49 | .04 / .64 |
| LF A_won S2 | .01 / .13 | .01 / .26 |
| LF A_ER_high S2 | .03 / .44 | .04 / .78 |
| NC L_narrow S2 | .10 / .01 | .12 / .03 |
| LNC L_lost S2 | .36 / .13 | .15 / .04 |
| ovl LONDON x0 A_wide&A_ER_low (the story cell) | .28 / .01 | .50 / .01 |
| ovl LONDON x0 A_ER_low | .63 / .07 | 1.00 / .01 |
| ovl LONDON x0 ALL | .58 / .38 | 1.00 / .60 |
| ovl LONDON x0.5 A_ER_low | .65 / .10 | 1.00 / .01 |
Reading: the reversion rules (LR, LNR, LF, 'rev' = fades) had a deflated placebo (FLATTERING leak): stack-gain p rises from .10-.49 to .14-.78, i.e. the real cells look slightly LESS special. The continuation rules (LNC, NC) had the opposite (conservative) leak: LNC L_lost stack p .13 -> .04, L6M .36 -> .15 (that cell has a negative L6M mean and family p >= .64, so no label). Label before / after: unchanged (REGIME / noise-level for the London x0 story cell; family p 0.64-1.00 for every cell; nothing flagged).

### Q10 (12 cells), shifted-trigger p (L6M mean / HOLD stack gain), old -> delay-only
OMF10 F16 S2 .01/.01 -> .02/.01; OMF05 F16 S2 .04/.01 -> .15/.01; OMF10 F16 S1 .01/.05 -> .06/.10; OMF05 F16 S1 .01/.07 -> .09/.04; OMF10 NONE S1 .05/.01 -> .15/.01; OMF10 NONE S2 .05/.26 -> .11/.12; GO MEGA5 ALL S2 .01/.06 -> .02/.04; GO MEGA5 LARGE S2 .07/.01 -> .03/.01; FILL NONE LARGE S2 .02/.01 -> .05/.02; FILL NONE ALL S2 .02/.07 -> .03/.08; FILL NONE LARGE S1 .02/.05 -> .01/.05; GO15 MEGA5 S2 .41/.67 -> .22/.69.
Reading: the opening-move fade (OMF, fade side) placebo was FLATTERING the real cells (L6M p up to .15 forward-only); the gap-go / gap-fill rules are fixed-time entries and barely move. Label before / after: unchanged ('nothing flagged'; family p >= 0.96, BH q >= 0.9). The sentence 'placebos on the stack gain 0.01 / 0.01 / 0.01' for OMF10 F16 S2 survives (.01 delay-only); its L6M-delta shifted-trigger p moves 0.01 -> 0.02.

### Q12 (12 cells; shift +-30..300 s), shifted-trigger p (L6M mean / HOLD stack gain), old -> delay-only
PB tick 1000 london .45/.40 -> .81/.61; KB volume 500 asia .58/.53 -> .09/.05; SM Renko 40 asia .64/.73 -> .31/.51; SM tick 1000 asia .44/.41 -> .02/.01; KB UniRenko 40/60 asia .56/.89 -> .01/.59; KB Renko 48 nypm .68/.59 -> .19/.22; KB Renko 40 asia .86/.82 -> .73/.56; PB tick 500 london .08/.38 -> .18/.60; PB tick 2000 london .16/.36 -> .28/.57; KB Renko 80 asia .91/.60 -> .76/.28; PB tick 1000 pre .29/.19 -> .45/.45; SM Renko 80 pre .52/.99 -> .08/.87.
Reading: bar-follower engines are continuation signals, so the old placebo was inflated (CONSERVATIVE leak): three Asia cells (SM tick 1000, KB UniRenko, KB volume 500) now beat the trigger placebo at p <= .10. Label before / after: unchanged ('nothing flagged'): the same cells fail the shifted-bar-start placebo (p .50 / .36 / .01-.38 stack) or the family test (max t 2.80 vs null 95th pct 3.77, family p >= 0.21, BH q 1.00), which do not use a time-shifted side. The sentence 'no cell has the three placebos below 0.10 on the stack gain' still holds (KB volume 500 Asia: start .14, side .04, trigger .05 -> not all three; SM tick 1000 asia: start .36).

## Inventory (one row per program)
| program | code path | time-shift placebo keeping side? | leaky | direction | label before -> after | action |
|--|--|--|--|--|--|--|
| Q9 session chain (ZL-2) | zones3/discover/q9_zl2_stage2.py, q9_stage2b (`shifted_series`, sh = +-15..120 min) | yes, random sign | Y | mixed: FLATTERING for reversion rules (LR, LNR, LF, 'rev' overlays), CONSERVATIVE for continuation (LNC, NC) | REGIME / noise -> REGIME / noise (family p .64-1.00) | correction line appended; delay-only table above |
| Q10 earnings (ZL-2) | q10_zl2_stage2.py (`shifted_ser`, +-15..120 min) | yes, random sign | Y | FLATTERING for opening-move fade (OMF), small for fixed-time gap go/fill | nothing flagged -> nothing flagged | correction line appended |
| Q12 bar types (ZL-2) | q12_zl2_plc.py via `trades_for(dshift=)` (+-30..300 SECONDS) | yes, random sign | Y | CONSERVATIVE (continuation engines) | nothing flagged -> nothing flagged | correction line appended; 3 Asia cells now beat trigger placebo but fail start/family |
| Q11 daily-trend pullbacks (BASE-4) | code/q11 (+-5..120 min) | yes | Y | CONSERVATIVE (pullback continuation) | statement 'random-time entries beat the live trigger' WITHDRAWN (2026-11-04 Q11 CORRECTION); 0 of 44 beat shifted trigger -> not interpretable, p's withdrawn | already corrected (DS3_DISCOVER.md Q11 CORRECTION) |
| DIS-M drift benchmark P1 (BASE-4) | code/dism (anywhere in session) | yes | Y | CONSERVATIVE for the excess test; superseded by causal P1c | EXCESS survives only NYAM ORBF (family .08/.02, q .06/.05) and VB2 NYPM T1 (.05/.03) | already corrected (addendum 1, P1c) |
| Q7 passive entries (Z2) | q7/q7_p2.py, q7_run.py: 'timing' = delay rng.integers(5,61) (forward only: OK); 'level' placebo takes reference price from t +-300 s (`SC[idx_at(sec+rng.integers(-300,301))]`, up to 5 min of FUTURE price) | timing no; level price-only, no side | timing N; level possible | level: ambiguous (a limit offset from a price that is later reached fills more often) | null -> null (not rerun: Q7 reports nothing changes / no positive cell) | note only; recommend forward-only draw (-300..0) if Q7 is ever cited |
| Q13 gap books (ZL-1) | q13/q13_lead.py, q13_final.py: harness `placebos=100` (shift5 forward) + shifted gap LABELS on random days (rule applied to that day's own real gap) | no | N | - | unchanged (LEAD-thin / tolerant) | none |
| Q14 NQ-ES spread (fork) | q14/q14_run.py: `add = 300*rng.integers(1,13)` seconds (+5..60 min, forward only), side, days | forward only | N | - | unchanged | none |
| Q6 pyramiding | q6/q6_rep.py: placebos on incremental values (random-side / day shuffle), no entry-time shift | no | N | - | unchanged | none |
| Q8 day-type | zones3/discover/q8_zl2_stage2.py: shifts day-type PREDICTIONS by whole days | no (no intraday look-ahead) | N | - | unchanged | none |
| Q5 hold shapes | harness `evaluate` placebos (shift5 forward) | no | N | - | unchanged | none |
| DIS-H | dish/dish_run.py `make_placebo(t,'shift5',rng)` forward | no | N | - | unchanged | none |
| DIS-K | disk/dk_run.py, dk_stage2.py: state-date rolls +-20 days; harness shift5 forward (the 'shifted trigger .02-.08' in the ranked list is shift5) | no | N | - | best-of-F -> best-of-F | none |
| DIS-Q | discover/disq.py: P1 'shifted clock bucket' REBUILDS the book at offsets -90..+60 min with the trigger recomputed causally; plus harness shift5 / side | no (rebuilt, not shifted) | N | - | unchanged | none |
| DIS-E | disc/dise_stage2.py, dise_final.py: harness shift5 + side | no | N | - | unchanged | none |
| DIS-B / DIS-C | disb/disb_s2.py, disb_fam.py; disc/dc_stage2.py: harness shift5 / side, weekend shuffle | no | N | - | unchanged | none |
| DIS-G / DIS-A / DIS-J / DIS-I | fade_mz/disg_*.py, famshift.py; dis_a/d2_run.py; dis_j (price-line shifts rebuilt causally); code/disi (calendar-date placebos) | no | N | - | unchanged | none |
| T-FADE line placebo | code/fade/fade_lineplacebo.py, fade_lv/fl_or15.py: LEVELS moved +-15..60 pt (or +-10..80), events regenerated with the causal trigger | no (price shift, not time) | N | - | unchanged | none |
| T-INSTR / S-DISC 6 | DS3_SDISC_6.md post-prereg placebo: trigger minutes moved +-1..30 CALENDAR days, same minute of day | no | N | - | unchanged | none |
| L2 UNTIL_FOUND / INFO_C2 | 'within-trade shifted-trigger null' and 'shuffled trigger' (DS3_L2_*): read from the page text only, trigger moved inside the same trade whose side is fixed at entry | not verified in code | N? | - | unchanged | owner should confirm; not in this audit's scope |
| T-SIZER | SIZER pages cite no time-shift placebo; 'shifted-entry rows' in the L2SL hook (DS3_SIZER.md addendum 3) are the re-evaluated shifted-entry ROWS of an exit hook, not a placebo | no | N | - | unchanged | none |

## Fixed shared code
`FadeHarness.make_placebo` / `placebos()` shift5: forward only in current and pre-gate_v3 versions (verified by reading both). No harness change needed. Recommendation: any program that wants a time-shift placebo should call `make_placebo(t,'shift5',rng)` (forward-only, label-day safe) instead of a signed shift.

## Programs with a CHANGED label
None. Changed p-values (all logged above): Q9 reversion cells (stack-gain p up, real cells look less special), Q10 OMF cells (L6M p up to .15), Q12 three Asia cells (trigger p down to <= .05; still fail start / family).

| Part 2 (AUDIT-L2, 2026-11-04T21:32Z) | L2 UNTIL_FOUND P3 within-trade shift | circular trigger shift (uf_p3_shift_lib.cshift) | Y | FLATTERING | rank 0.95 -> 0.49 (C4 B1trail); labels BEST-AVAILABLE-NEGATIVE unchanged | correction appended |
