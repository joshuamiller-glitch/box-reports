# DS3_MAJOR_DELIVERABLES - best settings for the user to decide (W-DL assembler; rebuilt 2026-11-17 18:47Z, every 30 min)
VERDICT (data ends 2026-10-31; FIRST PASS; every row is a BEST SETTING with its honest label; rows labelled LEAD-ASSEMBLED are copied by the assembler from existing pages and wait for the owner to confirm)

> HEADER: trials counted = per row (see each row; ledger families CT1, RB3, RB5, ME, MF1/MF2); correction = per row (BH / White RC / controls where run, else 'not run'); in-sample vs walk-forward is stated per row (untouched-year line). Labels CONFIRMED / LEAD need engine-exact persistent-draw controls (calibrated pass rule); a missing field prints 'n/a (owner has not delivered)'. Seal untouched.

## Summary (plain)
1. Table 1: 30 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 6, BEST-AVAILABLE-NOT-PROVEN 24) + 0 reference rows
2. Table 5: 16 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 0, BEST-AVAILABLE-NOT-PROVEN 16) + 0 reference rows
3. Table 6: 14 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 9, BEST-AVAILABLE-NOT-PROVEN 5) + 0 reference rows
4. Table 2: 23 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 3, BEST-AVAILABLE-NOT-PROVEN 20) + 0 reference rows
5. Table 3: 36 main rows (CONFIRMED 1, LEAD 0, WEAK-BUT-POSITIVE 7, BEST-AVAILABLE-NOT-PROVEN 28) + 0 reference rows
6. Table 4: 13 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 7, BEST-AVAILABLE-NOT-PROVEN 6) + 0 reference rows
6. Decide first: Table 3 row 1 (M7 London 4 -> 0 lots, CONFIRMED, but HOLD mean -445 $/wk); then the P7 flat -42 question (L6M worse with it on); then whether to fund the engine runs for the unproven books. No file yet from: W-BAR.

How to read: ulcer % is positive when the cell is better than today (lower RMS daily drawdown); max DD and worst week are base -> cell in dollars (negative numbers, closer to zero is better); mean per week is shown at base lots, at x1.75 live lots and with $4.84 round-turn commission. Live lots = max(1, floor(1.75 x base + 0.5)). Weak spots are stated on each row; GAP / PRE percentiles are often weak.

