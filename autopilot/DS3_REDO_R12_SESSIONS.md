# DS3_REDO_R12_SESSIONS - session boundaries, blocks, flatten, day-of-week / roll / event days on the state base (REDO-R12)

**FINAL DRAFT 2026-11-10 14:41Z** - exact L6M + PRE rows (section 9) are in for every set; where exact and first-order disagree the exact row governs. Rules 2/2a labels and the bi-weekly WF are beside every cell. Live settings stay.

Version 2026-11-10 14:41Z. **ROLL-FIXED rows (exact)**. Sections 0-4 are the FIRST-ORDER SCREEN; EXACT L6M + PRE rows are in section 9 and govern (removals, lot re-reads, flatten re-walks, calendar multipliers on the S1B-COMB trade list; stack metrics, drawdown first, equal-mean key, permutation placebo B=100 within book, family max over this page, bi-weekly WF as its own column, rule 2a prior label). Exact hooks (guards / ends / flat / cal) are in code/th_r7/r7_hooks.py; exact runs: R12_FLAT1700, R12_ASIA3, R12_OPEN930, R12_BLK0, R12_NFP0. No PASS claims; shadow only.

## 0. Plain verdict
Nothing here changes a live setting. (a) The 09:00-09:59 block, the Asia guard 15:00-17:59 and the 09:00-09:29 part of the block are INERT in the engine as configured: the pre (08:30-09:30) and close (15:00-18:00) sessions carry lots 0 for every book, so only 09:30-09:59 (nyam lots K7 1, H7 1, M7 1, P7 7) and the 18:00-18:04 asia-open window carry trades; opening them ADDS trades the base does not contain and needs the engine (exact only), a first-order screen cannot score it. (b) Flatten: 17:00 is ~neutral (+39 $/wk L6M), 16:30 / 16:45 are slightly worse, hold-through for asia entries touches only 34 trades. (c) Calendar: most x0 / x0.5 cells lose mean and deepen maxDD (exceptions: NFP-day x0 / x0.5 gain +587 / +333 $/wk L6M with PRE dM -342 / -4); cells flagged LEAD+ have family p >= .1 and a bi-weekly WF beating live in <= 53 % of periods, so none is a CANDIDATE. (d) Session-clock moves: asia end 03:00 removes 882 M7 trades from 02:00-03:00 (london lots M7 2 -> asia 0) with a small eq cut and PRE dM -463; london end 08:00 and nyam end 11:30 lose mean.
**Exact (section 9, L6M + PRE, 23 months):** FLAT1700 0.1 % L6M cut / +342 $/wk but WF beat 5 %; ASIA3, BLK0 and OPEN930 lose L6M mean and cut (OPEN930 L6M -38 %, PRE +2.7 % / +1,499 $/wk: RECENT-ONLY-style split, fails recents); NFP0 gives up mean. None passes; live stays.

## 1. Screen table (live = every row compared with)
cols: eq cut = equal-mean maxDD cut % (L6M / L3M / L1M) on the STACK; dM L6M = delta mean $/wk; PRE = maxDD cut % / dM; WF = bi-weekly re-pick beat %; p = own / family.

