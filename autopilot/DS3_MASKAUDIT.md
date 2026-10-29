# DS3_MASKAUDIT - which reports quote HOLD / WF / L8W numbers that include days after 2026-02-06 (MASKAUDIT, 2026-10-29)

Read-only audit. Nothing rescored, no report edited, no deletion, no outcome column of any day after 2026-02-06 opened. Evidence = code text, date axes, report text, DECISIONS.md. Trigger: L2EA finding that `vs_lib.WINS['HOLD']` = `s48score.WINMASK['HOLD']` = `DAYS>=20250701` with no upper bound.

## 1. Verdict (plain)

- The defect is real and wide. `s48score.WINMASK` HOLD, WF and L8W have no upper bound, and the stack DAYS table (`setA_daily.parquet`, 953 label days 2023-02-10..2026-10-16) runs 180 days past 2026-02-06. Capped: HOLD 2025-07-01..2026-02-06 = 31-32 weeks, WF = 105-106 weeks. Uncapped: HOLD 68 wk, WF 142 wk.
- Post-cutoff share of the quoted windows: HOLD about 53% of weeks (36 of 68), WF about 26% (36 of 142). **L8W is 100% post-cutoff** (last 8 WF weeks = 2026-08-24..2026-10-16), so every L8W number from this harness is UNTOUCHED data.
- Scope: about 127 early DS3 reports (written 2026-10-26 T12Z .. 2026-10-28 T11Z, before the cap was adopted), 4 later DS3 reports (CONFIRM_B/FINAL, DIV_VOLGATE, STACK_D, DIV2_A_AUDIT), the whole struct48 / pair-era harness (LEADERBOARD.md PASS/CANDIDATE rows, REPORT_STRUCT48_*, REPORT_BK*, FAILPRED, FOURTH, PBDAY, ASSEMBLY, PRED_ROUND_*) and the DS3 `ds3_addbook` holdout looks.
- Intent differs by program (section 3). In the DS3 early phase the post-cutoff days were knowingly called HOLD in the reports themselves ("HOLD 2025-07..2026-10, 68 wk"); the standing 2026-02-06 cap was applied from about 2026-10-28 13Z. So this is a retroactive protocol breach by the later rule, disclosed in the reports' own text, not a hidden bug. It is still a read of UNTOUCHED aggregates in many quoted numbers.
- Whether any verdict flips is NOT known; that needs the capped rerun. What the reports themselves show about magnitude (all from report text):
  - Live stack, uncapped WF 142 wk: mean 45,947/wk, SD 136,281, maxDD 601,016 (DS3_STACK_D, DS3_DIV_VOLGATE). Capped WF 106 wk: mean 46,785/wk, SD 138,333, maxDD 578,442 (DS3_STACK_B). Implied mean of the 36 post-cutoff weeks about 43.5k/wk; maxDD differs +3.9%; worst week identical (-318,557, pre-cutoff).
  - Stack 20 worst weeks: -$3.74M on the uncapped audit window vs -$3.53M capped (DS3_DIV2_FINAL), 6% apart.
  - Uncapped HOLD for the stack: 47,279/wk, SD 140,987, 68 wk (DS3_STACK_D). The D3SL stack HOLD 49.2k (68 wk) in DS3_PORTFOLIO_SOLVE.
  - Reports that quote a "holdout mean > 0" gate or a HOLD CI therefore had roughly half their HOLD weeks from UNTOUCHED. Sign-level gate flips are plausible for thin cells, unknowable here.
- Selection was not contaminated by this: PRE (WFPRE 2024-02..2025-06) and X (2023-04..2024-01) windows are bounded. The leak is into HOLD, WF, L8W, by-year, and anything built on them (HOLD gate, WF CI, MDE with 142 wk, DSR on WF Sharpe, placebo rank on WF, portfolio WF, year_share).

## 2. Code consumers (file, window, status)

