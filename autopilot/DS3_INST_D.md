# DS3_INST_D - T-INSTITUTIONAL section D: volatility-market state (INST-4). Research only; nothing promoted. STATUS: FINAL for the first pass (Sat 2026-10-31 ~19:40Z).
**DATA line (Sat 2026-10-31 16:10Z).** ON DISK: (1) CME ES.OPT and NQ.OPT definitions, statistics (OI/settlement) and daily bars 2019-01..2026-10-14 plus the NQ weekly/EOM families 2023+ (data/autopilot/opts, 31 GB) -> daily GEX / zero-gamma distance / skew / term / ATM-30 IV / 0DTE share features in outputs/autopilot/opt/feat_{NQ,ES}.parquet, ndx_vol_daily.parquet (1,949-1,957 days); (2) OPRA NDX/NDXP daily bars 2019+, NDX monthly OI; (3) the 0DTE package (OPRA SPX/SPXW/NDX/NDXP trades + SPXW 1-min bars, GLBX ES/NQ option trades, 2022-01..2026-10-14, data/autopilot/opt0dte, 5.6 GB) -> 30-min flow-implied gamma tables gex_NDXF / gex_SPXF (zero-gamma level Z, gamma at spot G0, 0DTE ATM IV) and per-minute x DTE aggregates; (4) CBOE daily VIX, VIX3M, VIX6M, VIX9D, VVIX, SKEW to 2026-10-16 (data/gap/vix); (5) NQ/ES/RTY 1-minute store with ET minute-of-day and label day (aux_bar, to 2026-02-06). DERIVABLE now from (5): variance ratio at 5/30 min, range compression, open-to-10:30 realised vol vs the prior-day-range implied equivalent, realised vol-of-vol, 20-day realised vs VIX/NQ-IV spread. MUST BE BOUGHT / FETCHED (nothing bought): VXN history ($0 CBOE public file; DBIX.CORE only starts 2025-12-07); true NDXP open interest incl. 0DTE/weeklies ($140.05 OPRA statistics 2023-26); SPXW OI ($162.76). Quote table: DS3_INSTITUTIONAL.md PURCHASE table (P-D1..P-D5). Prior closed work on these data (REPORT_OPTIONS, REPORT_OPT0DTE, T-TREND-GATE store): GEX/zero-gamma/skew/term as pair size switch: 0 of 22 pass; hedging-flow drift 1-60 min: 0 of 304; this section re-asks the question as a REGIME for the six live D6 books at live lots on the one-convention engine, which those studies did not do.

## Page 1

**Plain sentence.** Volatility-market state as a regime for the six live books: none of 1,044 pre-registered cells (30 option / VIX / realised-vol states x 9 book scopes x skip or half size) is a usable regime; the 12 cells chosen on PRE and X' alone give two literal-TOLERANT LEADs, both tiny and inside MDE (ndx_G0 high -> half size KB: +0.08k/wk L6M, MDE 0.57, placebo rank 68/201 and 67/201; open-hour realised-vol ratio low -> skip MV: +0.57k/wk L6M, MDE 2.99, placebo rank 26/201 and 39/201, size recommended 0 after shrinkage), the other 10 SEL cells lose in L3M and L6M, and the eight named hypotheses (variance ratio, range compression, gamma sign) are all DEAD or NOW-ONLY with PRE/X' losses of 3-12k/wk; program Romano-Wolf survivors 0, White RC p 1.00, PBO 0.50; nothing promoted, no D6 change.

**Counts.** 1,044 cells scored on the ONE-CONVENTION engine (C1, tie-out exact). Positive in BOTH PRE and X': 8.0% (chance level for independent coin flips is 25%, the volume lost by skipping hurts PRE: only 12.2% of cells are positive in PRE); positive in PRE, X', L3M and L6M together: 15 cells (NOT a selection; looked after the fact, post-hoc, no inference). Share positive in PRE and X' by state family: {'CAL': 0.083, 'GEX0': 0.285, 'IVRV': 0.083, 'OPT': 0.025, 'REAL': 0.051, 'VIX': 0.069}. Eligible (>= 40 fired live signals in each of PRE and X'): 43; SEL = top 12 by min z; canon = 8 named hypotheses (prereg INST_D_prereg.md sha256 f1bd41e2e3dbf19ecdb4a5bbe382316f0f4bfee245b2370cc820c9bc7d765008, DECISIONS.md). Program validity on the PRE u X' selection data: White RC p 1.00 (studentised 0.95), Romano-Wolf survivors 0, PBO 0.50. Expiry-cycle family placebo (6 calendar cells x 200 shuffled-expiry-Friday draws): real best selection statistic rank 83/201 (p 0.41); real post-opex-week and VIX-expiry-day cells are all negative in the selection windows. The opex-day / opex-week / quad-witch states were NOT rescored (EINT2 and NTE1 scored them; EINT2 opex-day skip on the stack was +10.9k/wk L6M but -5.1k PRE, research lots).

