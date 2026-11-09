# DS3_REDO_R5_CUTWAIT - T-STACK-REDO R5 (CUTWAIT / NTZ / OTE / O7) on the state base, 2026-11-09 21:08Z first version / refresh

## 0. Summary block (setting | live value | best on the state base | holds OOS? | change recommended | panel field)

All "best" values are FIRST-ORDER screens until the exact rows land (section 5); no change is recommended on screens alone.

| setting | live value | best on the state base (screen) | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| post-cut / post-stop blackout (books, minutes, side) | U7, 30 min, same side, on StateCut | N=120 same=both scope=allbooks trig=cut | placebo p 0.27/0.47, family p 1.00, WF ok | no (screen only; U7 live row changes nothing in the list) | ThL2BlackoutMins / ThL2BlackoutBooks / ThL2BlackoutSameSideOnly (post-stop blackout has no panel field) |
| blackout, single-book best (P7) | none on P7 | N=30 same=same scope=book:P7 trig=cutstop | placebo p 0.14/0.12, family p 1.00, WF ok | no | ThL2BlackoutBooks |
| NTZ action / distance (global) | Half, D 20 | N1 D=60 act=retarget | placebo p 0.30/0.18, family p 1.00, WF ok | no (UP / optimistic retarget path; exact R5_NTZ_1 decides) | NtzAction / NtzDistancePts |
| Kijun line (timeframe, period, own D / action) | Kijun 1h, 26 periods, D 20 Half | N3 Dk=40 act=skip p=52 tf=4h | placebo p 0.02/0.17, family p 1.00, WF ok | no | none (Kijun definition is in code, not a panel field) |
| OTE-62 band / D / action / max minutes | .62, D 30, B73, 60 | {"D": 10, "act": "WT", "f": 0.65, "maxmin": 15} | placebo p 0.06/0.15, family p 1.00, WF fails | no | OteMode / OteAction / OteDistancePts / OteMaxMinutes |
| O7 opening drive (arm, trigger, window, stop/target, time exit, lots) | 0.5 x median5, pb1, before 09:45, 40/90, 16:00, 1 lot | lots=1.0 rm=0.5 stop=30 texit=1400 tgt=90 trig=pb1 wend=945 | placebo p 0.18/0.58, family p 1.00, WF ok | no (stack effect < 2 points; O7-only drawdown cells listed) | O7Enabled / O7Qty (the rest is hardcoded in OpenDriveEngine) |
STATUS: post-hoc, Shadow only, no PASS claims, PRE-PROOF (entry match < .85), ROLL-EXCL (33 roll-artifact trades weight 0). Base S1b-COMB (live D7 v1.5 state cut, Q1-A, HALF D20 + OTE-62 B73 D30); carrying week dropped from MEANS only, maxDD / worst-20 / Ulcer on all weeks; windows as of 2026-11-09, trade lists end 2026-10-30. **Every cell below is a FIRST-ORDER SCREEN unless the exact column says EXACT**; exact runs go through the SZ-CORE queue (prefix R5_, tier 2, hooks code/th_r5/r5_hooks.py). Prereg autopilot/R5_PREREG.md (sha in DECISIONS.md). Standing rule: every layer stays ON; the live setting is a reference row; "no rule" never a verdict. Held-out live week = frozen file only; 11-08/09 night v1.5 cuts are bug exits and live NQ cuts are not ground truth, so no live-cut input is used (the live week is used for stop-triggered blackout and O7 only, see section 6).
## 1. Blackouts (post-cut / post-stop; all books)
First-order skip table processed in signal order (a skipped trade does not trigger). **Live reference** = U7, 30 min, same side, on the state cut: in the base list it removes NOTHING (U7 has 0 same-side signals within 30 min of a StateCut: Supertrend 10-min does not re-signal that fast), so the live row equals the base to the dollar by construction (not a testing defect: no signal falls in the window); the engine base itself carries NO blackout (the old per-print ThL2Cut that set it is neutralised), the exact hook row R5_BO_LIVE checks the reconstruction. 402 cells scored; purged monthly WF of the pick (lowest trailing maxDD): WF maxDD cut vs live 28.9%, picks differ from live in 34 of 34 months, WF ok = True.
| cell | n changed | cut L1M/L3M | prior (PRE tolerant) | maxDD cut % L6M/HOLD/PRE/X' | equal-mean cut % L6M/PRE/X' | w20 L6M cell/ref | d mean $/wk L6M | placebo p L6M/PRE | family p | label |
|---|---|---|---|---|---|---|---|---|---|---|
| N=120 same=both scope=allbooks trig=cut | 5437 | 27/27 | OK-PRIOR (PRE deeper -30%, allow 25%, WF2w 66%, d mean -832) | 27/-17/30/-46 | 38/40/-26 | 223005/165224 | 3811 | 0.27/0.47 | 1.00 | LEAD PRE-PROOF |
| N=120 same=both scope=allbooks trig=cutstop | 7137 | 29/29 | OK-PRIOR (PRE deeper -36%, allow 25%, WF2w 66%, d mean -407) | 29/-27/36/-27 | 36/42/-14 | 212092/165224 | 2516 | 0.28/0.38 | 1.00 | LEAD PRE-PROOF |
| N=45 same=both scope=allbooks trig=cutstop | 4768 | 45/25 | OK-PRIOR (PRE deeper 14%, allow 25%, WF2w 66%, d mean -483) | 25/-66/-14/-61 | 26/-13/-59 | 228624/165224 | 387 | 0.19/0.98 | 1.00 | no |
| N=30 same=same scope=book:P7 trig=cutstop | 401 | 20/9 | OK-PRIOR (PRE deeper -18%, allow 19%, WF2w 66%, d mean 692) | 9/4/18/2 | 22/29/16 | 231958/165224 | 3881 | 0.14/0.12 | 1.00 | LEAD PRE-PROOF |
| N=45 same=both scope=allbooks trig=stop | 1675 | 23/20 | OK-PRIOR (PRE deeper -6%, allow 25%, WF2w 66%, d mean 897) | 20/6/6/6 | 22/8/8 | 176877/165224 | 609 | 0.03/0.58 | 1.00 | LEAD PRE-PROOF |
**Bi-weekly WF (primary OOS; trailing 26 wk -> next 2 wk, 7-day embargo, 74 refits from 2024-01):** the pick differs from live in 74 refits; OOS maxDD 102855 vs live 140288 (cut 27%), OOS mean delta -3367 $/wk, switched picks beat live in 27 of 74 switched refits. Pick for the next refit (2026-11-22): 34d1e3c7f657. Caveat: the pick rule is lowest trailing maxDD only, so it prefers whichever cell removes the most exposure; read the OOS mean delta beside the cut.

