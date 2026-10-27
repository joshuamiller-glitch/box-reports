# DS3_SESSION_LOCKS - T-SESSION-LOCKS (D3SL, 2026-10-27). Research output; NOT a live recommendation. No execution-server / chart / live-file change.

**Session locks: 0 PASS, 3 CANDIDATE. Best: WT/NY/P2+N1 (MAPPED basis), stack maxDD delta -31,005, worst-week delta +474, income delta +1,386/wk, Sharpe delta +0.118.** (stack = DS2+DS3 at unchanged lots, WF 142 weeks; all three CANDIDATEs fail ONLY G8, the family-wise best-of-N null at d_Sharpe > 0.334; best cell found is 0.118.) 795 of 798 cells DEAD.

Scored: 798 cells = 7 books (ST10, HM10, WT7, KB, SM, PB3B_R5_P1, PB_ST10_SWZ_T3) x 3 sessions x 38 (a 4 + b 6 + c 4 + d 24), 42 preregs of 14/24 cells (master l2vast/ds3/prereg/SL_MASTER_prereg.md sha256 7b97f178eac58d887bf010a5fdd7e153518f56ca749ceaab60cf5467a18bb4ce; per-group sha256 in DECISIONS.md and l2vast/ds3/out/sl/prereg_hashes.json; all written before any rule cell was scored; trial ledger +798, cumulative 53,018). Rows: l2vast/ds3/rows/DS3_TSESSLOCK_<BOOK>.json (7 files). Code l2vast/ds3/code/sl/. Disclosures: 42 holdout looks logged (one per prereg group, tracks DS3_TSESSLOCK_SL_<book>_<session>_<ABC|D>), 1 further holdout re-read through ds3_addbook (equal_risk.py marginal for the PB candidate, track EQUAL_RISK, logged in addbook_looks.jsonl).

## Definitions used (state)
- Sessions (user): Asia 18:00-02:00, London 02:00-09:30, NY 09:30-16:55 ET (session id by 1-minute bar start; FAILPRED used 18:00-03:00/03:00-09:30/09:30-18:00, not used here). Shifted-boundary placebos move all three boundaries by +/-1 h and +/-3 h.
- Halt semantics (PRIMARY): session P&L = realised + open mark-to-market on the 1-s tape since the session start (a carried-in position is re-based to the session-start mark); at the trigger the open position is FLATTENED at the next printed second and all later entries of the session are cancelled; resume at the next session. This mirrors the existing give-back arm / week floor (cancel entries + flatten). Sensitivity arms for candidates and the top 10: "real" (evaluated on realised P&L at trade closes, no flatten; the style of the existing -2R/+5R entry test) and "nofl" (MTM trigger, cancel entries, let the open position run to its bracket).
- Stack: DS2 = ST10+HM10+WT7 (per-book locks) + DS3 = KB + SM + PB3B_R5_P1 (monthly 26-week inverse-SD weights frozen at baseline, DS3 peak 23 lots; variant B = PB_ST10_SWZ_T3 in the PB slot for the PS cells). Baseline stack WF: $48,560/wk, SD 142,165, maxDD 731,292, worst -270,040, Sharpe 2.46 (HOLD 49,207). This is NOT the older published DS2+DS3 line (different third DS3 book and weighting scale); only deltas vs this baseline matter.
- Paired: every cell is the same stack with one book/session rule swapped in; weekly paired bootstrap (2,000) and per-session paired test (entry-session attribution).
- Engine identity: baseline (no rule) reproduces the published daily series of all 7 books to $0.00 (l2vast/ds3/code/sl/sl_ident.py).

## Gates (never softened; see master prereg)
G1 crit(WF-PRE) ; G2 crit(HOLD) ; G3 placebo rank of d_Sharpe vs 4 shifted-boundary + 100 random-halt runs (PASS >= 0.95, CAND >= 0.90) ; G4 >= 75% grid neighbours d_Sharpe > 0 ; G5 95% paired-bootstrap CI of d_SD or d_maxDD excludes 0 ; G6 crit(2023-04..2024-01) ; G7 worst week not worse and d_Sharpe > 0 ; G8 d_Sharpe above the 95th percentile of the max over all 798 cells of the paired sign-flip null. crit(w) = [d_mean >= 0 and (d_SD < 0 or d_maxDD < 0)] or [d_mean > 0 and d_maxDD <= 0]. Failure counts over all 798 cells: G8 798, G3 734, G5 639, G7 612, G4 570, G6 540, G2 531, G1 522. 15 cells are duplicates of an identical book series (flagged).

