# DS3_MAJOR_DELIVERABLES - best settings for the user to decide (W-DL assembler; rebuilt 2026-11-17 16:47Z, every 30 min)
VERDICT (data ends 2026-10-31; FIRST PASS; every row is a BEST SETTING with its honest label; rows labelled LEAD-ASSEMBLED are copied by the assembler from existing pages and wait for the owner to confirm)

> HEADER: trials counted = per row (see each row; ledger families CT1, RB3, RB5, ME, MF1/MF2); correction = per row (BH / White RC / controls where run, else 'not run'); in-sample vs walk-forward is stated per row (untouched-year line). Labels CONFIRMED / LEAD need engine-exact persistent-draw controls (calibrated pass rule); a missing field prints 'n/a (owner has not delivered)'. Seal untouched.

## Summary (plain)
1. Table 1: 30 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 6, BEST-AVAILABLE-NOT-PROVEN 24) + 0 reference rows
2. Table 2: 23 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 3, BEST-AVAILABLE-NOT-PROVEN 20) + 0 reference rows
3. Table 3: 27 main rows (CONFIRMED 1, LEAD 0, WEAK-BUT-POSITIVE 7, BEST-AVAILABLE-NOT-PROVEN 19) + 0 reference rows
4. Table 4: 13 main rows (CONFIRMED 0, LEAD 0, WEAK-BUT-POSITIVE 5, BEST-AVAILABLE-NOT-PROVEN 8) + 0 reference rows
5. Decide first: Table 3 row 1 (M7 London 4 -> 0 lots, CONFIRMED, but HOLD mean -445 $/wk); then the P7 flat -42 question (L6M worse with it on); then whether to fund the engine runs for the unproven books. 

How to read: ulcer % is positive when the cell is better than today (lower RMS daily drawdown); max DD and worst week are base -> cell in dollars (negative numbers, closer to zero is better); mean per week is shown at base lots, at x1.75 live lots and with $4.84 round-turn commission. Live lots = max(1, floor(1.75 x base + 0.5)). Weak spots are stated on each row; GAP / PRE percentiles are often weak.

## Table 1. BRACKET TABLE (stop / target / time-stop / half-off instead of 60/58)
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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

