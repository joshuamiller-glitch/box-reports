# DS3_SMART_A2 — T-SMART items A2 (stack as one position), A4 (hedge instead of exit), A5 (stop-and-reverse, opposite-book conflict), W-SM2

Generated 2026-11-14 13:25 UTC. Exact engine, one set per job, reference = JN05W2 (live panel base + F3 + E1 + C22 + BR3S + FLAT45K, 43 exact months). Shadow only, no PASS claim.
**CAVEAT (every page):** the engine state cut fires in the engine but did NOT fire live on 11-11 (autopilot/DS3_P7_CUT_FIDELITY.md). Rules below are scored with the engine cuts as in JN05W2; the full-stop-only variants are added when that base exists. Prereg autopilot/SMART_A2_PREREG.md (sha 597c41f51e81ba3c). Hook code/th_sm2/sm2_hooks.py. R = $1,200 fixed; at the user lots (x1.75) fixed-dollar thresholds x1.75, count rules unchanged. Hedge fee 12.0 $/NQ-equivalent RT assumed (MNQ, unverified), bound 4.84.

## 0. Trend-week clause first (L6M weekly check, 5 best JN05W2 weeks kept, JN05W2 winning weeks turned losing) and L6M/HOLD summary

| set | months | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | L6M run max/p95 (ref 13/6) | HOLD cut % | HOLD d mean/wk | HOLD run max/p95 | WF cut / beat |
|--|--|--|--|--|--|--|--|--|--|--|
| SM_A1E_C10L | 12 | 76% ($239k of $316k) | 1 of 20 | -41.9 | -5318 | 15/7 | -39.8 | -4226 | 15/6 | - |
| SM_A1E_L0L | 12 | 100% ($318k of $316k) | 0 of 20 | -1.4 | -13 | 11/6 | -15.2 | 1010 | 11/6 | - |
| SM_A1E_XL | 43 | 100% ($315k of $316k) | 0 of 20 | 0.0 | 508 | 15/6 | -4.8 | 468 | 15/6 | -1.3 / 9% |
| SM_A1N_C10L | 12 | 44% ($139k of $316k) | 5 of 20 | -86.2 | -13319 | 9/6 | -44.4 | -8222 | 10/5 | - |
| SM_A1N_L0L | 43 | 71% ($224k of $316k) | 2 of 20 | -72.2 | -6798 | 10/5 | -26.4 | -2859 | 10/5 | -4.9 / 14% |
| SM_A1N_XL | 12 | 68% ($216k of $316k) | 2 of 20 | -84.9 | -8032 | 10/5 | -57.6 | -3510 | 10/5 | - |
| SM_A1_ID | 1 | (running) |||||||||
| SM_A1_NC0 | 43 | 70% ($223k of $316k) | 2 of 20 | -51.3 | -6993 | 10/5 | -56.9 | -3370 | 10/5 | -30.1 / 15% |
| SM_A1_T | 1 | (running) |||||||||
| SM_A6_freshNP7 | 12 | 81% ($257k of $316k) | 0 of 20 | 15.8 | -4947 | 10/5 | 15.1 | -2246 | 10/5 | - |
| SM_A6_halfALL | 12 | 99% ($313k of $316k) | 0 of 20 | -5.2 | -1117 | 14/6 | -0.4 | -1188 | 14/6 | - |
| SM_A6_halfNP7 | 43 | 107% ($337k of $316k) | 0 of 20 | 11.8 | 383 | 13/6 | 11.6 | 724 | 13/6 | 0.8 / 42% |
| SM_A6_skipM7 | 12 | 100% ($316k of $316k) | 0 of 20 | -4.0 | -407 | 13/6 | 15.1 | 550 | 13/5 | - |
| SM_A6_skipNP7 | 12 | 88% ($278k of $316k) | 2 of 20 | -5.1 | -4620 | 9/5 | 15.8 | -1958 | 9/5 | - |
| SM_A7_P7a | 12 | 88% ($278k of $316k) | 1 of 20 | 19.7 | -4317 | 14/6 | 5.1 | -2111 | 14/6 | - |