## Table 1. BRACKET TABLE (stop / target / time-stop / half-off instead of 60/58)
Selection rule: trailing-6M pick, 2-week refit, prior years AMBER 15-30% / RED >30% (outputs/CLAUDE.md)
**U7 london**  `U7|london|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket U7 london stop=60 target=MIN(60, nearest UWO level ahead - 0) [DYNAMIC: prior-day level table]
- **L6M**: ulcer +5.0%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -445; x1.75 live lots -801; $4.84 -457
- **HOLD**: ulcer -8.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 463; x1.75 live lots 726; $4.84 415
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -9% / +5%, mean x1.75 -84 / -21 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: UW gex-levels/oi-per-strike daily table (Advanced tier) + roll guard
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 19, HOLD 12, L6M 11 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**P7 asia**  `P7|asia|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket P7 asia stop=60 target=MIN(60, nearest UWO level ahead - 0) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -6.6%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 15,763; x1.75 live lots 26,135; $4.84 14,934
- **HOLD**: ulcer -41.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 5,771; x1.75 live lots 19,024; $4.84 10,871
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -42% / -7%, mean x1.75 +8926 / -1450 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: UW gex-levels/oi-per-strike daily table (Advanced tier) + roll guard
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 56, HOLD 48, L6M 34 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**P7 london**  `P7|london|levelexit`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: 60/60 -> bracket P7 london stop=60 target=MIN(60, nearest R250 level ahead - 15) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -9.4%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 2,540; x1.75 live lots 5,340; $4.84 3,051
- **HOLD**: ulcer -47.2%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,266; x1.75 live lots 3,715; $4.84 2,123
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -47% / -9%, mean x1.75 +1500 / +895 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: own zones / round-number target (no feed)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 172, HOLD 55, L6M 99 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**H7 nyam**  `H7|nyam|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket H7 nyam stop=60 target=60 + DYNAMIC stop to -20 pts after rejection from a R100 level (within 5 pts then 10 pts pullback)
- **L6M**: ulcer -10.4%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 562; x1.75 live lots 777; $4.84 444
- **HOLD**: ulcer -26.5%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -18; x1.75 live lots -158; $4.84 -90
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -27% / -10%, mean x1.75 -125 / -207 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: own zones / round-number target (no feed)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 55, HOLD 7, L6M 12 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 london**  `K7|london|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket K7 london stop=60 target=MIN(60, nearest UWO level ahead - 0) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -10.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,105; x1.75 live lots -775; $4.84 -443
- **HOLD**: ulcer +4.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 327; x1.75 live lots -249; $4.84 -142
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer +5% / -11%, mean x1.75 -821 / +1158 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: UW gex-levels/oi-per-strike daily table (Advanced tier) + roll guard
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 45, HOLD 44, L6M 37 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**P7 nyam**  `P7|nyam|levelexit`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: 60/60 -> bracket P7 nyam stop=60 target=MIN(60, nearest UWG level ahead - 20) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -15.4%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -279; x1.75 live lots 347; $4.84 198
- **HOLD**: ulcer -0.2%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -2,585; x1.75 live lots -2,790; $4.84 -1,594
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -0% / -15%, mean x1.75 +1733 / +835 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: UW gex-levels/oi-per-strike daily table (Advanced tier) + roll guard
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 216, HOLD 98, L6M 105 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**A7 asia**  `A7|asia|levelexit`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: 60/60 -> bracket A7 asia stop=60 target=60 + DYNAMIC stop to -20 pts after rejection from a R250 level (within 5 pts then 10 pts pullback)
- **L6M**: ulcer -17.2%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 555; x1.75 live lots 1,628; $4.84 930
- **HOLD**: ulcer -42.3%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 808; x1.75 live lots 1,652; $4.84 944
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -42% / -17%, mean x1.75 +238 / +657 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: own zones / round-number target (no feed)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 47, HOLD 17, L6M 26 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 nyam**  `K7|nyam|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket K7 nyam stop=60 target=MIN(60, nearest R100 level ahead - 0) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -21.7%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,074; x1.75 live lots -1,320; $4.84 -755
- **HOLD**: ulcer +5.4%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,143; x1.75 live lots -2,504; $4.84 -1,431
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer +5% / -22%, mean x1.75 -504 / +559 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: own zones / round-number target (no feed)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 479, HOLD 118, L6M 119 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**H7 asia**  `H7|asia|levelexit`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: 60/60 -> bracket H7 asia stop=60 target=MIN(60, nearest UWG level ahead - 10) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -34.1%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 634; x1.75 live lots 4,556; $4.84 2,603
- **HOLD**: ulcer -46.4%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 97; x1.75 live lots 1,406; $4.84 803
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run; engine real cell H7_TUW10: HOLD -40% L6M -24% ulcer; engine real cell H7_SUWBE: HOLD -22% L6M -13% ulcer
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -46% / -34%, mean x1.75 +1236 / +3446 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: UW gex-levels/oi-per-strike daily table (Advanced tier) + roll guard
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 119, HOLD 54, L6M 44 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**M7 london**  `M7|london|levelexit`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: 60/60 -> bracket M7 london stop=60 target=MIN(60, nearest R250 level ahead - 20) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -35.6%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -790; x1.75 live lots 1,341; $4.84 766
- **HOLD**: ulcer -42.4%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 372; x1.75 live lots 1,572; $4.84 898
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -42% / -36%, mean x1.75 +920 / +2724 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: own zones / round-number target (no feed)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 283, HOLD 91, L6M 123 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 asia**  `K7|asia|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket K7 asia stop=60 target=MIN(60, nearest UW level ahead - 15) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -38.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 2,986; x1.75 live lots 4,999; $4.84 2,857
- **HOLD**: ulcer -66.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 3,497; x1.75 live lots 4,258; $4.84 2,433
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -67% / -39%, mean x1.75 -1861 / -226 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: UW gex-levels/oi-per-strike daily table (Advanced tier) + roll guard
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 353, HOLD 221, L6M 289 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 nypm**  `K7|nypm|levelexit`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: 60/60 -> bracket K7 nypm stop=60 target=MIN(60, nearest OWN level ahead - 20) [DYNAMIC: prior-day level table]
- **L6M**: ulcer -63.2%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,213; x1.75 live lots 2,856; $4.84 1,632
- **HOLD**: ulcer -39.7%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,985; x1.75 live lots -1,561; $4.84 -892
- Controls: screen only: shifted-label null 11/23/37 (family null holds 0-1 of 3 runs); engine controls not run; engine real cell K7_TUWN10: HOLD -11% L6M +15% ulcer
- Trials counted / correction: MD1: 31 rules x 15 cells + shape grid; best family per cell chosen on untouched ranking (inflated); 0 of 3 shifted nulls hold
- Untouched year: HOLD+L6M frozen pick from SEL: ulcer -40% / -63%, mean x1.75 +1912 / +732 $/wk
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code: own zones / round-number target (no feed)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: extra data that could help non-holding cells: intraday-refreshed UW levels / 0DTE strike levels (not available historically); fired in SEL 579, HOLD 145, L6M 160 trades; family chosen among 14 on untouched windows (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 x asia**  `K7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**K7 x london**  `K7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**K7 x nyam**  `K7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**K7 x nypm**  `K7|nypm|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**M7 x london**  `M7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59.5 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**M7 x nyam**  `M7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59.5 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**U7 x asia**  `U7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**U7 x london**  `U7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**P7 x asia**  `P7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/58 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**P7 x london**  `P7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/58 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**P7 x nyam**  `P7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/58 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**H7 x asia**  `H7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**H7 x nyam**  `H7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**A7 x asia**  `A7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (3 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T18:31:11Z

**M7 nyam**  `M7|nyam|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket M7 nyam stop=60 target=60 (no level exit survived selection on SEL; best available = native)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run (screen only)
- Trials counted / correction: MD1 765 rules/cells; shifted-label null
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line (existing)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: no level-based target/stop rule picked in selection for this cell
- Updated: 2026-11-17T17:48:25Z

**O7 nyam**  `O7|nyam|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 40/90 -> bracket O7 nyam stop=40 target=90 (no level exit survived selection on SEL; best available = native)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run (screen only)
- Trials counted / correction: MD1 765 rules/cells; shifted-label null
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line (existing)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: no level-based target/stop rule picked in selection for this cell
- Updated: 2026-11-17T17:48:25Z

**U7 asia**  `U7|asia|levelexit`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> bracket U7 asia stop=60 target=60 (no level exit survived selection on SEL; best available = native)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run (screen only)
- Trials counted / correction: MD1 765 rules/cells; shifted-label null
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line (existing)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: no level-based target/stop rule picked in selection for this cell
- Updated: 2026-11-17T17:48:25Z

**all books (pooled groups)**  `WALL|target-in-front`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/58 native -> target 1 pt in front of nearest resting >=8/16/32-lot order within 60 pts (age>=30/120 s); picks: London (8, 30); NYPM (8, 30)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: screen only; mode walk-forward (sampled older days)
- Trials counted / correction: MD3: 8 rules x 5 groups
- Untouched year: see page section 3
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: needs MBO/L3 (full-depth) feed: walls inside 60 pts are not visible in the CQG 20-level book (about 2-5 pts deep)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: wall rules lose money per fired trade on the covered span
- Updated: 2026-11-17T17:48:25Z

## Table 5. BAR SWAP (bar today -> bar proposed per weak book x session)
Selection rule: trailing-6M pick, 2-week refit, prior years AMBER 15-30% / RED >30% (outputs/CLAUDE.md)
**K7 x nyam**  `SWA|K7|nyam`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: K7 on the live time bar tm180 -> K7 nyam: bar today tm180 -> bar proposed vnorm_40 (vnorm size 40: variance-normalised bar: closes when sum of squared print-to-print price changes (ticks^2) >= trailing median daily RV / N; N bars per day-equivalent; scaling: rv); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: tsf_25_150), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 4,859; worst week n/a -> -1,212; mean/wk base lots n/a; $4.84 201
- **L3M**: ulcer n/a; max DD n/a -> 4,859; worst week n/a -> -2,425; mean/wk base lots n/a; $4.84 403
- Controls: White RC p=0.37 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS +24 vs ref -195 USD/wk, share beat ref 29%, older-year check NOT FINISHED (older-year coverage < 60%)
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: new custom BarsType: vnorm size 40: variance-normalised bar: closes when sum of squared print-to-print price changes (ticks^2) >= trailing median daily RV / N; N bars per day-equivalent; scaling: rv
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**P7 x NY AM**  `SWB|P7|NYAM`  (source: W-SWB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: P7 on live 1-minute time bar (tm60__A) -> P7 NY AM: bar today 1-minute time (live) -> proposed mrenko_80 | construction: mrenko_80 (median / mean Renko: brick N; reversal brick opens at the midpoint of last brick, triggers at 1.5N from last close) | param set A
- **L6M**: ulcer -90.1%; max DD 2,292 -> 303; worst week n/a; mean/wk (owner scalar, base lots) 556; x1.75 live lots 972; $4.84 556
- **L3M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 390
- Controls: White RC/SPA {'rc_p': 0.133, 'spa_p': 0.154, 'T': 26, 'K': 415}; random-clock / shifted-label nulls on the same pick procedure (page); 30 engine controls not yet run
- Trials counted / correction: 431 candidates, White RC/SPA
- Untouched year: none (rolling walk-forward instead): 6M->1M OOS -159.2 pts/mo vs live -421.8, share beat 0.60
- Behaviour / detail: standalone only; engine swap test pending; older-year check GREEN
- DS7 need: new custom BarsType: custom BarsType (MedianRenko / MeanRenko third-party) | scaling: size x s_rng (same, daily high-low range in points)
- Evidence: autopilot/DS3_BAR_SWAP_B.md
- Caveats: pick window 2026-05-04..2026-10-30 (trailing 6M), refit 2026-11-17 18:40:28 UTC, data end 2026-10-30, prior-year worst GREEN; persistence 0.60 / live bar not beaten on 6M
- Updated: 2026-11-17 18:40:28

**P7 x London**  `SWB|P7|London`  (source: W-SWB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: P7 on live 1-minute time bar (tm60__A) -> P7 London: bar today 1-minute time (live) -> proposed cusum_14 | construction: cusum_14 (CUSUM-filter events (Lopez de Prado): S+ = max(0,S+ + dp), S- = min(0,S- + dp) on print price changes; event when S+ > h or S- < -h, then reset; h = k x trailing sigma-scale (ticks)) | param set A
- **L6M**: ulcer -83.0%; max DD 558 -> 185; worst week n/a; mean/wk (owner scalar, base lots) 1,222; x1.75 live lots 2,138; $4.84 1,222
- **L3M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 2,444
- Controls: White RC/SPA {'rc_p': 0.999, 'spa_p': 0.995, 'T': 26, 'K': 348}; random-clock / shifted-label nulls on the same pick procedure (page); 30 engine controls not yet run
- Trials counted / correction: 427 candidates, White RC/SPA
- Untouched year: none (rolling walk-forward instead): 6M->1M OOS -33.4 pts/mo vs live 391.6, share beat 0.20
- Behaviour / detail: standalone only; engine swap test pending; older-year check GREEN
- DS7 need: new custom BarsType: custom BarsType (event-driven) | scaling: size x s_rng (same, daily high-low range in points)
- Evidence: autopilot/DS3_BAR_SWAP_B.md
- Caveats: pick window 2026-05-04..2026-10-30 (trailing 6M), refit 2026-11-17 18:40:28 UTC, data end 2026-10-30, prior-year worst GREEN; persistence 0.20 / live bar not beaten on 6M
- Updated: 2026-11-17 18:40:28

**M7 x london**  `SWA|M7|london`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: M7 on the live time bar tm60 -> M7 london: bar today tm60 -> bar proposed tm780 (time bar 780 s, epoch-aligned, closes on the first print of the next bar); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: tm300), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 7,284; worst week n/a -> -6,072; mean/wk base lots n/a; $4.84 367
- **L3M**: ulcer n/a; max DD n/a -> 3,357; worst week n/a -> -2,447; mean/wk base lots n/a; $4.84 461
- Controls: White RC p=0.23 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS -753 vs ref -731 USD/wk, share beat ref 9%, older-year check RED
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: native NT8 bar type (Minute/Second)
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**K7 x london**  `SWA|K7|london`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: K7 on the live time bar tm180 -> K7 london: bar today tm180 -> bar proposed tm780 (time bar 780 s, epoch-aligned, closes on the first print of the next bar); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: None), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 25,336; worst week n/a -> -7,410; mean/wk base lots n/a; $4.84 651
- **L3M**: ulcer n/a; max DD n/a -> 25,336; worst week n/a -> -7,187; mean/wk base lots n/a; $4.84 -498
- Controls: White RC p=0.40 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS -203 vs ref -202 USD/wk, share beat ref 21%, older-year check RED
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: native NT8 bar type (Minute/Second)
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**K7 x nypm**  `SWA|K7|nypm`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: K7 on the live time bar tm180 -> K7 nypm: bar today tm180 -> bar proposed tm1800 (time bar 1800 s, epoch-aligned, closes on the first print of the next bar); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: tsf_5_1200), refit every 2 weeks; ungated best, not a pick
- **L6M**: ulcer n/a; max DD n/a -> 3,637; worst week n/a -> -2,425; mean/wk base lots n/a; $4.84 603
- **L3M**: ulcer n/a; max DD n/a -> 3,637; worst week n/a -> -2,425; mean/wk base lots n/a; $4.84 222
- Controls: White RC p=0.67 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS -387 vs ref -178 USD/wk, share beat ref 15%, older-year check RED
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: native NT8 bar type (Minute/Second)
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**M7 x nyam**  `SWA|M7|nyam`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: M7 on the live time bar tm60 -> M7 nyam: bar today tm60 -> bar proposed tsf_5_100 (tsf_5 size 100: trade-size-filtered volume bar: only prints >= L lots count toward the volume threshold; grid L x N (id tsf_L_N); bar OHLC still uses only counted prints; scaling: vol (N scaled)); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: tsf_5_100), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 3,723; worst week n/a -> -2,187; mean/wk base lots n/a; $4.84 333
- **L3M**: ulcer n/a; max DD n/a -> 3,723; worst week n/a -> -2,459; mean/wk base lots n/a; $4.84 669
- Controls: White RC p=0.60 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS -65 vs ref +80 USD/wk, share beat ref 24%, older-year check NOT FINISHED (older-year coverage < 60%)
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: new custom BarsType: tsf_5 size 100: trade-size-filtered volume bar: only prints >= L lots count toward the volume threshold; grid L x N (id tsf_L_N); bar OHLC still uses only counted prints; scaling: vol (N scaled)
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**H7 x NY AM**  `SWB|H7|NYAM`  (source: W-SWB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: H7 on live 1-minute time bar (tm60__A) -> H7 NY AM: bar today 1-minute time (live) -> proposed drb_2000 | construction: drb_2000 (dollar-run bar (Lopez de Prado): close when max(sum of w over buys, sum over sells) >= E[T]*max(P(buy)E[w|buy],P(sell)E[w|sell])) | param set B
- **L6M**: ulcer -66.7%; max DD 366 -> 182; worst week n/a; mean/wk (owner scalar, base lots) 695; x1.75 live lots 1,216; $4.84 695
- **L3M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,120
- Controls: White RC/SPA {'rc_p': 1.0, 'spa_p': 0.996, 'T': 26, 'K': 451}; random-clock / shifted-label nulls on the same pick procedure (page); 30 engine controls not yet run
- Trials counted / correction: 642 candidates, White RC/SPA
- Untouched year: none (rolling walk-forward instead): 6M->1M OOS -123.3 pts/mo vs live 160.7, share beat 0.00
- Behaviour / detail: standalone only; engine swap test pending; older-year check GREEN
- DS7 need: new custom BarsType: custom BarsType (new code) | scaling: size x s_ntr (same, daily trade-print count)
- Evidence: autopilot/DS3_BAR_SWAP_B.md
- Caveats: pick window 2026-05-04..2026-10-30 (trailing 6M), refit 2026-11-17 18:40:28 UTC, data end 2026-10-30, prior-year worst GREEN; persistence 0.00 / live bar not beaten on 6M
- Updated: 2026-11-17 18:40:28

**U7 x london**  `SWA|U7|london`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: U7 on the live time bar tm600 -> U7 london: bar today tm600 -> bar proposed vsess_450 (vsess size 450: volume-clock / session-relative: N equal-volume bars per session; bar volume = trailing median session volume / N (a session with a typical volume curve gets N bars; NY open fast, lunch slow in clock time); scaling: sess); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: vsess_450), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 4,449; worst week n/a -> 0; mean/wk base lots n/a; $4.84 812
- **L3M**: ulcer n/a; max DD n/a -> 4,449; worst week n/a -> -518; mean/wk base lots n/a; $4.84 1,633
- Controls: White RC p=0.59 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS -139 vs ref -148 USD/wk, share beat ref 26%, older-year check NOT FINISHED (older-year coverage < 60%)
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: new custom BarsType: vsess size 450: volume-clock / session-relative: N equal-volume bars per session; bar volume = trailing median session volume / N (a session with a typical volume curve gets N bars; NY open fast, lunch slow in clock time); scaling: sess
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**O7 x NY AM**  `SWB|O7|NYAM`  (source: W-SWB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: O7 on live 1-minute time bar (tm60__A) -> O7 NY AM: bar today 1-minute time (live) -> proposed urenko_20 | construction: urenko_20 (UniRenko: brick N, reversal brick opens at last close and closes N beyond (reversal 1N)) | param set A
- **L6M**: ulcer -49.9%; max DD 445 -> 250; worst week n/a; mean/wk (owner scalar, base lots) 435; x1.75 live lots 761; $4.84 435
- **L3M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 84
- Controls: White RC/SPA {'rc_p': 0.742, 'spa_p': 0.664, 'T': 26, 'K': 41}; random-clock / shifted-label nulls on the same pick procedure (page); 30 engine controls not yet run
- Trials counted / correction: 58 candidates, White RC/SPA
- Untouched year: none (rolling walk-forward instead): 6M->1M OOS 7.8 pts/mo vs live 50.4, share beat 0.25
- Behaviour / detail: standalone only; engine swap test pending; older-year check GREEN
- DS7 need: new custom BarsType: custom BarsType (user has UniRenko) | scaling: size x s_rng (same, daily high-low range in points)
- Evidence: autopilot/DS3_BAR_SWAP_B.md
- Caveats: pick window 2026-05-04..2026-10-30 (trailing 6M), refit 2026-11-17 18:40:28 UTC, data end 2026-10-30, prior-year worst GREEN; persistence 0.25 / live bar not beaten on 6M
- Updated: 2026-11-17 18:40:28

**K7 x asia**  `SWA|K7|asia`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: K7 on the live time bar tm180 -> K7 asia: bar today tm180 -> bar proposed tm600 (time bar 600 s, epoch-aligned, closes on the first print of the next bar); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: tm600), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 7,131; worst week n/a -> -4,690; mean/wk base lots n/a; $4.84 2,183
- **L3M**: ulcer n/a; max DD n/a -> 7,131; worst week n/a -> -2,532; mean/wk base lots n/a; $4.84 2,502
- Controls: White RC p=0.50 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS +338 vs ref +50 USD/wk, share beat ref 44%, older-year check RED
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: native NT8 bar type (Minute/Second)
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**M7 x asia**  `SWA|M7|asia`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: M7 on the live time bar tm60 -> M7 asia: bar today tm60 -> bar proposed tm120 (time bar 120 s, epoch-aligned, closes on the first print of the next bar); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: tm120), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 12,471; worst week n/a -> -9,261; mean/wk base lots n/a; $4.84 2,368
- **L3M**: ulcer n/a; max DD n/a -> 12,471; worst week n/a -> -6,827; mean/wk base lots n/a; $4.84 2,953
- Controls: White RC p=0.62 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS +583 vs ref +628 USD/wk, share beat ref 18%, older-year check RED
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: native NT8 bar type (Minute/Second)
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**U7 x asia**  `SWA|U7|asia`  (source: W-SWA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: U7 on the live time bar tm600 -> U7 asia: bar today tm600 -> bar proposed vnorm_1500 (vnorm size 1500: variance-normalised bar: closes when sum of squared print-to-print price changes (ticks^2) >= trailing median daily RV / N; N bars per day-equivalent; scaling: rv); live book parameters, live bracket 60/60; pick = trailing 6M to 2026-11-13 (trailing-3M pick: vnorm_1500), refit every 2 weeks; gated pick
- **L6M**: ulcer n/a; max DD n/a -> 6,796; worst week n/a -> -6,200; mean/wk base lots n/a; $4.84 599
- **L3M**: ulcer n/a; max DD n/a -> 6,796; worst week n/a -> -517; mean/wk base lots n/a; $4.84 1,204
- Controls: White RC p=0.99 (L6M); engine controls not run; random-clock nulls see page
- Trials counted / correction: 57 rows x 3 books screened; White RC + neighbour gate
- Untouched year: rolling walk-forward 6M->1M: OOS +254 vs ref +293 USD/wk, share beat ref 29%, older-year check NOT FINISHED (older-year coverage < 60%)
- Behaviour / detail: standalone only; D7 drawdown behaviour and stack test pending
- DS7 need: new custom BarsType: vnorm size 1500: variance-normalised bar: closes when sum of squared print-to-print price changes (ticks^2) >= trailing median daily RV / N; N bars per day-equivalent; scaling: rv
- Evidence: autopilot/DS3_BAR_SWAP_A.md
- Caveats: standalone, flat at session end, data end 2026-11-13; rule: trailing-6M pick + rolling WF
- Updated: 2026-11-17T18:22:03Z

**A7 x Asia**  `SWB|A7|Asia`  (source: W-SWB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: A7 on live 1-minute time bar (tm60__A) -> A7 Asia: bar today 1-minute time (live) -> proposed tm900 | construction: 15-minute time bar | param set A
- **L6M**: ulcer -92.8%; max DD 972 -> 106; worst week n/a; mean/wk (owner scalar, base lots) 556; x1.75 live lots 974; $4.84 556
- **L3M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 177
- Controls: White RC/SPA {'rc_p': 0.415, 'spa_p': 0.21, 'T': 26, 'K': 320}; random-clock / shifted-label nulls on the same pick procedure (page); 30 engine controls not yet run
- Trials counted / correction: 429 candidates, White RC/SPA
- Untouched year: none (rolling walk-forward instead): 6M->1M OOS 61.6 pts/mo vs live 11.2, share beat 0.60
- Behaviour / detail: standalone only; engine swap test pending; older-year check GREEN
- DS7 need: native: native NT8 Minute bar (OnBarClose at the first print after the boundary)
- Evidence: autopilot/DS3_BAR_SWAP_B.md
- Caveats: pick window 2026-05-04..2026-10-30 (trailing 6M), refit 2026-11-17 18:40:28 UTC, data end 2026-10-30, prior-year worst GREEN; persistence 0.60 / live bar not beaten on 6M
- Updated: 2026-11-17 18:40:28

**P7 x Asia**  `SWB|P7|Asia`  (source: W-SWB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: P7 on live 1-minute time bar (tm60__A) -> P7 Asia: bar today 1-minute time (live) -> proposed cusum_40 | construction: cusum_40 (CUSUM-filter events (Lopez de Prado): S+ = max(0,S+ + dp), S- = min(0,S- + dp) on print price changes; event when S+ > h or S- < -h, then reset; h = k x trailing sigma-scale (ticks)) | param set B
- **L6M**: ulcer -88.8%; max DD 722 -> 151; worst week n/a; mean/wk (owner scalar, base lots) 507; x1.75 live lots 887; $4.84 507
- **L3M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,014
- Controls: White RC/SPA {'rc_p': 0.852, 'spa_p': 0.784, 'T': 26, 'K': 365}; random-clock / shifted-label nulls on the same pick procedure (page); 30 engine controls not yet run
- Trials counted / correction: 428 candidates, White RC/SPA
- Untouched year: none (rolling walk-forward instead): 6M->1M OOS -211.5 pts/mo vs live 375.7, share beat 0.00
- Behaviour / detail: standalone only; engine swap test pending; older-year check GREEN
- DS7 need: new custom BarsType: custom BarsType (event-driven) | scaling: size x s_rng (same, daily high-low range in points)
- Evidence: autopilot/DS3_BAR_SWAP_B.md
- Caveats: pick window 2026-05-04..2026-10-30 (trailing 6M), refit 2026-11-17 18:40:28 UTC, data end 2026-10-30, prior-year worst GREEN; persistence 0.00 / live bar not beaten on 6M
- Updated: 2026-11-17 18:40:28

**H7 x Asia**  `SWB|H7|Asia`  (source: W-SWB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: H7 on live 1-minute time bar (tm60__A) -> H7 Asia: bar today 1-minute time (live) -> proposed dib_400 | construction: dib_400 (dollar-imbalance bar (Lopez de Prado): theta = sum b_t*w_t (b = aggressor side, tick rule if none; w = dollars); close when |theta| >= E[T]*max(|EWMA(b w)|, EWMA|w|/sqrt(E[T])); E[T] = EWMA(0.2) of ba) | param set A
- **L6M**: ulcer -48.9%; max DD 392 -> 301; worst week n/a; mean/wk (owner scalar, base lots) 975; x1.75 live lots 1,706; $4.84 975
- **L3M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 667
- Controls: White RC/SPA {'rc_p': 0.584, 'spa_p': 0.61, 'T': 26, 'K': 382}; random-clock / shifted-label nulls on the same pick procedure (page); 30 engine controls not yet run
- Trials counted / correction: 628 candidates, White RC/SPA
- Untouched year: none (rolling walk-forward instead): 6M->1M OOS 221.1 pts/mo vs live 140.4, share beat 0.40
- Behaviour / detail: standalone only; engine swap test pending; older-year check GREEN
- DS7 need: new custom BarsType: custom BarsType (stateful EWMA; buildable, new code) | scaling: size x s_ntr (same, daily trade-print count)
- Evidence: autopilot/DS3_BAR_SWAP_B.md
- Caveats: pick window 2026-05-04..2026-10-30 (trailing 6M), refit 2026-11-17 18:40:28 UTC, data end 2026-10-30, prior-year worst GREEN; persistence 0.40 / live bar not beaten on 6M
- Updated: 2026-11-17 18:40:28

## Table 6. ENTRY CONDITIONS / SCORES (per book x session: condition or score, action skip / half / x1.5)
Selection rule: trailing-6M pick, 2-week refit, prior years AMBER 15-30% / RED >30% (outputs/CLAUDE.md)
**all books x sessions (15 cells), family levels and zones (own zones, session/round levels)**  `S1R|3|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 levels and zones (own zones, session/round levels) conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer +0.0%; max DD 8,448 -> 8,448; worst week n/a; mean/wk base lots n/a; x1.75 live lots 0; $4.84 0
- **L3M**: ulcer +0.0%; max DD 4,139 -> 4,139; worst week n/a; mean/wk base lots n/a; x1.75 live lots 0; $4.84 0
- **HOLD**: ulcer +0.0%; max DD 4,649 -> 4,649; worst week n/a; mean/wk base lots n/a; x1.75 live lots 0; $4.84 0
- **GAP**: ulcer +2.0%; max DD 4,489 -> 4,489; worst week n/a; mean/wk base lots n/a; x1.75 live lots -250; $4.84 -143
- **PRE**: ulcer +5.0%; max DD 7,024 -> 7,024; worst week n/a; mean/wk base lots n/a; x1.75 live lots -464; $4.84 -265
- **XP**: ulcer -49.5%; max DD 9,842 -> 4,253; worst week n/a; mean/wk base lots n/a; x1.75 live lots 87; $4.84 50
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.023 R, dUlcer -16.3%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 41%
- Excess over nulls: vs shifted-label nulls dMeanR -0.012 R, dUlcer -14.8%; beats random-skip draws 10% (dU) / 20% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ bars + prior-day levels
- D7 live-computable: yes: own zones/levels (UW levels need the UW feed)
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family causal trade context (raw)**  `S1R|9|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 causal trade context (raw) conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -29.2%; max DD 8,448 -> 5,471; worst week n/a; mean/wk base lots n/a; x1.75 live lots -57; $4.84 -33
- **L3M**: ulcer -13.1%; max DD 4,139 -> 3,094; worst week n/a; mean/wk base lots n/a; x1.75 live lots 212; $4.84 121
- **HOLD**: ulcer +9.1%; max DD 4,649 -> 3,964; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,701; $4.84 -972
- **GAP**: ulcer -45.6%; max DD 4,489 -> 2,889; worst week n/a; mean/wk base lots n/a; x1.75 live lots -607; $4.84 -347
- **PRE**: ulcer -45.8%; max DD 7,024 -> 3,959; worst week n/a; mean/wk base lots n/a; x1.75 live lots -636; $4.84 -363
- **XP**: ulcer -76.0%; max DD 9,842 -> 3,302; worst week n/a; mean/wk base lots n/a; x1.75 live lots -337; $4.84 -192
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.040 R, dUlcer -48.7%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 34%
- Excess over nulls: vs shifted-label nulls dMeanR -0.062 R, dUlcer -24.0%; beats random-skip draws 50% (dU) / 70% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: D7 trade log
- D7 live-computable: yes: D7 own trade state
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family confluence: oscillators**  `S1R|1c|rolling-top5`  (source: W-S1R)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 oscillators conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -29.7%; max DD 8,448 -> 3,892; worst week n/a; mean/wk base lots n/a; x1.75 live lots -603; $4.84 -345
- **L3M**: ulcer -69.0%; max DD 4,139 -> 1,280; worst week n/a; mean/wk base lots n/a; x1.75 live lots -477; $4.84 -273
- **HOLD**: ulcer -83.9%; max DD 4,649 -> 795; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,811; $4.84 -1,035
- **GAP**: ulcer -91.8%; max DD 4,489 -> 596; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,076; $4.84 -615
- **PRE**: ulcer -53.2%; max DD 7,024 -> 3,095; worst week n/a; mean/wk base lots n/a; x1.75 live lots -963; $4.84 -550
- **XP**: ulcer -40.8%; max DD 9,842 -> 3,484; worst week n/a; mean/wk base lots n/a; x1.75 live lots -561; $4.84 -321
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.099 R, dUlcer -42.1%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 32%
- Excess over nulls: vs shifted-label nulls dMeanR +0.001 R, dUlcer -56.6%; beats random-skip draws 10% (dU) / 60% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ bars
- D7 live-computable: yes: own bars
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family order flow: tape prints and speed**  `S1R|5a|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 tape prints and speed conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -71.0%; max DD 8,448 -> 1,883; worst week n/a; mean/wk base lots n/a; x1.75 live lots -546; $4.84 -312
- **L3M**: ulcer -86.4%; max DD 4,139 -> 750; worst week n/a; mean/wk base lots n/a; x1.75 live lots -534; $4.84 -305
- **HOLD**: ulcer -8.3%; max DD 4,649 -> 4,111; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,807; $4.84 -1,033
- **GAP**: ulcer -73.4%; max DD 4,489 -> 745; worst week n/a; mean/wk base lots n/a; x1.75 live lots -510; $4.84 -291
- **PRE**: ulcer -76.8%; max DD 7,024 -> 1,752; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,229; $4.84 -702
- **XP**: ulcer -67.7%; max DD 9,842 -> 2,079; worst week n/a; mean/wk base lots n/a; x1.75 live lots -366; $4.84 -209
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.226 R, dUlcer -64.5%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 38%
- Excess over nulls: vs shifted-label nulls dMeanR +0.035 R, dUlcer -55.3%; beats random-skip draws 60% (dU) / 70% (dm); beats all 3 shifts: yes
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ prints (+L3 for message rates)
- D7 live-computable: prints yes (NT8); message rates need L3
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family candle counting, ICT 7-13-21, IRL/ERL**  `S1R|2|rolling-top5`  (source: W-S1R)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 candle counting, ICT 7-13-21, IRL/ERL conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -78.1%; max DD 8,448 -> 2,937; worst week n/a; mean/wk base lots n/a; x1.75 live lots -204; $4.84 -117
- **L3M**: ulcer -89.3%; max DD 4,139 -> 435; worst week n/a; mean/wk base lots n/a; x1.75 live lots 146; $4.84 83
- **HOLD**: ulcer -84.9%; max DD 4,649 -> 591; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,829; $4.84 -1,045
- **GAP**: ulcer -69.9%; max DD 4,489 -> 1,046; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,041; $4.84 -595
- **PRE**: ulcer -64.1%; max DD 7,024 -> 1,235; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,244; $4.84 -711
- **XP**: ulcer -33.0%; max DD 9,842 -> 3,204; worst week n/a; mean/wk base lots n/a; x1.75 live lots -571; $4.84 -326
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.108 R, dUlcer -44.0%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 31%
- Excess over nulls: vs shifted-label nulls dMeanR +0.148 R, dUlcer -72.7%; beats random-skip draws 10% (dU) / 70% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ bars
- D7 live-computable: yes: own bars
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family confluence: alt-bar agreement**  `S1R|1h|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 alt-bar agreement conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -79.3%; max DD 8,448 -> 2,327; worst week n/a; mean/wk base lots n/a; x1.75 live lots -398; $4.84 -227
- **L3M**: ulcer -56.9%; max DD 4,139 -> 2,327; worst week n/a; mean/wk base lots n/a; x1.75 live lots -528; $4.84 -302
- **HOLD**: ulcer -75.6%; max DD 4,649 -> 880; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,855; $4.84 -1,060
- **GAP**: ulcer -93.4%; max DD 4,489 -> 215; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,006; $4.84 -575
- **PRE**: ulcer -83.5%; max DD 7,024 -> 596; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,271; $4.84 -726
- **XP**: ulcer -76.6%; max DD 9,842 -> 1,730; worst week n/a; mean/wk base lots n/a; x1.75 live lots -326; $4.84 -186
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.285 R, dUlcer -79.3%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 35%
- Excess over nulls: vs shifted-label nulls dMeanR +0.048 R, dUlcer -47.2%; beats random-skip draws 50% (dU) / 70% (dm); beats all 3 shifts: yes
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ prints -> alt bars
- D7 live-computable: yes, same as 1g
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family F5 order flow (all)**  `S1R|5|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 F5 order flow (all) conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -80.2%; max DD 8,448 -> 1,160; worst week n/a; mean/wk base lots n/a; x1.75 live lots -447; $4.84 -256
- **L3M**: ulcer -59.3%; max DD 4,139 -> 1,160; worst week n/a; mean/wk base lots n/a; x1.75 live lots -319; $4.84 -182
- **HOLD**: ulcer -89.0%; max DD 4,649 -> 795; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,384; $4.84 -791
- **GAP**: ulcer -37.8%; max DD 4,489 -> 3,261; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,384; $4.84 -791
- **PRE**: ulcer -86.4%; max DD 7,024 -> 795; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,025; $4.84 -586
- **XP**: ulcer -98.7%; max DD 9,842 -> 380; worst week n/a; mean/wk base lots n/a; x1.75 live lots -409; $4.84 -234
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.510 R, dUlcer -68.7%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 34%
- Excess over nulls: vs shifted-label nulls dMeanR +0.067 R, dUlcer -58.6%; beats random-skip draws 40% (dU) / 100% (dm); beats all 3 shifts: yes
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: n/a (owner has not delivered)
- D7 live-computable: partly
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family TICK internals**  `S1R|10|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 TICK internals conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -81.5%; max DD 8,448 -> 1,810; worst week n/a; mean/wk base lots n/a; x1.75 live lots 173; $4.84 99
- **L3M**: ulcer -65.6%; max DD 4,139 -> 1,810; worst week n/a; mean/wk base lots n/a; x1.75 live lots 113; $4.84 65
- **HOLD**: ulcer -76.9%; max DD 4,649 -> 1,226; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,668; $4.84 -953
- **GAP**: ulcer -46.9%; max DD 4,489 -> 2,409; worst week n/a; mean/wk base lots n/a; x1.75 live lots -669; $4.84 -383
- **PRE**: ulcer -63.8%; max DD 7,024 -> 2,369; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,205; $4.84 -689
- **XP**: ulcer -43.8%; max DD 9,842 -> 4,105; worst week n/a; mean/wk base lots n/a; x1.75 live lots -539; $4.84 -308
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.056 R, dUlcer -52.2%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 31%
- Excess over nulls: vs shifted-label nulls dMeanR -0.078 R, dUlcer -10.0%; beats random-skip draws 40% (dU) / 50% (dm); beats all 3 shifts: yes
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NYSE TICK
- D7 live-computable: needs NYSE TICK feed in NT8 (delayed-feed check open)
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family other markets and breadth**  `S1R|6|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 other markets and breadth conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -83.2%; max DD 8,448 -> 1,538; worst week n/a; mean/wk base lots n/a; x1.75 live lots -243; $4.84 -139
- **L3M**: ulcer -93.5%; max DD 4,139 -> 192; worst week n/a; mean/wk base lots n/a; x1.75 live lots -30; $4.84 -17
- **HOLD**: ulcer -70.0%; max DD 4,649 -> 1,353; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,786; $4.84 -1,020
- **GAP**: ulcer -70.4%; max DD 4,489 -> 800; worst week n/a; mean/wk base lots n/a; x1.75 live lots -356; $4.84 -204
- **PRE**: ulcer -72.4%; max DD 7,024 -> 1,419; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,278; $4.84 -730
- **XP**: ulcer -61.3%; max DD 9,842 -> 3,078; worst week n/a; mean/wk base lots n/a; x1.75 live lots -394; $4.84 -225
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.237 R, dUlcer -63.0%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 34%
- Excess over nulls: vs shifted-label nulls dMeanR +0.033 R, dUlcer -57.4%; beats random-skip draws 50% (dU) / 80% (dm); beats all 3 shifts: yes
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: ES/RTY/YM/rates/other markets
- D7 live-computable: NO today: other-market feeds not on the D7 chart
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker + the feed above)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family confluence: named indicators / session anchors**  `S1R|1a|rolling-top5`  (source: W-S1R)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 named indicators / session anchors conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -83.9%; max DD 8,448 -> 961; worst week n/a; mean/wk base lots n/a; x1.75 live lots -443; $4.84 -253
- **L3M**: ulcer -82.5%; max DD 4,139 -> 605; worst week n/a; mean/wk base lots n/a; x1.75 live lots -442; $4.84 -253
- **HOLD**: ulcer -79.9%; max DD 4,649 -> 1,200; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,699; $4.84 -971
- **GAP**: ulcer -96.9%; max DD 4,489 -> 100; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,130; $4.84 -646
- **PRE**: ulcer -29.2%; max DD 7,024 -> 2,882; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,482; $4.84 -847
- **XP**: ulcer -90.0%; max DD 9,842 -> 795; worst week n/a; mean/wk base lots n/a; x1.75 live lots -375; $4.84 -214
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.281 R, dUlcer -54.9%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 34%
- Excess over nulls: vs shifted-label nulls dMeanR +0.203 R, dUlcer -68.7%; beats random-skip draws 0% (dU) / 50% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ bars
- D7 live-computable: yes: own bars/session anchors
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family order flow: L3 / L2 book / flow library**  `S1R|5b|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 L3 / L2 book / flow library conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -85.6%; max DD 8,448 -> 1,767; worst week n/a; mean/wk base lots n/a; x1.75 live lots -431; $4.84 -246
- **L3M**: ulcer -63.9%; max DD 4,139 -> 1,767; worst week n/a; mean/wk base lots n/a; x1.75 live lots -413; $4.84 -236
- **HOLD**: ulcer -89.0%; max DD 4,649 -> 795; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,415; $4.84 -809
- **GAP**: ulcer -48.1%; max DD 4,489 -> 3,099; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,124; $4.84 -642
- **PRE**: ulcer -64.6%; max DD 7,024 -> 2,165; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,019; $4.84 -583
- **XP**: ulcer -81.9%; max DD 9,842 -> 1,676; worst week n/a; mean/wk base lots n/a; x1.75 live lots -419; $4.84 -239
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.373 R, dUlcer -70.6%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 38%
- Excess over nulls: vs shifted-label nulls dMeanR +0.006 R, dUlcer -57.6%; beats random-skip draws 60% (dU) / 100% (dm); beats all 3 shifts: yes
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: L3 / L2 book
- D7 live-computable: NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels)
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker + the feed above)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family confluence: vol / squeeze / state / ML**  `S1R|1f|rolling-top5`  (source: W-S1R)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 vol / squeeze / state / ML conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -87.6%; max DD 8,448 -> 1,690; worst week n/a; mean/wk base lots n/a; x1.75 live lots -306; $4.84 -175
- **L3M**: ulcer -100.0%; max DD 4,139 -> 0; worst week n/a; mean/wk base lots n/a; x1.75 live lots -279; $4.84 -159
- **HOLD**: ulcer -54.9%; max DD 4,649 -> 1,481; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,878; $4.84 -1,073
- **GAP**: ulcer -72.9%; max DD 4,489 -> 1,182; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,129; $4.84 -645
- **PRE**: ulcer -50.5%; max DD 7,024 -> 1,983; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,451; $4.84 -829
- **XP**: ulcer -87.9%; max DD 9,842 -> 1,155; worst week n/a; mean/wk base lots n/a; x1.75 live lots -256; $4.84 -146
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.199 R, dUlcer -67.0%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 32%
- Excess over nulls: vs shifted-label nulls dMeanR +0.088 R, dUlcer -64.9%; beats random-skip draws 40% (dU) / 70% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ bars
- D7 live-computable: yes: own bars
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family confluence: SMC / ICT structure**  `S1R|1e|rolling-top5`  (source: W-S1R)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 SMC / ICT structure conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -88.7%; max DD 8,448 -> 1,367; worst week n/a; mean/wk base lots n/a; x1.75 live lots -253; $4.84 -145
- **L3M**: ulcer -88.0%; max DD 4,139 -> 1,367; worst week n/a; mean/wk base lots n/a; x1.75 live lots -351; $4.84 -201
- **HOLD**: ulcer -55.8%; max DD 4,649 -> 1,600; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,651; $4.84 -943
- **GAP**: ulcer -54.2%; max DD 4,489 -> 800; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,033; $4.84 -590
- **PRE**: ulcer -15.8%; max DD 7,024 -> 4,510; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,230; $4.84 -703
- **XP**: ulcer -74.8%; max DD 9,842 -> 1,966; worst week n/a; mean/wk base lots n/a; x1.75 live lots -313; $4.84 -179
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.185 R, dUlcer -48.6%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 34%
- Excess over nulls: vs shifted-label nulls dMeanR +0.067 R, dUlcer -67.0%; beats random-skip draws 30% (dU) / 60% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ bars
- D7 live-computable: yes: own bars
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

**all books x sessions (15 cells), family confluence: entry-table universe**  `S1R|1b|rolling-top5`  (source: W-S1R)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no entry-condition rule today -> rolling: every 14 days pick the top 5 entry-table universe conditions on the trailing six months (rules skip / half / x1.5 on yes or no; both gates 15% prior-year; ranked by effect on mean R and ulcer), trade the next 2 weeks; score = equal-weight vote of the five
- **L6M**: ulcer -96.0%; max DD 8,448 -> 770; worst week n/a; mean/wk base lots n/a; x1.75 live lots -209; $4.84 -120
- **L3M**: ulcer -88.8%; max DD 4,139 -> 770; worst week n/a; mean/wk base lots n/a; x1.75 live lots -113; $4.84 -64
- **HOLD**: ulcer -69.6%; max DD 4,649 -> 1,167; worst week n/a; mean/wk base lots n/a; x1.75 live lots -2,017; $4.84 -1,152
- **GAP**: ulcer -55.6%; max DD 4,489 -> 1,350; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,026; $4.84 -586
- **PRE**: ulcer -83.8%; max DD 7,024 -> 800; worst week n/a; mean/wk base lots n/a; x1.75 live lots -1,133; $4.84 -648
- **XP**: ulcer -40.1%; max DD 9,842 -> 3,398; worst week n/a; mean/wk base lots n/a; x1.75 live lots -532; $4.84 -304
- Action (skip/half/x1.5): skip / half / x1.5 on the top-5 recent conditions (see the page for the current list per book x session)
- Trailing 6M / 3M effect: 6M picks: dMeanR +0.213 R, dUlcer -55.4%; 3M picks: dMeanR  R, dUlcer % (OOS, next 2 weeks chained)
- Rolling persistence: 34%
- Excess over nulls: vs shifted-label nulls dMeanR -0.066 R, dUlcer -59.5%; beats random-skip draws 50% (dU) / 90% (dm); beats all 3 shifts: no
- Prior-year % (AMBER 15-30 / RED >30): gate g15 keeps only picks <=15% worse than doing nothing on ulcer and mean in each prior 365-day block (30% line: g30 table on the page)
- Flag: GREEN by construction; fragile if 6M and 3M disagree
- Feed need: NQ bars
- D7 live-computable: yes: own bars
- Controls: shifted labels 11/23/37 + 10 random persistent skip draws + nonsense/random/planted families
- Trials counted / correction: 65,192 columns x 2 sides x 3 actions x 15 cells x 79 refits (nulls beside)
- Untouched year: rolling OOS (no frozen holdout); thirds in the page
- Behaviour / detail: not engine-exact; raw-chassis, no re-entry/freed-book effects
- DS7 need: new code (rolling bi-weekly condition picker on D7 own data)
- Evidence: autopilot/DS3_REBUILD_S1R.md
- Caveats: first pass, raw books, data end 2026-10-30; label from the page rules
- Updated: 2026-11-17T18:32:11Z

## Table 2. NEW YORK AND LONDON BOOKS
Selection rule: trailing-6M pick, 2-week refit, prior years AMBER 15-30% / RED >30% (outputs/CLAUDE.md)
**London book: M3_FAILED_BREAK_LON**  `BOOK|LON|M3_FAILED_BREAK_LON`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: not live -> Signal M3 failed break, lookback 60 min, reject 5 pts, London window, 1-min bars, market entry, exit E2 = stop 60 / target 60, equal-dollar-risk lots (round(1200/(stop x 20))); exact entry rule per owner page
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: 30 shifted-date engine controls NOT FINISHED; engine lots 1-4 rows not landed
- Trials counted / correction: 2,044 standalone cells counted; White RC p 0.40
- Untouched year: untouched year +0.057 R on 150 trades, 66.7% months positive
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): fails diversification test (b): worst 20 weeks $-1,696; correlation -0.064; engine stack test pending
- DS7 need: new code (new book + London window)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: Weak: LEAD-NO-HEDGE on the standalone screen only. LEAD-ASSEMBLED, owner to confirm (source: DS3_MAJOR_F_NEWBOOKS.md)
- Updated: n/a

**London book: R3_RTY_LED_LON (RTY-led)**  `BOOK|LON|R3_RTY_LED_LON`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: not live -> Signal RTY-led London catch-up L=15, bp=3, win=LON, src=RTY; exit E4_vol (volatility exit per owner page); 1-min bars
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: engine controls NOT FINISHED
- Trials counted / correction: 2,044 cells counted; White RC p 0.36, DSR 0.47
- Untouched year: +0.045 R on 256 trades, 67% months positive
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): passes diversification (b): corr 0.01, $6,854 in 20 worst weeks, $18,954 in 5 DDs; engine stack test pending
- DS7 need: new code (cross-market RTY feed + book)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: Not significant after best-of (RC p 0.36). LEAD-ASSEMBLED, owner to confirm (source: DS3_MAJOR_F_NEWBOOKS.md)
- Updated: n/a