**K7 x asia**  `K7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**K7 x london**  `K7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**K7 x nyam**  `K7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**K7 x nypm**  `K7|nypm|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**M7 x london**  `M7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59.5 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**M7 x nyam**  `M7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/59.5 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**U7 x asia**  `U7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**U7 x london**  `U7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**P7 x asia**  `P7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/58 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**P7 x london**  `P7|london|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/58 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**P7 x nyam**  `P7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/58 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**H7 x asia**  `H7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**H7 x nyam**  `H7|nyam|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

**A7 x asia**  `A7|asia|bracket`  (source: W-S3)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: 60/60 -> pending: stage 3 priority subset still landing (1 common SEL months)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: see TRIALS_LEDGER RB3
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: policy line
- Evidence: autopilot/DS3_REBUILD_S3.md; autopilot/DS3_REBUILD_S3_ENV.md
- Caveats: no data yet
- Updated: 2026-11-17T16:30:55Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

## Table 2. NEW YORK AND LONDON BOOKS
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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17 16:32

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
- Updated: 2026-11-17 16:32

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

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
- Updated: 2026-11-17T16:34Z

## Table 3. LOT VECTOR (lots per book x session)
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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

**K7 x asia**  `K7|asia|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**K7 x nyam**  `K7|nyam|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**K7 x nypm**  `K7|nypm|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**M7 x london**  `M7|london|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**U7 x asia**  `U7|asia|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**U7 x london**  `U7|london|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**P7 x asia**  `P7|asia|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**P7 x london**  `P7|london|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**P7 x nyam**  `P7|nyam|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**H7 x asia**  `H7|asia|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

**H7 x nyam**  `H7|nyam|lots`  (source: W-MA)
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
- Caveats: package vector, metrics = exact JL3 (all 43 months); NOT proven vs uniform trim/press
- Updated: 2026-11-17T16:29Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

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
- Updated: 2026-11-17T15:48:23Z

## Table 4. BEHAVIOUR RULES (DAY-DONE, same-side loser, late entry, same-side stack)
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

**stack: extended-entry bucket (SZ_o18_atr)**  `ME-late-entry-size-target`  (source: W-ME)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: full lots, native target/stop at every entry -> Feature o18_atr at the signal second (closed 1-min bars): bucket = top third of TRAIN trades (see page section 2b for the threshold); in the bucket trade lots x0.5 (round half up, min 1); no skip
- **L6M**: ulcer +11.7%; max DD -60,591 -> -50,136; worst week -31,735 -> -28,229; mean/wk (owner scalar, base lots) 17,017; x1.75 live lots 32,653; $4.84 16,243 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **L3M**: ulcer +16.1%; max DD -60,591 -> -50,136; worst week -31,735 -> -28,229; mean/wk (owner scalar, base lots) 14,139; x1.75 live lots 26,399; $4.84 13,399 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **HOLD**: ulcer +8.5%; max DD -152,332 -> -134,100; worst week -71,572 -> -59,948; mean/wk (owner scalar, base lots) 9,998; x1.75 live lots 19,466; $4.84 9,386 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **GAP**: ulcer +5.2%; max DD -83,942 -> -84,851; worst week -75,818 -> -70,700; mean/wk (owner scalar, base lots) 7,549; x1.75 live lots 13,658; $4.84 7,137 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **PRE**: ulcer +10.9%; max DD -172,602 -> -158,539; worst week -70,515 -> -59,167; mean/wk (owner scalar, base lots) 6,038; x1.75 live lots 11,579; $4.84 5,531 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **XP**: ulcer +7.1%; max DD -133,884 -> -127,345; worst week -71,105 -> -58,239; mean/wk (owner scalar, base lots) 2,553; x1.75 live lots 5,035; $4.84 2,197 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- **pooled**: ulcer +7.8%; max DD -172,602 -> -158,539; worst week -75,818 -> -70,700; mean/wk (owner scalar, base lots) 7,101; x1.75 live lots 13,654; $4.84 6,612 [basis: maxdd/worst_week/ulcer at live lots x1.75 (engine net)]
- Controls: screen only: 30 persistent random halvings per window (path arithmetic); tier FAIL
- Trials counted / correction: screen 30+68 configs (+6 ext features) + exact 0 cells; no multiple-testing correction beyond matched controls; selection on recents (post-hoc) for the best-available row
- Untouched year: thresholds frozen on TRAIN<=2025-10; TRAIN-best feature was used (+15.5% TRAIN, -0.4% L6M); this row is the best recent-consistent one
- Behaviour / detail: extended bucket earns more per trade (about $110 vs $60) but holds 39k of the -78k drawdown path losses; halving costs mean $/wk
- DS7 need: new code (feature at signal: distance from session open / 18:00 open in ATR5, VWAP sigma, share of typical session range used, chase count; lot/target multiplier)
- Evidence: autopilot/DS3_MAJOR_E_AGAINST.md section 2b
- Caveats: alternatives: SZ_open_atr -98.9, SZ_vwap_sig -98.9, SZ_chase -98.9; target/stop pull-in cells only exist as exact runs (queued); breakeven-after-+20 not built
- Updated: 2026-11-17T16:24Z

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
- Trials counted / correction: screen 30+68 configs (+6 ext features) + exact 0 cells; no multiple-testing correction beyond matched controls; selection on recents (post-hoc) for the best-available row
- Untouched year: walk-forward family pick (best TRAIN<=2025-10): LS_K2_M120 -> L6M -5.4% ulcer (fails); this row is selected on recents
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (stack-level same-side loser counter per session instance + per-side entry block with timer)
- Evidence: autopilot/DS3_MAJOR_E_AGAINST.md
- Caveats: source screen; score(min ulcer improvement L6M/L3M/HOLD)=4.2%; top 3 alternatives: LS_K2_M30 4.2, LS_K2_M20_R 2.8, LS_K2_M20 1.6
- Updated: 2026-11-17T16:24Z

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
- Updated: 2026-11-17T16:47:46Z

**DAY-DONE setting (stack-wide)**  `DAYDONE`  (source: W-DD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: live: >= 22 closes and day <= -4,200 until 18:00 ET reset -> DAY-DONE 22 / -4,200 counting open P&L (checked at entry) until reset [cell TL3_DD_JL3_BE]
- **L6M**: ulcer +0.1%; max DD -30,189 -> -30,189; worst week -15,066 -> -15,066; mean/wk (owner scalar, base lots) 18; x1.75 live lots 36; $4.84 19
- **L3M**: ulcer +0.3%; max DD -30,189 -> -30,189; worst week -15,066 -> -15,066; mean/wk (owner scalar, base lots) 186; x1.75 live lots 372; $4.84 188
- **HOLD**: ulcer -0.0%; max DD -82,017 -> -82,017; worst week -36,787 -> -36,787; mean/wk (owner scalar, base lots) -71; x1.75 live lots -188; $4.84 -71
- Controls: not finished (controls missing)
- Trials counted / correction: 37 settings + 14 resume cells counted; tier NO MATCHED CONTROLS; selection RC/SPA/DSR/PBO not finished
- Untouched year: not finished (older months landing)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (V9Gate: latch/duration/threshold change)
- Evidence: autopilot/DS3_DAYDONE_VARIANTS.md
- Caveats: first pass, in-sample 43 months; deltas vs the live rule (REF); does NOT beat the live rule in both L6M and HOLD
- Updated: 2026-11-17T16:18Z

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

**stack: other same-side positions after a book cut (CUT_half)**  `ME-same-side-stack-after-cut`  (source: W-ME)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: live stack rule exists only for Asia full stops (50% cut of same-side positions); no rule after book cuts -> When a book closes at a LOSS through a cut line (StateCut/EarlyCut/PolicyCut, not StackCut) while >=1 other book holds a same-side position: sell floor(50%) of each such position at market (a position of 1 lot is left alone)
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run yet (exact cells CUT_half / CUT_tight queued behind the engine queue)
- Trials counted / correction: screen 30+68 configs (+6 ext features) + exact 0 cells; no multiple-testing correction beyond matched controls; selection on recents (post-hoc) for the best-available row
- Untouched year: n/a (not selected by fit; two a-priori cells)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: new code (hook on a cut-line close that applies the existing StackCut partial-exit path to the other same-side positions in every session)
- Evidence: autopilot/DS3_MAJOR_E_AGAINST.md
- Caveats: no path-arithmetic screen is possible for exits; the result is exact-engine only
- Updated: 2026-11-17T16:24Z

**DAY-DONE conditional resume**  `DAYDONE-RESUME`  (source: W-DD)
- Label: **BEST-AVAILABLE-NOT-PROVEN**
- Today -> setting: no resume (halt to 18:00 ET) -> no variant landed yet
- Metrics (L6M first): n/a (owner has not delivered)
- Controls: not run
- Trials counted / correction: 37 settings + 14 resume cells; RC/SPA/DSR/PBO when all landed
- Untouched year: n/a (owner has not delivered)
- Behaviour / detail: n/a (owner has not delivered)
- DS7 need: n/a
- Evidence: autopilot/DS3_DAYDONE_VARIANTS.md
- Caveats: nothing landed
- Updated: 2026-11-17T16:18Z

## Status block (owner files in /mnt/l2/l2vast/_deliver/)
| owner | table | rows | bad lines | last update age | state |
|--|--|--|--|--|--|
| W-S3 | 1 | 14 | 0 | 17 min | ok |
| W-MD | 1 | 31 | 0 | 59 min | ok |
| W-MB | 2 | 7 | 0 | 15 min | ok |
| W-MF | 2 | 16 | 0 | 14 min | ok |
| W-MA | 3 | 11 | 0 | 18 min | ok |
| W-MC | 4 | 2 | 0 | 0 min | ok |
| W-ME | 4 | 3 | 0 | 23 min | ok |
| W-DD | 4 | 2 | 0 | 29 min | ok |

Bootstrap (LEAD-ASSEMBLED) rows currently shown: 13 (an owner row with the same row_id replaces them).