**Tier rule used (headline).** TOLERANT = the literal SIXTY gate: L3M and L6M positive (stack and per contract); PRE and X' each >= -0.5 x that window's MDE; PRE worst-20-weeks no worse than the stack's; L6M->PRE drop < 100% of the L6M gain (with L6M > 0 this means PRE > 0). STRICT = positive in all five windows (stack and per contract). NOW-ONLY = L3M and L6M positive. TOL-B (clause 5 loosened to PRE > -1.0 x L6M gain) and TOL-nc (clause 5 dropped) are shown only as post-hoc readings in the CSV (TOL_B_posthoc, TOL_nc_posthoc columns); they are not tiers: for the 20 rows they add nothing beyond the two TOLERANT rows. LEAD = TOLERANT but inside MDE; no CANDIDATE-RECENT; no PASS.

### Table 1 - the SEL set (12 best on PRE+X' alone) and the 8 named canon cells, ONE recent look (stack delta vs the one-convention composite at live lots, $k/wk, MDE = 2.8 x SE of the paired weekly delta in brackets, * = beyond MDE)

| cell (state cut / action / scope) | tag | L3M $k/wk (MDE) | L6M | HOLD | PRE | X' | pts/contract L6M fired / kept | fired live L6M | STRICT | TOLERANT (literal; post-hoc TOL-B / TOL-nc beside, not gates) | NOW-ONLY | placebo rank L6M (time-shift / random-fire) | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ro_ratio<=1.296|skip|MV | SEL | +0.8 (5.0) | +0.6 (3.0) | +0.0 (2.7) | +0.5 (2.0) | +0.6 (1.7) | -0.04 / +5.00 | 158 | Y | Y (post-hoc beside: TOL-B Y / TOL-nc Y) | Y | 26/201 / 39/201 | LEAD |
| nq_gex_norm<=-0.01309|skip|MV | SEL | +0.8 (3.0) | +0.4 (1.5) | +0.4 (1.3) | +0.4 (1.7) | +0.6 (1.8) | +2.92 / +4.85 | 58 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 66/201 / 66/201 | DEAD |
| ndx_G0>=0.3785|half|KB | SEL | +0.1 (1.0) | +0.1 (0.6) | +0.1 (0.5) | +0.2 (0.7) | +0.3 (0.8) | -4.45 / +5.15 | 151 | Y | Y (post-hoc beside: TOL-B Y / TOL-nc Y) | Y | 68/201 / 67/201 | LEAD |
| nq_zgd<=-0.003022|skip|MV | SEL | +0.0 (2.9) | +0.0 (1.4) | +0.0 (1.3) | +0.4 (1.7) | +0.5 (1.8) | +3.76 / +4.83 | 45 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 118/201 / 102/201 | DEAD |
| vix_over_vix3m>=0.9436|half|MV | SEL | -0.3 (1.9) | -0.1 (0.9) | -0.1 (0.8) | +0.2 (1.3) | +0.2 (0.5) | +7.35 / +4.77 | 93 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 149/201 / 79/201 | DEAD |
| nq_atm30>=0.2025|half|MV | SEL | -0.6 (2.5) | -0.4 (1.2) | -0.3 (1.1) | +0.3 (1.1) | +0.2 (0.9) | +9.28 / +4.65 | 160 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 180/201 / 120/201 | DEAD |
| cal_vix_exp_day==1|half|KB | SEL | -0.0 (1.0) | -0.4 (1.0) | -0.4 (0.9) | +0.1 (0.4) | +0.1 (0.4) | +4.54 / +4.83 | 71 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 201/201 / 158/201 | DEAD |
| nq_term>=1.002|half|MV | SEL | -1.0 (3.0) | -0.6 (1.5) | -0.5 (1.3) | +0.3 (1.2) | +0.2 (0.5) | +8.64 / +4.73 | 106 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 187/201 / 154/201 | DEAD |
| vv_240>=1.009|half|KB | SEL | -0.9 (4.6) | -0.6 (2.6) | -0.3 (2.5) | +0.4 (1.5) | +0.3 (1.0) | +0.12 / +5.19 | 320 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 162/201 / 82/201 | DEAD |
| rc_15_120>=1.184|half|HM | SEL | -2.8 (4.3) | -2.1 (2.7) | -1.9 (2.4) | +0.6 (1.2) | +0.3 (1.2) | +13.41 / +4.50 | 156 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 199/201 / 201/201 | DEAD |
| cboe_skew>=148.8|half|PE | SEL | -4.8 (9.4) | -4.6 (6.0) | -2.9 (6.2) | +0.8 (4.2) | +0.9 (0.9) | +2.66 / +4.97 | 273 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 81/201 / 58/201 | DEAD |
| rc_15_120>=1.184|skip|HM | SEL | -5.0 (7.4) | -4.6 (4.7) | -4.1 (4.2) | +0.7 (2.2) | +1.7 (2.2) | +13.41 / +4.50 | 156 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 201/201 / 201/201 | DEAD |
| vr30_600<=0.7966|skip|TREND | CANON | +11.0 (7.9)* | +1.9 (8.0) | +2.1 (7.3) | -2.9 (4.2) | -0.2 (4.4) | +1.23 / +5.76 | 907 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | Y | 8/201 / 1/201 | LEAD (NOW-ONLY) |
| nq_gex_norm<=-0.01309|skip|PULL | CANON | +2.9 (11.9) | +1.4 (5.9) | +1.3 (5.2) | -4.9 (7.2) | -1.1 (4.6) | -1.34 / +5.12 | 202 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | Y | 16/201 / 3/201 | LEAD (NOW-ONLY) |
| vr5_240<=0.8905|skip|TREND | CANON | +3.2 (15.5) | -1.1 (11.2) | +0.6 (10.4) | -2.7 (4.9) | -3.3 (6.0) | +1.36 / +5.72 | 895 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 56/201 / 9/201 | DEAD |
| ro_ratio<=1.296|skip|TREND | CANON | -2.6 (14.9) | -3.3 (10.0) | -4.2 (9.2) | -1.0 (6.4) | +0.8 (3.6) | +3.04 / +5.16 | 692 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 102/201 / 54/201 | DEAD |
| nq_gex_norm>=0.197|skip|TREND | CANON | +3.5 (8.8) | -6.2 (9.0) | -5.7 (10.2) | -2.9 (5.0) | -2.1 (4.9) | +3.71 / +5.35 | 1404 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 55/201 / 119/201 | DEAD |
| vr30_600>=1.091|skip|PULL | CANON | -8.1 (16.2) | -8.9 (10.9) | -6.6 (11.8) | -5.4 (8.7) | +1.5 (7.8) | +1.91 / +5.28 | 594 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 180/201 / 79/201 | DEAD |
| vr5_240>=1.042|skip|PULL | CANON | -14.2 (20.8) | -10.9 (13.5) | -10.1 (12.7) | -4.0 (8.8) | +0.6 (8.7) | +3.46 / +5.04 | 596 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 191/201 / 121/201 | DEAD |
| rc_15_120<=0.8884|skip|ALL6 | CANON | -19.5 (30.2) | -15.9 (19.8) | -16.2 (18.0) | -12.0 (11.0)* | -1.0 (12.5) | +4.99 / +4.74 | 1473 | n | n (post-hoc beside: TOL-B n / TOL-nc n) | n | 171/201 / 87/201 | DEAD |