**London book: R3_YM_LED_LON (YM-led)**  `BOOK|LON|R3_YM_LED_LON`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: not live -> Signal YM-led London catch-up L=15, bp=3, win=LON, src=YM; exit E3 = 40 / 90; 1-min bars
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: engine controls NOT FINISHED
- Trials counted / correction: 2,044 cells counted; White RC p 0.16, DSR 0.56
- Untouched year: +0.073 R on 253 trades, 67% months positive
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): passes diversification (b): corr 0.09, $24,511 in 20 worst weeks, $14,098 in 5 DDs; engine stack test pending
- DS7 need: new code (cross-market YM feed + book)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: Not significant after best-of (RC p 0.16). LEAD-ASSEMBLED, owner to confirm (source: DS3_MAJOR_F_NEWBOOKS.md)
- Updated: n/a

**NY PM book: R3V_W12_RSI2_3MIN_NYPM**  `BOOK|NYPM|RSI2_3MIN`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: not live -> RSI2 on 3-min bars, threshold 5 (tf=3, th=5), NY PM window; exit E3 = 40 / 90
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: engine controls NOT FINISHED
- Trials counted / correction: 2,044 cells counted; White RC p 0.79, DSR 0.67
- Untouched year: +0.105 R on 243 trades, 67% months positive
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): passes (b): corr -0.11, $26,858 in 20 worst weeks, $40,084 in 5 DDs; LEAD-WEAK (selection-window mean only 0.006 R)
- DS7 need: new code (new book)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: Untouched year does the work; RC p 0.79. LEAD-ASSEMBLED, owner to confirm (source: DS3_MAJOR_F_NEWBOOKS.md)
- Updated: n/a