| cell | n changed | eq cut L6M / L3M / L1M | dM L6M | PRE cut / dM | X' cut | WF beat % / cut % | p own / fam | prior | label |
|---|---|---|---|---|---|---|---|---|---|
| flatten=1630 | trades changed 387 | -0.7 / -0.7 / -0.7 | -171.1 | 0.0 / -76.6 | -0.6 | 10.8 / 0.0 | 0.45 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| flatten=1645 | trades changed 370 | -0.8 / -0.8 / -0.8 | -186.1 | 0.0 / -9.2 | -0.5 | 8.1 / 0.0 | 0.88 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| flatten=1700 | trades changed 376 | 0.3 / 0.3 / 0.2 | 38.9 | 0.0 / 20.8 | -0.2 | 9.5 / 0.0 | 0.06 / 0.98 | OK-PRIOR (old: OK-PRIOR) | LEAD+ |
| flatten=hold (asia-entry trades only) | trades changed 34 | 0.0 / 0.0 / 0.0 | 0.0 | 0.0 / 226.4 | 2.1 | 0.0 / 0.0 | 0.26 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| asia-open block 18:00-18:10 (live 18:05) | trades removed 364 | -0.5 / -0.5 / -0.6 | 752.4 | -3.6 / -841.4 | 10.2 | 39.2 / 0.0 | 0.34 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| asia-open block 18:00-18:15 (live 18:05) | trades removed 611 | -7.6 / -7.6 / -7.7 | 470.9 | -5.3 / -1520.5 | 24.3 | 25.7 / 0.0 | 0.49 / 1.00 | OK-PRIOR (old: RECENT-ONLY) | no |
| asia end 03:00 (removals/lot re-read only) | trades changed 882, removed 882 | 5.2 / 5.2 / 5.1 | -232.5 | 3.1 / -463.0 | -21.4 | 36.5 / 0.0 | 0.07 / 0.78 | OK-PRIOR (old: OK-PRIOR) | LEAD+ |
| london end 08:00 (removals/lot re-read only) | trades changed 530, removed 530 | -14.9 / -14.9 / 6.3 | -2099.1 | 10.2 / -522.8 | 2.2 | 17.6 / 10.2 | 0.56 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| london end 09:00 (removals/lot re-read only) | trades changed 0, removed 0 | 0.0 / 0.0 / 0.0 | 0.0 | 0.0 / 0.0 | 0.0 | 0.0 / 0.0 | 1.00 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| nyam end 11:30 (removals/lot re-read only) | trades changed 935, removed 625 | -1.4 / -1.4 / -1.5 | -184.8 | 5.2 / -625.7 | 0.9 | 27.0 / 0.0 | 0.40 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| nyam end 12:30 (removals/lot re-read only) | trades changed 54, removed 0 | 0.2 / 0.2 / 0.1 | 22.7 | -1.7 / -85.1 | -0.8 | 4.1 / 0.0 | 0.18 / 0.98 | OK-PRIOR (old: OK-PRIOR) | LEAD |
| FOMC day x0 | trades 683 | -1.0 / -1.0 / 47.0 | -279.8 | 0.0 / -796.3 | -13.9 | 0.0 / 0.0 | 0.02 / 0.19 | OK-PRIOR (old: OK-PRIOR) | no |
| FOMC day x0.5 | trades 683 | 0.1 / 0.1 / 16.5 | 36.2 | 0.0 / -315.6 | -0.7 | 1.4 / 0.0 | 0.06 / 0.76 | OK-PRIOR (old: OK-PRIOR) | LEAD+ |
| CPI day x0 | trades 938 | -14.3 / -14.3 / -10.5 | -2120.5 | -9.0 / -1130.7 | 28.4 | 2.7 / 0.0 | 0.50 / 1.00 | OK-PRIOR (old: RECENT-ONLY) | no |
| CPI day x0.5 | trades 938 | -2.7 / -2.7 / -2.7 | -648.3 | -0.8 / -180.5 | 13.5 | 5.4 / -0.8 | 0.48 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| NFP day x0 | trades 732 | 2.5 / 2.5 / 2.4 | 586.6 | 0.0 / -341.7 | 7.0 | 9.5 / 0.0 | 0.10 / 0.92 | OK-PRIOR (old: OK-PRIOR) | LEAD+ |
| NFP day x0.5 | trades 732 | 1.4 / 1.4 / 1.3 | 333.4 | 0.0 / -3.9 | 1.5 | 14.9 / 0.0 | 0.17 / 0.94 | OK-PRIOR (old: OK-PRIOR) | LEAD |
| opex Friday x0 | trades 724 | -10.3 / -10.3 / -10.3 | -2186.5 | 0.0 / -776.4 | -16.6 | 4.1 / 0.0 | 0.35 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| opex Friday x0.5 | trades 724 | -2.2 / -2.2 / -2.2 | -504.5 | 0.0 / -404.3 | -1.2 | 4.1 / 0.0 | 0.33 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| roll week x0 | trades 1835 | -10.1 / -10.1 / -10.1 | -2049.2 | 0.0 / -1525.5 | -25.4 | 4.1 / 0.0 | 0.21 / 1.00 | OK-PRIOR (old: RECENT-ONLY) | no |
| roll week x0.5 | trades 1835 | -3.2 / -3.2 / -3.2 | -691.4 | 0.0 / -484.7 | -4.6 | 2.7 / 0.0 | 0.28 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| any event (FOMC/CPI/NFP) x0 | trades 2343 | -5.8 / 6.0 / 38.3 | -4123.0 | -9.0 / -2495.5 | 32.8 | 20.3 / -9.0 | 0.01 / 0.27 | OK-PRIOR (old: RECENT-ONLY) | no |
| any event (FOMC/CPI/NFP) x0.5 | trades 2343 | 4.9 / 4.9 / 12.9 | -1105.7 | -0.8 / -599.9 | 16.7 | 36.5 / -0.8 | 0.04 / 0.65 | OK-PRIOR (old: OK-PRIOR) | LEAD+ |
| dow Mon x0 | trades 4041 | -22.1 / 15.6 / 15.5 | -3961.4 | 17.9 / -2720.1 | 47.7 | 27.0 / 17.9 | 0.04 / 0.91 | OK-PRIOR (old: RECENT-ONLY) | no |
| dow Mon x0.5 | trades 4041 | 1.0 / 1.0 / 0.9 | -2755.6 | 7.3 / -1047.9 | 13.7 | 45.9 / 7.3 | 0.07 / 0.96 | OK-PRIOR (old: RECENT-ONLY) | LEAD+ |
| dow Tue x0 | trades 4154 | -42.4 / -42.4 / -34.9 | -3551.9 | 38.6 / 237.4 | -32.8 | 35.1 / 21.7 | 0.52 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| dow Tue x0.5 | trades 4154 | -8.8 / -8.8 / -6.6 | -1016.1 | 12.1 / 502.6 | -1.5 | 52.7 / 12.1 | 0.50 / 1.00 | OK-PRIOR (old: OK-PRIOR) | no |
| dow Wed x0 | trades 4281 | 1.0 / 25.0 / 24.9 | -1847.4 | 5.4 / -5130.1 | 31.1 | 37.8 / 0.0 | 0.04 / 0.12 | RECENT-ONLY (old: RECENT-ONLY) | LEAD+ RECENT-ONLY |
| dow Wed x0.5 | trades 4281 | 12.4 / 12.4 / 14.5 | -499.2 | 7.5 / -1864.0 | 21.4 | 48.6 / 0.0 | 0.06 / 0.25 | OK-PRIOR (old: RECENT-ONLY) | LEAD+ |
| dow Thu x0 | trades 4293 | 0.0 / 8.0 / 50.2 | -3898.1 | -4.3 / -471.3 | -30.1 | 28.4 / -4.3 | 0.02 / 0.09 | OK-PRIOR (old: OK-PRIOR) | LEAD+ |
| dow Thu x0.5 | trades 4293 | 5.7 / 5.7 / 19.6 | -1314.0 | 0.8 / 74.0 | 3.5 | 52.7 / 0.8 | 0.01 / 0.44 | OK-PRIOR (old: OK-PRIOR) | LEAD+ |
| dow Fri x0 | trades 3053 | -11.3 / -11.3 / -11.4 | -2226.9 | 21.4 / -2345.3 | -22.5 | 23.0 / 21.4 | 0.14 / 1.00 | OK-PRIOR (old: RECENT-ONLY) | no |
| dow Fri x0.5 | trades 3053 | 1.6 / 1.6 / 1.5 | -145.2 | 13.0 / -760.1 | -2.1 | 29.7 / 13.0 | 0.12 / 0.94 | OK-PRIOR (old: OK-PRIOR) | LEAD |

