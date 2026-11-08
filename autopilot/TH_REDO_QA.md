> **VOID — engine failed Gate 0.** (user order 2026-11-08 15:00Z: this page is WITHDRAWN as a finding; the engine reproduces the live cut at 14% strict agreement and cannot rank cut rules, including "the live cell stays". No TH ranking from this page may be quoted. Original content below, unchanged. Backup: /mnt/l2/l2vast/_th_void_backup/)

# TH_REDO_QA - independent audit of the T-TH-REDO results (programs A-G, replica engine)
Auditor TH-REPORT, 2026-11-08. PRE-PROOF. Label carried by every number below: cut-input agreement with live 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false cuts; engine Gate 0 NOT passed. Read-only audit; no report of another agent was edited, no policy file touched. Scratch: /mnt/l2/l2vast/_th_report/ (recompute.py, rc2..rc8.py). Seal: md5 of /mnt/l2/l2vast/ds3_all_ea/manifest_after.json = 6baf7cf4a8b4052da3d7fb3a9a2fffc8 before and after (sha256 prefix 759f2258daac9d28, as the reports state).
Source checked: DS7.cs sha256 54697597a7057cfd2003f3d698b62fe01358c308a87adfbbfb5a764ab0cb63a7 (data/live_code/DS7.cs, matches).