Best cell per scope (equal-mean score = min of L6M and PRE equal-mean cut):

| scope | cell | cut % L6M/HOLD/PRE/X' | equal-mean L6M/PRE/X' | d mean L6M | label |
|---|---|---|---|---|---|
| allbooks | N=120 same=both scope=allbooks trig=cut | 27/-17/30/-46 | 38/40/-26 | 3811 | LEAD PRE-PROOF |
| book:A7 | N=15 same=both scope=book:A7 trig=cutstop | 2/0/0/-1 | 3/2/1 | 404 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| book:H7 | N=90 same=same scope=book:H7 trig=cut | 1/0/1/0 | 1/1/0 | 89 | LEAD PRE-PROOF |
| book:K7 | N=90 same=both scope=book:K7 trig=cutstop | 4/-7/11/8 | 4/11/8 | 44 | LEAD PRE-PROOF |
| book:M7 | N=90 same=both scope=book:M7 trig=cutstop | 6/8/8/11 | 10/12/14 | 992 | LEAD PRE-PROOF |
| book:P7 | N=30 same=same scope=book:P7 trig=cutstop | 9/4/18/2 | 22/29/16 | 3881 | LEAD PRE-PROOF |
| book:U7 | N=60 same=both scope=book:U7 trig=cut | 0/-5/0/0 | 1/0/0 | 118 | no |
| stack | N=45 same=same scope=stack trig=cutstop | 11/29/21/-0 | 19/28/9 | 2110 | LEAD PRE-PROOF |

Per book x session (top-3 cells, only scopes with >= 15 blocked trades; maxDD cut % and d mean $/wk L6M, all-weeks maxDD):