Table source: `l2vast/struct48/code/s48score.py:14-15` defines the unbounded masks (IS, WF `>=20240201`, WFPRE bounded, HOLD `>=20250701`, L8W = last 8 weeks of WF). `l2vast/ds3/code/vs/vs_lib.py:13` copies them into `WINS` (WFPRE, HOLD, WF, X). Weekly counts and `weeks` come from the mask.

UNCAPPED consumers (windows run to 2026-10-16):

| code | window | consumed by (reports) |
|---|---|---|
| `struct48/code/s48score.py` (WINMASK, weekly, maxdd, port_score, score_cell final) | WF/HOLD/L8W | all struct48 tracks: REPORT_STRUCT48*, REPORT_BK*, NEARMISS_RESCORE, LEADERBOARD.md / STRUCT48_LEADERBOARD.md PASS+CANDIDATE rows |
| `struct48/code/{t1score,t2so_score,t2so2_score,t2stack,t2run,t3*,t310b_lib,t4_score,t4_interim,bk1_score,asm_*,nm_e_register,hb_run}.py` | WF/HOLD/L8W (hb_run, t4_score define own `>=20250701`) | REPORT_STRUCT48_T1..T4, _HB, _T2_SO*, _T3_*, BK1/BK2.., ASSEMBLY |
| `ds3/code/vs/vs_lib.py:13` (WINS) | HOLD/WF | D3VS: DS3_SIZING_VOLSCALE, DS3_SIZING_REGIME; imported by dvg, stk_d, bk, close3, open2, sz, sf, ... |
| `ds3/code/ds3_addbook.py:13,51` (S.WINMASK WF/HOLD/L8W, logs addbook_looks.jsonl) | WF/HOLD/L8W | every `ds3_marginal_sharpe`/`add_book` call by early DS3 agents (SPEC_*, PORTFOLIO, CHOP, ...); each call is a logged holdout look at the uncapped HOLD |
| `ds3/code/{tg_run,tg2_run,tg3_run,tl_r8,chop_rob,x_spec,tb_exact}.py` | WF | DS3 portfolio/ED1 reports |
| `ds3/code/chopx_run.py:39`, `nt/nt_score.py:14`, `nt/nt2.py:42`, `cutwait`-style own masks `ld>=20250701` in `te/*`, `tcx/*`, `pbx/*`, `pb3/*`, `pro1-3/*`, `tr1/tr2/tr4`, `tp`, `sl`, `sz`, `ab/ba/cfa/cfc/close3/e1/fp/g1-3/h2-4/ic/m/open2/open2b2/pb4/pf/py/sb/sf/stk_d/t4/ta/tb2/thl/tso/wo` | HOLD `>=20250701` or S./V. masks, no upper bound | all early DS3 reports (list in 3b) |
| `ds3/code/dvg/*` (V.WINS['WF'/'HOLD'], k4 state to 20261016) | WF 142 wk, HOLD 68 wk | DS3_DIV_VOLGATE (written 10-28 14Z, after the first capped code) |
| `ds3/code/stk_d/*` (`ALLM` to 20261016, V.WINS) | WF 142, HOLD 68 | DS3_STACK_D (states "HOLD includes 2026-02..2026-10 as in D3D2A/D3DVG") |
| `ds3/code/dv2a/audit_lib.py` | window 2023-04-03..2026-10-16 | DS3_DIV2_A_AUDIT (descriptive audit; DS3_DIV2_FINAL quotes both uncapped and capped numbers) |
| `failpred/econlib.py:16`, `fourth/step3lib.py:6`, `pred/code/{A_r2_score,A_r11_valid,X5_gscore*}.py` | HOLD `>=20250701` | REPORT_FAILPRED*, REPORT_FOURTH_BOOK, FOURTH_BOOK_PROGRESS, PRED_ROUND_* (102 of them mention HOLD), PRED_FINAL |