## Summary
Every sampled table row reproduces from the stored trade files (14 rows, 12 exact). Four substantive discrepancies (basis, D scope, G sha log, smoke coverage) and several minor ones; none flips a program verdict (no program claims a rule), but two lead numbers change (D F10; A P05 X').

## (a) Smoke / HOLD reproduction
- A: claim 203 trades, +60,200, 108 cuts. Verified: out/smoke.json (hold and live_cell both 203 / 60,200.0000 / 108, exact True) and out/blind_trades_hold.parquet (203 trades, gross 60,200.0; exit_name ThL2Cut 99 + PolicyCut 9 = 108). OK.
- E: claim HOLD 201 trades +55,890 (ITER14). Verified: hold14.pkl (201 trades, pnl_usd sum 55,890.0) and E/out/blind_HOLD.pkl (201, 55,890). E blind numbers recomputed from blind_*.pkl: A:P10 66,120 (170 tr), A:P10+D:F07 63,545, A:P10+D:F08 61,555, B:F07 63,010 (165), B:F07+C4 56,035 (155); the stated +7.7k/+5.7k/+0.1k vs HOLD and the 2.6k/4.6k/7.0k cost of the profit rule all reproduce. OK.
- B, C, D, G did NOT run the 203/+60,200 or 201/+55,890 smoke themselves. They rely on TH-A's HOLD month chunks (hist/A2/*/trades_hold.parquet): 43 months, 23,788 trades (B, D, G figure verified; C's "2026-10: 917 trades, 58,115" verified: 917 trades, gross 58,115.0; B's 917 HOLD / 689 NO-CUT verified). So (a) holds indirectly for these four; no explicit headline smoke is in their reports. Minor: hist/A1 (an early superseded tag, same 43 months) holds 23,776 trades, not 23,788; A uses the A2 tag.

## (b) Adoption label on every table header
All six reports carry the full label directly under the title. Tables without a literal label line within 6 lines above them (label only at report top or at the addendum head): A: main Tier F table (l.21), candidates table (l.47), Addendum 1 Tier F (l.90), A7 Tier F (l.150), B3 (l.167); C: thick-trigger table (l.17) and Tier S sub-grid summary (l.52). B, D, G tables are labelled; E Table 1 second block is under the label. Minor, no numbers affected.

## (c) PASS wording
No standalone PASS in any report (hits are all "No PASS claim(s)" / "no PASS words"). A l.7 says "Smoke test passed" (lower case, about the smoke only) and C says "NOT a pass of the fragile-cut cap" (negation); suggest "reproduces" wording. DS3_TH_REDO.md has none. I use no pass-words in the consolidated section.

## (d) Prereg shas logged before the first score
DECISIONS.md line order (prereg A-G sha lines 5289-5295 on 2026-11-06T20:09Z; replica-run sha lines 5336-5339, 5345): A 19:16Z (l.5336) before A's first output (SHAS file 19:16:19 and later runs); B 20:27Z before B's first file 20:29:48; C 20:28:34Z before 20:28:53 (c_rec.py; code only); D 20:29Z before 20:31:58 and D code-freeze line 20:54Z before the first full-history number (stage-1 files 21:55); E 05:25Z prereg written BEFORE any E number (E combos selection code select_E.py and combos.json carry mtime 05:13, 12 min before the log line; they are built from published A-D tables, no E score exists then; flag as an order irregularity of 12 min, not a scoring violation). Sha16 values of the prereg files on disk equal the logged values (A 0dce7cef, B a9320dd8, C acf18f20, D 29a2c2f1, E a32a651d, G 641dbb4d, adoption fb6d42b6, addenda 07f947b4 / 95ff9a48).
DISCREPANCY (G): no replica-run sha line for TH-G exists in DECISIONS.md. The G report says "shas in DECISIONS.md" and "finalists chosen by a frozen rule before any engine number (DECISIONS.md)"; the only G lines are the Nov 6 prereg lines (5284, 5295) and MORNING.md l.2872 "TH-G STARTED" (03:08Z). thG_rec.py mtime 03:10:34, first rows 03:12 on Nov 8; code files thG_*.py were edited until 04:44 (report admits thG_final.py gained fragile() after the sha line). The code shas, adoption sha and finalist rule therefore cannot be checked against a pre-score log. G's verdict is null, but its provenance is incomplete. Action for TH-G owner: append the sha line now, marked late.

## (e) Windows on every candidate row
L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' present on all main tables of A, B, C (E1), D, E, G. Blank PRE/X' on A, A7, B3 rows is legitimate (12-month recents-only runs, months column shows coverage). A's "Candidates that beat the live cell" table shows only L6M, PRE, X' (the full windows are in the Tier F table above it).

## (f) Recomputation of table rows from stored files
Method: stored trade parquet files under /mnt/l2/l2vast/_th_redo_replica/ (run) minus hist/A2/<month>/trades_hold.parquet (HOLD), gross by exit label day (tiers_core.label_day_of, common_dst.off_ns; shared library), ISO weeks inside each window as of 2026-10-30, mean weekly delta with the largest-|delta| week dropped when >= 8 weeks. Two bases: ALL trades and 14 live units (units = mapped books K7/P7/U7/H7/M7/A7 x session; excludes book O7, 506 HOLD trades).
| claim (report) | file(s) | recomputed L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | result |
|---|---|---|---|
| A P05 (A table) | hist/F_A2/*/P05.parquet | ALL: -2139/636/3816/4565/2220/-285/3007/-1160 | exact |
| A P06 | hist/F_A2/*/P06.parquet | ALL: -958/-5305/2393/5576/4965/1236/1866/-703 | exact |
| A P10 | hist/F_A2/*/P10.parquet | ALL: -8973/-3754/1207/3506/1862/-6415/4943/-3111 | exact |
| A P11 | hist/F_A2/*/P11.parquet | ALL: -4345/-4652/783/5364/3705/4785/2147/-1910 | exact |
| A4 BO_both_5 | hist/F2_A2/*/BO_both_5.parquet | 2426/1948/1643/3390/1833/-41/647/263 (both bases equal) | exact |
| A4 placebo L6M p 0.048 | hist/F3/*/PBO_0..19.parquet (12 months) | placebo mean 428, sd 1315, 1 + count(>= 3390) over 21 = 0.048 | exact |
| B F10 (B Table 1) | B/fin/T1/F10/*.parquet | 1298/2552/2166/911/1355/1003/1608/-440 (both bases) | exact |
| B3 F10+P11 (A Add. 3) | B/fin/B3/B3_F10_P11/*.parquet | 2115/2971/3275/3188/2219/370/190/97 | exact |
| C C3 KB 70%/+2 (C E1) | C/full/C.C3.pct0.7_buf2@KB/*.parquet | 2201/2492/1877/2577/606/-325/342/23 | exact |
| C C3 70%/+4 (C table) | C/full/C.C3.pct0.7_buf4/*.parquet | ALL: 2322/2838/1579/2378/-1397/-4262/-2021/-507; 14U: 2188/2816/1667/2404/-1349/-4360/-1995/-541 | exact on 14U (C uses 14U) |
| D F08 (D table) | D/tier1/F08_c216_PE_nyam/*.parquet | PE_nyam unit only: 0/174/350/168/301/485/401/293 | exact on unit basis; stack basis differs (below) |
| D F10 | D/tier1/F10_c233_MV_london/*.parquet | MV_london unit only: 370/645/571/385/-287/-1772/-69/-82; STACK: 235/320/554/-190/-675/-1866/-21/-32 | exact on unit basis; stack differs |
| E B:F07+C4 | E/runs/B:F07+C:C4run_target70/*.parquet | ALL = 14U: -2909/147/3411/3862/3088/-3937/4557/-2098 | exact |
| E A:P10+D:F07 | E/runs/A:P10+D:F07_PEny_decay60/*.parquet | 14U: -8567/-2138/2912/8016/2408/-6421/5369/-4104 (ALL basis: L6M 4151) | exact on 14U |
| G G01 / G03 / G06 / G08 | G/fin/T1/G0x/*.parquet | G01 -239/366/36/234/-311/-514/32/-195; G03 0/30/129/85/77/11/31/9; G06 -147/534/256/22/-27/-331/106/-30; G08 0/94/62/78/21/0/46/87 | exact |
Lead claims by program: A (P05/P06/P07 and the 12 finalists): the 12 are exactly P02, P05, P06, P07, P10, P11, P12, P13, P14, P17, P18, P24 (L6M>0 and PRE>0, p_placebo/p_thin/p_family clean in the A table); numbers right. A4 5-min blackout: right, including the 0.048 placebo floor. B3 F10+P11: right. C3 lock KB 70%/+2: right (DD-first fails: 161,280 -> 172,810 as stored). D F08/F10: see discrepancy 2. E: B:F07+C4 and A:P10+D:F07/F08: right on the 14-unit basis. G: right; G01/G03/G06/G08 positive on L6M and PRE by $22..$234 and $31..$106 per week.

## Discrepancies (precise)
1. BASIS: A's Tier F tables (final_A.py daily_of) score ALL trades including book O7 (not one of the six mapped live books); C, D (scope), E score 14 live units (score_E.daily filters T.book in D2BK and unit>=0). B, G, A4, B3, C3-KB are unaffected (O7 unchanged). Effect on A leads (ALL vs 14U): P05 X' -1160 vs +116 (the A text "X' deltas are negative for all candidates" is true only on the ALL basis); P05 PRE 3007 vs 2664; P06 PRE 1866 vs 1550; P07 PRE 1886 vs 1570; P10 L6M 3506 vs 3632; P11 PRE 2147 vs 2001; others within +-250. No lead changes sign on L6M or PRE. Recommend a common 14-unit basis. E's A:P10 / A:P02 loss-only rows (3632 / 3350 L6M) equal the 14U values, not A's published ones; unlabelled.
2. D SCOPE: D's tier1 table (dfinal.py: daily(..., unit mask)) is the delta of ONE unit (PE_nyam or MV_london), although D's text says "14 units". Stack basis (also E's component rows): F08 HOLD +232 / PRE +528 / X' +321 (D: 301/401/293); F10 L1M..X' = 235/320/554/-190/-675/-1866/-21/-32 versus D's 370/645/571/385/-287/-1772/-69/-82. On the stack F10 is NEGATIVE on L6M, so D's statement that F10 clears recents / tolerant / drawdown-first holds only for the unit series; DS3_TH_REDO.md D row (F10 L6M +385) repeats the unit figure. F08 stays positive on both bases. Both remain non-qualifying (family .89, walk-forward not positive, fragile 5.3x).
3. G sha log missing (see d).
4. SMOKE COVERAGE: explicit 203/+60,200 only in A; explicit 201/+55,890 only in E; B, C, D, G rely on A's HOLD chunks (see a).
5. DS3_TH_REDO.md structure: the directive asks for Gate 0 status first and A-F plain sentences; the file starts with Program D, rows were appended in finish order, A's earlier row ("A2,A4,A5,A6,A7 not run") and "A7 15 of 161" are superseded by later rows. The consolidated section appended below puts Gate 0 first and supersedes ordering; earlier rows left as written (append-only).
6. A fragile-cut: A says only P06/P07 clear the fragile cap with a stable sign; P02, P10, P12 have sign_stable True but a blank fragile share (not computed), i.e. unknown rather than failed; P11 fragile share 41.16 (4,116%), which carries into B3 F10+P11.
7. E L6M +8.0k / +7.3k for A:P10+D:F07 / F08 is carrying-week-sensitive: with that week kept (nodrop) L6M is +5.9k / +5.2k, and on the ALL basis the dropped-week figure is +4.2k. Treat as 4-8k, not 8k.
8. A "Smoke test passed" wording (see c); E select_E.py 12 min before the log (see d).
9. Positive: ledger sound (h), seal unchanged, no program wrote to MORNING.md as a rule; leads in MORNING.md are labelled leads.

## (g) Live-definition lines vs DS7.cs (checked)
- L443 ThL2Mode ReplacePath (price-path TH off), ThL2ProfitOn false, ProfitMinPts 30, ThickMult 2.0, ThickSecs 10, ProfitTake false, ProfitTrailPts 30; L444 LossOn true, LossMinPts 30, PulledSecs 5, PulledMult 30, warmup 300: matches C and A.
- ManageThL2 L1580 evaluates at most once per second per book; loss cut (L1593-1608) fires when -unreal >= 30 pt AND pulled support in 5 s >= 30 x MedLevel AND the adverse extreme was made within the last 5 s (newMae): matches A "live cell 30/30x/5 s/1, ext 0" and the policy expression pct<=-0.5, pulled_mult>=30, secs_ext<=5.
- Profit branch L1581-1590 (C cites 1579-1590): correct in substance. ice_against L2095 counts refills in the last 30 s (C right). Policy action lock L2204 exists (C right).
- PhOn false: StPhOn/WtPhOn/HmPhOn at L382-385 and the Book constructors (L532-545) set PhOn=false; D right. Note StThOn=true at L381 (TH loss-side ON "by user decision") is inert under ReplacePath; B's baseline (L2 cut = HOLD) consistent.
No inaccuracy found in the live-definition lines.

## (h) Dead-cells ledger appended, not rebuilt
l2vast/ds3/out/uf/DEAD_CELLS.csv: 764,776,439 bytes, 2,424,426 lines. Backup DEAD_CELLS.csv.bak_inst5_1832 (458,669,258 bytes, 2026-10-31): cmp over the full backup length shows the live file begins with the backup byte-for-byte. Last 100 rows: THA_REPLICA_PREPROOF 78 (= 40 + 16 + 22 as A reports), THE_REPLICA_PREPROOF 10, THG_REPLICA_PREPROOF 12, all 25 fields. B, C, D appended no rows and do not claim to (B/C/D reports do not mention the ledger). DEAD_CELLS_NOTES.md untouched since Nov 6.
