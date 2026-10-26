# REPORT PX33 - WT-10 as a separate-account sleeve with ONE denoiser each (2-min path, Heikin-Ashi, Kalman, 3-bar median)

**Verdict: NO (0 FOUND, 0 LEAD).** Most important number: the only cell to pass Stage A, P3 (Kalman-filtered trail input), adds +0.39 weekly Sharpe on clean at a 20% share (above the selection-corrected null p99 0.35) but **-0.04 on H1 and 0.00 on H2** (fails gate 3 on both), plateau 5/10, and **1 of 3 replication legs** (needs 2): H0 -0.08, ES -0.13 / RTY -0.06, alternating months pass. The other three denoisers fail already at Stage A on clean (P1 -0.06, P2 +0.07, P4 +0.06 vs the +0.10 eligibility line), so their H1/H2 were never read. The denoisers do not cure WT-10's plateau or replication failures; the parent control reproduces at +0.37 clean. Cells: 4 (+ untested control C0 = WT-10). Runtime about 1 h on a 4-worker pool. Pre-registered in PREREG_AUTOPILOT.md ('PX33 ...') before any denoised cell ran. Status: `status/PX33.txt`.

## 0. Setup (as registered)
- Parent: WT-10 = ATR14 / mult 3 / no EMA / 10-min / 60-60 bracket, TH off (REPORT_WT.md, REPORT_WT2.md: LEAD, plateau 3/8, ERA negative pre-2023, no modern replication). Engine = the WT/WT2 NT8-faithful 1-second path (nt8sim stop/target on second bars, entry at flip-bar close -> next 1-min open, sessions as ST/HM), sleeve in its OWN account with its own rules at R = $9,600 (per-book 5R/-2R, day lock cap 8R / arm 2R / keep 33%, week floor 8R, 4R variant reported), no netting with ST/HM. Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = 2 ticks/side. Baseline pair = pair_base.npz (B.Cfg(wk_floor=8,wk_loss_pb=None), clean process) weekly Sharpe 1.46/2.83/2.30. Control C0 reproduces WT-10 bit-for-bit (signals and trade list equal to `ap_wt_gate.cell_trades`; clean 20% uplift +0.367).
- Cells (denoised series replaces the 10-min close in the Wilder ratchet trail; ATR14 from the stated bars): P1 2-min sampled path for bar H/L/ATR (s=2); P2 Heikin-Ashi (alpha 0.5); P3 local-linear-trend Kalman (rho 0.03, steady level gain 0.45); P4 3-bar median close.
- Code: `code/census/night_ins/ap_pd4_sig.py` (denoisers), `ap_pd4_gate.py`, `ap_pd4_a.py` (Stage A), `ap_pd4_b.py` (Stage B), `ap_pd4_fam.py` (selection-corrected null), `ap_pd4_rep.py` (legs), `ap_pd4_era.py`, `ap_pd4_lib.py`; outputs `outputs/autopilot/pd4/`.
- Non-virgin disclosure: the parent's clean, H1, H2, H0, ES/RTY and parity months were all read in WT/WT2/B8WT. No span is virgin for this lead; selection here is clean-only and H1/H2 were read once, only for the one eligible cell. Newest live weeks: none beyond 2026-10-13 (leg L1 n/a).

## 1. Stage A (clean 2023-08..2025-07 only; uplift = additive weekly Sharpe at 20% share)
| cell | trades (all / clean) | win % clean | pts/trade clean | clean sleeve Sharpe | clean uplift @20% | eligible |
|---|---|---|---|---|---|---|
| C0 WT-10 (control) | 2280 / 1191 | 53.7 | +4.48 | 1.99 | +0.367 | yes (not a test cell) |
| P1 2-min path | 3251 / 1658 | 49.8 | -0.25 | -0.25 | -0.057 | NO |
| P2 Heikin-Ashi | 1704 / 914 | 50.8 | +1.02 | 0.76 | +0.070 | NO |
| P3 Kalman | 2003 / 1051 | 54.1 | +5.51 | 2.08 | +0.389 | yes |
| P4 3-bar median | 1847 / 988 | 51.2 | +1.87 | 0.65 | +0.058 | NO |
Win rate moves by at most +0.4 pt (P3) or falls 2-4 pts (P1, P2, P4), i.e. the E1 lever (2-5 pts of win rate) is not delivered by smoothing the trail input. P1 shortens the sampled-path ATR (about 1.6x the flips), so it is effectively a tighter trail; reported as registered. Non-eligible cells are NO; H1/H2 not reported for them (library files store the full series by rule; not used for any verdict).