CAPPED or bounded (fine): `dvc, dve, dvr, dvx (dvx_flib WMASK & DAYS<=CUT), dv2b, dv2c, dv2d, dv2e, dv2f, ss1, ss2, ss3, sb1, sb2, sb3, sd1, sd2a, sd2b, sd34, sd56, sd6b, ssa, stk_a, stk_b, stk_c, stk_c2, stk_d2, stk_e, stk_f, zen/*, thl_rules, thp, thp_c2, thp_c3, thp_rules, thp_wf_c1, abr, abr_c1, abr_c2, abr_exp2 (after the EXP2 fix), exp1, cutwait, adduw, l2feat, l2h, dipentry, ob, xi, czt/asim own tables`. Notes from reading the code: `thp/thp_run.py:23`, `thp_rules/thpr_run.py:23`, `abr/thp_run.py:23` and `cutwait/cw_run.py:28` have an unbounded `ld>=20250701` mask but the frame D is cut to 20260206 before use (thpr_lib `LD_MAX`, thp_common `CUT_LD`, cw_lib header), so they are fine. `ds3/code/ta/ta1_pseries.py:41` prints a whole-span HOLD row from the full frame (check that frame is cut; it is in the 10-26 early phase and so counts as uncapped). L2EB (10-29) already confirmed own caps.

## 3. Program conventions (what was intended)

a) struct48 (l2vast/struct48, DIRECTIVE_STRUCT48.md, COMMON_BRIEF.md, HARNESS.md, 2026-10-17..19). Brief: "holdout 2025-07+ scored once per track", "UNTOUCHED never read". Harness docs: setA_daily 953 days 2023-02-10..2026-10-16; s48score docstring "WF (>=20240201, 142 wks, includes holdout), HOLD (>=20250701), L8W (last 8 weeks)". So the harness was built to run HOLD and WF to the end of the table, 68 and 142 weeks, and nothing in the struct48 docs defines a sealed forward set. The pair program briefs (BRIEF_COMMON.md) explicitly read "H2 2026-02-07..2026-10-13 once after selection". DECISIONS.md 2026-10-19 (line 1132-1133): the whole program had scored and reported the 2026-02-07..10-16 span; user ruling "HOLDOUT-1 CANCELLED: UNTOUCHED not virgin, never read; forward weeks from 2026-10-19 are the only holdout." Conclusion: in struct48 / pair / pred / failpred / fourth the post-2026-02-06 days were part of the readable HOLD/WF by design and by practice; the s48score unbounded mask matches that convention. They are not "violations" of the then-rule but they are NOT comparable to DS3-capped numbers, and the "UNTOUCHED never read" boilerplate in struct48/COMMON_BRIEF.md is inconsistent with what the harness did. Ambiguity flagged for the user (MORNING).

b) DS3 early phase (2026-10-26 T12Z..2026-10-28 T11Z). COMMON_BRIEF.md/DIRECTIVE_DS3.md say "UNTOUCHED never read; holdout (2025-07+) once per track", no end date. Agents inherited the s48score windows and wrote them into the reports (HOLD 2025-07..2026-10, 68 wk; WF 142 wk). DIRECTIVE_ZEN_20261028.md still wrote HOLD "2025-07..2026-10"; main's note (DECISIONS line 3394, 2026-10-28 18Z) says "standing rule caps reads at 2026-02-06". Cap first appears in code at 2026-10-28 13Z (D3DV1 maps, dvc/dve/dvr/dvx) and in decisions at line 3285. Everything before that is uncapped; exceptions after it that stayed uncapped by choice or oversight: dvg (DS3_DIV_VOLGATE), stk_d (DS3_STACK_D), CONFIRM_B/FINAL (cfa/cfc code dated 10-28 11Z), DIV2_A audit.

c) EXP2 (abr_exp2) hit the same issue, discarded the uncapped run and reran capped (DECISIONS line 3728). That is the only prior self-report found.

## 4. Reports

Classification key: AFFECTED-STATED = the report itself states HOLD to 2026-10 / 68 wk or WF 142 wk. AFFECTED-CODE = no span stated, but code lineage is uncapped (assumed from the era and from sibling reports; flagged weaker). FINE = capped mask, or table only to 2026-02-06, or PRE/X only.

### 4a. AFFECTED-STATED, HOLD span printed (16 DS3 + others)