| cell | scope | n blocked | cut L6M/PRE/X' | d mean L6M | equal-mean cut L6M/PRE/X' |
|---|---|---|---|---|---|
| N=120 same=both scope=allbooks trig=cut | KB 0 | 465 | 9/9/6/-0 | 8 | 9/7/0 |
| N=120 same=both scope=allbooks trig=cut | KB 1 | 519 | 18/21/33/6 | -393 | -/-/- |
| N=120 same=both scope=allbooks trig=cut | KB 3 | 509 | 28/34/-1/-9 | 282 | -/-/- |
| N=120 same=both scope=allbooks trig=cut | KB 4 | 425 | 48/45/45/1 | 54 | 52/49/8 |
| N=120 same=both scope=allbooks trig=cut | PE 0 | 645 | 34/-23/-13/-73 | -696 | 31/-19/-83 |
| N=120 same=both scope=allbooks trig=cut | PE 1 | 695 | 46/46/21/-46 | 2707 | 76/65/36 |
| N=120 same=both scope=allbooks trig=cut | PE 3 | 355 | -9/7/-7/-19 | 50 | -/-/- |
| N=120 same=both scope=allbooks trig=cut | HM 0 | 27 | 3/10/27/0 | -143 | -3/23/-6 |
| N=120 same=both scope=allbooks trig=cut | HM 3 | 24 | -0/17/24/-7 | 47 | 10/31/3 |
| N=120 same=both scope=allbooks trig=cut | MV 1 | 947 | 41/49/-1/-68 | 822 | -/-/- |
| N=120 same=both scope=allbooks trig=cut | MV 3 | 759 | 33/61/21/-35 | -162 | -3/-22/-109 |
| N=120 same=both scope=allbooks trig=cut | PB 0 | 46 | 35/-40/-6/0 | 364 | 54/26/30 |
| N=120 same=both scope=allbooks trig=cutstop | KB 0 | 751 | 6/6/18/24 | -392 | -19/-4/4 |
| N=120 same=both scope=allbooks trig=cutstop | KB 1 | 786 | -19/-7/45/23 | 213 | -/-/- |
| N=120 same=both scope=allbooks trig=cutstop | KB 3 | 783 | 54/37/8/66 | 285 | -/-/- |
| N=120 same=both scope=allbooks trig=cutstop | KB 4 | 686 | 73/50/57/42 | 146 | 78/64/51 |
| N=120 same=both scope=allbooks trig=cutstop | PE 0 | 693 | 37/-23/11/-60 | -321 | 35/8/-64 |
| N=120 same=both scope=allbooks trig=cutstop | PE 1 | 732 | 46/46/16/-30 | 2478 | 79/66/48 |
| N=120 same=both scope=allbooks trig=cutstop | PE 3 | 469 | 9/26/-11/-9 | 589 | -/-/- |
| N=120 same=both scope=allbooks trig=cutstop | SM 0 | 52 | -12/-15/0/0 | -630 | -39/-25/-25 |
| N=120 same=both scope=allbooks trig=cutstop | SM 1 | 88 | -16/-36/12/-15 | -178 | -86/-42/-84 |
| N=120 same=both scope=allbooks trig=cutstop | HM 0 | 38 | 3/10/35/0 | -228 | -6/29/-10 |
| N=120 same=both scope=allbooks trig=cutstop | HM 3 | 58 | -0/18/35/22 | 44 | 8/41/28 |
| N=120 same=both scope=allbooks trig=cutstop | MV 1 | 1016 | 43/51/-0/-81 | 501 | -/-/- |
| N=120 same=both scope=allbooks trig=cutstop | MV 3 | 853 | 25/63/-11/3 | -225 | -47/-117/-89 |
| N=120 same=both scope=allbooks trig=cutstop | PB 0 | 132 | 53/-89/-19/0 | 422 | 72/29/40 |
| N=45 same=both scope=allbooks trig=cutstop | KB 0 | 533 | -3/-3/-10/15 | -471 | -23/-30/-1 |
| N=45 same=both scope=allbooks trig=cutstop | KB 1 | 562 | -0/9/26/8 | -436 | -/-/- |
| N=45 same=both scope=allbooks trig=cutstop | KB 3 | 505 | 40/24/10/63 | 180 | -/-/- |
| N=45 same=both scope=allbooks trig=cutstop | KB 4 | 456 | 26/12/53/25 | 26 | 28/55/28 |
| N=45 same=both scope=allbooks trig=cutstop | PE 0 | 478 | 30/-47/-19/-40 | -1633 | 21/-33/-57 |
| N=45 same=both scope=allbooks trig=cutstop | PE 1 | 523 | 41/13/-24/-94 | 30 | 42/-21/-90 |
| N=45 same=both scope=allbooks trig=cutstop | PE 3 | 291 | 34/59/38/-12 | 913 | -/-/- |
| N=45 same=both scope=allbooks trig=cutstop | SM 0 | 36 | 19/-39/0/0 | -49 | 17/-2/-2 |
| N=45 same=both scope=allbooks trig=cutstop | SM 1 | 53 | 1/1/-2/-5 | -435 | -69/-74/-79 |
| N=45 same=both scope=allbooks trig=cutstop | HM 0 | 18 | 22/7/26/0 | -2 | 22/26/-0 |
| N=45 same=both scope=allbooks trig=cutstop | HM 3 | 28 | -0/35/26/8 | 21 | 4/28/12 |
| N=45 same=both scope=allbooks trig=cutstop | MV 1 | 677 | 39/8/-14/-43 | 806 | -/-/- |
| N=45 same=both scope=allbooks trig=cutstop | MV 3 | 535 | 59/60/15/3 | 251 | 96/92/91 |
| N=45 same=both scope=allbooks trig=cutstop | PB 0 | 73 | 8/-99/-22/0 | 192 | 23/-1/17 |