## 2. Items that need the engine (additions) - EXACT ONLY, not scored in v1
| setting | live | variants | why first-order cannot score |
|---|---|---|---|
| 09:00-09:59 entry block | block | 09:00-09:29 only / 09:30-09:59 only / none | 09:00-09:29 is inert (pre lots 0); 09:30-09:59 adds nyam trades the base lacks |
| 18:00-18:04 block | 5 min | 0 / 10 / 15 min | 10 / 15 min are removals (screened above); 0-4 min add asia trades |
| Asia guard 15:00-17:59 | on | off / 15:30 / 16:00 / 16:30 start | inert while the close session has lots 0 (a lot-table question: R3) |
| flatten 16:55 | 16:55 | 16:30 / 16:45 / 17:00 / hold (asia) | screened above by re-walk (first-order, no re-entries) |
| session clock | asia 18-02, london -08:30, nyam -12:00 | asia end 03:00; london end 08:00 / 09:00; nyam end 11:30 / 12:30 | removals and lot re-reads screened above; ADDED trades (H7 asia lots 4 in 02:00-03:00; P7/K7 in 08:30-09:00; P7 7 lots in 12:00-12:30) exact only |

Hook parameters for the exact sets: `{"flat":{"hm":1645|1700|null,"asia_only_hold":true},"guards":[[900,1080],[1080,1085+X],[570,600]],"ends":[300,830,930,1200,1500],"cal":{"dowm":{"2":0.5},"datem":{...}}}` (R12_ sets, hooks module r7_hooks).