| report | what it states | numbers that would change |
|---|---|---|
| DS3_SPEC_ST10 | WF 2024-02..2026-10 (142 wk); HOLD 2025-07+ (68 wk); L8W | WF 14,350/wk SD 57,331 maxDD 217,475; HOLD 16,463/wk SD 61,612; L8W 22,235 (100% post-cutoff) |
| DS3_SPEC_PB3B_R5_P1, DS3_P9_PB3B_R5_P1 | HOLD 2025-07.. (68-69 wk, to 2026-10-16/23), WF 142-143 wk | WF 15,062 SD 50,017 Sharpe 2.17 maxDD 361,439; HOLD 18,374; L8W 37,957 / 64,337; HOLD 2x 13,072 / 13.1k; bootstrap CIs; add-book marginal Sharpe (2 + 3 looks) |
| DS3_SPEC_TR1A_ens_s0.5_k4, DS3_SPEC_TR1C_MAMA_10m_flip | HOLD 68 wk | HOLD 24,041 (TR1A), 9,614 (TR1C); L8W; WF maxDD 361,829 / 331,543 |
| DS3_SPEC_PB_ST10_SWZ_T3 | HOLD to 2026-10 | HOLD, WF, L8W rows |
| DS3_SIZING_VOLSCALE, DS3_SIZING_REGIME | HOLD = 2025-07..2026-10, 68 wk | all HOLD deltas, HOLD maxDD single path |
| DS3_PORTFOLIO_SOLVE (+ DS3_PORTFOLIO, DS3_PORTFOLIO_ED1) | PRE 74 / HOLD 68 / WF 142 wk | D3SL stack HOLD 49.2k maxDD 560k; DS2 27.8k maxDD 498k; cap30 HOLD 54.9k maxDD 714k, delta vs DS2 +27.1k [-2.0k,+56.6k] MDE 42k; cap20 +3.9k; every comparator row; NOTHING PASSES verdict is unlikely to flip toward PASS but is unverified |
| DS3_CONFIRM_A / CONFIRM_C / CONFIRM_B | HOLD 2025-07-01..2026-10-16; 68 wk; WF 142 wk | CONFIRM_B headline M +$909 [-546,+2,414] (MDE 2,119) WF; HOLD (68 wk) M +$396 [-1,691,+2,416]; CONFIRM_C HOLD 68 wk table; CONFIRM_FINAL (derived) |
| DS3_STACK_D | WF 142 wk, HOLD 68 wk, base HOLD 47,279 SD 140,987 maxDD 601,016 | all 9 cells' HOLD LM d_mean and WF d_mean (report states the span openly) |
| DS3_DIV_VOLGATE | WF = 2024-02-01..2026-10-16, 142 wk; HOLD MDE 68 wk | WF raw d_mean/CI for all 21 cells (A_skipB -25,067 [-39,455,-11,731] etc.); HOLD LM d_mean (+34,473 [+5,586,+62,952] A_skipT, +8,432 F_hu_vs ...) |
| DS3_OPEN_B2_OR_DRIVE (+ OPEN_FINAL, OPEN_B2_HARNESS, B2_PB_LEVELS_IB, PM_XASSET) | WF 142, HOLD 68 wk | HOLD/WF rows |
| DS3_CENSUS | HOLD 2025-07+ (68 wk) for the library census (MBO part 31 wk, fine) | holdout column and top-50 ranking by holdout Sharpe |
| DS3_ASIM_FINAL, DS3_CZT_FINAL | HOLD (2025-07..2026-10-16) | HOLD columns |
| DS3_TH_LOSS | HOLD to 2026-10 | HOLD rows |
| DS3_DIV2_A_AUDIT | audit window 2023-04..2026-10-16 (185 weeks), 25,898 trades, $7.43M | descriptive; DS3_DIV2_FINAL already quotes both (worst-20 -$3.74M uncapped vs -$3.53M capped); loss-by-slot / range-day shares recomputed on capped table would shift slightly |
| FORWARD_REGISTER, REPORT_DS2_FIRM_V5/V6 | text names 2025-07..2026-10 (H2) | pair-era convention (section 3a) |