## Verdicts
| tier | n | cells |
|---|---|---|
| PASS | 0 | - |
| CANDIDATE | 3 | WT|NY|P2; WT|NY|P2+N1; PB|NY|G1k50 |
| DEAD | 795 | listed with failed gates in rows JSON; insurance-flagged (income down, risk down) 38 |

## Candidates (all fail only G8)
| cell | basis | d_mean $/wk | d_SD | d_maxDD | d_worst | d_Sharpe | HOLD d_mean / d_Sharpe | 2023 span d_mean | placebo rank (shift min / random beaten) | G5 CI d_SD | session-paired d_mean $/session [CI] (MDE) | equal-risk d_mean / d_maxDD / d_worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| WT|NY|P2 | MAPPED | +695 | -1,131 | -20,216 | +0 | +0.055 | +1,083 / +0.063 | +35 | 0.962 (-0.018 / 0.97) | [-1,978, -378] | +263 [-30, 575] (1,677) | +1,090 / -14,515 / -2,165 |
| WT|NY|P2+N1 | MAPPED | +1,386 | -2,626 | -31,005 | +474 | +0.118 | +2,718 / +0.174 | +1,617 | 0.962 (+0.004 / 0.97) | [-4,628, -641] | +525 [-159, 1,242] (1,677) | +2,325 / -17,828 / -4,599 |
| PB|NY|G1k50 | DIRECT | +526 | -2,066 | -41,126 | +0 | +0.063 | +563 / +0.037 | +398 | 0.962 (-0.028 / 0.96) | [-4,012, -42] | +142 [-441, 746] (2,037) | +1,250 / -30,947 / -3,983 |

Reading: all three are risk-side improvements with a small non-negative income effect (the mean effect is inside the MDE: weekly mean MDE 5-6k $/wk and per-session MDE 1.7-2.0k vs effects of 0.5-1.4k/wk; the d_maxDD CI includes 0 in every case, the d_SD CI excludes 0 for WT P2, WT P2+N1 and PB G1k50 [upper bounds -378, -641, -42]). They are NOT insurance (income not down). WT cells are on the MAPPED basis (no direct replay of WT rows) and WT7 P2 is a trigger subset of P2+N1 (one idea, not two). The PB give-back (arm +1R, keep 50%, NY) has HOLD d_Sharpe +0.04, 2023 span d_mean +398, but L8W d_Sharpe -0.09; VIX terciles mixed (low-VIX d_mean -2.7k, high +4.1k).

### Candidate detail by year / VIX tercile (WF weeks; d_mean $/wk, d_SD $/wk)
- WT|NY|P2: y2024 (49 wk) -360/-1,934; y2025 (52 wk) +1,298/-1,147; y2026 (41 wk) +1,191/-298; v0 (55 wk) +249/-619; v1 (38 wk) +1,326/-1,878; v2 (49 wk) +705/-1,015  (v0 low, v1 mid, v2 high VIX)
- WT|NY|P2+N1: y2024 (49 wk) +345/-4,169; y2025 (52 wk) +638/-673; y2026 (41 wk) +3,577/-3,140; v0 (55 wk) +1,783/-2,428; v1 (38 wk) +391/-3,485; v2 (49 wk) +1,710/-2,256  (v0 low, v1 mid, v2 high VIX)
- PB|NY|G1k50: y2024 (49 wk) +1,557/-4,130; y2025 (52 wk) -546/+198; y2026 (41 wk) +654/-2,227; v0 (55 wk) -2,713/-1,297; v1 (38 wk) +599/-3,725; v2 (49 wk) +4,105/-1,271  (v0 low, v1 mid, v2 high VIX)

