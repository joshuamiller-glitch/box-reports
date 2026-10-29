# DS3_ADAPTIVE_EXP1 - (a) tighten-family walk-forward, (c) loss deeper arms / MAE-tighten, (e) 3x3 regime tables (2026-10-29)
Research only; no live/execution change; UNTOUCHED (> 20260206) never read; fees identical both arms (FEES.md $4.84 RT); MEASURED basis (market exit 0.995 pt profit side, thl_lib M loss side); deltas paired vs hold-to-bracket (profit) / hold-to-stop (loss), pts/trade over all scored trades, MDE = 2.8 SE (cluster day x session).
Prereg l2vast/ds3/prereg/EXP1_prereg.md sha256 7e9757c26940f1d7bd3481a7e7fd9f43c646b9b5684ce916e3b22e09b23b9615 (DECISIONS.md, with amendments A1-A4: compute-only A1/A2, distillation variants A3, exploratory A4). PREHOLD autopilot/DS3_ADAPTIVE_EXP1_PREHOLD.md sha256 8c4788e0f91884609b2222aab7fa6e5baea255fc31c9ff7e1bfcfab0e06efec2; one HOLD+X' look per side (tracks EXP1_P, EXP1_L). HM sole primary THLHM_L6_a30_r3_w10 untouched. Window audit (coordinator): all masks two-sided, HOLD capped 20260206 (DECISIONS.md). Code l2vast/ds3/code/exp1/, outputs l2vast/ds3/out/thp/wf/exp1/.
Cells scored: 1,526 (profit 66 fixed + 120 chains; loss P11 67 + 60; per-stream 18 x 67 = 1,206; 7 descriptive stream chains).

## Verdicts (V2)
* PROFIT chains: 0 PASS / 3 CANDIDATE / 117 DEAD; fixed cells 0/0/66 (RC family N=186, p=0.035). LOSS P11 chains: 0/0/60 (RC N=127 p=0.64); fixed P11 0/0/67; per-stream fixed 1,206: 0 PASS, 1 in-sample LEAD (HM L6_a45_r3_w20, adj p 0.020, no placebo/neighbour run), rest DEAD (RC N=1,206 p=0.0205).
* Expectations in the prereg held: loss P11 walk-forward ~ +0.1 to +0.3 below MDE; L7m negative; student keeps <50%. Profit was predicted <= +0.1 and came out higher (+0.64 PRE) - but see NOTC.

## (a)+(e) Profit: top chains (pts/trade; PRE / HOLD / X'; N = no target-fill correction, C = doubled friction)
| chain | PRE (MDE) | HOLD | X' | PRE N / HOLD N | PRE C / HOLD C | plc1/plc2 | RC adj p | verdict |
|---|---|---|---|---|---|---|---|---|
| tight\|cell\|6m\|m0.5 | +0.64 (0.84) | +0.41 | +0.29 | +0.16 / -0.48 | +0.34 / +0.08 | 1.0/1.0 | 0.32 | CANDIDATE (fails NOTC) |
| all\|cell\|6m\|m1.0 | +0.61 (0.79) | +0.53 | +0.34 | +0.17 / -0.31 | +0.34 / +0.23 | 0.9/1.0 | 0.31 | CANDIDATE (NOTC, placebo<0.95) |
| all\|cell\|6m\|m0.5 | +0.61 (0.83) | +0.65 | +0.33 | +0.11 / -0.56 | +0.31 / +0.25 | 0.9/1.0 | 0.35 | CANDIDATE (NOTC, placebo<0.95) |
| all\|cell\|6m\|m0.0 | +0.60 | +0.73 | +0.25 | -0.04 / -0.66 | | 0.9/1.0 | 0.40 | DEAD (placebo, NOTC, year share) |
* By scope (mean chain PRE): cell +0.36, bookcell -0.04, pooled -0.15, perbook -0.53. Only the 3x3 (vol x session) regime keying carries the effect; per-book and pooled chains are negative. At the (e)-primary 3-month window every cell chain is DEAD (PRE +0.17..+0.50, HOLD -0.36..+0.18).
* Where the gain comes from (top chain, PRE): trades whose base exit was the stop: +6.98 pt-per-span-trade contribution (45% of them exited early); trades whose base exit was the target: -6.46; net +0.64. About 0.48 of the 0.64 is the measured target limit-fill correction (fill_cost 2.7 pt PRE, 4.2 HOLD) that market exits avoid: on N basis PRE +0.16 / HOLD -0.48. This is why NOTC fails; treat the profit candidate as basis-dependent, not as an edge established by the path alone. Weekly-path maxDD at lots 1.82M vs 2.92M base; worst-20-weeks -7.4M vs -10.1M ($; 1.0 lot multiples as in THPC3) - drawdown improves because stop-base trades are cut.
* Fixed cells: no tighten-family fixed cell is robust (family bests PRE: F0 D4_a75 +0.04, F7 take_p70 +0.26, others <= 0; F6 steps -0.40). F7_take_p90: PRE +0.23 (CI > 0), HOLD +0.62, X' 0.00, adj p 0.035, N -0.15/-0.14 (fails only NOTC); DEAD by V2.
* Best fixed action per 3x3 cell is dominated by one cell (descriptive, post-look): vol_lo+ON take at 50% of target: PRE +4.27 (CI +2.1..+6.4, n=3,224), HOLD +3.52 (+0.7..+6.4), X' +2.97 (-1.0..+6.9); N basis +2.9/+1.65/+2.3 and C basis positive in all three; 9 of 10 books positive; every year positive; RC over 594 cell x action pairs adj p 0.027. Exploratory A4: F7-only cell chains PRE +0.73 (CI +0.31), HOLD +1.22, X' +0.15, but HOLD N basis <= 0. LEAD only (found after the look); needs the forward sample.