cut % = maxDD of the stack vs JN05W2 (positive = shallower); d mean = all-weeks mean difference ($/wk); a window appears only when all its months are present. PRE / X' / GAP follow for cells with L6M cut >= 5% and d mean >= -$1,000/wk (prereg).

Identity gate: SM_ID99 (hook on, no rule fires) must equal JN05W2 on 202610 (598 trades, net $25,943.82) - see section I below once its month is DONE.


## NOCUT base (JN05W2_NOCUT = JN05W2 with the engine state cut OFF on all books: native 60 worked stop + 80 catastrophe only; FLAT45K, E1, C22, BR3S, F3 panel layers untouched; F3 context cut removed because it is a cut)

Compare every rule against this base: it is the engine as the live D7 behaved on 11-11 (state cut not firing). Reference below = JN05W2 (cut on).

**JN05W2_NOCUT**: 43 of 43 months DONE.

Trend-week clause (L6M, vs cut-on reference): 5 best weeks kept $227k of $316k (72%); winning weeks turned losing 2 of 20.

| window | maxDD $ (NOCUT) | maxDD $ (ref) | cut % | d mean/wk (all wks) | stack run max/p95 |
|--|--|--|--|--|--|
| L1M | 36253 | 36371 | 0.3 | -2728 | 8/5 |
| L3M | 36253 | 36371 | 0.3 | -1556 | 10/5 |
| L6M | 50815 | 36371 | -39.7 | -5410 | 10/5 |
| HOLD | 99884 | 63185 | -58.1 | -2907 | 10/5 |
| PRE | 103094 | 76186 | -35.3 | 2966 | 7/4 |
| X' | 76557 | 55326 | -38.4 | -154 | 6/4 |

behavioural scorecard a-e (JN05W2_NOCUT):
```
JN05W2_NOCUT L6M (stack, per week): full stops 36.6/wk $-92239; give-backs 7.5/wk (7.4 round-trips) realised $-13409, forgone vs target $30925; same-side losing runs max 10, p95 5, $-43683 lost on 3rd-and-later; no-new-evidence re-entries 22.8/wk $3070; recoveries cut 0.9/wk $1719, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $60211/wk, losers avoided $59557/wk, net +1090 $/wk; pnl $20874/wk.
JN05W2_NOCUT HOLD (stack, per week): full stops 33.3/wk $-82802; give-backs 6.8/wk (6.6 round-trips) realised $-12329, forgone vs target $28539; same-side losing runs max 10, p95 5, $-37791 lost on 3rd-and-later; no-new-evidence re-entries 18.0/wk $1712; recoveries cut 0.9/wk $1581, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $56441/wk, losers avoided $52638/wk, net -250 $/wk; pnl $15102/wk.
JN05W2_NOCUT PRE (stack, per week): full stops 24.3/wk $-58817; give-backs 4.6/wk (4.2 round-trips) realised $-7410, forgone vs target $17605; same-side losing runs max 7, p95 4, $-21335 lost on 3rd-and-later; no-new-evidence re-entries 7.8/wk $984; recoveries cut 0.5/wk $985, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $31243/wk, losers avoided $30054/wk, net +1481 $/wk; pnl $13363/wk.
JN05W2_NOCUT X' (stack, per week): full stops 18.4/wk $-42178; give-backs 3.4/wk (2.8 round-trips) realised $-5013, forgone vs target $12370; same-side losing runs max 6, p95 4, $-12236 lost on 3rd-and-later; no-new-evidence re-entries 2.4/wk $181; recoveries cut 0.3/wk $516, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $15598/wk, losers avoided $15449/wk, net +2112 $/wk; pnl $3454/wk.
```