### 4b. AFFECTED-STATED via WF 142/143 wk (HOLD span not printed)  [38]

DS3_BLOCKRULES, BOOKS, BOOKS_ED1, CHOP_FINAL, CLOSE_BLOCK1, CLOSE_BLOCK2, CLOSE_FINAL, CONFIRM_D, FOOTPRINT_FINAL, OPEN_B2_HARNESS, OPEN_B2_PB_LEVELS_IB, OPEN_FINAL, PORTFOLIO, PORTFOLIO_ED1, SESSION_LOCKS, SIM_TE6_st10m_n7_m3.0, SIM_TE7_emax5m_f30_s50, SIM_TE7_kelt3m_n14_m1.0, SPEC_B3_F19, SPEC_RVW1_F30, SPEC_TB1_ST_k15_P60_N, SPEC_TB4D_volume_00_volume_1000_ST15_E20_1_T1, SPEC_TB7_ORBNY_k3_P60_N, SPEC_TB9_RENKO_c2_k1_P60_N, SPEC_TB9_RENKO_c5_k1_A3_N, SPEC_TR3_DON15_S, TA, TC, TD, TD1, TD3, TD4, TF, TH, TJ, TK, TPULLBACK2, TPULLBACK3. Their WF mean/CI/DSR/placebo/year-share and HOLD (68 wk) rows include 36 post-cutoff weeks (WF) and 36 (HOLD). (DS3_TA and DS3_CENSUS state the MBO series end 2026-02-06 - that part is fine.)

### 4c. AFFECTED-CODE (no span printed; era + uncapped lineage; verify at rerun)  [73]

DS3_BRACKET_T4, CHOP_B1, CHOP_B23, CHOP_BLOCK0, CLOSE_BLOCK3, CRT_XINSTR, DN_STOPFILL, EXITS_FINAL, FORWARD_W44, H_ITEMS, OPEN_B2_GAP_FADE, OPEN_B2_OR_DRIVE_B3, OPEN_B2_PM_XASSET, OPEN_BLOCK1, PBX_FINAL, PRO1, PRO2, PRO3, PULLBACK_FINAL, SPEC_CRT_H4_M5_close, SPEC_H4_MAMA, SPEC_RSI2T_t10, SPEC_TE6_* (3), SPEC_TE7_* (2), SPEC_TF1_FOMC_NY_block, SPEC_TOPEN_DR5m_pb1_rm0.5_X60_75, STRUCTBRACKET_FINAL, TA1, TB, TB6, TB8, TBRACKET, TBRACKET_SESSION, TB_top20, TC1C2, TC3C4, TC4R4, TC5, TC6PB (+ the *_v1_INVALID_pricing_bug files, already invalid), TD2, TE, TE2E3, TENTRY, TH_G1, TH_G2, TH_G3, TI, TICT, TICT_PROGRESS, TPBX, TPBX_B2, TPBX_B3, TPBX_B3B, TPBX_B4, TPBX_DIRECT, TPULLBACK, TPULLBACK4, TPYRAMID, TR1, TR2, TR4, TREND_FINAL, TSBS, TSCALEOUT, TSTRUCTFIB, TWASHOUT. Also 141 early *_PREHOLD files: these compute PRE only (fine) but name the coming HOLD as 2025-07..2026-10, so their FINAL reports are in 4a-4c. Most of these were "one look at HOLD"; the holdout_looks.jsonl entries for these tracks are looks at the uncapped window.

### 4d. struct48 / pair-era / pred (uncapped by design, section 3a)