### Sensitivity of the halt reading (stack WF deltas: mean / SD / maxDD / worst / Sharpe)
| cell | mtm+flatten (primary) | realised only, no flatten | MTM trigger, run to bracket |
|---|---|---|---|
| WT|NY|P2 | +695 / -1,131 / -20,216 / +0 / +0.06 | +91 / -267 / -1,730 / +0 / +0.01 | -37 / -701 / -7,936 / +0 / +0.01 |
| WT|NY|P2+N1 | +1,386 / -2,626 / -31,005 / +474 / +0.12 | +960 / -2,109 / -18,726 / +474 / +0.09 | +856 / -2,250 / -18,726 / +474 / +0.08 |
| PB|NY|G1k50 | +526 / -2,066 / -41,126 / +0 / +0.06 | +216 / -709 / +4,615 / +0 / +0.02 | +541 / -2,121 / -27,204 / +0 / +0.07 |
| HM|London|P2+L1 | +4,403 / -2,279 / -2,807 / -6,048 / +0.27 | +1,601 / -3,309 / -159 / -9,833 / +0.14 | +2,606 / -2,319 / -24,247 / -9,833 / +0.18 |
| HM|London|P1.5+L1 | +2,967 / -3,483 / +12,753 / +1,994 / +0.22 | +2,539 / -3,782 / +5,916 / -9,833 / +0.20 | +2,614 / -2,567 / -18,172 / -21,785 / +0.18 |
| ST|London|P2+N1 | +3,056 / -2,970 / -127,291 / -16,431 / +0.21 | +1,546 / -2,409 / -136,678 / -16,431 / +0.12 | +1,546 / -2,409 / -136,678 / -16,431 / +0.12 |
| HM|London|P1.5+N1 | +1,789 / -5,395 / -65,979 / +1,344 / +0.19 | +1,773 / -4,041 / -84,724 / -22,243 / +0.16 | +1,756 / -4,035 / -84,724 / -22,243 / +0.16 |
| HM|London|P1+L1 | +1,157 / -6,720 / -40,813 / +1,752 / +0.18 | +3,694 / -6,182 / -17,496 / +0 / +0.31 | +4,328 / -5,448 / -39,602 / +0 / +0.33 |
| HM|London|P2+N1 | +2,216 / -3,780 / -81,540 / -22,243 / +0.18 | +989 / -3,668 / -90,799 / -22,243 / +0.12 | +989 / -3,668 / -90,799 / -22,243 / +0.12 |
| ST|London|N1 | +3,048 / -1,044 / -141,892 / -16,431 / +0.17 | +3,048 / -1,044 / -141,892 / -16,431 / +0.17 | +3,048 / -1,044 / -141,892 / -16,431 / +0.17 |
| HM|London|L1 | +2,995 / -1,182 / -13,309 / -6,048 / +0.17 | +2,191 / -1,830 / -1,401 / -9,833 / +0.14 | +2,900 / -1,015 / -25,490 / -9,833 / +0.17 |
| HM|London|P3+L1 | +2,711 / -1,448 / -13,309 / -6,048 / +0.16 | +2,186 / -1,836 / -1,401 / -9,833 / +0.14 | +2,901 / -1,019 / -25,490 / -9,833 / +0.17 |
| HM|NY|L1 | +1,800 / -3,899 / -41,437 / -11,894 / +0.16 | +1,413 / -1,214 / -23,051 / +0 / +0.09 | +2,644 / -1,754 / -14,147 / +0 / +0.17 |

Flatten vs run-to-bracket changes the answer: the WT NY P2 effect disappears under run-to-bracket (mean -37, Sharpe +0.01) and the PB give-back maxDD gain is partly the flatten price convention (realised-only reading: maxDD +4.6k worse). A live implementation must therefore flatten at market exactly as modelled; the modelled flatten price (next-second tape, no stop-join credit) is the engine convention.