## 3. REFIT 2026-11-22
The bi-weekly procedure over the R12 cell set (trailing 26 weeks ending at the data end, drawdown first) is reported below; live retained when no cell has a lower trailing maxDD.

Pick: **dow Thu x0** (trailing maxDD 66426 vs live 79907); screen label LEAD+, prior OK-PRIOR (old: OK-PRIOR), WF beat 28 %. Walk-forward says do not adopt without the exact run.

## 4. Summary block (setting | live value | best on the state base | holds OOS? | change recommended | panel field)
| setting | live value | best on the state base (screen) | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| session flatten | 16:55 | flatten=1700 | no (label LEAD+, WF beat 9 %) | no | flatten time (D7 constant 16:55) |
| asia-open block | 5 min | asia-open block 18:00-18:10 (live 18:05) | no (label no, WF beat 39 %) | no | block 18:00-18:04 (constant) |
| session clock boundaries | asia 18-02 / london -08:30 / nyam -12:00 | asia end 03:00 (removals/lot re-read only) | no (label LEAD+, WF beat 36 %) | no | session clock constants |
| calendar (dow / roll / events) | normal | dow Thu x0 | no (label LEAD+, WF beat 28 %) | no | day-of-week / event lot policy (not in panel) |
| 09:00-09:59 block / Asia guard 15:00-17:59 | block / on | not scored (additions, exact only; 09:00-09:29 and the guard are inert at lots 0) | n/a | no | guard constants |

## 9. EXACT engine results (auto-refreshed 2026-11-10 14:41Z) - R12 cells
Prior label = rule 2a with the PRE mean floor at 25 % of the live PRE mean (user decision 2026-11-10 13:45Z); the old fixed -$1k label is shown in brackets. Engine column: ROLLFIX1 = every contract-roll month of the set ran on the roll-patched engine (RollRep) and is scored against base_b_rollfix = ROLL-FIXED; ROLLEXCL = old unpatched runs scored with the 33 roll-alive trades excluded (superseded, shown until the rerun lands). L6M = 202605-202610, PRE = 202402-202506; X' = 202304-202401 and HOLD = 202511-202604 only for R7_P3 and R12_OPEN930 (the leads). cuts = maxDD cut % vs exact Q1-A, all weeks; eq = at equal L6M mean; dM = $/wk mean vs live; WF = bi-weekly re-pick on the exact block (beat % of periods / OOS cut %); prior = rule 2a label; no placebo on exact rows, so the highest label is LEAD.

| set | engine | months | L6M cut / eq / dM | L3M cut | L1M cut | PRE cut / dM | X' cut / dM | HOLD cut / dM | WF beat % / cut % | prior | label |
|---|---|---|---|---|---|---|---|---|---|---|---|
| R12_FLAT1700 | ROLLFIX1 | 23 | 0.1 / 1.6 / 342 | 0.1 | 0.0 | 0.0 / -311 | nan / nan | nan / nan | 5 / 0.0 | OK-PRIOR (old -$1k floor: OK-PRIOR) | LEAD ; WF fails |
| R12_ASIA3 | ROLLFIX1 | 23 | -4.9 / -10.8 / -1289 | -4.9 | -1.8 | -1.0 / -304 | nan / nan | nan / nan | 36 / 3.2 | OK-PRIOR (old -$1k floor: OK-PRIOR) | no |
| R12_OPEN930 | ROLLFIX1 | 35 | -38.3 / -45.5 / -1171 | -38.3 | -24.4 | 2.7 / 1499 | nan / nan | -11.1 / -344 | 36 / 2.7 | OK-PRIOR (old -$1k floor: OK-PRIOR) | no |
| R12_BLK0 | ROLLFIX1 | 23 | -12.3 / -21.5 / -1777 | -12.3 | 7.5 | -2.3 / -1426 | nan / nan | nan / nan | 0 / -2.5 | OK-PRIOR (old -$1k floor: RECENT-ONLY) | no |
| R12_NFP0 | ROLLFIX1 | 23 | 0.1 / -3.5 / -922 | 0.1 | 0.0 | 0.0 / -473 | nan / nan | nan / nan | 14 / 0.0 | OK-PRIOR (old -$1k floor: OK-PRIOR) | LEAD (mean given up: eq cut <= 0) ; WF fails |

**Live-stays line:** no exact row passes recents + eq-mean + prior + WF; the live setting stays (brackets 60/60, O7 40/90; flatten 16:55; blocks and session clock as live).