## 2. No-trade set / Kijun NTZ (live: 8 lines, D 20, Half)
First-order: line states from a replay of the live PoiSet on 1-min bars (agreement with the half inferred from base lots: 90% overall, precision .93, recall .53 because A06/B02 halves are in the same lot signature), lots chain per trade; retarget = target to the line minus 2 ticks via the 1-s print MFE before the base exit (optimistic: touch = fill, no queue). Cells with M > 1 (live half undone) are UP rows (report only). WF of the pick: maxDD cut vs live 5.0%, WF ok = True. REF_REPLAY (live rule through the model) must be 0 everywhere = model self-check.
| cell | n changed | cut L1M/L3M | prior (PRE tolerant) | maxDD cut % L6M/HOLD/PRE/X' | equal-mean cut % L6M/PRE/X' | w20 L6M cell/ref | d mean $/wk L6M | placebo p L6M/PRE | family p | label |
|---|---|---|---|---|---|---|---|---|---|---|
| N1 D=60 act=retarget | 843 | 22/22 | OK-PRIOR (PRE deeper -18%, allow 15%, WF2w 50%, d mean -682) | 20/26/18/22 | 22/20/24 | 184833/165224 | 576 | 0.30/0.18 | 1.00 | UP (report, never promoted) |
| N1 D=50 act=retarget | 843 | 22/23 | OK-PRIOR (PRE deeper -17%, allow 15%, WF2w 50%, d mean -350) | 20/25/17/25 | 20/17/25 | 169922/165224 | -6 | 0.22/0.29 | 1.00 | UP (report, never promoted) |
| N1 D=40 act=retarget | 843 | 17/17 | OK-PRIOR (PRE deeper -16%, allow 15%, WF2w 50%, d mean -122) | 17/25/16/25 | 16/15/24 | 153437/165224 | -313 | 0.31/0.18 | 1.00 | UP (report, never promoted) |
| N3 Dk=60 act=retarget p=26 tf=1h | 214 | 8/8 | OK-PRIOR (PRE deeper 3%, allow 15%, WF2w 50%, d mean -562) | 8/0/-3/-0 | 10/-1/2 | 204657/165224 | 551 | 0.18/0.72 | 1.00 | UP (report, never promoted) |
| N3 Dk=60 act=retarget p=52 tf=30m | 205 | 7/7 | RECENT-ONLY (PRE deeper 3%, allow 15%, WF2w 50%, d mean -1263) | 7/0/-3/2 | 9/0/5 | 213784/165224 | 754 | 0.24/0.72 | 1.00 | UP (report, never promoted) |
**Bi-weekly WF (primary OOS; trailing 26 wk -> next 2 wk, 7-day embargo, 74 refits from 2024-01):** the pick differs from live in 74 refits; OOS maxDD 136024 vs live 140288 (cut 3%), OOS mean delta -785 $/wk, switched picks beat live in 34 of 74 switched refits. Pick for the next refit (2026-11-22): 4fb9ccee5b03. Caveat: the pick rule is lowest trailing maxDD only, so it prefers whichever cell removes the most exposure; read the OOS mean delta beside the cut.


By family (best by equal-mean score): N1 global D/action, N2 Kijun substitution, N3 Kijun own D/action

| family | best cell | cut % L6M/HOLD/PRE/X' | equal-mean L6M/PRE/X' | d mean L6M | label |
|---|---|---|---|---|---|
| N1 | N1 D=60 act=retarget | 20/26/18/22 | 22/20/24 | 576 | UP (report, never promoted) |
| N2 | N2 D=20 act=half p=52 tf=30m | 0/0/0/0 | 1/1/1 | 237 | UP (report, never promoted) |
| N3 | N3 Dk=40 act=skip p=52 tf=4h | 6/0/5/-13 | 9/8/-10 | 733 | UP (report, never promoted) |