**Late-session book: R3V_W9_LATE_EXT_LOOSE (session per owner page)**  `BOOK|LATE|LATE_EXT_LOOSE`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: not live -> Late extension fade, k=1.0; exit E2 = 60 / 60
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: engine controls NOT FINISHED
- Trials counted / correction: 2,044 cells counted; White RC p 0.90, DSR 0.87
- Untouched year: +0.088 R on 240 trades, 75% months positive
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): passes (b): corr -0.10, $18,426 in 20 worst weeks, $4,933 in 5 DDs; LEAD-WEAK (selection-window mean -0.017 R)
- DS7 need: new code (new book)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: RC p 0.90; session assignment not stated in the page extract used. LEAD-ASSEMBLED, owner to confirm (source: DS3_MAJOR_F_NEWBOOKS.md)
- Updated: n/a

**NYAM N4_1000_REVERSAL**  `NYAM-book-1`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> 10:00 reversal window: move = close(09:59) - open(09:30); if |move| >= 0.3 x ATR14 enter at 10:00 cont (fade = against, cont = with). Exact parameters: k=0.3,mode=cont. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) -0.073 R on 87 trades, 42% months positive; selection window 0.244 R on 183 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.06; $ at $1,200 risk/trade inside JL3 five deepest DDs 17523, in 20 worst weeks 31785; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYAM X4_OPEN_DRIVE_DR**  `NYAM-book-2`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Opening drive DR10: drive = close(09:30 + 10 min) - open(09:30); needs |drive| >= 0.75 x trailing-20-day median 5-min opening move; wait for 1 consecutive against-drive 1-min closes then enter with the drive at the close of the first bar that closes beyond the prior bar's extreme in the drive direction (until 11:00 ET). Exact parameters: W=10,rm=0.75,pb=1. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) 0.024 R on 170 trades, 50% months positive; selection window 0.203 R on 448 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.12; $ at $1,200 risk/trade inside JL3 five deepest DDs 40956, in 20 worst weeks 27302; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYAM X4_ORB_DIR_PULLBACK**  `NYAM-book-3`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Opening-range direction + first pullback: OR = first 15 minutes from 09:30 ET; first 1-min close beyond it until 11:00 gives the direction (ctx=with: with = only if the gap sign agrees, |gap| >= 0.05 x ATR14); then enter in that direction at the close of the first bar (until 11:30) that traded back to edge (the OR edge, or VWAP) and closed back on the trend side. Exact parameters: OR=15,lvl=edge,ctx=with. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) -0.145 R on 107 trades, 33% months positive; selection window 0.195 R on 233 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.10; $ at $1,200 risk/trade inside JL3 five deepest DDs 11924, in 20 worst weeks -6353; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYPM W7_POWER_HOUR_LOOSE**  `NYPM-book-1`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Power-hour continuation: at (14, 59) ET if |close - 09:30 open| >= 0.3 x ATR14 (and, for filt=dvh, the close is on the same side of VWAP and the last-60-min move has the same sign) enter with the day's direction; flat 15:58. Exact parameters: t=(14, 59),k=0.3,filt=dvh. Exit: stop = target = clip(0.12 x ATR14, 25, 90) points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) 0.153 R on 90 trades, 50% months positive; selection window 0.083 R on 253 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.07; $ at $1,200 risk/trade inside JL3 five deepest DDs -2379, in 20 worst weeks 2519; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYPM X4_RSI2_15MIN_NYPM**  `NYPM-book-2`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> RSI(2) washout on 15-min closes (RSI computed from 09:30 or 02:00 start of session): RSI2 < 5 with price below session VWAP = long, RSI2 > 95 above VWAP = short; first signal in the session window. Exact parameters: tf=15,th=5. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) 0.028 R on 158 trades, 50% months positive; selection window 0.055 R on 450 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily -0.08; $ at $1,200 risk/trade inside JL3 five deepest DDs 14250, in 20 worst weeks 18268; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**LONDON NQ.FADE_LV.f4d004a6**  `LONDON-book-1`  (source: W-MB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no book in this slot -> Shelf book NQ.FADE_LV.f4d004a6: nan; stop/target/time exit as in its trade list; engine test pending
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 517
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -539
- **PRE**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -971
- **XP**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -629
- Controls: not run (harness screen only; date-shift p=0.37)
- Trials counted / correction: 6,836 screened
- Untouched year: not run
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): screen: P&L on JL3 20 worst weeks $-1515, inside 5 deepest DDs $1555, corr -0.10 (equal-risk scaling, base dollars)
- DS7 need: new code (book; see setting)
- Evidence: autopilot/DS3_MAJOR_B_BOOKS.md
- Caveats: harness basis only until the engine stack test lands
- Updated: 2026-11-17 18:33