## 2. Stage B: P3 Kalman (WT-10 + Kalman), gates
Sleeve alone (own rules, 8 contracts): weekly Sharpe clean/H1/H2/all 2.08/0.98/0.12/1.45 (WT-10 parent all-in 2.05). 1,787 trades in the pair window (not small-sample). Scale to pair risk x2.24.

Additive uplift (weekly Sharpe) by share, clean / H1 / H2 / all (bootstrap 90% CI of all-in, own-null p95 of all-in uplift):
| share | clean | H1 | H2 | all | boot CI | null p95 |
|---|---|---|---|---|---|---|
| 10% | +0.20 | -0.01 | +0.01 | +0.14 | [+0.04,+0.24] | 0.17 |
| 20% | +0.39 | -0.04 | 0.00 | +0.25 | [+0.06,+0.46] | 0.31 |
| 30% | +0.55 | -0.10 | -0.04 | +0.34 | [+0.05,+0.65] | 0.43 |
| 50% | +0.80 | -0.25 | -0.16 | +0.45 | [-0.01,+0.94] | 0.58 |
Constant-risk framing (16 contracts-equivalent total) 20%: +0.47 / -0.07 / -0.02 / +0.30; 50%: +1.08 / -0.61 / -0.57 / +0.46. Worst week of pair+sleeve vs pair (8R floor): +4.4 / +15.3 / +36.4 / +78.7% at 10/20/30/50% (limit = share: fails at 30 and 50%); with the 4R floor +4.6 / +15.6 / +26.6 / +48.7% (passes all shares) and uplift clean +0.42 / H1 +0.05 / H2 +0.11 at 20%.

Insurance metric set, sleeve alone (8 contracts, own rules):
| span | net $ | Sharpe | Sortino | MAR | maxDD $ | worst week $ | CVaR5 | CVaR10 | %neg weeks |
|---|---|---|---|---|---|---|---|---|---|
| clean | 844,303 | 2.08 | 3.42 | 3.51 | 240,769 | -77,749 | -52,277 | -45,679 | 31.4 |
| H1 | 115,335 | 0.98 | 1.51 | 1.05 | 109,624 | -58,749 | -53,739 | -50,377 | 46.4 |
| H2 | 18,116 | 0.12 | 0.17 | 0.12 | 149,873 | -77,949 | -68,349 | -54,293 | 50.0 |
| all | 977,754 | 1.45 | 2.25 | 4.06 | 240,769 | -77,949 | -57,562 | -49,445 | 38.1 |

Other gates: own timing-destroyed null (200 draws, same count/hold/bracket) standalone all-in Sharpe 1.45 vs p95 0.72, rank 1.00 PASS; 2x slippage uplift (20%, all-in) +0.35 / -0.05 / -0.01 (all-in +0.22) FAIL on H1/H2; worst-decile-week corr with pair -0.27 (all-weeks corr +0.01) PASS; margin/NT8: NQ 8 lots in a separate NT8 account via Rithmic, margin not verifiable on the box (as WT).

Plateau, ten one-at-a-time +-25% neighbours (all-in uplift, keep = >= 75% of 0.252): ATR 11 / 18: 0.211 K / 0.175 -; mult 2.25 / 3.75: 0.201 K / 0.008 -; bracket 45 / 75: 0.127 - / 0.069 -; tf 7 / 13: 0.234 K / 0.005 -; rho 0.0225 / 0.0375: 0.269 K / 0.320 K. **5 of 10 keep = 0.50, FAIL** (parent 3 of 8). The 16 denoiser x WT-parameter corners (reported): 4 of 16 keep. The denoiser parameter itself is flat; the failures are the same WT sensitivities as the parent (multiplier 3.75, timeframe 13, bracket width), so the Kalman filter changes none of them.