## (c) Loss: deeper arms 25-45, windows 5-20 s, MAE-tighten
* P11 walk-forward: best chain all|pooled|ew10|m0.5 PRE +0.29 (MDE 0.73), HOLD +0.28, X' +0.75 (all three positive, none distinguishable from 0), N +0.20/+0.02, DEAD (CI, neighbours, RC p 0.64, placebo-1 rank 0.0: random cell choice does as well, because the menu itself is mildly positive). Regime/book keyed loss chains: cell scope best +0.10, perbook <= -0.12, bookcell <= +0.11.
* Arm trend (equal weight over 11 intraday streams, fixed cells, PRE): arm 25 -1.0 (2 of 3) / -0.5 (3 of 3); arm 30 -0.8/-0.3; 35 -0.6/-0.3; 40 -0.4/-0.1; 45 +0.10/+0.01 (HOLD +0.21/+0.26). Deeper is monotonically less harmful; window 5-20 s makes no systematic difference (PRE -0.5..-0.6 for 2 of 3, -0.1..-0.3 for 3 of 3). L7m (stop to MAE-b after N s) mean -0.84 PRE, best fixed -0.16: no value.
* Every book (best PRE cell per stream, see exp1/stream_fixed_B.csv): HM L6_a45_r3_w20 +1.64 (MDE 1.24) HOLD +0.52 X' +0.01 adj p 0.020 (in-sample LEAD); PB L6_a45_r2_w10 +1.62 but HOLD -0.37 (DEAD); all other streams adj p >= 0.93 or negative HOLD. Only HM and PB positive on average across the grid (stream means PRE +0.67 / +0.90).
* HM primary a30_r3_w10 in this grid: PRE +1.37, HOLD positive, X' <= 0 (SPAN2 fail), CI includes 0, adj p 0.94 in the 1,206 family; consistent with the HM retest. Nothing here changes it; no second primary. Kernel check: a30_r3_w10 reproduces hm9.npz to 3.6e-6.
* D6 and CR streams (descriptive 3m chain): all CI include 0 (MDE 2.6-9.8).

## Distillation to <= 12 rules (rolling monthly refit on trailing 12 months, so student numbers are out of sample)
Profit teacher tight|cell|6m|m0.5 (PRE +0.636, HOLD +0.411, X' +0.422 on the common trades):
| student | PRE | HOLD | X' | retained PRE / HOLD / X' |
|---|---|---|---|---|
| bal (pooled 12 leaves) | -1.30 | -1.27 | -2.41 | negative (fires 75%) |
| unbal (pooled) | -0.03 | +0.12 | -0.11 | -5% / +30% / -26% |
| volsplit (3 x 4 leaves, vol regimes) | +0.19 | +0.07 | +0.09 | 29% / 18% / 22% |
The 8 THP features cannot see the vol x session key that carries the teacher, so distillation keeps < 30%. The table (teacher) beats the distilled rules; it needs a two-token regime (vol_x+ON|AM|PM) that the current format lacks.
Loss teacher all|pooled|ew10|m0.5 (PRE +0.292, HOLD +0.285, X' +0.585): students PRE -0.56 (bal) / -0.31 (unbal) / -0.33 (volsplit), HOLD -0.16 / +0.04 / -0.06: retained gain negative / ~0 -> no loss rule.

## Candidate rule text (THP_POLICY format) and nightly
* l2vast/ds3/out/thp/wf/exp1/policy_candidate_exp1.txt (what the nightly would publish for asof 20260206: profit = 8-rule 3x3 table from the 6m cell chain, WF last-6m +0.40 / all +0.53; loss EMPTY) and policy_candidates_tables_students.txt (table and student rules for both sides; loss table is the 3m cell chain, whose own WF is +0.01 all / -0.26 last-6m, so not published). Approximations flagged in the header: profit trails latch once matched, arm uses current pct instead of MFE/target, ATR and MFE-fraction trails are frozen to cell medians, L6 conditions use vel30/eff120 for the w-second windows.
* decisions_exp1_profit.parquet / decisions_exp1_loss.parquet (THP SCHEMA, all 120 + 60 chains, cfg = chain id, cell_action = chosen cell, exit_ts from the 1-s exits, scored trades only; loss trade_id = stream*10^7 + row, there is no tid in the THL streams).
* Nightly (single command, ~10-15 min, refuses asof > 20260206 unless EXP1_ALLOW_POST_CUT=1): `cd l2vast/ds3/code/exp1 && OMP_NUM_THREADS=1 python3 exp1_nightly.py --asof YYYYMMDD [--rebuild] [--no-student]`; config out/thp/wf/exp1/winners.json; writes nightly/EXP1_POLICY_<asof>.txt, *_candidates.txt, table CSVs and MORNING_LINE_<asof>.txt (does not edit MORNING.md or THP_POLICY.txt). New days need the THPA/THL tables extended first (--rebuild); sections with WF < -0.5 publish EMPTY.

## Caveats / for the lead
1. Profit CANDIDATEs fail NOTC; the choice between M and N target-fill bases decides whether the 3x3 table is real. Needs the live target-fill measurement.
2. Profit selection by regime is the only thing that works; the format needs a two-token regime to publish it.
3. All loss results are below MDE; HM deeper arm a45 is in-sample LEAD only; HM primary a30_w10 remains the sole forward test.
4. Distillation was changed after stage B (A3) - all three variants are shown; none of them reaches 50% retained gain.