## Top 10 by stack d_Sharpe (WF) regardless of verdict
| # | cell | verdict | failed gates | d_mean | d_SD | d_maxDD | d_worst | d_Sharpe | HOLD d_Sharpe | rank | weekly-mean MDE / session MDE | forward weeks |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | HM|London|P2+L1 | DEAD | G5,G7,G8 | +4,403 | -2,279 | -2,807 | -6,048 | +0.267 | +0.123 | 0.99 | 9,550 / 2,632 | 0 |
| 2 | HM|London|P1.5+L1 | DEAD | G2,G3,G5,G8 | +2,967 | -3,483 | +12,753 | +1,994 | +0.216 | +0.011 | 0.91 | 9,550 / 2,632 | 0 |
| 3 | ST|London|P2+N1 | DEAD | G3,G5,G6,G7,G8 | +3,056 | -2,970 | -127,291 | -16,431 | +0.211 | +0.308 | 0.91 | 9,282 / 2,828 | 0 |
| 4 | HM|London|P1.5+N1 | DEAD | G3,G8 | +1,789 | -5,395 | -65,979 | +1,344 | +0.192 | +0.057 | 0.84 | 9,550 / 2,632 | 0 |
| 5 | HM|London|P1+L1 | DEAD | G2,G3,G6,G8 | +1,157 | -6,720 | -40,813 | +1,752 | +0.184 | +0.116 | 0.88 | 9,550 / 2,632 | 0 |
| 6 | HM|London|P2+N1 | DEAD | G3,G5,G7,G8 | +2,216 | -3,780 | -81,540 | -22,243 | +0.183 | +0.063 | 0.82 | 9,550 / 2,632 | 0 |
| 7 | ST|London|N1 | DEAD | G3,G5,G6,G7,G8 | +3,048 | -1,044 | -141,892 | -16,431 | +0.174 | +0.227 | 0.87 | 9,282 / 2,828 | 0 |
| 8 | HM|London|L1 | DEAD | G2,G3,G5,G7,G8 | +2,995 | -1,182 | -13,309 | -6,048 | +0.174 | -0.001 | 0.90 | 9,550 / 2,632 | 0 |
| 9 | HM|London|P3+L1 | DEAD | G2,G3,G5,G7,G8 | +2,711 | -1,448 | -13,309 | -6,048 | +0.164 | -0.004 | 0.92 | 9,550 / 2,632 | 0 |
| 10 | HM|NY|L1 | DEAD | G7,G8 | +1,800 | -3,899 | -41,437 | -11,894 | +0.163 | +0.235 | 0.97 | 8,236 / 3,029 | 0 |

The top-ranked cells (HM London P2+L1, ST London P2+N1/N1) are the large d_maxDD or d_Sharpe cells; they fail on worst week (G7), the CI (G5), the 2023 span (G6) or placebo (G3): e.g. ST London N1 cuts stack maxDD by 141,892 (income +3,048/wk) but the worst week is 16,431 worse, the d_maxDD CI includes 0 and its rank is 0.87.

## Which books and sessions the rules help (cells of 38 per book/session; sh+ = share with stack d_Sharpe > 0; G1 = passed the PRE criterion; G1&G2 = PRE and holdout both)
| book | session | sh+ cells | G1 | G1&G2 | insurance | best cell (d_Sharpe) | median d_Sharpe |
|---|---|---|---|---|---|---|---|
| HM | Asia | 2 | 19 | 2 | 0 | Asia|G2k70 (+0.030) | -0.053 |
| HM | London | 34 | 20 | 8 | 0 | London|P2+L1 (+0.267) | +0.078 |
| HM | NY | 24 | 15 | 11 | 2 | NY|L1 (+0.163) | +0.033 |
| KB | Asia | 5 | 10 | 0 | 2 | Asia|P3+N3 (+0.023) | -0.034 |
| KB | London | 18 | 20 | 1 | 0 | London|P1+L1 (+0.045) | -0.002 |
| KB | NY | 7 | 0 | 0 | 0 | NY|N2 (+0.013) | -0.046 |
| PB | Asia | 9 | 15 | 2 | 0 | Asia|P1.5+N3 (+0.036) | -0.045 |
| PB | London | 16 | 35 | 2 | 4 | London|P3+N2 (+0.058) | -0.005 |
| PB | NY | 28 | 5 | 5 | 13 | NY|P1+N2 (+0.105) | +0.027 |
| PS | Asia | 7 | 4 | 3 | 0 | Asia|P2+L1.5 (+0.022) | -0.016 |
| PS | London | 19 | 25 | 3 | 3 | London|P3+L1 (+0.098) | +0.001 |
| PS | NY | 27 | 7 | 6 | 8 | NY|P1.5+L1 (+0.027) | +0.007 |
| SM | Asia | 23 | 18 | 10 | 0 | Asia|L1.5 (+0.025) | +0.005 |
| SM | London | 2 | 10 | 0 | 0 | London|P3 (+0.003) | -0.029 |
| SM | NY | 4 | 4 | 0 | 0 | NY|P3+L2 (+0.002) | -0.024 |
| ST | Asia | 19 | 23 | 2 | 3 | Asia|G1k70 (+0.120) | +0.001 |
| ST | London | 17 | 9 | 3 | 0 | London|P2+N1 (+0.211) | -0.015 |
| ST | NY | 3 | 2 | 0 | 2 | NY|P2 (+0.015) | -0.065 |
| WT | Asia | 13 | 10 | 3 | 1 | Asia|P1+L2 (+0.100) | -0.018 |
| WT | London | 27 | 12 | 7 | 0 | London|P1+L1 (+0.110) | +0.025 |
| WT | NY | 32 | 13 | 10 | 0 | NY|P1.5+N1 (+0.121) | +0.059 |