**LONDON NQ.FADE_LV.6fb3aa4d**  `LONDON-book-2`  (source: W-MB)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no book in this slot -> Shelf book NQ.FADE_LV.6fb3aa4d: nan; stop/target/time exit as in its trade list; engine test pending
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 254
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 507
- **PRE**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -178
- **XP**: ulcer n/a; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -53
- Controls: not run (harness screen only; date-shift p=0.83)
- Trials counted / correction: 6,836 screened
- Untouched year: not run
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): screen: P&L on JL3 20 worst weeks $18860, inside 5 deepest DDs $14159, corr -0.04 (equal-risk scaling, base dollars)
- DS7 need: new code (book; see setting)
- Evidence: autopilot/DS3_MAJOR_B_BOOKS.md
- Caveats: harness basis only until the engine stack test lands
- Updated: 2026-11-17 18:33

**LON W11_SESSION_EXTREME_RSI14_LON**  `LON-book-1`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Session-extreme fade: 5-min bar high (low) equals the running session high (low) with 5-min RSI(14) >= 80 (<= 100-80): fade at that bar close; windows LON 03:30-08:00, NYAM 10:30-11:45, NYPM 12:00-15:30 ET. Exact parameters: r=80. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) -0.046 R on 56 trades, 33% months positive; selection window 0.162 R on 151 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily -0.08; $ at $1,200 risk/trade inside JL3 five deepest DDs 2364, in 20 worst weeks 13379; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**LON X4_FAILED_BREAK_BARS_LON**  `LON-book-2`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Failed-breakout re-entry on 15-minute bars (aggregated from 1-min, aligned to the session start 02:00 or 09:30 ET): first 15-min close beyond the prior 120-minute high/low inside the session window (LON 03:00-08:00, NYAM 10:30-11:45, NYPM 12:30-15:30), then a close back inside within 10 minutes: enter against the break at that bar close. Exact parameters: tf=15,lb=120,rj=10. Exit: stop 40 / target 40 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) 0.094 R on 63 trades, 67% months positive; selection window 0.105 R on 159 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily -0.11; $ at $1,200 risk/trade inside JL3 five deepest DDs 14588, in 20 worst weeks 10768; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**LON R3_YM_LED_LON**  `LON-book-3`  (source: W-MF)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> ES-led catch-up: over the last 15 minutes ES (continuous) moved |r_es| > 3 bp and NQ moved less in the same direction by more than 3 bp: enter NQ with ES at that close. Window LON: LON 02:30-08:00 ET, NYAM 09:45-11:30 ET. One trade per day. (ES bar file ends 2026-10-16; DAX not available.) Exact parameters: L=15,bp=3,win=LON,src=YM. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ranked on the selection window only (2023-04..2025-10); untouched year is out-of-sample
- Untouched year: UNT (2025-11..2026-10) 0.073 R on 253 trades, 67% months positive; selection window 0.079 R on 660 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.09; $ at $1,200 risk/trade inside JL3 five deepest DDs 14098, in 20 worst weeks 24511; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYAM X4_OPEN_DRIVE_DR**  `NYAM-book-alt-1`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Opening drive DR5: drive = close(09:30 + 5 min) - open(09:30); needs |drive| >= 0.75 x trailing-20-day median 5-min opening move; wait for 1 consecutive against-drive 1-min closes then enter with the drive at the close of the first bar that closes beyond the prior bar's extreme in the drive direction (until 11:00 ET). Exact parameters: W=5,rm=0.75,pb=1. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.151 R on 158 trades, 50% months positive; selection window 0.201 R on 399 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.13; $ at $1,200 risk/trade inside JL3 five deepest DDs 29338, in 20 worst weeks 32863; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYAM X4_ORB_DIR_PULLBACK**  `NYAM-book-alt-2`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Opening-range direction + first pullback: OR = first 15 minutes from 09:30 ET; first 1-min close beyond it until 11:00 gives the direction (ctx=with: with = only if the gap sign agrees, |gap| >= 0.05 x ATR14); then enter in that direction at the close of the first bar (until 11:30) that traded back to vwap (the OR edge, or VWAP) and closed back on the trend side. Exact parameters: OR=15,lvl=vwap,ctx=with. Exit: stop 30 / target 60 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.115 R on 101 trades, 58% months positive; selection window 0.152 R on 207 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.03; $ at $1,200 risk/trade inside JL3 five deepest DDs 33427, in 20 worst weeks 3218; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYAM N2_GAP**  `NYAM-book-alt-3`  (source: W-MF)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Gap fill: at 09:34 bar close, if |gap| >= 0.15 x ATR14 (prior-14-day mean RTH range) enter with the gap (go) or against it (fill). One trade per day. Exact parameters: k=0.15,mode=fill. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.146 R on 204 trades, 83% months positive; selection window 0.050 R on 465 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily -0.06; $ at $1,200 risk/trade inside JL3 five deepest DDs 21304, in 20 worst weeks 14387; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYPM W7_POWER_HOUR_LOOSE**  `NYPM-book-alt-1`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Power-hour continuation: at (14, 59) ET if |close - 09:30 open| >= 0.3 x ATR14 (and, for filt=dvh, the close is on the same side of VWAP and the last-60-min move has the same sign) enter with the day's direction; flat 15:58. Exact parameters: t=(14, 59),k=0.3,filt=day. Exit: stop = target = clip(0.12 x ATR14, 25, 90) points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.121 R on 156 trades, 67% months positive; selection window 0.065 R on 386 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.03; $ at $1,200 risk/trade inside JL3 five deepest DDs -1549, in 20 worst weeks 10300; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**NYPM X4_RSI2_15MIN_NYPM**  `NYPM-book-alt-2`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> RSI(2) washout on 15-min closes (RSI computed from 09:30 or 02:00 start of session): RSI2 < 5 with price below session VWAP = long, RSI2 > 95 above VWAP = short; first signal in the session window. Exact parameters: tf=15,th=5. Exit: stop 60 / target 60 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.045 R on 158 trades, 58% months positive; selection window 0.031 R on 450 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily -0.09; $ at $1,200 risk/trade inside JL3 five deepest DDs 21660, in 20 worst weeks 13504; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**LON W11_SESSION_EXTREME_RSI14_LON**  `LON-book-alt-1`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Session-extreme fade: 5-min bar high (low) equals the running session high (low) with 5-min RSI(14) >= 75 (<= 100-75): fade at that bar close; windows LON 03:30-08:00, NYAM 10:30-11:45, NYPM 12:00-15:30 ET. Exact parameters: r=75. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.095 R on 138 trades, 58% months positive; selection window 0.126 R on 330 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily -0.10; $ at $1,200 risk/trade inside JL3 five deepest DDs 16286, in 20 worst weeks 10122; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**LON R3_YM_LED_LON**  `LON-book-alt-2`  (source: W-MF)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> ES-led catch-up: over the last 15 minutes ES (continuous) moved |r_es| > 3 bp and NQ moved less in the same direction by more than 3 bp: enter NQ with ES at that close. Window LON: LON 02:30-08:00 ET, NYAM 09:45-11:30 ET. One trade per day. (ES bar file ends 2026-10-16; DAX not available.) Exact parameters: L=15,bp=3,win=LON,src=YM. Exit: stop 40 / target 90 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.073 R on 253 trades, 67% months positive; selection window 0.079 R on 660 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily 0.09; $ at $1,200 risk/trade inside JL3 five deepest DDs 14098, in 20 worst weeks 24511; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