### Table 2 - per-contract (pts per contract of the fired set vs the kept set), fills side by side, session split of the delta (L6M $k/wk; skip-restricted runs), persistence and shrunk size

| cell | pts/contract fired / kept: L3M | L6M | HOLD | PRE | X' | LIVE-CAL stop 2.45: L6M (MDE) / PRE | 12R lock: L6M (MDE) / PRE | session L6M asia / london / nyam / nypm | neighbourhood L6M mean (n) | purged 5-fold means PRE u X' ($k/wk) | PRE worst-20 rule vs stack | persistence | shrunk L3M | size | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| rc_15_120>=1.184|skip|HM | +13.17 / +2.10 | +13.41 / +4.50 | +12.04 / +4.16 | +1.61 / +3.28 | -4.54 / +1.81 | -4.6 (4.7) / +0.8 | -6.2 (13.9) / +0.6 | -3.5 / -0.0 / -1.4 / -0.0 | -4.4 (2) | +1.7 +2.5 +0.4 -0.5 +1.8 | -841 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| rc_15_120>=1.184|half|HM | +13.17 / +2.10 | +13.41 / +4.50 | +12.04 / +4.16 | +1.61 / +3.28 | -4.54 / +1.81 | -2.1 (2.7) / +0.6 | -0.7 (1.9) / +0.0 | -2.1 / -0.0 / -0.1 / -0.0 | -1.9 (2) | +0.1 +1.2 +0.2 -0.0 +1.1 | -846 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| ndx_G0>=0.3785|half|KB | -9.13 / +2.99 | -4.45 / +5.15 | -6.09 / +4.83 | +2.15 / +3.29 | -9.05 / +2.25 | +0.1 (0.6) / +0.2 | +0.0 (0.5) / -0.3 | -0.0 / -0.0 / +0.3 / -0.0 | +0.0 (2) | +0.4 +0.2 +0.3 +0.5 -0.1 | -870 vs -875 | 0.46 | +0.0 | 0.00 | RISING |
| nq_zgd<=-0.003022|skip|MV | +3.76 / +2.50 | +3.76 / +4.83 | +3.76 / +4.44 | -1.26 / +3.48 | -3.89 / +1.75 | +0.0 (1.5) / +0.5 | -0.4 (0.8) / +0.3 | -0.0 / -0.2 / +0.2 / -0.0 | +0.5 (2) | -0.4 +1.0 -0.6 +0.7 +0.8 | -844 vs -875 | 0.44 | +0.0 | 0.00 | NEW |
| nq_term>=1.002|half|MV | +5.77 / +2.40 | +8.64 / +4.73 | +8.64 / +4.34 | +1.83 / +3.31 | -12.64 / +1.74 | -0.5 (1.5) / +0.3 | -0.6 (1.5) / +0.4 | -0.0 / -0.5 / -0.4 / -0.0 | -0.6 (2) | +0.2 +0.3 -0.1 -0.4 +1.4 | -841 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| vv_240>=1.009|half|KB | -1.74 / +2.85 | +0.12 / +5.19 | +0.94 / +4.72 | +4.40 / +3.11 | -2.74 / +1.97 | -0.6 (2.6) / +0.3 | -0.3 (2.7) / -3.0 | -0.3 / -0.3 / +0.1 / -0.1 | -0.8 (2) | +0.5 +0.6 +0.8 +0.6 +0.3 | -856 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| nq_atm30>=0.2025|half|MV | +7.37 / +2.28 | +9.28 / +4.65 | +9.28 / +4.27 | +1.26 / +3.34 | -8.44 / +1.81 | -0.4 (1.2) / +0.4 | -0.4 (1.2) / +0.4 | -0.0 / -0.6 / -0.1 / -0.0 | -0.5 (2) | -0.3 +0.6 -0.2 -0.4 +1.6 | -858 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| nq_gex_norm<=-0.01309|skip|MV | +2.92 / +2.52 | +2.92 / +4.85 | +2.92 / +4.46 | -1.15 / +3.47 | -4.10 / +1.77 | +0.4 (1.5) / +0.4 | +0.0 (0.9) / +0.3 | -0.0 / +0.1 / +0.3 / -0.0 | +0.5 (2) | -0.3 +1.2 -0.7 +0.7 +0.8 | -848 vs -875 | 0.48 | +0.0 | 0.00 | NEW |
| ro_ratio<=1.296|skip|MV | -4.72 / +2.77 | -0.04 / +5.00 | +0.88 / +4.57 | -0.07 / +3.40 | -6.29 / +1.85 | +0.6 (3.0) / +0.5 | -0.8 (6.3) / +0.2 | -0.0 / -0.1 / +0.9 / -0.0 | +1.1 (2) | -0.0 +1.0 +0.1 -1.3 +2.1 | -829 vs -875 | 0.47 | +0.0 | 0.00 | RISING |
| cboe_skew>=148.8|half|PE | -0.32 / +2.70 | +2.66 / +4.97 | +2.55 / +4.56 | +0.41 / +3.51 | -3.35 / +1.64 | -4.5 (6.0) / +0.9 | -6.5 (7.2) / +2.5 | -4.2 / -0.6 / -1.7 / -0.0 | -5.4 (2) | +1.3 +1.0 -1.1 +3.6 +0.2 | -703 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| vix_over_vix3m>=0.9436|half|MV | +7.09 / +2.41 | +7.35 / +4.77 | +7.35 / +4.38 | +2.67 / +3.26 | -12.17 / +1.76 | -0.1 (0.9) / +0.2 | +0.1 (0.4) / +0.3 | -0.0 / -0.3 / -0.1 / -0.0 | -0.2 (2) | -0.0 +0.4 -0.8 -0.5 +1.7 | -853 vs -875 | 0.43 | -0.0 | 0.00 | FADING |
| cal_vix_exp_day==1|half|KB | -5.08 / +2.66 | +4.54 / +4.83 | +6.75 / +4.40 | +2.38 / +3.23 | -6.39 / +1.66 | -0.7 (1.4) / +0.1 | -0.5 (1.0) / -0.1 | -0.6 / -0.1 / -0.3 / -0.2 | n/a (0) | +0.3 +0.2 -0.0 +0.5 -0.2 | -873 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| vr5_240<=0.8905|skip|TREND | -4.02 / +4.15 | +1.36 / +5.72 | +0.40 / +5.47 | +2.74 / +3.35 | +3.47 / +1.14 | -1.0 (11.2) / -2.6 | -2.4 (18.1) / -5.5 | -2.7 / +1.8 / +1.6 / -0.2 | +1.1 (2) | -3.4 +0.3 -3.2 -2.6 -1.2 | -833 vs -875 | 0.43 | +0.0 | 0.00 | NEW |
| vr5_240>=1.042|skip|PULL | +2.96 / +2.46 | +3.46 / +5.04 | +3.01 / +4.67 | +1.72 / +3.44 | -2.37 / +2.18 | -11.2 (13.7) / -4.0 | -14.5 (16.8) / -0.7 | -4.6 / -3.3 / -4.6 / -0.0 | -10.4 (2) | -3.4 +3.7 -6.9 +0.8 -12.6 | -844 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| vr30_600<=0.7966|skip|TREND | -4.56 / +4.33 | +1.23 / +5.76 | +0.55 / +5.50 | +4.93 / +2.73 | -2.07 / +2.44 | +2.1 (8.0) / -2.8 | +4.3 (11.8) / -0.8 | +0.7 / +1.7 / +1.2 / -0.3 | +2.6 (2) | +0.2 -0.5 -1.2 -3.3 -5.5 | -873 vs -875 | 0.47 | +0.0 | 0.00 | NEW |
| vr30_600>=1.091|skip|PULL | +2.87 / +2.47 | +1.91 / +5.28 | +1.20 / +4.95 | -1.71 / +4.02 | +2.65 / +1.36 | -9.2 (11.0) / -5.2 | -7.3 (11.9) / -5.0 | -0.6 / -2.5 / -6.1 / -0.0 | -7.9 (2) | +2.8 +2.1 -6.3 +1.8 -12.9 | -724 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| rc_15_120<=0.8884|skip|ALL6 | +3.45 / +2.10 | +4.99 / +4.74 | +4.91 / +4.20 | +4.34 / +2.69 | +1.29 / +1.71 | -16.1 (20.0) / -11.5 | -10.2 (17.3) / -6.6 | -8.6 / -4.9 / -1.9 / +0.7 | -17.4 (2) | -1.5 +1.6 -11.9 -1.9 -24.5 | -1030 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| ro_ratio<=1.296|skip|TREND | +2.64 / +2.51 | +3.04 / +5.16 | +3.86 / +4.54 | +2.37 / +3.46 | -3.68 / +2.57 | -3.2 (10.0) / -0.8 | +4.4 (16.7) / -0.9 | -2.3 / -1.0 / +0.7 / +0.2 | -1.6 (2) | -1.1 +2.9 +4.1 -4.5 +0.3 | -820 vs -875 | 0.43 | -0.0 | 0.00 | NEW |
| nq_gex_norm>=0.197|skip|TREND | -1.26 / +3.55 | +3.71 / +5.35 | +3.04 / +5.17 | +2.59 / +3.38 | +1.90 / +1.49 | -5.8 (9.0) / -2.8 | -1.0 (11.8) / +0.1 | -2.7 / -1.1 / -1.3 / +0.2 | -6.8 (2) | -1.4 -2.5 -1.9 -7.5 +0.5 | -810 vs -875 | 0.43 | +0.0 | 0.00 | NEW |
| nq_gex_norm<=-0.01309|skip|PULL | -1.34 / +2.88 | -1.34 / +5.12 | -1.34 / +4.69 | +3.36 / +3.20 | +5.37 / +1.11 | +1.2 (5.7) / -4.8 | +1.4 (6.8) / -4.6 | +0.4 / +1.4 / -1.8 / -0.0 | +0.3 (2) | +0.8 -4.0 -6.7 +4.1 -16.0 | -909 vs -875 | 0.48 | +0.0 | 0.00 | NEW |