Structural read: (1) HM London is the one broad effect: 34 of 38 cells raise the stack Sharpe (median +0.078; halting HM in the 02:00-09:30 session after a profit/loss cut helps almost regardless of parameters), consistent with the FAILPRED finding that London is the chop session for the trend books; but the best cells fail the worst-week/holdout/placebo gates, so it is not a PASS. ST London shows the largest drawdown cuts (-127k to -142k with a stop-out halt) at a worse worst week. WT7 (mapped) helps in NY and London (32 and 27 of 38 cells positive). (2) KB and SM: nothing (KB NY 0 G1 passes, SM trades 3-4 times a week per session and the rules barely fire, d_Sharpe <= 0.025). (3) Asia is the worst session: 29% of cells raise the Sharpe, median -0.017, and ST/PB/PS Asia gains do not survive the holdout. (4) By family the median cell is slightly negative (a: -107 $/wk, b: -232, c: -193, d: -444) and 38 cells are risk-down/income-down (insurance); the shifted-boundary and random-halt placebos are as good as most real cells, so most of the effect is plain exposure reduction. Cells that pass G1 and G2 and beat the placebos at >= 0.95 exist in HM London/NY, WT Asia/NY, PB London/NY and SM Asia, but all of them additionally fail the CI (G5), worst-week (G7) or best-of-798 (G8) gates; only the three CANDIDATEs fail G8 alone.