**LON M3_FAILED_BREAK_LON**  `LON-book-alt-3`  (source: W-MF)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no equivalent book (K7/P7/M7/H7 NY: raw 0.006-0.047 R) -> Failed breakout re-entry: first 1-min close beyond the prior 60-bar high/low in the session window, then a close back inside within 5 bars: enter against the break at that close. Exact parameters: lb=60,rj=5. Exit: stop 60 / target 60 points; flat at session end (LON 08:28, PRE 09:28, NYAM 11:58, NYPM 15:58 ET). Lots = round(1200/(stop x $20)), 1 to 10 (equal ~$1,200 risk); market entry at the open after the signal bar; $4.84 RT per lot. Lots: equal-risk base lot (live = max(1,floor(1.75 x base + 0.5))). Engine path: market events via mf_inject on JL3.
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: standalone 1-min screen; shifted-date controls and 30 engine controls not finished
- Trials counted / correction: 3604 cells counted; ALT ranking min(selection, untouched): PARTLY PICKED ON THE UNTOUCHED YEAR
- Untouched year: UNT (2025-11..2026-10) 0.057 R on 150 trades, 67% months positive; selection window 0.064 R on 357 trades
- Behaviour (untouched-year R, five deepest drawdowns, 20 worst weeks, stack test): standalone: corr with JL3 daily -0.06; $ at $1,200 risk/trade inside JL3 five deepest DDs 10907, in 20 worst weeks -1696; engine stack rows queued (TL3_MF sets, not landed yet)
- DS7 need: new code (event book with its own cap; market entry at signal-bar close)
- Evidence: autopilot/DS3_MAJOR_F_NEWBOOKS.md
- Caveats: 1-min screen with measured exit-kind agreement 85-91% vs engine; needs the engine stack rows and 30 date-shifted controls to be believed
- Updated: 2026-11-17T18:35Z

## Table 3. LOT VECTOR (lots per book x session)
Selection rule: trailing-6M pick, 2-week refit, prior years AMBER 15-30% / RED >30% (outputs/CLAUDE.md)
**M7 x London (live 4 lots)**  `LOT|M7|london|0`  (source: bootstrap)
- Label: **CONFIRMED**
- Today -> setting: M7 London 4 live lots (base ~2) -> M7 London session lots: 4 -> 0 (do not trade M7 in London); all other lots unchanged
- **L6M**: ulcer +15.0%; max DD -30,189 -> -23,870; worst week -15,066 -> -14,160; mean/wk base lots 20,109 -> 21,147; x1.75 live lots 37,463 -> 39,514; $4.84 19,265 -> 20,359
- **HOLD**: ulcer +11.8%; max DD -82,017 -> -67,418; worst week -36,787 -> -34,209; mean/wk base lots 9,996 -> 9,552; x1.75 live lots 19,402 -> 18,442; $4.84 9,332 -> 8,942
- **GAP**: ulcer +14.4%; max DD n/a; worst week n/a; mean/wk base lots n/a (change +1,859)
- **PRE**: ulcer +17.5%; max DD n/a; worst week n/a; mean/wk base lots n/a (change +314)
- **XP**: ulcer +5.7%; max DD n/a; worst week n/a; mean/wk base lots n/a (change +443)
- **pooled**: ulcer +11.7%; max DD -88,502 -> -76,979; worst week -38,412 -> -36,455; mean/wk base lots 8,022 -> 8,528; x1.75 live lots 15,137 -> 16,121; $4.84 7,493 -> 8,042
- Controls: 30 engine persistent-draw controls (19 valid in L6M): percentile of ulcer L6M 1.00, HOLD 0.95, GAP 0.26, PRE 0.37, X' 0.32, pooled 0.68; W44-removed variant also CONFIRMED
- Trials counted / correction: 26 engine cells counted (13 definitions x JL3/JL2), ledger CT1; no family-wide White/SPA
- Untouched year: n/a (in-sample cell test on 43 months, not walk-forward; chosen as the weakest raw cell)
- Behaviour / detail: Freed-book effect JL3: whole stack +37,989 L6M, -29,527 HOLD, +90,690 pooled (base-lot $, stack total not per week)
- DS7 need: panel setting (M7 session lot table, London = 0; same switch as M7 Asia = 0 today)
- Evidence: autopilot/DS3_CELL_TESTS.md
- Caveats: HOLD mean -445 $/wk and HOLD worst-week percentile only 0.11; on JL2 base ulcer change is only +0.7% (JL3 stack effect); half-session variants: zero 05:00-08:30 only is +12.1% L6M / +15.1% HOLD. LEAD-ASSEMBLED, owner to confirm (source: DS3_CELL_TESTS.md)
- Updated: n/a