REPORT_STRUCT48.md, _T1.._T4 (+ _HB, _T2_SO, _T2_SO2, _T3_1.._T3_10b), REPORT_BK1.._BK11, REPORT_BK1_SETB (holdout +405,178 on 68 wk, 5,959/wk), NEARMISS_RESCORE (+LEAD_CHECK), REPORT_FAILPRED / _STEP2 (holdout 68 wk), REPORT_FOURTH_BOOK, FOURTH_BOOK_PROGRESS (holdout -15.5k/wk), REPORT_PBDAY, REPORT_ASSEMBLY (+ dated runs; HOLD 68 wk, WF-PRE 75 wk, L8W), REPORT_L2_PAIR, REPORT_DS2_*, PRED_ROUND_* / PRED_FINAL, LEADERBOARD.md and STRUCT48_LEADERBOARD.md. LEADERBOARD.md PASS/CANDIDATE counts that rest on the uncapped WF/HOLD columns: PASS 18 (T3 11, NM 7), CANDIDATE 29 (T3 13, NM 14, T1 1, T4 1), PENDING 10. Their effect $/wk CIs, MDE (derived from 142 wk), placebo ranks, DSR and holdout-d columns include 36 post-cutoff WF/HOLD weeks. Under the user's 2026-10-19 ruling these were known-H2-reading programs, so this is a comparability issue with DS3-capped numbers, not an unreported breach.

### 4e. FINE

- Capped mask or bounded table: DS3_STACK_A, STACK_B (149 wk, WF 46,785, 106 wk), STACK_C (HOLD 31 wk), STACK_C2, STACK_D2 (HOLD 32 wk), STACK_E and sub-files, STACK_F, SESSION_1_BOOKS ("HOLD = 2025-07-01..2026-02-06, 32 weeks; the older HOLD is not used"), SESSION_3_PAIRS (32 wk), SESSION2_*, SDISC_*, DIV_1_MAPS, DIV_ES/RTY/YM/ZN/6E/XMKT/CL/GC (cut 2026-02-06), DIV2_B..F, THP_*, THL_*, ZEN_*, ABR_* and ADAPTIVE_EXP1/EXP2 (post fix), CUTWAIT, ADDUW, L2FEAT, L2H, DIPENTRY, SPEC_*_SESSION, all PREHOLD texts (PRE only), L2EB. Caveat: DS3_STACK_E / D3SKE baseline "WF 45,947/wk" printed in an identity test is the uncapped number (disclosed); scoring was capped.
- EXP2 first uncapped run: discarded already (DECISIONS 2026-10-29T19:22Z).

## 5. Recommended capped reruns (no one has run these; owners suggested)

1. MASKFIX (owner: main / a single fresh agent, first): apply the patch below to a COPY or with an env switch, then regenerate `vs_lib.WINS` consumers. Do not touch existing outputs.
2. CAPRERUN-DS3 (owner: one agent per cluster, existing agent names where they exist): SPEC deliverables first - D3X (ST10), D3PB3 / D3P9 (PB3B_R5_P1), D3TR1 (TR1A/TR1C), D3SL (STACK identity), D3VS (SIZING_*), D3PF (PORTFOLIO_SOLVE, ED1), D3CF (CONFIRM_A/B/C/D/FINAL), D3DVG (VOLGATE), D3SKD (STACK_D), then OPEN/CLOSE/CHOP/FOOTPRINT/PULLBACK/TREND finals. Output: new files `*_CAPPED.md` / json next to the old ones (append-only), with the deltas: WF 105-106 wk, HOLD 31-32 wk, L8W re-defined as last 8 weeks to 2026-02-06 (2025-12-15..2026-02-06).
3. Leaderboard rerun (owner: struct48 leaderboard owner / main): recompute WF, HOLD, L8W, MDE (142 -> 106 wk), DSR, year_share for the 18 PASS + 29 CANDIDATE and re-decide verdicts under capped windows; keep the old rows tagged `uncapped`. Also record that struct48 PASS needs 6 conditions that include WF CI and holdout d - these may flip for thin cells.
4. Re-log holdout looks: a capped rerun is a second view of data already seen (HOLD capped is a subset of the uncapped HOLD), so it should be tagged `RESCORE_CAPPED` in `holdout_looks.jsonl`, not a new virgin look; DS3 HOLD 2025-07..2026-02-06 is not virgin either way.
5. Not needed: PRE / X windows, PREHOLD texts, anything in 4e.
6. Priority by decision weight: items that were used to pick live/deliverable books (SPEC_*), the portfolio/stack comparators (PORTFOLIO_SOLVE, STACK_D, VOLGATE), and the LEADERBOARD PASS rows.