### Table 3 - validity: placebos (rank of the real number among 200 draws; p one-sided), RC/Romano-Wolf/DSR on the PRE u X' selection data, why not CANDIDATE-RECENT, failed TOLERANT gates

| cell | P1 time-shifted: L6M rank / selection-stat rank | P2 random-fire: L6M rank / selection-stat rank | placebo draw mean L6M (P1 / P2 not shown) | RW p (PRE u X', 1,044/396 cells) | DSR | top-5% share of the fired L6M loss | failed TOLERANT gates | why not CANDIDATE-RECENT |
|---|---|---|---|---|---|---|---|---|
| rc_15_120>=1.184|skip|HM | 201/201 / 4/201 | 201/201 / 1/201 | -1.0 | 0.95 | 0.10 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| rc_15_120>=1.184|half|HM | 199/201 / 6/201 | 201/201 / 1/201 | -0.4 | 0.99 | 0.05 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| ndx_G0>=0.3785|half|KB | 68/201 / 3/201 | 67/201 / 3/201 | -0.0 | 1.00 | 0.02 | 1.90 |  | L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| nq_zgd<=-0.003022|skip|MV | 118/201 / 6/201 | 102/201 / 3/201 | +0.2 | 1.00 | 0.01 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| nq_term>=1.002|half|MV | 187/201 / 10/201 | 154/201 / 2/201 | +0.1 | 1.00 | 0.01 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| vv_240>=1.009|half|KB | 162/201 / 1/201 | 82/201 / 1/201 | -0.2 | 1.00 | 0.01 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| nq_atm30>=0.2025|half|MV | 180/201 / 36/201 | 120/201 / 5/201 | +0.1 | 1.00 | 0.01 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| nq_gex_norm<=-0.01309|skip|MV | 66/201 / 7/201 | 66/201 / 4/201 | +0.2 | 1.00 | 0.01 | 1.04 | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| ro_ratio<=1.296|skip|MV | 26/201 / 1/201 | 39/201 / 1/201 | -0.4 | 1.00 | 0.02 | 0.93 |  | L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| cboe_skew>=148.8|half|PE | 81/201 / 2/201 | 58/201 / 1/201 | -5.0 | 1.00 | 0.01 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| vix_over_vix3m>=0.9436|half|MV | 149/201 / 12/201 | 79/201 / 6/201 | +0.1 | 1.00 | 0.01 | 170.92 | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| cal_vix_exp_day==1|half|KB | 201/201 / 1/201 | 158/201 / 11/201 | -0.4 | 1.00 | 0.00 | nan | L3M/L6M_not_both_positive | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| vr5_240<=0.8905|skip|TREND | 56/201 / 119/201 | 9/201 / 63/201 | -3.2 | 1.00 | 0.00 | nan | L3M/L6M_not_both_positive,PRE/X_below_-0.5MDE,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| vr5_240>=1.042|skip|PULL | 191/201 / 88/201 | 121/201 / 64/201 | -5.4 | 1.00 | 0.00 | nan | L3M/L6M_not_both_positive,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| vr30_600<=0.7966|skip|TREND | 8/201 / 141/201 | 1/201 / 84/201 | -2.4 | 1.00 | 0.00 | 4.52 | PRE/X_below_-0.5MDE,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,program_RC_p>0.1 |
| vr30_600>=1.091|skip|PULL | 180/201 / 146/201 | 79/201 / 121/201 | -4.9 | 1.00 | 0.00 | nan | L3M/L6M_not_both_positive,PRE/X_below_-0.5MDE,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| rc_15_120<=0.8884|skip|ALL6 | 171/201 / 180/201 | 87/201 / 179/201 | -9.7 | 1.00 | 0.00 | nan | L3M/L6M_not_both_positive,PRE/X_below_-0.5MDE,PRE_worst20_worse_than_base,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| ro_ratio<=1.296|skip|TREND | 102/201 / 17/201 | 54/201 / 11/201 | -3.4 | 1.00 | 0.00 | nan | L3M/L6M_not_both_positive,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| nq_gex_norm>=0.197|skip|TREND | 55/201 / 31/201 | 119/201 / 57/201 | -8.2 | 1.00 | 0.00 | nan | L3M/L6M_not_both_positive,PRE/X_below_-0.5MDE,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |
| nq_gex_norm<=-0.01309|skip|PULL | 16/201 / 144/201 | 3/201 / 163/201 | -3.0 | 1.00 | 0.00 | 3.47 | PRE/X_below_-0.5MDE,PRE_worst20_worse_than_base,L6M_to_PRE_drop_ge_100pct | not_TOLERANT,L6M_inside_MDE,placebo_L6M_not_beaten,program_RC_p>0.1 |

### Realised-proxy descriptive (not a test): pts per contract of the base signals (live lots, N basis) by tercile of the proxy, TREND books (KB SM HM MV) and PULL books (PE PB)
| state | group | tercile | L6M | PRE | X' |
|---|---|---|---|---|---|
| nq_gex_norm | PULL | high | +8.75 | +0.72 | -2.23 |
| nq_gex_norm | PULL | low | -1.34 | +3.36 | +5.37 |
| nq_gex_norm | PULL | mid | +3.37 | +4.65 | +9.81 |
| nq_gex_norm | TREND | high | +3.71 | +2.59 | +1.90 |
| nq_gex_norm | TREND | low | +2.99 | +2.29 | -2.08 |
| nq_gex_norm | TREND | mid | +4.13 | +6.14 | -1.55 |
| rc_15_120 | PULL | high | +2.68 | +3.48 | +2.79 |
| rc_15_120 | PULL | low | +7.39 | +5.95 | +4.48 |
| rc_15_120 | PULL | mid | +7.35 | -0.63 | +7.12 |
| rc_15_120 | TREND | high | +5.15 | +4.84 | -2.64 |
| rc_15_120 | TREND | low | +2.78 | +3.23 | -1.20 |
| rc_15_120 | TREND | mid | +3.24 | +2.16 | +1.81 |
| ro_ratio | PULL | high | +13.21 | +0.82 | +1.90 |
| ro_ratio | PULL | low | -1.13 | +2.96 | +3.40 |
| ro_ratio | PULL | mid | -0.22 | +5.00 | +8.46 |
| ro_ratio | TREND | high | +6.02 | +4.02 | -1.74 |
| ro_ratio | TREND | low | +3.04 | +2.37 | -3.68 |
| ro_ratio | TREND | mid | +0.65 | +4.16 | +2.24 |
| ro_ratio_vix | PULL | high | +6.87 | +4.37 | -4.56 |
| ro_ratio_vix | PULL | low | +10.29 | +6.98 | +6.31 |
| ro_ratio_vix | PULL | mid | +0.94 | -3.40 | +9.12 |
| ro_ratio_vix | TREND | high | +5.39 | +3.45 | -3.83 |
| ro_ratio_vix | TREND | low | +2.92 | +3.99 | +1.38 |
| ro_ratio_vix | TREND | mid | +2.73 | +2.96 | -0.62 |
| vr30_600 | PULL | high | +1.91 | -1.71 | +2.65 |
| vr30_600 | PULL | low | +3.57 | +6.43 | -5.41 |
| vr30_600 | PULL | mid | +11.41 | +4.31 | +14.12 |
| vr30_600 | TREND | high | +4.40 | +1.63 | -3.40 |
| vr30_600 | TREND | low | +1.23 | +4.93 | -2.07 |
| vr30_600 | TREND | mid | +5.98 | +3.53 | +3.22 |
| vr5_240 | PULL | high | +3.46 | +1.72 | -2.37 |
| vr5_240 | PULL | low | +4.87 | +2.58 | +9.50 |
| vr5_240 | PULL | mid | +10.05 | +4.18 | +7.58 |
| vr5_240 | TREND | high | +6.30 | +2.74 | -3.69 |
| vr5_240 | TREND | low | +1.36 | +2.74 | +3.47 |
| vr5_240 | TREND | mid | +3.87 | +4.90 | -1.21 |
| vv_240 | PULL | high | +6.28 | +2.96 | -0.58 |
| vv_240 | PULL | low | +4.56 | +1.94 | +19.92 |
| vv_240 | PULL | mid | +7.74 | +3.74 | -2.83 |
| vv_240 | TREND | high | +2.34 | +4.09 | -2.80 |
| vv_240 | TREND | low | +5.91 | +4.25 | +1.62 |
| vv_240 | TREND | mid | +2.86 | +2.00 | -0.28 |

Reading: the variance-ratio, range-compression and open-hour proxies do not sort the books consistently across windows (a tercile that is best in L6M is mid or worst in PRE or X'); the strongest sorting is the mean-reverting tape (low VR30) for the TREND books in L6M, which is the NOW-ONLY canon cell C3: skipping it gains +1.9k/wk L6M and loses -2.9k PRE (placebo ranks 8/201 and 1/201 for the L6M number, i.e. the L6M gain is unusual for a time-shifted or random subset, but PRE and X' disagree: a regime flip, not a rule).

### What else was checked
* Fills: every SEL/canon row has the LIVE-CAL stop (all-days join 2.45) and the 12R combined-lock stack beside it (Table 2); the two LEAD rows keep their sign on LIVE-CAL (+0.09 / +0.61 L6M) and lose it under the 12R lock for the MV row (-0.75). Decision delay: the states use only bars completed before the signal minute, so a 1-s / 3-s delay changes nothing by construction. Capacity: not applicable (a filter removes size).
* Sessions (Table 2) and sensitivity (neighbourhood mean of the cut +-1 step) are in the tables; persistence scores are 0.43-0.48 (at the RE-1 coin-flip level) and the shrunk recommended size is 0 for every row.
* Prior art on the same data: REPORT_OPTIONS (GEX/zero-gamma/skew/term as pair size switch: 0 of 22), REPORT_OPT0DTE (hedging flow: 0 of 304), T-TREND-GATE state store (VRP, flow gamma, rv30/VIX); NTE1/EINT2 (VIX level, VVIX, VIX9D/VIX, opex flags, r30m vs median) not rescored. This section adds: the six live books as targets, the one-convention lock engine, the new proxies (VR5/VR30, compression, vol-of-vol, open-hour ratio, VIX/VIX3M, VVIX/VIX, VIX6M/3M, NQ-IV minus RV20).
* Purged 5-fold on PRE u X' weekly deltas for each SEL cell is in Table 2 (fold means).

## PURCHASE (D) - quotes only, nothing bought
See DS3_INSTITUTIONAL.md table P-D1..P-D6. Verdict on the data question: the on-disk options and VIX family gave a null regime; buying NDXP open interest ($140.05) or SPXW OI ($162.76) is NOT justified by this result; VXN (free) and the VX futures daily ($22.53) are cheap completeness items only.

Files: code l2vast/ds3/code/inst/{inst_lib.py,score1.py,score2_jobs.py,score3.py,report.py,desc.py,D/}; out l2vast/ds3/out/inst/D/ (cells.csv, grid_table.parquet, final_rows.csv, tables.md, res_*.npz); rows out/recent_wins/inst_D.csv; DEAD_CELLS +1,044 (program INST_D) via append_cells.