Per book x session for the top-3 NTZ cells (>= 15 changed trades; cut % L6M/HOLD/PRE/X' on that scope):

| cell | scope | n changed | cut L6M/HOLD/PRE/X' | d mean L6M | equal-mean L6M/PRE/X' |
|---|---|---|---|---|---|
| N1 D=60 act=retarget | KB s0 | 877 | 12/12/-9/29 | -776 | -25/-54/0 |
| N1 D=60 act=retarget | KB s1 | 517 | 15/13/14/17 | -11 | 2/0/4 |
| N1 D=60 act=retarget | KB s3 | 477 | 16/35/-12/46 | -154 | -/-/- |
| N1 D=60 act=retarget | KB s4 | 336 | 54/-4/31/28 | -41 | 52/29/26 |
| N1 D=60 act=retarget | PE s0 | 732 | 10/13/-16/-0 | -779 | 5/-23/-6 |
| N1 D=60 act=retarget | PE s1 | 424 | 29/29/-8/21 | 224 | 41/9/33 |
| N1 D=60 act=retarget | PE s3 | 290 | -8/-3/-11/-22 | -316 | -/-/- |
| N1 D=60 act=retarget | SM s0 | 330 | -2/7/-0/13 | 296 | 6/8/21 |
| N1 D=60 act=retarget | SM s1 | 248 | 0/-22/9/-23 | 212 | 44/49/31 |
| N1 D=60 act=retarget | HM s0 | 274 | 41/-21/20/35 | -279 | 33/10/27 |
| N1 D=60 act=retarget | HM s3 | 106 | -0/10/15/-8 | -24 | -4/11/-12 |
| N1 D=60 act=retarget | MV s1 | 770 | -8/0/18/4 | 6 | -/-/- |
| N1 D=60 act=retarget | MV s3 | 368 | 10/2/-5/-7 | 65 | 33/23/21 |
| N1 D=60 act=retarget | PB s0 | 409 | 15/-5/-4/45 | -352 | -30/-58/16 |
| N1 D=60 act=retarget | OD s3 | 110 | 0/0/-2/-2 | -68 | -21/-24/-23 |
| N1 D=50 act=retarget | KB s0 | 776 | 12/12/-9/29 | -713 | -21/-49/3 |
| N1 D=50 act=retarget | KB s1 | 462 | 16/14/14/17 | 9 | 25/23/26 |
| N1 D=50 act=retarget | KB s3 | 416 | 17/31/-12/47 | -133 | -/-/- |
| N1 D=50 act=retarget | KB s4 | 278 | 54/-2/31/19 | -24 | 53/30/17 |
| N1 D=50 act=retarget | PE s0 | 613 | 10/13/-15/3 | -717 | 5/-21/-2 |
| N1 D=50 act=retarget | PE s1 | 351 | 9/9/-2/21 | -324 | -26/-43/-11 |
| N1 D=50 act=retarget | PE s3 | 239 | -4/1/-11/-21 | -203 | -/-/- |
| N1 D=50 act=retarget | SM s0 | 292 | -2/7/-0/13 | 150 | 2/4/17 |
| N1 D=50 act=retarget | SM s1 | 223 | 0/-22/9/-23 | 233 | 47/51/34 |
| N1 D=50 act=retarget | HM s0 | 253 | 41/-20/20/35 | -261 | 34/11/28 |
| N1 D=50 act=retarget | HM s3 | 99 | -0/10/15/-8 | -24 | -4/12/-12 |
| N1 D=50 act=retarget | MV s1 | 679 | -19/-8/20/8 | -142 | -/-/- |
| N1 D=50 act=retarget | MV s3 | 312 | 11/4/-5/-4 | 75 | 37/26/27 |
| N1 D=50 act=retarget | PB s0 | 366 | 15/-2/-4/45 | -319 | -23/-50/20 |
| N1 D=50 act=retarget | OD s3 | 90 | 0/0/-2/-4 | -33 | -17/-20/-22 |
| N1 D=40 act=retarget | KB s0 | 645 | 10/10/-7/31 | -632 | -18/-41/10 |
| N1 D=40 act=retarget | KB s1 | 385 | 19/18/12/21 | 91 | 63/59/63 |
| N1 D=40 act=retarget | KB s3 | 355 | 19/31/-23/49 | -179 | -/-/- |
| N1 D=40 act=retarget | KB s4 | 220 | 54/2/31/21 | -200 | 47/20/9 |
| N1 D=40 act=retarget | PE s0 | 505 | -15/-11/-15/-3 | -1280 | -26/-26/-13 |
| N1 D=40 act=retarget | PE s1 | 293 | 9/9/-7/21 | -65 | 4/-13/16 |
| N1 D=40 act=retarget | PE s3 | 195 | -1/1/-11/-23 | -87 | -/-/- |
| N1 D=40 act=retarget | SM s0 | 245 | -2/7/10/13 | 186 | 3/15/18 |
| N1 D=40 act=retarget | SM s1 | 199 | 0/-22/9/-27 | 233 | 47/51/32 |
| N1 D=40 act=retarget | HM s0 | 216 | 41/-20/22/36 | -356 | 31/10/26 |
| N1 D=40 act=retarget | HM s3 | 83 | -0/10/15/-5 | -24 | -4/12/-10 |
| N1 D=40 act=retarget | MV s1 | 579 | -13/-1/22/13 | -333 | -/-/- |
| N1 D=40 act=retarget | MV s3 | 267 | 16/0/-6/-1 | 38 | 30/12/16 |
| N1 D=40 act=retarget | PB s0 | 295 | -1/-2/-4/51 | -365 | -57/-61/24 |
| N1 D=40 act=retarget | OD s3 | 65 | 0/0/-2/-4 | 0 | 0/-2/-4 |

## 3. OTE-62 (live: .62 line, D 30, B73 70/30, no max minutes for the reserve)
First-order via a mini bracket simulator on 1-s print extremes (stop at the signal level -60, target = average fill +60 re-based after the add, base non-bracket exits kept); variant minus live-state delta added to the base P&L only on trades whose OTE state changes. WF of the pick: cut vs live -5.6%, WF ok = False.
| cell | n changed | cut L1M/L3M | prior (PRE tolerant) | maxDD cut % L6M/HOLD/PRE/X' | equal-mean cut % L6M/PRE/X' | w20 L6M cell/ref | d mean $/wk L6M | placebo p L6M/PRE | family p | label |
|---|---|---|---|---|---|---|---|---|---|---|
| {"D": 10, "act": "WT", "f": 0.65, "maxmin": 15} | 1239 | 6/3 | OK-PRIOR (PRE deeper -4%, allow 15%, WF2w 43%, d mean -98) | 3/0/4/-11 | 6/7/-8 | 172275/165224 | 688 | 0.06/0.15 | 1.00 | LEAD PRE-PROOF |
| {"D": 50, "act": "B73", "f": 0.68, "maxmin": 0} | 1844 | 3/3 | OK-PRIOR (PRE deeper -3%, allow 15%, WF2w 43%, d mean 70) | 3/1/3/1 | 4/4/2 | 151148/165224 | 279 | 0.02/0.15 | 1.00 | LEAD PRE-PROOF |
| {"D": 30, "act": "WT", "f": 0.6, "maxmin": 15} | 1261 | 3/1 | OK-PRIOR (PRE deeper 4%, allow 15%, WF2w 43%, d mean -320) | 1/3/-4/9 | 3/-2/10 | 167504/165224 | 456 | 0.16/0.63 | 1.00 | no |
| {"D": 50, "act": "B73", "f": 0.72, "maxmin": 0} | 2080 | 4/2 | OK-PRIOR (PRE deeper 4%, allow 15%, WF2w 43%, d mean -99) | 2/-0/-4/-2 | 2/-3/-2 | 157021/165224 | 176 | 0.10/0.94 | 1.00 | no |
| {"D": 40, "act": "B73", "f": 0.72, "maxmin": 0} | 1953 | 4/2 | OK-PRIOR (PRE deeper 4%, allow 15%, WF2w 43%, d mean -16) | 2/-0/-4/-3 | 2/-4/-2 | 156327/165224 | 149 | 0.07/0.97 | 1.00 | no |
**Bi-weekly WF (primary OOS; trailing 26 wk -> next 2 wk, 7-day embargo, 74 refits from 2024-01):** the pick differs from live in 74 refits; OOS maxDD 132670 vs live 140288 (cut 5%), OOS mean delta -846 $/wk, switched picks beat live in 30 of 74 switched refits. Pick for the next refit (2026-11-22): 3d75c2cebd75. Caveat: the pick rule is lowest trailing maxDD only, so it prefers whichever cell removes the most exposure; read the OOS mean delta beside the cut.


B73 vs WT (best by equal-mean score):

| action | best cell | cut % L6M/HOLD/PRE/X' | equal-mean | d mean L6M | label |
|---|---|---|---|---|---|
| B73 | {"D": 50, "act": "B73", "f": 0.68, "maxmin": 0} | 3/1/3/1 | 4/4/2 | 279 | LEAD PRE-PROOF |
| WT | {"D": 10, "act": "WT", "f": 0.65, "maxmin": 15} | 3/0/4/-11 | 6/7/-8 | 688 | LEAD PRE-PROOF |

## 4. O7 opening drive (separate book, own simulator on the state base)
Own 1-s simulator (state cut O7 arm 25 / mult 20 / win 10 / pers 10, give-back lock, entry slip +.25, stop fill -1), calibration vs the engine O7 list on 480 matched days: corr .95, P&L 82.7k vs 81.8k (exit types match 88%). Stack = S1b-COMB without O7 + the cell list; O7 is ~1 lot so the STACK maxDD moves by < 2 points for every cell: rank by the O7-ONLY columns too. Equal-$-risk rows (exit cells with lots x 40/stop) vs equal-lots rows (`exit_eqlots`). WF of the pick on the stack: cut 0.6%, ok = True. Own-sim live stack mean L6M 23038 vs engine stack 22948 $/wk (own sim O7 is better than the engine O7 by that margin; all variants are compared with the own-sim live row).
Top-5 on the stack (drawdown first), with O7-alone L6M mean/maxDD and PRE/X' maxDD:

| cell | ntr | stack cut % L6M/HOLD/PRE/X' | equal-mean | O7 alone mean L6M / dd L6M / dd PRE / dd X' (live: 271 / 6683 / 2942 / 13598) | placebo p | family p | label |
|---|---|---|---|---|---|---|---|
| lots=1.0 rm=0.5 stop=30 texit=1400 tgt=90 trig=pb1 wend=945 | 498 | 1/2/-3/2 | 1/-2/3 | 693 / 7607 / 8988 / 13847 | 0.18/0.58 | 1.00 | no |
| lots=1.0 rm=0.5 stop=30 texit=1600 tgt=75 trig=pb1 wend=945 | 498 | 0/3/-3/0 | 1/-2/1 | 708 / 6584 / 11095 / 13778 | 0.28/0.52 | 1.00 | no |
| lots=1.0 rm=0.35 stop=40 texit=1600 tgt=90 trig=imm wend=942 | 614 | 0/-4/2/4 | 1/2/4 | 506 / 5342 / 10512 / 9677 | 0.21/0.61 | 1.00 | LEAD PRE-PROOF |
| lots=1.0 rm=0.5 stop=30 texit=1500 tgt=120 trig=pb1 wend=945 | 498 | 1/-0/-3/3 | 1/-3/3 | 511 / 7863 / 8826 / 13157 | 0.24/0.47 | 1.00 | no |
| lots=1.0 rm=0.5 stop=30 texit=1200 tgt=60 trig=pb1 wend=945 | 498 | 0/1/-3/2 | 1/-2/3 | 598 / 6984 / 7577 / 11455 | 0.13/0.47 | 1.00 | no |
**Bi-weekly WF (primary OOS; trailing 26 wk -> next 2 wk, 7-day embargo, 74 refits from 2024-01):** the pick differs from live in 74 refits; OOS maxDD 138338 vs live 139182 (cut 1%), OOS mean delta 500 $/wk, switched picks beat live in 42 of 74 switched refits. Pick for the next refit (2026-11-22): 6df4f6200fea. Caveat: the pick rule is lowest trailing maxDD only, so it prefers whichever cell removes the most exposure; read the OOS mean delta beside the cut.


Top-5 by O7-alone L6M maxDD gain at equal-or-better L6M mean:

| cell | O7 dd L6M cut % | O7 mean L6M | O7 dd PRE | O7 dd X' |
|---|---|---|---|---|
| lots=1.0 rm=1.0 stop=40 texit=1600 tgt=90 trig=imm wend=950 | 34 | 314 | 7180 | 4548 |
| lots=1.0 rm=1.0 stop=40 texit=1600 tgt=90 trig=imm wend=1000 | 34 | 314 | 7180 | 4548 |
| lots=1.0 rm=1.0 stop=40 texit=1600 tgt=90 trig=imm wend=942 | 34 | 314 | 7180 | 4548 |
| lots=1.0 rm=1.0 stop=40 texit=1600 tgt=90 trig=imm wend=945 | 34 | 314 | 7180 | 4548 |
| lots=1.0 rm=0.5 stop=35 texit=1600 tgt=60 trig=pb1 wend=945 | 30 | 412 | 6908 | 11251 |

## 6. Old vs new (previously published cells, base-change proof in SZ_BASE_PROOF.md)
Base change: old DS3 engine = per-print TH-L2 cut on 54-57% of exits, 1-min H7, library thinning, optimistic fills; S1b-COMB = tick engine with the 1-s state cut (38% of exits, stops 3% -> 14%, Q1-A L6M maxDD 105k -> 82k, PRE 88k -> 140k). Nothing here can be identical to the old page to the dollar: units differ (old = per-book $/wk vs hold-to-bracket, new = stack $/wk and stack maxDD), so the table pairs the old best-PRE cell with the nearest new cell (same book, same side, same N; trigger = StateCut).

| book | old CUTWAIT best-PRE cell (old base) | old PRE $/wk | old verdict | new cell (state base) | new cut % L6M/PRE/X' | new d mean PRE $/wk (stack) | new label |
|---|---|---|---|---|---|---|---|
| H7 | HM x30 N10 any | 3250 | DEAD | N=10 same=both scope=book:H7 trig=cut | 0/0/0/0 | 0 | no |
| K7 | KB x25 N15 same | -4868 | DEAD | N=15 same=same scope=book:K7 trig=cut | -3/-2/4/-2 | 23 | no |
| U7 | SM x25 N60 same | -1966 | DEAD | not in grid (0 trades blocked: no U7 signal falls in the window, effect nil) | | | |
| M7 | MV x30 N60 any | -3203 | DEAD | N=60 same=both scope=book:M7 trig=cut | 5/9/-3/1 | -416 | no |
| P7 | PE x30 N30 same | 239 | DEAD | N=30 same=same scope=book:P7 trig=cut | 5/-6/21/0 | -18 | LEAD PRE-PROOF |
| A7 | PB x30 N30 any | 5821 | DEAD | N=30 same=both scope=book:A7 trig=cut | 2/0/0/0 | 0 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |

Zone-as-target (DS3_B8_ZONE_TARGET_SHIPPED, old V13X): ALL8 rt100 cut L6M/PRE/X' -11/-9/-34 %% (worse) and rt7030 -19/+11/-11; new first-order retarget (N1 D 40/50/60, all 8 lines, lots restored, 1-s path) +17..20/+16..18/+22..25 %% with UP exposure; old and new SIGNS DISAGREE, so the retarget verdict is the exact rows (R5_NTZ_1 vs R5_NTZ_LIVE). B73 ordering note (exit before the add fill): the state-base engine cancels the 30% reserve when the position exits (l2_pump "trade is exiting"), so the old orphan-add behaviour is not in the base; OTE cells here inherit that. O7: old approximations (ZL-1 PB7-on-NY-AM, engine PB-on-NY-AM) are SUPERSEDED by the user answer of 11-04; the live cell is the reference and all O7 variants are measured against the own-sim live row.

## 7. Control bases (NOCUT, UNIF): the same top cells re-scored (first-order, params matched)

| layer | cell | COMB cut L6M/HOLD/PRE/X' | NOCUT cut L6M/HOLD/PRE/X' | UNIF cut L6M/HOLD/PRE/X' |
|---|---|---|---|---|
| blackout | N=120 same=both scope=allbooks trig=cut | 27/-17/30/-46 | pending | 37/23/28/0 |
| blackout | N=120 same=both scope=allbooks trig=cutstop | 29/-27/36/-27 | 17/17/40/-27 | 54/11/39/-27 |
| blackout | N=45 same=both scope=allbooks trig=cutstop | 25/-66/-14/-61 | 30/23/-3/-51 | 45/35/-2/-53 |
| blackout | N=30 same=same scope=book:P7 trig=cutstop | 9/4/18/2 | 4/4/11/-8 | 11/11/11/-3 |
| blackout | N=45 same=both scope=allbooks trig=stop | 20/6/6/6 | 30/23/-3/-51 | 9/9/-9/-48 |
| ntz | N1 D=60 act=retarget | 20/26/18/22 | 41/41/-8/29 | 20/20/-3/29 |
| ntz | N1 D=50 act=retarget | 20/25/17/25 | 31/31/-6/32 | 19/19/-3/32 |
| ntz | N1 D=40 act=retarget | 17/25/16/25 | 13/13/1/36 | 7/7/-4/35 |
| ntz | N3 Dk=60 act=retarget p=26 tf=1h | 8/0/-3/-0 | 28/28/-4/-4 | 23/23/-3/-3 |
| ntz | N3 Dk=60 act=retarget p=52 tf=30m | 7/0/-3/2 | 32/32/-3/-3 | 22/22/-3/-2 |

## 8. REFIT 2026-11-22 (what the bi-weekly procedure would pick today; first-order screens, labels RECENT-ONLY / OK-prior per the tolerant PRE rule)

| layer | pick today | setting | note |
|---|---|---|---|
| blackout | 34d1e3c7f657 | N=45 same=both scope=allbooks trig=cutstop | screen pick; exact rows decide, nothing goes live from a screen |
| NTZ / Kijun | 4fb9ccee5b03 | N3 Dk=60 act=retarget p=26 tf=30m | screen pick; exact rows decide, nothing goes live from a screen |
| OTE-62 | 3d75c2cebd75 | {"D": 20, "act": "WT", "f": 0.68, "maxmin": 15} | screen pick; exact rows decide, nothing goes live from a screen |
| O7 | 6df4f6200fea | lots=2 rm=0.5 stop=40 texit=1600 tgt=90 trig=pb1 wend=945 | screen pick; exact rows decide, nothing goes live from a screen |

## 5. Exact engine status (SZ-CORE queue, prefix R5_)
Exact rows (hooks, table windows complete only; cut = maxDD cut vs the exact S1b-COMB list, all weeks, ROLL-EXCL; EXACT only where L6M, PRE and X' are all present, else [EXACT partial]):

| set | months | par | cut % L6M/HOLD/PRE/X' | equal-mean cut L6M/PRE/X' | d mean L6M $/wk | w20 cut L6M | status |
|---|---|---|---|---|---|---|---|
| R5_TEST | 1 | {} | -/-/-/- | -/-/- | - | - | [EXACT partial] |

Months done per set: R5_TEST 1. Identity test R5_TEST (empty hooks par) on 202610: 823 trades, net 47,330.50, all columns identical to base_b/S1-COMB (PASSED).

Hook semantics and the first-order-vs-exact lesson (SZ_BASE_PROOF): first-order overstates anything that adds lots or changes exits; only the drawdown RANKING is usable first-order; all retarget / OTE / O7 rows are screens.