## Power statement
Weekly stack-mean MDE of one session rule is 4.4k-10.6k $/wk (80% power, 75 WF-PRE weeks, upper bound = the whole session's SD) and 2-4k per session on the session-paired test, against predicted and observed effects of 0.1-3k $/wk: the box can only see a session rule's MEAN effect if it is several times larger than the best observed here. The RISK side (SD, worst week, maxDD) is better powered for SD (CI widths about 2-4k $/wk) but maxDD CIs are +/-60-100k wide on 142 weeks, so the maxDD deltas of -20k to -140k are not resolved individually. Best-of-798: the sign-flip null's 95th percentile is d_Sharpe 0.334; no cell reaches it (max 0.267), so with this multiplicity no single session rule is distinguishable from the best of 798 chance draws. A null here reads: "could not have seen a stack Sharpe gain below about 0.33 as a family-wise result and a mean effect below about 5k $/wk at the weekly level".

## Equal risk and DS3 marginal (equal_risk.py; holdout re-read logged)
| cell | base lots | equal-risk lots (ST10 WF SD) | $/wk at equal risk | delta vs ST10 at equal risk | baseline book equal-risk $/wk | DS3 marginal Sharpe add-one (base KB+SM+EM) WF-PRE / WF / HOLD |
|---|---|---|---|---|---|---|
| WT|NY|P2 | 7.0 | 14.5 | 4,420 | -9,930 | 2,971 (lots 14.5) | n/a (DS2 book) |
| WT|NY|P2+N1 | 7.0 | 15.7 | 6,339 | -8,010 | 2,971 (lots 14.5) | n/a (DS2 book) |
| PB|NY|G1k50 | 10.0 | 12.4 | 19,583 | +5,233 | 17,265 (lots 11.5) | +0.23 / +0.40 / +0.58 (baseline PB3B add-one +0.09 / +0.26 / +0.45 in DS3_SPEC_PB3B_R5_P1.md) |

## Spec (parameter level; NT8) and independent-replay identity
**WT|NY|P2+N1 and WT|NY|P2 (WT7, 7 lots, MAPPED basis).** Session NY = 1-minute bars starting 09:30-17:59 ET (entries exist 09:30-14:59). R = 7 lots x 45 pt x $20 = $6,300. State at 09:30: snapshot = cumulative realised + unrealised of the WT strategy (account/strategy PnL). Every tick/second: sessionPnL = realised + unrealised - snapshot. Trigger P2: sessionPnL >= +2R = +$12,600; trigger N1 (P2+N1 only): the first stop-order fill of the session. On trigger: cancel working orders, market-flatten the open position, block WT7 entries until 18:00 (next session start, 18:00 Asia), no other change; day -2R/+5R, give-back 2R/50% and week -12R stay as live (R for those = $6,300 at 7 lots). Predicted: stack d_mean +695 (P2) / +1,386 (P2+N1) $/wk, d_SD -1,131 / -2,626, d_maxDD -20k / -31k (MAPPED; weekly mean effect inside the 5.2k MDE). Forward: 8 weeks cannot resolve the mean; judge the SD/worst-week side.
**PB|NY|G1k50 (PB3B_R5_P1).** NY session as above. R = lots x 60 x $20 (12,000 at 10 lots; scale with the live lots, the stack runs PB at about 5 lots so R about $6,100). Rule: track session peak of sessionPnL; once the peak >= +1R and sessionPnL <= 50% of the peak, cancel, flatten at market, no PB entries until 18:00. Predicted: stack d_mean +526 $/wk, d_SD -2,066, d_maxDD -41k, book maxDD 361k -> 316k, worst book week -110k -> -99k. HOLD d_Sharpe +0.04, 2023 span d_mean +398, L8W d_Sharpe -0.09 (noted).
Session start snapshots: the strategy must carry the position across the 02:00 and 09:30 boundaries unchanged; a position open at a boundary has its P&L re-based to the boundary mark (modelled), not flattened. In NT8: OnBarUpdate (1-minute series, ET): detect boundary by bar start time; OnExecutionUpdate: stop-out counter and realised P&L; OnMarketData (or a 1-second series) for the unrealised leg; ExitLong/ExitShort("SessHalt") and a haltedSession flag in the entry handler.
Identity test (independent replay from this spec text): l2vast/ds3/code/sl/x_sess.py (own ET-clock session builder, per-trade vectorised equity path, no use of the engine/numba) vs the engine stage on WT cells P2, P2+N1, London L1, Asia G1k50: 0 mismatches in kept flag, exit sample and exit points over 11,641 trades (out/sl/xsess_WT.json); PB cells G1k50 and London P2+N1: 3 kept-flag, 1 exit and 1 exit-points mismatches in 8,339 trades for NY G1k50 (0.04%, float tie at a threshold sample), 0 for London P2+N1 (out/sl/xsess_PB.json). Limits: the identity test covers the session stage, the day/week stages are the existing engine (identity to the published series is $0.00); the NT8 market flatten will not fill at the modelled next-second price.

## Deviations / disclosures
- Staged engine (as the live-engine model): session stage first, then the day entry test, day arm and week floor; an entry removed later by the day test was still seen by the session stage; a flattened trade's busy window cannot produce replacement entries (not in the trade list).
- WT7: rows exist only on the mapped basis (corrected-P9 year x exit-type map); its three sessions are scored but labelled MAPPED. ST/HM post-2026-10-16 rows are mapped but outside the s48score calendar (data end 2026-10-16).
- Stack definition is mine (DS3 peak 23 with KB+SM+PB3B weights), because no single published line fixes KB+SM+PB at the cap; the baseline therefore differs from DS3_PORTFOLIO.md (which has TB7 as third book).
- Series for all days are computed in one pass; holdout metrics were read only after each group's pre text was logged (code order in sl_score.py).
- Random-halt placebo only for cells passing G1 (others are DEAD at G1 anyway); shifted placebos for all.
- No paper-all registration outside the three CANDIDATEs; no live, chart, credentials or purchases touched.
- 15 duplicate-series cells flagged in the rows JSON (duplicate_of).