## 6. Recommended patch for `s48score.WINMASK` (text only, NOT applied)

```diff
--- l2vast/struct48/code/s48score.py
+++ l2vast/struct48/code/s48score.py
@@ -11,6 +11,10 @@
 _D=pd.read_parquet(OUT+'setA_daily.parquet'); DAYS=_D.ld.values.astype(int); WK=_D.wk.values.astype(int); NDAY=len(DAYS)
-WINMASK={'IS':DAYS<=20240131,'WF':DAYS>=20240201,'WFPRE':(DAYS>=20240201)&(DAYS<=20250630),'HOLD':DAYS>=20250701}
-_wf_wks=np.unique(WK[WINMASK['WF']]); WINMASK['L8W']=np.isin(WK,_wf_wks[-8:])
+# UNTOUCHED rule: trade dates after 2026-02-06 are never read. S48_CAP=0 restores the legacy uncapped harness
+# (struct48 / pair-era reproduction only; windows then run to 2026-10-16: HOLD 68 wk, WF 142 wk).
+UNTOUCHED_AFTER=int(os.environ.get('S48_CAP','20260206'))
+_CAP=(DAYS<=UNTOUCHED_AFTER) if UNTOUCHED_AFTER else np.ones(len(DAYS),bool)
+WINMASK={'IS':(DAYS<=20240131),'WF':(DAYS>=20240201)&_CAP,'WFPRE':(DAYS>=20240201)&(DAYS<=20250630),'HOLD':(DAYS>=20250701)&_CAP}
+_wf_wks=np.unique(WK[WINMASK['WF']]); WINMASK['L8W']=np.isin(WK,_wf_wks[-8:])&_CAP
+assert UNTOUCHED_AFTER==0 or DAYS[WINMASK['HOLD']].max()<=UNTOUCHED_AFTER
```

Companion edits (same patch set):
- `ds3/code/vs/vs_lib.py:13`: no change needed once WINMASK is capped; keep `WINS['X']` bounded. Add `assert DAYS[WINS['HOLD']].max()<=20260206` unless `S48_CAP=0`.
- Hard-coded week counts: `s48score` docstring and `weekly_mde` default ("142 weeks"), `ds3/code/bk/bk_score.py:110` (`/142`), `tb_exact.py:65`; there are 35 grep hits for `/142|142)` in ds3+struct48 code. Replace with `len(weekly(...,'WF'))`.
- `s48score` stage='final' guard: refuse to compute HOLD/WF/L8W if `UNTOUCHED_AFTER` is 0 and the caller did not pass `legacy=True`, and write `S48_CAP` into every rows file so a capped and an uncapped row cannot be mixed in a leaderboard.
- Rows already written by the legacy harness need a `window='uncapped'` tag at read time (leaderboard.py) rather than editing them.
- Side effect to expect: with the cap the whole `WF` MDE changes (142 -> 106 weeks, MDE up about 16%), L8W moves to 2025-12-15..2026-02-06 (a December/January stretch, not a recent stretch), and `S48` DSR n-trials unchanged.
- Alternative minimal patch if no default change is wanted: export `WINMASK_CAPPED` alongside and migrate callers; riskier because the unbounded mask stays the default and the next agent repeats the slip.

## 7. Open questions for the user (also in MORNING.md)

1. Confirm that for struct48 / pair-era programs the post-2026-02-06 days were intended as readable HOLD/WF (the evidence says yes: 142-wk WF in the harness doc, H2 reads in BRIEF_COMMON, user 10-19 ruling), so only the leaderboard comparability needs a capped view, or whether you want those PASS/CANDIDATE rows re-decided on capped windows.
2. DIRECTIVE_ZEN_20261028 wrote HOLD as 2025-07..2026-10 while the standing rule caps at 2026-02-06; please restate the single HOLD definition for DS3 so future agents stop inheriting the unbounded one.
3. Approve the patch with default cap on (legacy via S48_CAP=0), and approve the capped reruns in section 5 (priority order given).