## 3. Nulls
- Own timing-destroyed null: PASS (above).
- Selection-corrected null (100 replicates; each replaces the pair-window trades of all four cells by timing-destroyed ones with the same count/hold/bracket and re-runs Stage A): best clean uplift across the four cells has median 0.04, p90 0.19, p95 0.235, p99 0.35; the real best (P3, 0.389) is above the 99th percentile (1 of 100 replicates reach it; at least one eligible cell in 31 of 100). The clean-span edge is therefore not a four-cell selection artefact (the same finding as WT2's family null: the 2023-26 structure is real as structure); what it lacks is H1/H2, plateau and replication. No replicate passed uplift >= +0.10 on all three spans (0 of 100).
- Circular-shift null: reported by the harness only through the all-in own-null above (no hedge claim made).

## 4. Replication legs (>= 2 of L2-L4 needed, each with the same sign and >= 50% of the cell's all-in 20% uplift)
| leg | C0 parent (context) | P3 Kalman | pass for P3 |
|---|---|---|---|
| L1 newest live weeks | none after 2026-10-13 | none | n/a |
| L2 H0 2023-02-10..07-31 (26 weeks) | uplift -0.09 | -0.08 (needs >= +0.13) | FAIL |
| L3 ES 2023-26 (1-min engine, scaled bracket) | +0.07 | -0.13 | FAIL |
| L3 RTY 2023-26 | -0.06 | -0.06 | FAIL |
| L4 odd / even months (all-in 0.25) | +0.07 / +0.61 (full 0.37) | +0.16 / +0.33 (needs >= +0.13 each) | PASS |
**1 of 3 legs -> replication FAILS.** The denoiser does not add a single leg relative to the parent (parent: 0 of 3; P3 passes the parity split because its odd-month uplift is higher than the parent's, +0.16 vs +0.07, but both are still concentrated in even months). NQ on the 1-minute engine (cross-check of the same cell, different fill model): P3 20% uplift +0.27 / +0.09 / -0.31 clean/H1/H2.

## 5. ERA flag (NQ 2013-2026 back-adjusted 1-min, bracket 60 x price/20000, reported not gating)
P3 gross ticks per trade by year: 2013-22 mean about -2.3 (range -17.2 in 2022 to +5.4 in 2018), 2023 -1.9, 2024 +27.2, 2025 +12.0, 2026 -5.2 (WT-10 parent: 2013-22 mean about -1.0, 2023-25 +16 to +24). Net R per trade at fixed cost 2013-22 negative in 9 of 10 years; at price-scaled cost negative in 7 of 10. **ERA FLAG: negative pre-2023** (gross-negative, not only cost-eaten), and P3's 2023 and 2026 are also negative gross, i.e. weaker than the parent in the modern era. Full table: `pd4/era.csv`.

## 6. Mechanism and structure dependence
Mechanism (one sentence): a Kalman-smoothed trail input should delay noise flips of the 10-min ratchet more than real ones; it does not change win rate (54.1% vs 53.7%) and leaves WT-10's multiplier/timeframe/bracket sensitivities intact, so the clean gain is the parent's 2023-25 trend-persistence edge (even-month, regime dependent), not a denoising effect. Depends on current structure: yes (negative before 2023, absent on ES/RTY and H0).

## 7. FOUND checklist, P3 (others failed Stage A)
| gate | result |
|---|---|
| 1 pre-registered | PASS |
| 2 clean-only selection, H1/H2 once | PASS |
| 3 uplift >= +0.10 clean/H1/H2 | clean PASS, **H1 FAIL (-0.04), H2 FAIL (0.00)** |
| 3b worst week not worse than share | PASS 10/20% (8R), fail 30/50% (8R); pass all with 4R floor |
| 4 own null p95 / bootstrap CI > 0 / selection-corrected null | PASS / PASS (lo +0.06) / PASS (above p99) |
| 5 plateau | **FAIL 5/10** |
| 5 2x slippage | **FAIL (H1 -0.05, H2 -0.01)** |
| 6 worst-decile corr <= +0.30 | PASS (-0.27) |
| 7 NT8 spec + margin | spec yes; margin not on box |
| replication >= 2 of {L2,L3,L4} | **FAIL (1 of 3)** |
| ERA flag | negative pre-2023 |

## 8. Library
Saved P1-P4 as `PX33_WT10_P1..P4` (standard size 8 contracts, R = $9,600, netting NQ_INTRADAY, separate account required) with verdict NO. Control WT-10 is already in the library.

## 9. Disclosure, executability
Four cells registered, one eligible; no re-runs; no parameter changes after seeing results. Expected false FOUNDs for this family under all gates: well below 0.01 (0 of 100 null replicates pass uplift on all three spans). Executability: NT8 strategy with a Kalman/median/HA series computed bar by bar in OnBarUpdate on the 10-min series; NQ via Rithmic in a separate account.

DONE PX33