acceptance_p7 (JN05W2_NOCUT):
```
   03-25 21:34:02 L  4 lots  #2 runbefore=0 gap=72m atr_rel=0.71 chase_k=-0.3  -> StopJoin -4635

-- 3.5y worst #10  label day 20260506 asia  reference P7 net -12366  set P7 net -15522  trades ref 2 set 2  => pass
  reference:
   05-05 19:48:00 L  7 lots  #1 runbefore=0 gap=- atr_rel=1.37 chase_k=5.1  -> StateCut -6223
   05-05 20:48:01 S  7 lots  #2 runbefore=0 gap=42m atr_rel=1.47 chase_k=-0.6  -> StateCut -6143
  set:
   05-05 19:48:00 L  7 lots  #1 runbefore=0 gap=- atr_rel=1.37 chase_k=5.1  -> StopJoin -8263
   05-05 20:48:01 S  7 lots  #2 runbefore=0 gap=42m atr_rel=1.47 chase_k=-0.6  -> StopJoinFallback -7258

== TEST 2: consecutive same-side losing entries per session (all sessions with a P7 trade; months of the set)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W2_NOCUT | 2143 | 3 | 2.0 | 0.68 | 3 | 3 | -10467 | 0 / +0 | 0 | 53 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W2_NOCUT | 917 | 3 | 1.0 | 0.71 | 2 | 2 | -8104 | 0 / +0 | 0 | 20 |

== TEST 3: best trend sessions (5 best L6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +25414 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +10595 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +21574 (5 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +26354 (5 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net -686 (6 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 1 ($+8402); all re-entry winners (any evidence) reference 13, set 7
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY JN05W2_NOCUT: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT JN05W2_NOCUT PASS fails=1/20
```

**JN05W2J_NOCUT**: 43 of 43 months DONE.

Trend-week clause (L6M, vs cut-on reference): 5 best weeks kept $204k of $244k (83%); winning weeks turned losing 3 of 21.

| window | maxDD $ (NOCUT) | maxDD $ (ref) | cut % | d mean/wk (all wks) | stack run max/p95 |
|--|--|--|--|--|--|
| L1M | 28277 | 17862 | -58.3 | -7192 | 8/5 |
| L3M | 28277 | 17862 | -58.3 | -4597 | 10/5 |
| L6M | 36550 | 23965 | -52.5 | -4077 | 10/5 |
| HOLD | 83574 | 43622 | -91.6 | -3222 | 10/5 |
| PRE | 47503 | 56843 | 16.4 | 1563 | 7/4 |
| X' | 42819 | 39577 | -8.2 | -14 | 6/4 |

behavioural scorecard a-e (JN05W2J_NOCUT):
```
JN05W2J_NOCUT L6M (stack, per week): full stops 38.8/wk $-71401; give-backs 8.1/wk (8.0 round-trips) realised $-11333, forgone vs target $25980; same-side losing runs max 10, p95 5, $-32958 lost on 3rd-and-later; no-new-evidence re-entries 24.2/wk $2530; recoveries cut 1.3/wk $2390, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $61039/wk, losers avoided $57723/wk, net -2020 $/wk; pnl $17764/wk.
JN05W2J_NOCUT HOLD (stack, per week): full stops 35.0/wk $-64494; give-backs 7.2/wk (7.0 round-trips) realised $-10122, forgone vs target $23193; same-side losing runs max 10, p95 5, $-29157 lost on 3rd-and-later; no-new-evidence re-entries 18.8/wk $1218; recoveries cut 1.1/wk $1867, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $56285/wk, losers avoided $51954/wk, net -4027 $/wk; pnl $11324/wk.
JN05W2J_NOCUT PRE (stack, per week): full stops 24.8/wk $-43203; give-backs 4.6/wk (4.2 round-trips) realised $-5676, forgone vs target $13475; same-side losing runs max 7, p95 4, $-15550 lost on 3rd-and-later; no-new-evidence re-entries 8.1/wk $813; recoveries cut 0.6/wk $1159, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $32081/wk, losers avoided $30016/wk, net -2911 $/wk; pnl $8971/wk.
JN05W2J_NOCUT X' (stack, per week): full stops 18.3/wk $-31991; give-backs 3.3/wk (2.7 round-trips) realised $-3533, forgone vs target $9374; same-side losing runs max 6, p95 4, $-9100 lost on 3rd-and-later; no-new-evidence re-entries 2.3/wk $231; recoveries cut 0.3/wk $520, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $16448/wk, losers avoided $16663/wk, net +2466 $/wk; pnl $3808/wk.
```