**U7 asia x fresh**  `U7|asia|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by fresh bucket (exposure neutral): rechase:1.50;other:1.00;fresh:0.50
- **L6M**: ulcer +4.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 2,644
- **HOLD**: ulcer -4.6%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -773
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (trade-log context)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**P7 london x range_used**  `P7|london|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by range_used bucket (exposure neutral): 50-100:1.50;lt50:1.00;gt100:0.50
- **L6M**: ulcer +4.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 2,540
- **HOLD**: ulcer -37.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,266
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (HAR range forecast)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**O7 nyam x roomOWN**  `O7|nyam|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by roomOWN bucket (exposure neutral): lt30:1.50;gt60:1.00;30-60:0.50
- **L6M**: ulcer +1.1%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 311
- **HOLD**: ulcer -3.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,020
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (zone room)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 x nyam**  `K7|nyam|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 1 base / 2 live lots -> session lot table K7 nyam: base lots 1 -> 0 (live lots 2 -> 0); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**K7 x nypm**  `K7|nypm|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 2 base / 4 live lots -> session lot table K7 nypm: base lots 2 -> 0 (live lots 4 -> 0); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**M7 x london**  `M7|london|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 2 base / 4 live lots -> session lot table M7 london: base lots 2 -> 0 (live lots 4 -> 0); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**U7 x asia**  `U7|asia|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 4 base / 7 live lots -> session lot table U7 asia: base lots 4 -> 3 (live lots 7 -> 5); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**U7 x london**  `U7|london|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 4 base / 7 live lots -> session lot table U7 london: base lots 4 -> 0 (live lots 7 -> 0); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**P7 x asia**  `P7|asia|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 7 base / 12 live lots -> session lot table P7 asia: base lots 7 -> 6 (live lots 12 -> 11); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**H7 x london**  `H7|london|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 0 base / 0 live lots -> session lot table H7 london: base lots 0 -> 2 (live lots 0 -> 4); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**H7 x nyam**  `H7|nyam|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 1 base / 2 live lots -> session lot table H7 nyam: base lots 1 -> 2 (live lots 2 -> 4); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**A7 x london**  `A7|london|lots`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 0 base / 0 live lots -> session lot table A7 london: base lots 0 -> 2 (live lots 0 -> 4); vector R2A = ENGINE-LOOP-A (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -1.5%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 16,588; x1.75 live lots 31,603; $4.84 30,215
- **L3M**: ulcer -8.2%; max DD -65,865 -> -64,665; worst week -33,041 -> -41,150; mean/wk (owner scalar, base lots) 14,992; x1.75 live lots 28,222; $4.84 26,905
- **HOLD**: ulcer -52.0%; max DD -155,735 -> -98,358; worst week -72,626 -> -39,130; mean/wk (owner scalar, base lots) 11,213; x1.75 live lots 22,389; $4.84 21,309
- **GAP**: ulcer -3.8%; max DD -86,295 -> -85,137; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 7,099; x1.75 live lots 13,081; $4.84 12,424
- **PRE**: ulcer +8.4%; max DD -178,374 -> -182,978; worst week -71,328 -> -52,960; mean/wk (owner scalar, base lots) 4,710; x1.75 live lots 9,012; $4.84 8,165
- **XP**: ulcer -24.9%; max DD -136,464 -> -117,246; worst week -72,178 -> -58,193; mean/wk (owner scalar, base lots) 2,885; x1.75 live lots 5,334; $4.84 4,763
- **pooled**: ulcer -13.9%; max DD -178,374 -> -182,978; worst week -76,769 -> -71,763; mean/wk (owner scalar, base lots) 6,834; x1.75 live lots 13,058; $4.84 12,231
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: HEADLINE R2A = essentially an x0.75-style trim (untouched 2023-04..2025-10: ulcer -8%, mean -23%, 14% worse than uniform ray at same mean); first evidenced lot change = M7 London 0 (CONFIRMED w/ caveats, DS3_CELL_TESTS.md); metrics = exact JL3 (all 43 months)
- Updated: 2026-11-17T18:39Z

**A7 asia x vote**  `A7|asia|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by vote bucket (exposure neutral): with:1.50;mixed:0.50
- **L6M**: ulcer -4.6%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 555
- **HOLD**: ulcer +8.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 808
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (day vote exists in v2.0)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 nypm x er60**  `K7|nypm|size-by-env`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: x1 all buckets -> lots multiplier by er60 bucket (exposure neutral): t3:1.50;t2:1.00;t1:0.50
- **L6M**: ulcer -14.5%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,213
- **HOLD**: ulcer -17.2%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,985
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (ER ladder)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**H7 nyam x fresh**  `H7|nyam|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by fresh bucket (exposure neutral): rechase:1.50;other:1.00;fresh:0.50
- **L6M**: ulcer -16.1%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 562
- **HOLD**: ulcer +7.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -18
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (trade-log context)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 x asia**  `K7|asia|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 2 base / 4 live lots -> session lot table K7 asia: base lots 2 -> 0 (live lots 4 -> 0); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**K7 x nyam**  `K7|nyam|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 1 base / 2 live lots -> session lot table K7 nyam: base lots 1 -> 0 (live lots 2 -> 0); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**K7 x nypm**  `K7|nypm|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 2 base / 4 live lots -> session lot table K7 nypm: base lots 2 -> 0 (live lots 4 -> 0); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**M7 x london**  `M7|london|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 2 base / 4 live lots -> session lot table M7 london: base lots 2 -> 0 (live lots 4 -> 0); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**U7 x asia**  `U7|asia|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 4 base / 7 live lots -> session lot table U7 asia: base lots 4 -> 0 (live lots 7 -> 0); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**U7 x london**  `U7|london|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 4 base / 7 live lots -> session lot table U7 london: base lots 4 -> 1 (live lots 7 -> 2); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**P7 x asia**  `P7|asia|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 7 base / 12 live lots -> session lot table P7 asia: base lots 7 -> 14 (live lots 12 -> 25); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**P7 x london**  `P7|london|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 4 base / 7 live lots -> session lot table P7 london: base lots 4 -> 0 (live lots 7 -> 0); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**P7 x nyam**  `P7|nyam|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 4 base / 7 live lots -> session lot table P7 nyam: base lots 4 -> 2 (live lots 7 -> 4); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**H7 x asia**  `H7|asia|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 4 base / 7 live lots -> session lot table H7 asia: base lots 4 -> 6 (live lots 7 -> 11); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**H7 x nyam**  `H7|nyam|lots|H3_in_sample_fit`  (source: W-MA)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 1 base / 2 live lots -> session lot table H7 nyam: base lots 1 -> 0 (live lots 2 -> 0); vector H3 = INSAMPLE-F2 (all rows of the vector are one package, evaluated jointly)
- **L6M**: ulcer -17.0%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 20,363; x1.75 live lots 36,052; $4.84 34,800
- **L3M**: ulcer -13.6%; max DD -65,865 -> -51,330; worst week -33,041 -> -32,157; mean/wk (owner scalar, base lots) 12,875; x1.75 live lots 22,494; $4.84 21,330
- **HOLD**: ulcer -12.0%; max DD -155,735 -> -132,543; worst week -72,626 -> -88,981; mean/wk (owner scalar, base lots) 6,230; x1.75 live lots 11,622; $4.84 10,691
- **GAP**: ulcer -31.6%; max DD -86,295 -> -51,316; worst week -76,769 -> -37,992; mean/wk (owner scalar, base lots) 9,008; x1.75 live lots 16,388; $4.84 15,815
- **PRE**: ulcer -49.6%; max DD -178,374 -> -83,010; worst week -71,328 -> -39,230; mean/wk (owner scalar, base lots) 7,226; x1.75 live lots 12,729; $4.84 12,011
- **XP**: ulcer -15.0%; max DD -136,464 -> -102,585; worst week -72,178 -> -51,905; mean/wk (owner scalar, base lots) 3,092; x1.75 live lots 5,701; $4.84 5,201
- **pooled**: ulcer -25.6%; max DD -178,374 -> -132,543; worst week -76,769 -> -88,981; mean/wk (owner scalar, base lots) 7,353; x1.75 live lots 13,211; $4.84 12,490
- Controls: arithmetic: shuffled-null + 30 random same-size vectors (see page); exact-engine controls NOT run (additivity of the cell P&L failed on exact random vectors: median ulcer error 24%, theta 0.49)
- Trials counted / correction: 1,350+ vectors solved / WF + null; no multiple-testing correction applied (first pass)
- Untouched year: walk-forward 12m/6m trailing, hold 3 (calibrated model); see page
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting
- Evidence: autopilot/DS3_MAJOR_A_LOTS.md
- Caveats: SECONDARY: best in-sample fit, training data, proves nothing
- Updated: 2026-11-17T18:39Z

**P7 asia x atr_terc**  `P7|asia|size-by-env`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: x1 all buckets -> lots multiplier by atr_terc bucket (exposure neutral): t3:1.50;t1:1.00;t2:0.50
- **L6M**: ulcer -19.2%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 17,040
- **HOLD**: ulcer -12.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 6,746
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting / own bars (atr_rel)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 nyam x atr_terc**  `K7|nyam|size-by-env`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: x1 all buckets -> lots multiplier by atr_terc bucket (exposure neutral): t2:1.50;t3:0.50
- **L6M**: ulcer -22.0%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,074
- **HOLD**: ulcer -19.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,143
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting / own bars (atr_rel)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 asia x roomOWN**  `K7|asia|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by roomOWN bucket (exposure neutral): lt30:1.50;gt60:1.00;30-60:0.50
- **L6M**: ulcer -22.4%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 3,351
- **HOLD**: ulcer -2.0%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 3,683
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (zone room)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**P7 nyam x er60**  `P7|nyam|size-by-env`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: x1 all buckets -> lots multiplier by er60 bucket (exposure neutral): t3:1.50;t2:1.00;t1:0.50
- **L6M**: ulcer -23.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -365
- **HOLD**: ulcer -24.5%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -2,270
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (ER ladder)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**H7 asia x atr_live**  `H7|asia|size-by-env`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: x1 all buckets -> lots multiplier by atr_live bucket (exposure neutral): lt1.3:1.50;gt1.6:0.50
- **L6M**: ulcer -29.5%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 1,182
- **HOLD**: ulcer -2.3%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 97
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: existing switch (atr_rel marks 1.3/1.6)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**U7 london x vote**  `U7|london|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by vote bucket (exposure neutral): mixed:1.50;with:0.50
- **L6M**: ulcer -31.9%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -263
- **HOLD**: ulcer +14.2%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 468
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (day vote exists in v2.0)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**K7 london x roomOWN**  `K7|london|size-by-env`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: x1 all buckets -> lots multiplier by roomOWN bucket (exposure neutral): 30-60:1.50;lt30:1.00;gt60:0.50
- **L6M**: ulcer -36.3%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -1,286
- **HOLD**: ulcer -11.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 225
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (zone room)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**M7 nyam x atr_terc**  `M7|nyam|size-by-env`  (source: W-MD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: x1 all buckets -> lots multiplier by atr_terc bucket (exposure neutral): t3:1.50;t2:0.50
- **L6M**: ulcer -36.3%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 161
- **HOLD**: ulcer -14.1%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 628
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: panel setting / own bars (atr_rel)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

**M7 london x vote**  `M7|london|size-by-env`  (source: W-MD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: x1 all buckets -> lots multiplier by vote bucket (exposure neutral): mixed:1.50;with:0.50
- **L6M**: ulcer -52.8%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) -790
- **HOLD**: ulcer +34.7%; max DD n/a; worst week n/a; mean/wk (owner scalar, base lots) 372
- Controls: screen only: shifted-label null 11/23/37 and nonsense bucketings; real holds across dims at the null rate (14 of 130 vs 9%); no engine run
- Trials counted / correction: MD2: 12 dims x 15 cells = 180; best dim per cell picked on untouched ranking (inflated)
- Untouched year: frozen tilt from SEL; HOLD/L6M read untouched
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (day vote exists in v2.0)
- Evidence: autopilot/DS3_REBUILD_S3_ENV.md (W-MD sections)
- Caveats: lot rounding ignored; best dimension per cell chosen by untouched result (optimistic)
- Updated: 2026-11-17T17:48:25Z

## Table 4. BEHAVIOUR RULES (DAY-DONE, same-side loser, late entry, same-side stack)
Selection rule: trailing-6M pick, 2-week refit, prior years AMBER 15-30% / RED >30% (outputs/CLAUDE.md)
**K7 flat stop 45 (live EC_FLAT45K)**  `FLAT|K7|45`  (source: bootstrap)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: K7 flat 45 ON -> Keep K7 flat -45 ON
- **L6M**: ulcer +23.8%; max DD n/a; worst week n/a; mean/wk base lots n/a (change +570)
- **HOLD**: ulcer +1.9%; max DD n/a; worst week n/a; mean/wk base lots n/a (change -752)
- **pooled**: ulcer +5.8%; max DD n/a; worst week n/a; mean/wk base lots n/a (change -80)
- Controls: 3 persistent-trigger controls per book only (ulcer better than 3 of 3 in each window); not the 30-draw standard
- Trials counted / correction: FIRST PASS, pairs counted per page
- Untouched year: n/a
- Behaviour / detail: JL3 flat ON vs OFF: L6M mean +570 (x1.75 +997, $4.84 +558); HOLD -752 (x1.75 -1316, $4.84 -762); pooled -80 (x1.75 -140, $4.84 -91). On JL2: L6M +24.6% ulcer / +1,264, HOLD +18.5% / +105, pooled +19.3% / +709
- DS7 need: existing switch (K7 flat -45 live)
- Evidence: autopilot/DS3_FLAT_VS_BOOK.md ; autopilot/DS3_REBUILD_S5.md
- Caveats: HOLD ulcer gain is only 1.9% on JL3 with mean down 752 $/wk. LEAD-ASSEMBLED, owner to confirm (source: DS3_FLAT_VS_BOOK.md)
- Updated: n/a

**Same-side loser pause (all books)**  `SAME-SIDE-LOSER|LS_K2_M30`  (source: bootstrap)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no such rule -> After 2 consecutive same-side losers, pause that side for 30 minutes (LS_K2_M30); longer pauses (60/120 min) help HOLD (+14%/+19%) but hurt L6M
- **L6M**: ulcer +4.3%; max DD n/a; worst week n/a; mean/wk base lots n/a (change +90)
- **L3M**: ulcer +7.3%; max DD n/a; worst week n/a; mean/wk base lots n/a
- **HOLD**: ulcer +4.2%; max DD n/a; worst week n/a; mean/wk base lots n/a (change +635)
- **GAP**: ulcer +4.3%; max DD n/a; worst week n/a; mean/wk base lots n/a
- **PRE**: ulcer +4.7%; max DD n/a; worst week n/a; mean/wk base lots n/a
- **XP**: ulcer +2.1%; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: screen only (path arithmetic, no freed-book effect): percentile vs <=30 persistent draws L6M 0.73, L3M 0.80, HOLD 0.63; screen tier LEAD (post-hoc), no engine-exact controls yet
- Trials counted / correction: 30 screen configs + 6 exact picks counted; no White RC/SPA/DSR run on this family; PBO not computed
- Untouched year: TRAIN (<=2025-10) ulcer +5.2%; HOLD/L6M untouched for the 6 frozen exact picks (exact cells queued)
- Behaviour / detail: share of trades affected 2.41%
- DS7 need: new code (same-side loser pause counter per side, 30 min)
- Evidence: autopilot/DS3_MAJOR_E_AGAINST.md
- Caveats: Chosen post-hoc among 30 screen configs; the ordered vote rules do nothing (bind on 0.0-0.6% of trades). LEAD-ASSEMBLED, owner to confirm (source: DS3_MAJOR_E_AGAINST.md)
- Updated: n/a

**stack: same-side loser streak (LS_K2_M30)**  `ME-same-side-loser`  (source: W-ME)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no such rule (each book trades every signal) -> After K=2 consecutive CLOSED losers on the same side, counted STACK-WIDE over all books, within one session instance (Globex day x session asia/london/nyam/nypm; any winner resets the count; counter updated only at trade closes), block NEW entries on that side for M=30 min after the K-th loss close
- **L6M**: ulcer +4.2%; max DD -60,591 -> -57,137; worst week -31,735 -> -31,539; mean/wk (owner scalar, base lots) 20,199; x1.75 live lots 37,712; $4.84 19,380 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **L3M**: ulcer +7.0%; max DD -60,591 -> -57,137; worst week -31,735 -> -31,539; mean/wk (owner scalar, base lots) 16,639; x1.75 live lots 30,375; $4.84 15,859 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **HOLD**: ulcer +4.4%; max DD -152,332 -> -143,937; worst week -71,572 -> -66,094; mean/wk (owner scalar, base lots) 10,631; x1.75 live lots 20,584; $4.84 9,981 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **GAP**: ulcer +5.0%; max DD -83,942 -> -75,647; worst week -75,818 -> -69,362; mean/wk (owner scalar, base lots) 8,796; x1.75 live lots 15,883; $4.84 8,358 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **PRE**: ulcer +4.5%; max DD -172,602 -> -159,363; worst week -70,515 -> -70,515; mean/wk (owner scalar, base lots) 6,452; x1.75 live lots 12,344; $4.84 5,917 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **XP**: ulcer +2.0%; max DD -133,884 -> -118,141; worst week -71,105 -> -63,749; mean/wk (owner scalar, base lots) 3,172; x1.75 live lots 6,010; $4.84 2,793 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **pooled**: ulcer +4.8%; max DD -172,602 -> -159,363; worst week -75,818 -> -70,515; mean/wk (owner scalar, base lots) 8,116; x1.75 live lots 15,330; $4.84 7,598 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- Controls: screen (path arithmetic, kept trades keep outcome, freed-book effects not in) controls, valid draws {'L6M': 30, 'HOLD': 30}; tier LEAD
- Trials counted / correction: screen 30+68 configs (+6 ext features) + exact 27 cells; no multiple-testing correction beyond matched controls; selection on recents (post-hoc) for the best-available row
- Untouched year: walk-forward family pick (best TRAIN<=2025-10): LS_K2_M120 -> L6M -5.4% ulcer (fails); this row is selected on recents
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (stack-level same-side loser counter per session instance + per-side entry block with timer)
- Evidence: autopilot/DS3_MAJOR_E_AGAINST.md
- Caveats: source screen; score(min ulcer improvement L6M/L3M/HOLD)=4.2%; top 3 alternatives: LS_K2_M30 4.2, LS_K2_M20_R 2.8, LS_K2_M20 1.6
- Updated: 2026-11-17T18:25Z

**DAY-DONE conditional resume**  `DAYDONE-RESUME`  (source: W-DD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: no resume (halt to 18:00 ET) -> resume when realised + open day P&L >= trip level + 2,000 live [cell TL3_DD_JL3_R3_2000]
- **L6M**: ulcer +2.7%; max DD -30,189 -> -30,189; worst week -15,066 -> -15,066; mean/wk (owner scalar, base lots) -173; x1.75 live lots -347; $4.84 -167
- **L3M**: ulcer +1.3%; max DD -30,189 -> -30,189; worst week -15,066 -> -15,066; mean/wk (owner scalar, base lots) -566; x1.75 live lots -1,132; $4.84 -556
- **HOLD**: ulcer +0.0%; max DD -82,017 -> -82,017; worst week -36,787 -> -36,787; mean/wk (owner scalar, base lots) 128; x1.75 live lots 256; $4.84 129
- Controls: not finished (controls missing)
- Trials counted / correction: 37 settings + 14 resume cells counted; tier NOT FINISHED; selection RC/SPA/DSR/PBO not finished
- Untouched year: not finished (older months landing)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (shadow-trade ledger for R1/R2; day-scoped lot multiplier for R4/R6; open-P&L check for R3; side P&L counter for R5)
- Evidence: autopilot/DS3_DAYDONE_VARIANTS.md
- Caveats: first pass, in-sample 43 months; deltas vs the live rule (REF); beats live in L6M and HOLD
- Updated: 2026-11-17T18:23Z

**DAY-DONE setting (stack-wide)**  `DAYDONE`  (source: W-DD)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: live: >= 22 closes and day <= -4,200 until 18:00 ET reset -> G_22_3000 [cell TL3_DD_JL3_G_22_3000]
- **L6M**: ulcer +1.6%; max DD -30,189 -> -29,642; worst week -15,066 -> -14,518; mean/wk (owner scalar, base lots) 28; x1.75 live lots 56; $4.84 35
- **L3M**: ulcer +3.2%; max DD -30,189 -> -29,642; worst week -15,066 -> -14,518; mean/wk (owner scalar, base lots) 350; x1.75 live lots 701; $4.84 362
- **HOLD**: ulcer +6.3%; max DD -82,017 -> -78,034; worst week -36,787 -> -33,774; mean/wk (owner scalar, base lots) 231; x1.75 live lots 461; $4.84 234
- Controls: not finished (controls missing)
- Trials counted / correction: 37 settings + 14 resume cells counted; tier NOT FINISHED; selection RC/SPA/DSR/PBO not finished
- Untouched year: not finished (older months landing)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (V9Gate: latch/duration/threshold change)
- Evidence: autopilot/DS3_DAYDONE_VARIANTS.md
- Caveats: first pass, in-sample 43 months; deltas vs the live rule (REF); beats live in L6M and HOLD
- Updated: 2026-11-17T18:23Z

**stack risk overlay (JL3)**  `STACKRISK`  (source: W-MC)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: none (day lock + London cap only) -> overlay SS_noAsia_T4000 (SS) [cell SS_noAsia_T4000; lots removed 2.8%]
- **L6M**: ulcer +1.5%; max DD -30,189 -> -32,044; worst week -15,066 -> -16,616; mean/wk (owner scalar, base lots) 1,728; x1.75 live lots 3,401; $4.84 1,756 [basis: engine]
- **L3M**: ulcer +3.3%; max DD -30,189 -> -32,044; worst week -15,066 -> -16,616; mean/wk (owner scalar, base lots) 3,223; x1.75 live lots 6,335; $4.84 3,244 [basis: engine]
- **HOLD**: ulcer -0.2%; max DD -82,017 -> -78,616; worst week -36,787 -> -34,161; mean/wk (owner scalar, base lots) -323; x1.75 live lots -600; $4.84 -314 [basis: engine]
- **GAP**: ulcer -12.2%; max DD -41,050 -> -35,942; worst week -38,412 -> -34,350; mean/wk (owner scalar, base lots) 477; x1.75 live lots 1,045; $4.84 482 [basis: engine]
- **PRE**: ulcer -4.0%; max DD -88,502 -> -89,997; worst week -37,204 -> -34,841; mean/wk (owner scalar, base lots) -803; x1.75 live lots -1,585; $4.84 -786 [basis: engine]
- **XP**: ulcer -3.1%; max DD -70,704 -> -63,083; worst week -36,802 -> -29,905; mean/wk (owner scalar, base lots) -122; x1.75 live lots -269; $4.84 -118 [basis: engine]
- **pooled**: ulcer -3.5%; max DD -88,502 -> -89,997; worst week -38,412 -> -34,841; mean/wk (owner scalar, base lots) 12; x1.75 live lots 23; $4.84 23 [basis: engine]
- Controls: engine cell; arithmetic controls: 60 valid draws, screen tier FAIL; engine controls queued through the gate
- Trials counted / correction: 65 screen cells + 15 engine cells; White RC mean p 0.00 (leverage cells), ulcer RC p 0.49, PBO 0.524
- Untouched year: selected on 2023-04..2025-10 only; HOLD and L6M columns are untouched; rolling-12m pick is worse (pooled ulcer +9.7%, mean -9.2%)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (a stack-level trailing daily-P&L series and a lot multiplier below one base lot: 2 -> 1 live lots only)
- Evidence: autopilot/DS3_MAJOR_C_RISK.md
- Caveats: does not beat a uniform trim by more than noise; benchmark uniform trim/press row is in Table 3
- Updated: 2026-11-17T17:18:15Z

**stack: other same-side positions after a book cut (CUT_half)**  `ME-same-side-stack-after-cut`  (source: W-ME)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: live stack rule exists only for Asia full stops (50% cut of same-side positions); no rule after book cuts -> When a book closes at a LOSS through a cut line (StateCut/EarlyCut/PolicyCut, not StackCut) while >=1 other book holds a same-side position: sell floor(50%) of each such position at market (a position of 1 lot is left alone)
- **L6M**: ulcer -0.0%; max DD -60,591 -> -61,626; worst week -31,735 -> -29,790; mean/wk (owner scalar, base lots) 19,410; x1.75 live lots 36,263; $4.84 18,573 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **L3M**: ulcer -2.2%; max DD -60,591 -> -61,626; worst week -31,735 -> -29,790; mean/wk (owner scalar, base lots) 13,957; x1.75 live lots 25,457; $4.84 13,171 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **HOLD**: ulcer -5.9%; max DD -152,332 -> -153,234; worst week -71,572 -> -70,472; mean/wk (owner scalar, base lots) 9,698; x1.75 live lots 18,757; $4.84 9,033 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- Controls: ENGINE-EXACT cell vs JL3; tier NOT FINISHED
- Trials counted / correction: screen 30+68 configs (+6 ext features) + exact 27 cells; no multiple-testing correction beyond matched controls; selection on recents (post-hoc) for the best-available row
- Untouched year: n/a (not selected by fit; two a-priori cells)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (hook on a cut-line close that applies the existing StackCut partial-exit path to the other same-side positions in every session)
- Evidence: autopilot/DS3_MAJOR_E_AGAINST.md
- Caveats: no path-arithmetic screen is possible for exits; the result is exact-engine only
- Updated: 2026-11-17T18:25Z

**stack: extended-entry bucket (EXT_used_ST67)**  `ME-late-entry-size-target`  (source: W-ME)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: full lots, native target/stop at every entry -> Bucket by feature per code EXT_used_ST67 (threshold frozen on TRAIN): act = stop x0.67 with the target points unchanged, lots unchanged
- **L6M**: ulcer -1.3%; max DD -60,591 -> -58,039; worst week -31,735 -> -32,790; mean/wk (owner scalar, base lots) 19,508; x1.75 live lots 36,413; $4.84 18,682 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **L3M**: ulcer -0.8%; max DD -60,591 -> -58,039; worst week -31,735 -> -32,790; mean/wk (owner scalar, base lots) 16,704; x1.75 live lots 30,527; $4.84 15,920 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **HOLD**: ulcer +3.2%; max DD -152,332 -> -140,406; worst week -71,572 -> -66,455; mean/wk (owner scalar, base lots) 10,034; x1.75 live lots 19,555; $4.84 9,391 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- Controls: ENGINE-EXACT; tier NOT FINISHED
- Trials counted / correction: screen 30+68 configs (+6 ext features) + exact 27 cells; no multiple-testing correction beyond matched controls; selection on recents (post-hoc) for the best-available row
- Untouched year: thresholds frozen on TRAIN<=2025-10; TRAIN-best feature was used (+15.5% TRAIN, -0.4% L6M); this row is the best recent-consistent one
- Behaviour / detail: extended bucket earns more per trade (about $110 vs $60) but holds 39k of the -78k drawdown path losses; halving costs mean $/wk
- DS7 need: new code (feature at signal: distance from session open / 18:00 open in ATR5, VWAP sigma, share of typical session range used, chase count; lot/target multiplier)
- Evidence: autopilot/DS3_MAJOR_E_AGAINST.md section 2b
- Caveats: alternatives: EXT_used_TG67 -16.3, SZ_o18_atr -98.9, SZ_open_atr -98.9; target/stop pull-in cells only exist as exact runs (queued); breakeven-after-+20 not built
- Updated: 2026-11-17T18:25Z

**P7 flat stop 42 (live since 11-12)**  `FLAT|P7|42`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: P7 flat 42 ON -> Best available: keep P7 flat -42 as live, but L6M is WORSE with it on (see numbers): flag for the user to decide
- **L6M**: ulcer -27.6%; max DD n/a; worst week n/a; mean/wk base lots n/a (change -1,011)
- **HOLD**: ulcer +7.0%; max DD n/a; worst week n/a; mean/wk base lots n/a (change +532)
- **pooled**: ulcer +2.0%; max DD n/a; worst week n/a; mean/wk base lots n/a (change -259)
- Controls: 3 persistent-trigger controls only; ulcer better than 3 of 3 controls but the real effect on L6M is a worse ulcer
- Trials counted / correction: FIRST PASS
- Untouched year: n/a
- Behaviour / detail: JL3 flat ON vs OFF: L6M mean -1011 (x1.75 -1769, $4.84 -1008); HOLD +532 (x1.75 +932); pooled -259 (x1.75 -453). Stage 5 ADD_P7FLAT42: COSTS MONEY (ulcer worse, P(helps) 0.09)
- DS7 need: existing switch (P7 flat -42 live)
- Evidence: autopilot/DS3_FLAT_VS_BOOK.md ; autopilot/DS3_REBUILD_S5.md
- Caveats: Recent window is against it, older windows for it. LEAD-ASSEMBLED, owner to confirm (source: DS3_FLAT_VS_BOOK.md)
- Updated: n/a

**U7 delta_mult tighten (profit line)**  `PROFITLINE|U7|tighten`  (source: bootstrap)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: coded but INERT live (shared persistence counter cleared each winning second, DS7.cs line 1790) -> U7 delta_mult tighten, persist=5, as designed (counter fix needed)
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a (change +817)
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a (change +394)
- Controls: not run (no persistent-draw controls for these cells)
- Trials counted / correction: 12 months HOLD+L6M, JL2 base, FIRST PASS
- Untouched year: n/a
- Behaviour / detail: line adds weekly DD cut +14.6 pts HOLD / +5.2 pts L6M; verdict KEEP
- DS7 need: new code (fix the persistence counter so persist>=2 lines can fire)
- Evidence: autopilot/DS3_PROFIT_LINES_LOO.md
- Caveats: World A: as coded the line never fires live. MBO-derived delta series. LEAD-ASSEMBLED, owner to confirm (source: DS3_PROFIT_LINES_LOO.md)
- Updated: n/a

**M7 tot_rel step (profit line)**  `PROFITLINE|M7|step`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: coded but INERT live (counter bug) -> M7 tot_rel step persist=2 as designed
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a (change +792)
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a (change +619)
- Controls: not run
- Trials counted / correction: 12 months, FIRST PASS
- Untouched year: n/a
- Behaviour / detail: adds mean in both windows but deepens HOLD max DD by 7.8 pts; L6M DD cut +29.5 pts; verdict MIXED
- DS7 need: new code (counter fix)
- Evidence: autopilot/DS3_PROFIT_LINES_LOO.md
- Caveats: Mixed on drawdown. LEAD-ASSEMBLED, owner to confirm (source: DS3_PROFIT_LINES_LOO.md)
- Updated: n/a

**K7 delta_mult lock (profit line)**  `PROFITLINE|K7|lock`  (source: bootstrap)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: coded but INERT live (counter bug) -> K7 delta_mult lock persist=10 as designed: best available, COSTS MONEY in HOLD (-966 $/wk) while cutting weekly DD +11.1 pts
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a (change -96)
- **HOLD**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a (change -966)
- Controls: not run
- Trials counted / correction: 12 months, FIRST PASS
- Untouched year: n/a
- Behaviour / detail: adds weekly DD cut +11.1 pts HOLD / +21.1 pts L6M; verdict COSTS MONEY
- DS7 need: new code (counter fix)
- Evidence: autopilot/DS3_PROFIT_LINES_LOO.md
- Caveats: Mean lower in both windows. LEAD-ASSEMBLED, owner to confirm (source: DS3_PROFIT_LINES_LOO.md)
- Updated: n/a

**Stage 5 KEEP layers (all stay ON)**  `STAGE5|KEEP-layers`  (source: bootstrap)
- Label: **WEAK-BUT-POSITIVE**
- Today -> setting: live layers -> Keep ON: L2GATE (engine value not transferable, live L2 gate was void), NTZ, F3CTXCUT, ERLADDER, STACKCAP, CUTLINE_P7, SIGQ, BREADTH, BLACKOUT, CUTLINE_U7. Costs money (reference, still ON per standing rule): LOT, ADD_P7FLAT42, GIVEBACKLOCK, DAYCAPS
- **L6M**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- **pooled**: ulcer n/a; max DD n/a; worst week n/a; mean/wk base lots n/a
- Controls: BH 10% across 30 layer cells; matched random-removal controls for skip-type layers; BLACKOUT tier CONFIRMED
- Trials counted / correction: 30 layer cells, no best-of
- Untouched year: n/a (IN-SAMPLE, every layer was fitted on this history)
- Behaviour / detail: e.g. NTZ ulcer +22.6% pooled / mean -136 $/wk; STACKCAP +14.6% / -273; CUTLINE_P7 +10.2% / +621; per-layer numbers on the page
- DS7 need: existing switch (all live)
- Evidence: autopilot/DS3_REBUILD_S5.md
- Caveats: In-sample; per-layer L6M/HOLD numbers on the page. LEAD-ASSEMBLED, owner to confirm (source: DS3_REBUILD_S5.md)
- Updated: n/a

## Status block (owner files in /mnt/l2/l2vast/_deliver/)
| owner | table | rows | bad lines | last update age | state |
|--|--|--|--|--|--|
| W-S3 | 1 | 14 | 0 | 17 min | ok |
| W-MD | 1 | 31 | 0 | 59 min | ok |
| W-MB | 2 | 7 | 0 | 15 min | ok |
| W-MF | 2 | 16 | 0 | 12 min | ok |
| W-MA | 3 | 20 | 0 | 8 min | ok |
| W-MC | 4 | 2 | 0 | 90 min | ok |
| W-ME | 4 | 3 | 0 | 23 min | ok |
| W-DD | 4 | 2 | 0 | 25 min | ok |
| W-SWA | 5 | 9 | 0 | 26 min | ok |
| W-SWB | 5 | 7 | 0 | 7 min | ok |
| W-BAR | 5 | 0 | 0 | n/a | NO FILE YET |
| W-S1R | 6 | 14 | 0 | 16 min | ok |

Bootstrap (LEAD-ASSEMBLED) rows currently shown: 13 (an owner row with the same row_id replaces them).
