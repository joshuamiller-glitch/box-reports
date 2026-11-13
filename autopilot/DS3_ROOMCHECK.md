# NOTE (W-ROOM 2026-11-13 ~01:40Z): all 9 cells x 43 months were already DONE (runs_rf, 11-12 17:xx, TP engine, prereg sha 651c470d... in DECISIONS.md 2026-11-12 13:17Z, before scoring); nothing was re-run, this page is the first score. Section headers read 'CELL vs CELL' by a label bug: the reference is JN04RM for RCL_* (panel 7/4/4 cap 8,400) and RCU_REF for RCU_* (12/7/7 cap 14,700). Fees = engine standard per FEES.md. Shadow only, no PASS claim.
## HEADLINE (trend-week clause first, then maxDD cut % / d mean $/wk, positive = better than reference)
- TREND-WEEK: P7 only f=0.5/0.667 gives up little in winning weeks (L6M $-3.6k / $-16.6k panel U, $-12k / $-16k panel L; 0 of 18-19 winning weeks turned losing) and the reference's 5 best weeks are kept (+$372k vs +$371k at U f0.5). f=1.0 and ALL books give up more ($-45k..-79k in L6M) and ALL f100 turns a winning week losing.
- Panel U (live 12/7/7, cap 14,700), P7 f0.5: L6M +6.8% / +410, HOLD +5.8% / +484, X' +5.1% / +258, GAP +7.2% / +444, PRE -5.9% / +14 (maxDD worse), WF2W 0% / +154, beat live 14% of refits. f0.667: L6M +3.7/+193, HOLD +4.9/-56, PRE -0.1/-152, X' +6.1/+314. f1.0: L6M +3.8/-1,056 (costs mean). ALL f100: L6M -15% / -2,033 (harm).
- Panel L (7/4/4 cap 8,400): f1.0 L6M -33% DD / -980 (HARM); f0.667 -4.8% / -237; f0.5 -2.6% / +275; PRE +2.2..+8.9% DD cut. ALL f100: L6M -52.7% / -2,073 (HARM). On the 7/4/4 panel the cap rarely binds, so f0.5 is a near-tie.
- The live-panel change alone (RCU_REF vs JN04RM, 12/7/7 + 14,700) raises L6M mean +3,991/wk but worsens maxDD by 35.6% (L6M) / 29.9% (X'); that, not the room check, is the big effect. Room check at U f0.5 recovers ~7% of that DD.
- Acceptance (P7 sessions): every cell FAILS 3-4 of 20 sessions (RCU_REF itself fails 4; f0.5 / f0.667 fail 3). All Rule-2a labels OK-PRIOR. Best live-form candidate: P7-only f=0.5 on 12/7/7: small, consistent in 4 of 5 windows, PRE negative; evidence is thin (rule rarely fires; WF beat-live 14%).
- Reason case 11-12 (P7 -$20,285 vs cap 14,700): replay on exact engine not part of this page; the live bug is the cut path (see DS3_LIVE_CUT_PORT.md).

# DS3_ROOMCHECK - room check at entry (user order 2026-11-12 13:15Z), W-C, page 2026-11-13 01:23Z; Shadow only, no PASS claim

Rule: at the entry sizing step, room = book daily loss cap + book realised day P&L; per-lot risk = stop pts x f x $20; if lots x per-lot risk > room then lots = floor(room / per-lot risk), 0 = skip. f = 1.0 / 0.667 / 0.5. Panel L = LPB (P7 7/4/4, day loss cap 8,400, reference JN04RM); panel U = the user's live P7 12/7/7 with cap 14,700 (reference RCU_REF = JN04RM with that panel). JN04 dials ON in every set. Prereg autopilot/WORKS_C_ROOM_PREREG.md. Hook code/th_works_c/c_gov.py key room (placed inside the JN04 rule layers: the check sees lots before LOT/SIGQ/REG halving, so it can only be stricter than an outermost check). Exact, 43 months each, TP engine.

## RCU_REF vs JN04RM panel 7/4/4 cap 8,400 (what the panel change 12/7/7 + 14,700 does by itself)
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 4.3 | -2134 | 25896 | 27056 | 19 / 15 |
| L3M | -35.6 | +1020 | 56529 | 41699 | 200 / 164 |
| L6M | -35.6 | +3991 | 56529 | 41699 | 184 / 138 |
| HOLD | -10.6 | +3215 | 80481 | 72757 | -349 / -285 |
| PRE | -12.0 | +857 | 74707 | 66714 | -371 / -328 |
| X' | -29.9 | +889 | 83231 | 64077 | -245 / -222 |
| GAP 2025-07..10 | -43.2 | +3784 | 33935 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut -10.6 %, d mean -76 $/wk, beat live in 0 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+371355; winning weeks turned losing: 1 of 19; $ given up inside winning weeks: -51426; sum of the 20 worst weeks cell +232034 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+400631; winning weeks turned losing: 2 of 36; $ given up inside winning weeks: -69440; sum of the 20 worst weeks cell -346649 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+403230; winning weeks turned losing: 5 of 118; $ given up inside winning weeks: -191227; sum of the 20 worst weeks cell -638955 vs ref -560640.

## RCL_P7_f100 vs RCL_P7_f100
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -22.6 | +33 | 33165 | 27056 | 9 / 15 |
| L3M | -33.4 | -2341 | 55638 | 41699 | 123 / 164 |
| L6M | -33.4 | -980 | 55638 | 41699 | 109 / 138 |
| HOLD | -2.6 | -334 | 74617 | 72757 | -287 / -285 |
| PRE | 8.9 | +125 | 60798 | 66714 | -325 / -328 |
| X' | 1.0 | +174 | 63426 | 64077 | -212 / -222 |
| GAP 2025-07..10 | 15.5 | +563 | 20017 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut -2.6 %, d mean +114 $/wk, beat live in 32 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+291715; winning weeks turned losing: 1 of 19; $ given up inside winning weeks: -50374; sum of the 20 worst weeks cell +151283 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+315140; winning weeks turned losing: 2 of 36; $ given up inside winning weeks: -71649; sum of the 20 worst weeks cell -283213 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+342837; winning weeks turned losing: 2 of 118; $ given up inside winning weeks: -119771; sum of the 20 worst weeks cell -547062 vs ref -560640.

## RCL_P7_f067 vs RCL_P7_f067
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -26.0 | +152 | 34090 | 27056 | 8 / 15 |
| L3M | -4.8 | -466 | 43683 | 41699 | 151 / 164 |
| L6M | -4.8 | -237 | 43683 | 41699 | 129 / 138 |
| HOLD | -4.2 | -262 | 75831 | 72757 | -283 / -285 |
| PRE | 2.2 | +36 | 65230 | 66714 | -326 / -328 |
| X' | -0.0 | +206 | 64087 | 64077 | -214 / -222 |
| GAP 2025-07..10 | 7.1 | +210 | 22012 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut -4.2 %, d mean +18 $/wk, beat live in 14 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+294723; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -16319; sum of the 20 worst weeks cell +171738 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+319337; winning weeks turned losing: 1 of 36; $ given up inside winning weeks: -25835; sum of the 20 worst weeks cell -280084 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+344319; winning weeks turned losing: 2 of 118; $ given up inside winning weeks: -60082; sum of the 20 worst weeks cell -556483 vs ref -560640.

## RCL_P7_f050 vs RCL_P7_f050
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -1.6 | +0 | 27485 | 27056 | 15 / 15 |
| L3M | -2.6 | -48 | 42783 | 41699 | 165 / 164 |
| L6M | -2.6 | +275 | 42783 | 41699 | 142 / 138 |
| HOLD | -5.0 | +100 | 76377 | 72757 | -276 / -285 |
| PRE | 2.4 | +85 | 65135 | 66714 | -326 / -328 |
| X' | 0.0 | +196 | 64077 | 64077 | -214 / -222 |
| GAP 2025-07..10 | 0.0 | +143 | 23701 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut -5.0 %, d mean +53 $/wk, beat live in 10 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+296321; winning weeks turned losing: 0 of 19; $ given up inside winning weeks: -12315; sum of the 20 worst weeks cell +184119 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+320935; winning weeks turned losing: 1 of 36; $ given up inside winning weeks: -19553; sum of the 20 worst weeks cell -271273 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+343494; winning weeks turned losing: 2 of 118; $ given up inside winning weeks: -46319; sum of the 20 worst weeks cell -553892 vs ref -560640.

## RCL_ALL_f100 vs RCL_ALL_f100
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -21.2 | -1555 | 32803 | 27056 | 1 / 15 |
| L3M | -52.7 | -4284 | 63662 | 41699 | 102 / 164 |
| L6M | -52.7 | -2073 | 63662 | 41699 | 87 / 138 |
| HOLD | -4.8 | -783 | 76219 | 72757 | -299 / -285 |
| PRE | 5.4 | +140 | 63110 | 66714 | -316 / -328 |
| X' | 14.2 | +269 | 54976 | 64077 | -200 / -222 |
| GAP 2025-07..10 | -2.0 | +12 | 24171 | 23701 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut -4.8 %, d mean +53 $/wk, beat live in 42 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+299107 and the cell's same weeks to $+294653; winning weeks turned losing: 1 of 19; $ given up inside winning weeks: -78807; sum of the 20 worst weeks cell +120311 vs ref +180775.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+323722 and the cell's same weeks to $+315145; winning weeks turned losing: 1 of 36; $ given up inside winning weeks: -98455; sum of the 20 worst weeks cell -295269 vs ref -281405.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+347086 and the cell's same weeks to $+341647; winning weeks turned losing: 1 of 118; $ given up inside winning weeks: -165320; sum of the 20 worst weeks cell -563112 vs ref -560640.

## RCU_P7_f100 vs RCU_P7_f100
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -25.3 | -1182 | 32440 | 25896 | 9 / 19 |
| L3M | 3.8 | -2543 | 54366 | 56529 | 189 / 200 |
| L6M | 3.8 | -1056 | 54366 | 56529 | 181 / 184 |
| HOLD | 7.3 | -655 | 74574 | 80481 | -325 / -349 |
| PRE | 1.6 | -310 | 73538 | 74707 | -369 / -371 |
| X' | 4.6 | -163 | 79427 | 83231 | -236 / -245 |
| GAP 2025-07..10 | 12.6 | +816 | 29665 | 33935 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut 0.0 %, d mean +72 $/wk, beat live in 51 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+371355 and the cell's same weeks to $+365889; winning weeks turned losing: 0 of 18; $ given up inside winning weeks: -45466; sum of the 20 worst weeks cell +231275 vs ref +232034.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+400631 and the cell's same weeks to $+394356; winning weeks turned losing: 0 of 34; $ given up inside winning weeks: -74772; sum of the 20 worst weeks cell -322051 vs ref -346649.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+416156 and the cell's same weeks to $+417545; winning weeks turned losing: 4 of 122; $ given up inside winning weeks: -166173; sum of the 20 worst weeks cell -625034 vs ref -638955.

## RCU_P7_f067 vs RCU_P7_f067
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -25.3 | -401 | 32453 | 25896 | 11 / 19 |
| L3M | 3.7 | +380 | 54429 | 56529 | 198 / 200 |
| L6M | 3.7 | +193 | 54429 | 56529 | 189 / 184 |
| HOLD | 4.9 | -56 | 76566 | 80481 | -332 / -349 |
| PRE | -0.1 | -152 | 74797 | 74707 | -369 / -371 |
| X' | 6.1 | +314 | 78173 | 83231 | -233 / -245 |
| GAP 2025-07..10 | 6.0 | +623 | 31903 | 33935 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut 0.0 %, d mean +63 $/wk, beat live in 19 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+371355 and the cell's same weeks to $+367432; winning weeks turned losing: 0 of 18; $ given up inside winning weeks: -16606; sum of the 20 worst weeks cell +234228 vs ref +232034.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+400631 and the cell's same weeks to $+398302; winning weeks turned losing: 0 of 34; $ given up inside winning weeks: -25456; sum of the 20 worst weeks cell -329565 vs ref -346649.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+416156 and the cell's same weeks to $+413465; winning weeks turned losing: 1 of 122; $ given up inside winning weeks: -63595; sum of the 20 worst weeks cell -620296 vs ref -638955.

## RCU_P7_f050 vs RCU_P7_f050
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | 0.0 | +0 | 25896 | 25896 | 19 / 19 |
| L3M | 6.8 | +572 | 52660 | 56529 | 212 / 200 |
| L6M | 6.8 | +410 | 52660 | 56529 | 199 / 184 |
| HOLD | 5.8 | +484 | 75831 | 80481 | -333 / -349 |
| PRE | -5.9 | +14 | 79145 | 74707 | -375 / -371 |
| X' | 5.1 | +258 | 79010 | 83231 | -235 / -245 |
| GAP 2025-07..10 | 7.2 | +444 | 31488 | 33935 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut 0.0 %, d mean +154 $/wk, beat live in 14 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+371355 and the cell's same weeks to $+372104; winning weeks turned losing: 0 of 18; $ given up inside winning weeks: -3601; sum of the 20 worst weeks cell +246724 vs ref +232034.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+400631 and the cell's same weeks to $+402574; winning weeks turned losing: 0 of 34; $ given up inside winning weeks: -5453; sum of the 20 worst weeks cell -329711 vs ref -346649.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+416156 and the cell's same weeks to $+417291; winning weeks turned losing: 0 of 122; $ given up inside winning weeks: -26332; sum of the 20 worst weeks cell -621941 vs ref -638955.

## RCU_ALL_f100 vs RCU_ALL_f100
| window | maxDD cut % | d mean $/wk | cell maxDD $ | ref maxDD $ | worst-20 cell / ref $k |
|---|---|---|---|---|---|
| L1M | -32.7 | -1051 | 34365 | 25896 | 5 / 19 |
| L3M | -15.0 | -4002 | 64981 | 56529 | 172 / 200 |
| L6M | -15.0 | -2033 | 64981 | 56529 | 155 / 184 |
| HOLD | 5.1 | -890 | 76378 | 80481 | -329 / -349 |
| PRE | 0.3 | -340 | 74513 | 74707 | -365 / -371 |
| X' | 11.7 | -42 | 73516 | 83231 | -226 / -245 |
| GAP 2025-07..10 | 0.3 | +284 | 33819 | 33935 | |

Bi-weekly WF (re-pick every 2 weeks, purged): maxDD cut 0.0 %, d mean -233 $/wk, beat live in 51 % of refit periods (most periods are ties because the rule rarely fires).
Rule-2a label: **OK-PRIOR**.
TREND-WEEK CLAUSE (L6M): the reference's 5 best weeks sum to $+371355 and the cell's same weeks to $+368091; winning weeks turned losing: 1 of 18; $ given up inside winning weeks: -68553; sum of the 20 worst weeks cell +204450 vs ref +232034.
TREND-WEEK CLAUSE (HOLD): the reference's 5 best weeks sum to $+400631 and the cell's same weeks to $+393624; winning weeks turned losing: 1 of 34; $ given up inside winning weeks: -94009; sum of the 20 worst weeks cell -324609 vs ref -346649.
TREND-WEEK CLAUSE (all 3.5 years): the reference's 5 best weeks sum to $+416156 and the cell's same weeks to $+415120; winning weeks turned losing: 5 of 122; $ given up inside winning weeks: -204148; sum of the 20 worst weeks cell -635122 vs ref -638955.

## Acceptance test and scorecard (P7 sessions)
### RCU_REF
```
ACCEPTANCE P7 RCU_REF  2026-11-13 01:23Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCU_REF | 2460 | 6 | 2.0 | 0.93 | 73 | 88 | -128852 | 151 / +27563 | 85 | 98 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCU_REF | 918 | 6 | 2.0 | 0.91 | 23 | 31 | -65825 | 57 / +23807 | 29 | 45 |
SUMMARY RCU_REF: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCU_REF FAIL fails=4/20
```
```
RCU_REF L6M (stack, per week): full stops 25.4/wk $-38467; give-backs 9.8/wk (9.7 round-trips) realised $-13148, forgone vs target $34047; same-side losing runs max 13, p95 6, $-51363 lost on 3rd-and-later; no-new-evidence re-entries 42.7/wk $1610; recoveries cut 14.9/wk $47603, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2878/wk, losers avoided $3466/wk, net +5026 $/wk; pnl $24557/wk.
RCU_REF HOLD (stack, per week): full stops 23.6/wk $-35738; give-backs 8.5/wk (8.2 round-trips) realised $-11439, forgone vs target $29268; same-side losing runs max 13, p95 6, $-43852 lost on 3rd-and-later; no-new-evidence re-entries 33.9/wk $1765; recoveries cut 13.0/wk $41171, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2844/wk, losers avoided $2889/wk, net +3623 $/wk; pnl $16120/wk.
RCU_REF PRE (stack, per week): full stops 16.6/wk $-26130; give-backs 5.4/wk (5.0 round-trips) realised $-6417, forgone vs target $17099; same-side losing runs max 11, p95 5, $-20486 lost on 3rd-and-later; no-new-evidence re-entries 14.3/wk $129; recoveries cut 7.2/wk $19946, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2434/wk, losers avoided $2039/wk, net +1139 $/wk; pnl $10547/wk.
RCU_REF X' (stack, per week): full stops 17.4/wk $-26577; give-backs 3.5/wk (3.0 round-trips) realised $-4210, forgone vs target $11226; same-side losing runs max 8, p95 4, $-10881 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $1089; recoveries cut 2.5/wk $8438, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1044/wk, losers avoided $1651/wk, net +507 $/wk; pnl $2054/wk.

```
### RCL_P7_f100
```
ACCEPTANCE P7 RCL_P7_f100  2026-11-13 01:24Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCL_P7_f100 | 2493 | 6 | 2.0 | 0.94 | 79 | 97 | -97396 | 162 / +5391 | 93 | 49 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCL_P7_f100 | 918 | 6 | 2.0 | 0.93 | 26 | 36 | -43786 | 63 / +8939 | 33 | 35 |
SUMMARY RCL_P7_f100: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCL_P7_f100 FAIL fails=4/20
```
```
RCL_P7_f100 L6M (stack, per week): full stops 25.4/wk $-38135; give-backs 9.8/wk (9.7 round-trips) realised $-10804, forgone vs target $26869; same-side losing runs max 13, p95 7, $-41965 lost on 3rd-and-later; no-new-evidence re-entries 43.6/wk $1453; recoveries cut 15.2/wk $38369, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1024/wk, losers avoided $672/wk, net -1501 $/wk; pnl $18029/wk.
RCL_P7_f100 HOLD (stack, per week): full stops 23.6/wk $-35428; give-backs 8.7/wk (8.5 round-trips) realised $-9427, forgone vs target $23571; same-side losing runs max 13, p95 6, $-36392 lost on 3rd-and-later; no-new-evidence re-entries 34.4/wk $862; recoveries cut 13.1/wk $32613, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $877/wk, losers avoided $672/wk, net -582 $/wk; pnl $11915/wk.
RCL_P7_f100 PRE (stack, per week): full stops 16.8/wk $-26444; give-backs 5.4/wk (5.0 round-trips) realised $-5447, forgone vs target $14117; same-side losing runs max 11, p95 5, $-17602 lost on 3rd-and-later; no-new-evidence re-entries 14.5/wk $90; recoveries cut 7.2/wk $17148, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $195/wk, losers avoided $177/wk, net +42 $/wk; pnl $9451/wk.
RCL_P7_f100 X' (stack, per week): full stops 17.6/wk $-27166; give-backs 3.4/wk (2.9 round-trips) realised $-3503, forgone vs target $9496; same-side losing runs max 7, p95 4, $-9908 lost on 3rd-and-later; no-new-evidence re-entries 3.1/wk $296; recoveries cut 2.4/wk $6178, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $247/wk, losers avoided $335/wk, net +327 $/wk; pnl $1874/wk.

```
### RCL_P7_f067
```
ACCEPTANCE P7 RCL_P7_f067  2026-11-13 01:25Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCL_P7_f067 | 2476 | 6 | 2.0 | 0.94 | 77 | 96 | -97674 | 160 / +1855 | 93 | 54 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCL_P7_f067 | 918 | 6 | 2.0 | 0.93 | 25 | 35 | -43786 | 63 / +8079 | 33 | 40 |
SUMMARY RCL_P7_f067: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCL_P7_f067 FAIL fails=4/20
```
```
RCL_P7_f067 L6M (stack, per week): full stops 25.5/wk $-38232; give-backs 9.8/wk (9.7 round-trips) realised $-10914, forgone vs target $27211; same-side losing runs max 13, p95 7, $-42433 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1531; recoveries cut 15.1/wk $39215, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $781/wk, losers avoided $770/wk, net -546 $/wk; pnl $18984/wk.
RCL_P7_f067 HOLD (stack, per week): full stops 23.6/wk $-35441; give-backs 8.6/wk (8.4 round-trips) realised $-9555, forgone vs target $23930; same-side losing runs max 13, p95 6, $-36452 lost on 3rd-and-later; no-new-evidence re-entries 34.1/wk $1021; recoveries cut 13.0/wk $33299, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $593/wk, losers avoided $1058/wk, net -105 $/wk; pnl $12392/wk.
RCL_P7_f067 PRE (stack, per week): full stops 16.8/wk $-26445; give-backs 5.4/wk (4.9 round-trips) realised $-5490, forgone vs target $14226; same-side losing runs max 11, p95 5, $-17661 lost on 3rd-and-later; no-new-evidence re-entries 14.4/wk $38; recoveries cut 7.2/wk $17089, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $146/wk, losers avoided $168/wk, net -62 $/wk; pnl $9347/wk.
RCL_P7_f067 X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9931 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $343; recoveries cut 2.5/wk $6588, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $439/wk, losers avoided $95/wk, net -72 $/wk; pnl $1475/wk.

```
### RCL_P7_f050
```
ACCEPTANCE P7 RCL_P7_f050  2026-11-13 01:26Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCL_P7_f050 | 2463 | 6 | 2.0 | 0.94 | 77 | 95 | -96832 | 161 / +5095 | 92 | 52 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCL_P7_f050 | 918 | 6 | 2.0 | 0.93 | 26 | 36 | -44608 | 65 / +8456 | 34 | 38 |
SUMMARY RCL_P7_f050: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCL_P7_f050 FAIL fails=3/20
```
```
RCL_P7_f050 L6M (stack, per week): full stops 25.5/wk $-38232; give-backs 10.0/wk (9.8 round-trips) realised $-11130, forgone vs target $27720; same-side losing runs max 13, p95 7, $-42532 lost on 3rd-and-later; no-new-evidence re-entries 43.5/wk $1888; recoveries cut 15.1/wk $39420, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $244/wk, losers avoided $162/wk, net +23 $/wk; pnl $19553/wk.
RCL_P7_f050 HOLD (stack, per week): full stops 23.6/wk $-35512; give-backs 8.7/wk (8.4 round-trips) realised $-9621, forgone vs target $24067; same-side losing runs max 13, p95 6, $-36553 lost on 3rd-and-later; no-new-evidence re-entries 34.3/wk $1311; recoveries cut 13.1/wk $33582, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $308/wk, losers avoided $707/wk, net +243 $/wk; pnl $12740/wk.
RCL_P7_f050 PRE (stack, per week): full stops 16.8/wk $-26445; give-backs 5.4/wk (5.0 round-trips) realised $-5535, forgone vs target $14336; same-side losing runs max 11, p95 5, $-17691 lost on 3rd-and-later; no-new-evidence re-entries 14.3/wk $8; recoveries cut 7.2/wk $17074, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $98/wk, losers avoided $135/wk, net -22 $/wk; pnl $9387/wk.
RCL_P7_f050 X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9998 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $370; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $412/wk, losers avoided $58/wk, net -81 $/wk; pnl $1466/wk.

```
### RCL_ALL_f100
```
ACCEPTANCE P7 RCL_ALL_f100  2026-11-13 01:26Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCL_ALL_f100 | 2493 | 6 | 2.0 | 0.94 | 79 | 97 | -97396 | 162 / +5391 | 93 | 49 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCL_ALL_f100 | 918 | 6 | 2.0 | 0.93 | 26 | 36 | -43786 | 63 / +8939 | 33 | 35 |
SUMMARY RCL_ALL_f100: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCL_ALL_f100 FAIL fails=4/20
```
```
RCL_ALL_f100 L6M (stack, per week): full stops 24.6/wk $-37066; give-backs 9.7/wk (9.6 round-trips) realised $-10721, forgone vs target $26640; same-side losing runs max 12, p95 7, $-41265 lost on 3rd-and-later; no-new-evidence re-entries 41.6/wk $990; recoveries cut 14.8/wk $37370, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $5574/wk, losers avoided $4465/wk, net -2642 $/wk; pnl $16888/wk.
RCL_ALL_f100 HOLD (stack, per week): full stops 22.7/wk $-34245; give-backs 8.5/wk (8.3 round-trips) realised $-9286, forgone vs target $23217; same-side losing runs max 12, p95 6, $-35336 lost on 3rd-and-later; no-new-evidence re-entries 32.5/wk $721; recoveries cut 12.7/wk $31762, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $4563/wk, losers avoided $4026/wk, net -1048 $/wk; pnl $11449/wk.
RCL_ALL_f100 PRE (stack, per week): full stops 16.5/wk $-25864; give-backs 5.3/wk (4.9 round-trips) realised $-5351, forgone vs target $13875; same-side losing runs max 11, p95 4, $-17024 lost on 3rd-and-later; no-new-evidence re-entries 13.8/wk $-21; recoveries cut 7.1/wk $16860, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1665/wk, losers avoided $1709/wk, net +8 $/wk; pnl $9417/wk.
RCL_ALL_f100 X' (stack, per week): full stops 17.4/wk $-26791; give-backs 3.4/wk (2.9 round-trips) realised $-3420, forgone vs target $9357; same-side losing runs max 7, p95 4, $-9792 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $273; recoveries cut 2.4/wk $6178, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $667/wk, losers avoided $759/wk, net +420 $/wk; pnl $1967/wk.

```
### RCU_P7_f100
```
ACCEPTANCE P7 RCU_P7_f100  2026-11-13 01:27Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCU_P7_f100 | 2496 | 6 | 2.0 | 0.93 | 77 | 91 | -126525 | 152 / +11947 | 88 | 100 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCU_P7_f100 | 918 | 6 | 2.0 | 0.92 | 26 | 34 | -64398 | 60 / +13281 | 32 | 46 |
SUMMARY RCU_P7_f100: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCU_P7_f100 FAIL fails=4/20
```
```
RCU_P7_f100 L6M (stack, per week): full stops 25.5/wk $-38653; give-backs 9.8/wk (9.6 round-trips) realised $-12487, forgone vs target $32556; same-side losing runs max 13, p95 6, $-50484 lost on 3rd-and-later; no-new-evidence re-entries 43.4/wk $2065; recoveries cut 14.7/wk $45778, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $244/wk, losers avoided $734/wk, net -253 $/wk; pnl $24303/wk.
RCU_P7_f100 HOLD (stack, per week): full stops 23.6/wk $-35771; give-backs 8.4/wk (8.2 round-trips) realised $-10905, forgone vs target $27952; same-side losing runs max 13, p95 6, $-43086 lost on 3rd-and-later; no-new-evidence re-entries 34.2/wk $1938; recoveries cut 12.9/wk $39295, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $403/wk, losers avoided $639/wk, net -262 $/wk; pnl $15858/wk.
RCU_P7_f100 PRE (stack, per week): full stops 16.6/wk $-26083; give-backs 5.4/wk (5.0 round-trips) realised $-6172, forgone vs target $16440; same-side losing runs max 11, p95 5, $-20371 lost on 3rd-and-later; no-new-evidence re-entries 14.3/wk $-6; recoveries cut 7.2/wk $20021, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $228/wk, losers avoided $182/wk, net -12 $/wk; pnl $10535/wk.
RCU_P7_f100 X' (stack, per week): full stops 17.4/wk $-26631; give-backs 3.5/wk (3.0 round-trips) realised $-4157, forgone vs target $11091; same-side losing runs max 8, p95 4, $-10757 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $684; recoveries cut 2.5/wk $8678, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $192/wk, losers avoided $113/wk, net -450 $/wk; pnl $1604/wk.

```
### RCU_P7_f067
```
ACCEPTANCE P7 RCU_P7_f067  2026-11-13 01:27Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCU_P7_f067 | 2468 | 6 | 2.0 | 0.93 | 76 | 91 | -128050 | 149 / +12187 | 86 | 95 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCU_P7_f067 | 918 | 6 | 2.0 | 0.92 | 26 | 34 | -65850 | 58 / +12684 | 31 | 43 |
SUMMARY RCU_P7_f067: fails 3 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCU_P7_f067 FAIL fails=3/20
```
```
RCU_P7_f067 L6M (stack, per week): full stops 25.5/wk $-38662; give-backs 9.9/wk (9.7 round-trips) realised $-12520, forgone vs target $33516; same-side losing runs max 13, p95 6, $-50237 lost on 3rd-and-later; no-new-evidence re-entries 42.9/wk $1937; recoveries cut 14.9/wk $47219, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $537/wk, losers avoided $722/wk, net -70 $/wk; pnl $24486/wk.
RCU_P7_f067 HOLD (stack, per week): full stops 23.6/wk $-35729; give-backs 8.5/wk (8.3 round-trips) realised $-11084, forgone vs target $28818; same-side losing runs max 13, p95 6, $-42991 lost on 3rd-and-later; no-new-evidence re-entries 34.0/wk $1859; recoveries cut 13.0/wk $40445, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $403/wk, losers avoided $622/wk, net +121 $/wk; pnl $16241/wk.
RCU_P7_f067 PRE (stack, per week): full stops 16.6/wk $-26083; give-backs 5.4/wk (5.0 round-trips) realised $-6254, forgone vs target $16665; same-side losing runs max 11, p95 5, $-20436 lost on 3rd-and-later; no-new-evidence re-entries 14.3/wk $-10; recoveries cut 7.1/wk $20028, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $211/wk, losers avoided $197/wk, net +146 $/wk; pnl $10693/wk.
RCU_P7_f067 X' (stack, per week): full stops 17.4/wk $-26577; give-backs 3.5/wk (3.0 round-trips) realised $-4210, forgone vs target $11226; same-side losing runs max 8, p95 4, $-10867 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $787; recoveries cut 2.5/wk $8438, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $82/wk, losers avoided $97/wk, net +34 $/wk; pnl $2088/wk.

```
### RCU_P7_f050
```
ACCEPTANCE P7 RCU_P7_f050  2026-11-13 01:28Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCU_P7_f050 | 2462 | 6 | 2.0 | 0.93 | 72 | 87 | -126298 | 148 / +20531 | 84 | 97 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCU_P7_f050 | 918 | 6 | 2.0 | 0.91 | 23 | 31 | -65007 | 58 / +21033 | 29 | 45 |
SUMMARY RCU_P7_f050: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCU_P7_f050 FAIL fails=4/20
```
```
RCU_P7_f050 L6M (stack, per week): full stops 25.4/wk $-38610; give-backs 9.9/wk (9.7 round-trips) realised $-12871, forgone vs target $33526; same-side losing runs max 13, p95 6, $-50595 lost on 3rd-and-later; no-new-evidence re-entries 42.9/wk $2039; recoveries cut 14.8/wk $47081, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $49/wk, losers avoided $214/wk, net +628 $/wk; pnl $25185/wk.
RCU_P7_f050 HOLD (stack, per week): full stops 23.6/wk $-35704; give-backs 8.5/wk (8.3 round-trips) realised $-11251, forgone vs target $28843; same-side losing runs max 13, p95 6, $-43260 lost on 3rd-and-later; no-new-evidence re-entries 34.0/wk $2037; recoveries cut 12.9/wk $40606, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $95/wk, losers avoided $221/wk, net +590 $/wk; pnl $16710/wk.
RCU_P7_f050 PRE (stack, per week): full stops 16.6/wk $-26099; give-backs 5.4/wk (5.0 round-trips) realised $-6326, forgone vs target $16865; same-side losing runs max 11, p95 5, $-20425 lost on 3rd-and-later; no-new-evidence re-entries 14.2/wk $-29; recoveries cut 7.1/wk $19917, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $211/wk, losers avoided $200/wk, net -67 $/wk; pnl $10480/wk.
RCU_P7_f050 X' (stack, per week): full stops 17.4/wk $-26577; give-backs 3.5/wk (3.0 round-trips) realised $-4210, forgone vs target $11226; same-side losing runs max 8, p95 4, $-10881 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $842; recoveries cut 2.5/wk $8438, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $27/wk, losers avoided $97/wk, net -20 $/wk; pnl $2033/wk.

```
### RCU_ALL_f100
```
ACCEPTANCE P7 RCU_ALL_f100  2026-11-13 01:29Z   (months 43: 202304..202610; reference LPB_BASE months 43)
| all P7 | LPB_BASE (live ref) | 2213 | 6 | 2.0 | 0.89 | 48 | 57 | -136326 | 90 / -11382 | 53 | 110 |
| all P7 | RCU_ALL_f100 | 2496 | 6 | 2.0 | 0.93 | 77 | 91 | -126525 | 152 / +11947 | 88 | 99 |
| Asia | LPB_BASE (live ref) | 919 | 6 | 2.0 | 0.90 | 21 | 26 | -80482 | 37 / -10876 | 24 | 33 |
| Asia | RCU_ALL_f100 | 918 | 6 | 2.0 | 0.92 | 26 | 34 | -64398 | 60 / +13281 | 32 | 46 |
SUMMARY RCU_ALL_f100: fails 4 of 20 sessions (rule: PASS needs <= 2); winners kept on the 5 best sessions ['0->0', '0->0', '0->0', '0->0', '0->0']
ACCEPT RCU_ALL_f100 FAIL fails=4/20
```
```
RCU_ALL_f100 L6M (stack, per week): full stops 24.7/wk $-37640; give-backs 9.7/wk (9.6 round-trips) realised $-12385, forgone vs target $32308; same-side losing runs max 12, p95 7, $-49797 lost on 3rd-and-later; no-new-evidence re-entries 41.4/wk $1637; recoveries cut 14.3/wk $44854, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $4904/wk, losers avoided $4565/wk, net -1255 $/wk; pnl $23301/wk.
RCU_ALL_f100 HOLD (stack, per week): full stops 22.8/wk $-34613; give-backs 8.3/wk (8.1 round-trips) realised $-10782, forgone vs target $27663; same-side losing runs max 12, p95 6, $-41978 lost on 3rd-and-later; no-new-evidence re-entries 32.4/wk $1865; recoveries cut 12.5/wk $38478, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $3900/wk, losers avoided $4009/wk, net -503 $/wk; pnl $15617/wk.
RCU_ALL_f100 PRE (stack, per week): full stops 16.2/wk $-25536; give-backs 5.3/wk (4.9 round-trips) realised $-6091, forgone vs target $16230; same-side losing runs max 11, p95 4, $-19819 lost on 3rd-and-later; no-new-evidence re-entries 13.6/wk $-182; recoveries cut 7.1/wk $19732, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $1649/wk, losers avoided $1626/wk, net -16 $/wk; pnl $10531/wk.
RCU_ALL_f100 X' (stack, per week): full stops 17.2/wk $-26307; give-backs 3.5/wk (3.0 round-trips) realised $-4115, forgone vs target $11021; same-side losing runs max 8, p95 4, $-10689 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $716; recoveries cut 2.5/wk $8678, clipped fills 0.0/wk $0; vs RCU_REF: winners skipped $475/wk, losers avoided $463/wk, net -331 $/wk; pnl $1723/wk.

```