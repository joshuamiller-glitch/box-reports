# DS3 T-STACK FINAL (F verdict + G specs) - D3SKF

## Section verdicts
| section | best rule | verdict | failed gates |
|---|---|---|---|
| A slots | A03 (block WT 05:00/22:00), A06 (halve per-book loose slots) | DEAD (A03 G3,G4,G6; A06 G2,G3,G4,G5,G6) | see DS3_STACK_A.md |
| B range days | B02 (ON_085 halve trend books) | DEAD | G2,G3,G4,G5,G6,G8 |
| C chop weeks | B1_CONS2 | DEAD | G1,G3,G5,G6,G7 |
| D concurrency | D_L40s | DEAD | G2,G3,G4,G6 |
| E timeframe | HM5 (5-min HM) | LEAD (numbers need rerun, see below) | G3,G4,G6 |
| **F combine** | **A06 + HM5 REPL + B02** | **CANDIDATE** | **F6 (HOLD CI), F7 (best-of-F 1.000), F8 (no admitted rule passed its section)** |

**F verdict line:** the stack with the rule set vs the stack as it is (label weeks to 2026-02-06, 10-lot dollars): WF mean 52,914 vs 46,785/wk (d +6,129, MDE 20,857, CI -8,620..+20,258); WF SD 111,683 vs 138,333; WF maxDD 512,198 vs 578,442; worst week -325,947 vs -318,557 (slightly worse); HOLD mean 43,406 vs 53,670 (d -10,264, MDE 34,726); 2023 span 6,337 vs 15,127 (d -8,790, MDE 23,298); years d_mean 2023 -8,790 / 2024 +12,610 / 2025 -3,424 / 2026 (6 wk) +6,865. **These rules would have turned the worst 20 weeks from -$3,534,170 to -$2,502,987 and cost $6,629/wk in the other 129 weeks.** No mean claim is supported; the benefit is tail only and is partly a lot cut. Full tables: DS3_STACK_F.md. Not live-ready: nothing goes live from this file; a CANDIDATE needs forward evidence or a lot-matched engine re-run first.

Section E caveat: DS3_STACK_E.md REPL/MIX/ADD/LM numbers for every cell but KB5 were computed with a mutating WDAY (stack_parts bug); fixed HM5 PRE REPL is +2,315/wk (E: +1,138) and MIX +1,157 (E: -553). E verdicts are unchanged on disk and flagged for a rerun with code/stk_f/f_fix_stke.py.

## G specs (rules admitted at the F look). All tested on the DS3 stack trade table only (books ST, HM, WT, KB, PE, SM; ET clock; label day = 18:00 ET to 17:00 ET). DualStrat2 and DS5 were NOT tested: treat the rules as not applicable there until re-scored on those books.

### G1 - A06 "halve per-book loose slots" (sizing layer; CANDIDATE only inside the F set)
Rule: for each book, when a new entry's ET half-hour entry slot (slot start = floor of entry time to 30 min) is in that book's list below, enter with 0.5 x the normal lots (the study scaled P&L linearly; lot rounding is not specified by the study). All other entries unchanged; exits, locks, TH cuts unchanged. Lists derived on PRE (2024-02..2025-06) only: ST 03:30, 04:30, 05:00, 11:30, 12:30, 14:00, 14:30, 19:00; HM 04:00, 05:30, 08:30, 10:30, 12:30, 13:00, 14:00, 18:30; KB 03:30, 04:00, 04:30, 05:00, 05:30, 14:30, 19:00, 19:30, 20:30, 21:00; PE 03:30, 05:00, 08:30; SM 02:00, 08:30; WT 01:00, 01:30, 03:30, 04:30, 05:00, 07:00, 08:00, 10:30, 12:30, 13:00, 13:30, 14:30, 19:30, 21:00, 22:00, 23:00, 23:30 (list source out/stk_a/pre_slots.json, minutes after midnight ET: 210/270/300/690/750/840/870/1140 etc.). Affects about 24% of entries. DS3: tested. DualStrat2/DS5: not applicable (different books and slot profile). Evidence: standalone PRE +10,563/wk (MDE 12,104), HOLD -4,378 (MDE 15,304), X -9,764 (MDE 12,475); the PRE-negative slots do not stay negative in HOLD (section A binomial p 0.91). Weakest component of the set; treat as a lot reduction, not a signal.

### G2 - HM5 REPL "HM on 5-minute bars instead of 1-minute"
Rule: run the HM book's signal on 5-minute bars (bucket = epoch minute // 5; signal available at the close of the 5-min bucket; enter at the open of the next 1-min bar). Indicator parameters keep their BAR COUNTS from the live 1-min version: HMA(20) and HMA(55) of (close - session VWAP) (cross with slope confirmation: HMA55 slope sign agrees), EMA(200) trend filter on the 5-min close. Same live entry blocks, signals 16:55-18:00 ET blocked, same busy chain, lots, locks and exits as live HM. It REPLACES the 1-min HM (do not run both). DS3 only; DualStrat2 and DS5 do not run HM (not applicable). Evidence: trade-level swap PRE +2,681/wk (MDE 19,962), HOLD -4,456 (MDE 25,181), X -3,858 (MDE 18,099); engine-level fixed PRE +2,315; direct replay on raw mbp-10, 37 months.

### G3 - B02 "ON_085 halve trend books after 10:30"
Rule: at 10:30 ET each label day, compute overnight range = high - low of the 18:00 ET (prior evening) to 09:29 ET session. Compare with the median overnight range of the prior 20 label days. If range < 0.85 x median, then for entries between 10:30 and 18:00 ET (inclusive of 10:30, exclusive of 18:00) on ST, HM, WT, KB, PE use 0.5 x lots (halve; study scaled linearly, rounding unspecified). SM unchanged. Trades opened before 10:30 and exits unchanged. If HM5 REPL is also on, the halving applies to the 5-min HM entries. DS3 only. Evidence: standalone PRE +514 (MDE 5,947), HOLD +955 (MDE 8,813), X +3,377 (MDE 7,873); section B DEAD (G2,G3,G4,G5,G6,G8); control 1.5x on the same days has the opposite sign in all windows. Adds +46,945 HOLD worst-quintile $ to the F stack and costs 1,430/wk HOLD mean (MDE 6,409).

### Not admitted / do not implement
D_L40s (cap 40 weighted lots per direction, first-in; rejected at the F look: HOLD W20F falls 16,795), B1_CONS2 (PRE mean -6,811; not stacked), A03, HM5 MIX (+1,340 PRE trade-level; lost to REPL on PRE). Section DEAD cells (A-D) are not specs.

### Order of application if ever coded
(1) A06 slot halving and B02 halving multiply (a trade in both gets 0.25 x; this combination was evaluated additively, not as a product, so the product case is APPROXIMATE). (2) HM5 replaces HM signals. Honest status: CANDIDATE, forward-watch only.