acceptance_p7 (JN05W2J_NOCUT):
```

-- 3.5y worst #10  label day 20260506 asia  reference P7 net -12366  set P7 net +1565  trades ref 2 set 3  => pass
  reference:
   05-05 19:48:00 L  7 lots  #1 runbefore=0 gap=- atr_rel=1.37 chase_k=5.1  -> StateCut -6223
   05-05 20:48:01 S  7 lots  #2 runbefore=0 gap=42m atr_rel=1.47 chase_k=-0.6  -> StateCut -6143
  set:
   05-05 19:48:00 L  4 lots  #1 runbefore=0 gap=- atr_rel=1.37 chase_k=5.1  -> StopJoin -4760
   05-05 20:48:01 S  2 lots  #2 runbefore=0 gap=42m atr_rel=1.47 chase_k=-0.6  -> StopJoinFallback -2077
   05-06 00:22:00 L  7 lots  #3 runbefore=0 gap=46m atr_rel=0.71 chase_k=5.8  -> Target +8402

== TEST 2: consecutive same-side losing entries per session (all sessions with a P7 trade; months of the set)
| scope | who | sessions | max run | p95 | mean | sessions with run>=3 | n 3rd+ losers | $ lost on 3rd+ losers | entries 3rd+ attempt without new evidence (n / $) | losing 3rd+ no-evidence violations | bigger 2nd attempts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | JN05W2J_NOCUT | 2301 | 3 | 2.0 | 0.68 | 3 | 3 | -3880 | 0 / +0 | 0 | 26 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | JN05W2J_NOCUT | 916 | 3 | 2.0 | 0.73 | 2 | 2 | -2659 | 0 / +0 | 0 | 22 |

== TEST 3: best trend sessions (5 best L6M P7 sessions of the reference) and the frozen live week: re-entry winners after NEW EVIDENCE
-- best session 20260619 asia: reference net +28883 (5 trades, 0 evidence-backed re-entry winners $+0); set net +17013 (5 trades, 0 such winners $+0)
-- best session 20260515 asia: reference net +23369 (8 trades, 0 evidence-backed re-entry winners $+0); set net +7208 (5 trades, 0 such winners $+0)
-- best session 20260707 asia: reference net +23252 (7 trades, 0 evidence-backed re-entry winners $+0); set net +16768 (6 trades, 0 such winners $+0)
-- best session 20261022 asia: reference net +22466 (6 trades, 0 evidence-backed re-entry winners $+0); set net +14391 (5 trades, 0 such winners $+0)
-- best session 20260605 asia: reference net +22396 (9 trades, 0 evidence-backed re-entry winners $+0); set net +2163 (6 trades, 0 such winners $+0)
-- the 30 best L6M P7 sessions (reference ranking): evidence-backed re-entry winners kept: reference 1 ($+8402), set 2 ($+7188); all re-entry winners (any evidence) reference 13, set 8
-- frozen live week 11-01..05 (53 live P7 trades, not re-simulated by any set): max run 3, p95 2.5, mean 1.40, 3rd+ losers 1 ($-2719), losing 3rd+ no-evidence 1; re-entry winners after a same-side loser 10 ($+47812), of which with new evidence 4 ($+15522)

SUMMARY JN05W2J_NOCUT: fails 1 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
covered sessions 20 of 20
ACCEPT JN05W2J_NOCUT PASS fails=1/20
```
