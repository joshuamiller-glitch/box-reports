# DECISION_PACK_20261106 - one document for the user (CHAR-B, IDEAS_ROUND2 R3 + R4, 2026-11-06)
Research only. Nothing here is a recommendation, nothing goes live, nothing is bought. Every number carries its file in brackets; a number marked PROXY is an assumption from the cited file, not a broker figure; "n/a" = not in our files. Names the base wherever a base matters (V0 = engine as run, V1 = 18:00-18:04 blocked, V2 = V1 + 09:30-09:59 blocked, V3 = 09:30-09:59 only; USER_BRIEF_20261105_v2.md, DS3_LIVE_WINDOWS_BASE.md). Parts: (1) capital / margin / micro audit, (2) the WATCH register and a pooled sequential-evidence plan, (3) open decisions with defaults, (4) one-page summary of what the box found since 2026-11-05 19:30Z.
Simulation code and outputs: /mnt/l2/l2vast/find_b/pack/watch_sim.py, watch_sim.json, pool_sim.py, pool_sim.json, register_level.json (20,000 draws per cell, numpy, seed fixed in the code).

---------------------------------------------------------------------------------------------------
## PART 1. Capital, margin and micro-lot audit of the live stack and the Shadow watch items

### 1a. What the live stack is, in lots (engine of record = D7 Q1-A ts2, ENGINE_CONFIG_LIVE_Q1A.md rows 3, 4, 7, 8)
| item | value | file |
|--|--|--|
| Books and planned lots (NQ contracts) | PE 7, HM 4, SM 4, KB 2, MV 2, PB 1 | ENGINE_CONFIG_LIVE_Q1A.md row 3 |
| Session lots [asia london pre nyam nypm close] | KB 2/2/0/1/2/0, PE 7/7/0/7/0/0, SM 4/4/0/0/0/0, HM 4/0/0/1/0/0, MV 0/2/0/1/0/0, PB 1/0/0/0/0/0 | row 3 |
| Lot order | session lots -> A06 x0.5 -> B02 x0.5 (ONE rounding, floor(x+0.5), minimum 1) -> ER ladder (x0.5 when ER(20) < 0.30; rounded, min 1) -> zone HALF (x0.5, rounded, min 1) | row 4, 6, 7, 8 |
| $ per point and fee | NQ $20/pt; fee $4.84 round trip per contract (NQ exchange part is a PROXY: ES value) | FEES.md |
| Notional per NQ at 28,600 | about $570k per NQ; $57k per MNQ | WATCH_MONDAY_LONG_SPEC.md section 1 |
| Net exposure | absolute net lots reach 10 / 14 / 18 on 9.2% / 1.5% / 0.09% of entries (V0) | DS3_EXPOSURE_CAP.md (via USER_BRIEF_20261105_v2.md section 3) |

### 1b. Worst day, worst week, drawdown (engine runs; quote the base every time)
| quantity | V0 | V1 | V2 | V3 | file |
|--|--|--|--|--|--|
| Total P&L, 935 label days | $2,520k | $2,593k | $2,462k | $2,382k | USER_BRIEF_20261105_v2.md section 1 (DS3_LIVE_WINDOWS_BASE.md) |
| Mean per week | $17.7k | $17.5k | $16.5k | $16.7k | same |
| HOLD maxDD | $122.0k | $103.3k | $91.2k | $110.6k | same |
| PRE maxDD | $75.1k | n/a | n/a | n/a | same |
| Worst day / worst week (V0) | -$38.1k / -$62.6k | n/a | about -$60k (worst week, DIS-BJ note) | n/a | USER_BRIEF section 1; MORNING_FLAGS.md KEY (DIS-BJ/BR) |
| 52-week forward maxDD median / p90 / p99 (V0, all history) | $92.5k / $148.7k / $217.9k, P(>$150k) = .095; if 2026 lasts $122.0k / $181.7k / $263.3k (P = .21) | | V2: P(>$150k) .050 | | DS3_FWD_DD.md; DS3_LIVE_WINDOWS_BASE.md |
| Synthetic gap (NOT a replay): 18 net lots | -$522k for a 1,449-point move (= 18 x $20 x 1,449) | | | | DS3_TAIL_STRESS.md, DS3_EXPOSURE_CAP.md |
| Limit moves 7 / 13 / 20% (synthetic; CME limit rules UNVERIFIED) | -$630k / -$1.17M / -$1.8M | | | | DS3_TAIL_STRESS.md |
| Outage, orders resting at exchange vs not | about $110-114 per hour vs worst 60 min -$32.2k (lost profit) / -$48.6k; stop and target not OCO -$38.0k per hour; full Asia session -$79.2k = 65% of the HOLD episode | | | | DS3_OUTAGE.md (corrected section) |
| Concentration | PE = 53% of HOLD P&L (61% L6M) and $104k of the $122k HOLD drawdown; without PE: HOLD $13.6k/week, maxDD $32.9k | | | | DS3_CONCENTRATION.md |

### 1c. Margin (PROXY, labelled) and capital
No exchange or broker margin number for NQ exists in our files (the CL watch spec says "Margin: not in the repository", WATCH_CL_DONCHIAN_SPEC.md section 2). The only stated assumption is "8-10% of notional" there. Applying that same PROXY to the NQ stack, and to nothing more precise:
| exposure | notional (from the cited $570k per NQ) | PROXY margin at 8-10% of notional |
|--|--|--|
| 1 NQ | $570k | $46k-$57k |
| 10 net NQ (the 9.2%-of-entries level) | $5.7M | $456k-$570k |
| 18 net NQ (the 0.09% level) | $10.3M | $821k-$1.03M |
| 1 MNQ | $57k | $4.6k-$5.7k |
| 1 CL (watch) | median $66.7k (range $12.6k-$124k) | $5k-$7k stated by the spec (8-10%) |
Account equity is NOT in any file read here: SPEND.json's $711.74 is the DATA budget, not trading capital (USER_BRIEF_20261105_v2.md section 4 item 8). What the user must supply for a capital line: account equity and the broker's NQ / MNQ / CL / MGC intraday and overnight margin. With those, capital needed = margin proxy at the chosen net-lot cap + a drawdown cushion; the cushions in our files are HOLD maxDD $91.2k-$122.0k (V2-V0) and the 52-week p99 $217.9k-$263.3k (V0; DS3_FWD_DD.md). Net-lot cap options (DS3_EXPOSURE_CAP.md): cap 8/10/12/14 costs 21.6% / 13.4% / 6.7% / 2.9% of total P&L, synthetic tail $319k / $377k / $435k / $464k vs $522k, V0 HOLD maxDD $122.0k -> $101.9k at cap 8.

### 1d. Micro-lot granularity of the live lot logic (derived from the rules in 1a; no new compute)
The lot chain rounds once with floor(x + 0.5) and a minimum of 1 contract (ENGINE_CONFIG_LIVE_Q1A.md rows 4-8). Consequences in whole NQ contracts:
| book at planned lots | one x0.5 rule (ER, A06, B02 or zone HALF) gives | what a 1/10-size contract (MNQ) would give | 
|--|--|--|
| PE 7 | 3.5 -> 4 (+14% above the intended half) | 3.5 NQ = 35 MNQ exactly |
| HM 4, SM 4 | 2 | 20 MNQ |
| KB 2, MV 2 | 1 | 10 MNQ |
| PB 1 (asia) and the 1-lot NY-AM cells of KB, HM, MV | stays 1 (minimum 1): a x0.5 rule does nothing, so the book carries 2x its intended risk whenever a halving rule fires | 5 MNQ = exact half |
Two halvings in one entry (A06 and B02, then ER and zone HALF, with one rounding for the first pair only) therefore cannot reach below 1 NQ contract on any book; the live ladder is coarse by construction. Whether D7 trades NQ or MNQ for each book is not stated in the files (the 18-lot loss arithmetic in 1b is NQ at $20/pt). If the user wants halving to be exact, MNQ granularity is the only route; the cost is the fee: MNQ round trip $1.78 (PROXY: MES value) = $17.8 per NQ-equivalent vs $4.84 for NQ, 3.7x (FEES.md).

### 1e. Shadow lines: lots and risk at 1 lot (SHADOW_LOT_TABLE.md; research numbers, not recommendations)
Reference live-book lot = $1,200 stop risk (60-pt stop). Equal-risk lots per trade (integer, min 1, cap 6) from SHADOW_LOT_TABLE.md section (a), and the line's own tail from section (c):
| line | $ stop risk per lot | equal-risk lots | worst week at 1 lot (all weeks) | own HOLD maxDD at 1 lot | stack HOLD maxDD change at 1 lot |
|--|--|--|--|--|--|
| Q13GAP_T1 | $617 | 3 | -$3,117 | -$9,125 | +$7,987 |
| DISK_BO_CH | $1,200 | 1 | -$3,820 | -$5,133 | -$2,030 |
| DISB_PREL | $451 | 3 | -$3,922 | -$5,218 | +$792 |
| DISE_PDF | $453 | 3 | -$3,863 | -$5,271 | -$646 |
| DISC_SUN30 | $343 | 4 | -$1,345 | -$4,271 | +$383 |
| NYAM_bundle (ONRTH + VWAPF + ORBF) | $1,200 each | 1 each | -$13,968 | -$23,311 | +$11,621 |
| VB2NYPM_T1 / PDASIA_T2 / VB2NYAM_T3 | $414 / $545 / $567 | 3 / 3 / 2 | -$2,983 / -$3,239 / -$3,769 | -$3,141 / -$2,192 / -$5,375 | +$758 / +$555 / +$1,730 |
| OR15NYAM_T2 | $1,063 | 1 | -$8,490 | -$46,980 | -$13,803 |
| N_REL_rev | $563 | 2 | -$3,308 | -$11,020 | +$7,225 |
Conservative (winner's-curse deflated) weekly means are negative for all 14 lines in both ALL and HOLD (e.g. NYAM_bundle HOLD -$48, ORBF -$592, OR15NYAM_T2 -$2,622; SHADOW_LOT_TABLE.md section (b)). A line cannot be sized below one lot; for the 60/60 lines the 0.5x equal-risk size rounds to 1.

### 1f. WATCH-register items: granularity and size (from the specs)
| watch | instrument and unit | size facts | file |
|--|--|--|--|
| MONDAY_LONG | 1 MNQ ($57k notional; NQ-lot $ derived x10); Monday sd 120.6 bps = $690 per MNQ ($6.9k per NQ); fee $1.28 RT booked | worst ES Monday -644 bps = -$8.8k per ES, -$880 per MES; kill n = 8: cum <= -682 bps (-$3.9k per MNQ) | WATCH_MONDAY_LONG_SPEC.md sections 1-3 |
| NQ_PDL | 1 MNQ; NQ-sized equal-risk would be 14 contracts (not used); cost $14.84 per NQ RT, $2.28 per MNQ | per-trade sd $12.91 per MNQ; 3.3 trades/week | WATCH_NQ_PDL_SPEC.md sections 1-2 |
| RTY_PREMARKET | RTY equal-risk lots clip(floor(1200 / (stop x $50) + .5), 1, cap) with cap 6.7 (pre session); M2K would be 1/10 size | kill: cum net <= -$6,000 | WATCH_RTY_PREMARKET_SPEC.md section 1, 3 |
| CL_DONCHIAN | 1 CL ($66.7k median notional; MCL = 1/10 not specified in the spec; MCL fee $2.08 RT, WEAK, FEES.md) | PROXY margin $5k-$7k per lot held overnight; K1 $47,782 DD, K2 -$26,761 cum | WATCH_CL_DONCHIAN_SPEC.md sections 2, 4 |
| MBT_KELTNER | 1 MBT (cap 1.43 contracts/5 min); fee $1.78 RT PROXY-MICRO | $34-$80 risk per trade, $8-15 earned per trade before deflation, about $6-15 per week = 0.1% of the stack's $17.7k/week | WATCH_BTCM_KELTNER_SPEC.md header |
| GC_TREND | GC integer lots, median stop risk about $1,040 per lot; MGC = 10 x GC lots, MGC fee unmeasured | HOLD mean +$557/wk, maxDD $25,176; PRE -$270/wk | WATCH_GC_TREND_SPEC.md |

---------------------------------------------------------------------------------------------------
## PART 2. The WATCH register: data, cost, time to a verdict, and a pooled sequential-evidence plan

### 2a. Status today (WATCH_REGISTER.md, last run 2026-11-06T03:26Z) and what each item needs
| watch (spec sha12) | register status | data it needs | cost to run | event rate and time to the spec's decisive read |
|--|--|--|--|--|
| MONDAY_LONG (33734760..) | ACCUMULATING, N = 0 of 26; week 1 = Monday 2026-11-09 | forward NQ tables; CACHE_REFRESH_PLAN.md says no owned data exists for label days >= 2026-11-02 until the Sat 11-07 NQ pull (or the weekly L2 buy) is made; the register shows data to 2026-11-05 16:05Z, so the Monday 11-09 read needs the pull to have happened | $0 extra if the NQ feed arrives; the feed itself is $1.14/week (ohlcv-1s, cap $2.00, FEED_RUNBOOK_20261107.md) | 1 per week; PASS needs 26 Mondays = Monday 2027-05-03 at the earliest, read 05-04 (power about 50% at a true +28 bps, spec section 2); kill read from n = 8 (Monday 2026-12-28, read 12-29) |
| RTY_PREMARKET (c9b8563d..) | NO-DATA (no RTY after 2026-10-30) | weekly RTY mbp-10 tables | weekly L2 NQ+ES+RTY about $36-38; RTY alone about $3.3 per week (QUESTIONS.md Q9); default = no buy; metadata quote only | about 8 events per quarter = 0.62 per week; 20 trades about 7.8 months; PASS needs 40 trades = 4-5 years (spec section 2) |
| CL_DONCHIAN (ce175343..) | NO-DATA (CL ends 2026-10-16) | CL 1-min top-ups from 2026-10-17 (owned feed top-up job) | $0 (owned top-ups), 1 lot | episodes every few weeks; kill-only, first fixed read at 24 months (2028-10-16) |
| MBT_ASIA_KELTNER (b82f1d44..) | NO-DATA (MBT table ends 2026-10-31 23:43Z) | MBT 1-min top-ups | $0 | 39 trades/year = 0.75/week; n = 20 about 6 months, n = 60 about 18 months |
| NQ_PDL (8f7faa58..) | NO-DATA | NQ ohlcv-1s weekly pull (volume, front id); owned 1-min tables cannot carry a 30-s hold | about $1.14 per week (user approval pending); free secondary: L2 version on the already-arriving mbp-10, not counted for the pass | 3.3 trades/week; 60 trades about 18 weeks; final read at 26 weeks |
| GC_TREND (register name GC_REGIME, SPEC-PENDING: the register looks for WATCH_GC_REGIME_SPEC.md but the file is WATCH_GC_TREND_SPEC.md) | SPEC-PENDING (file-name mismatch, not a data fact) | GC 1-min weekly top-up (no purchase) | $0 | at least 100 trades and 26 active weeks for PASS-WATCH; kills checked every Friday |
The register table therefore shows 5 of 6 items with no forward data at all today; only MONDAY_LONG can start accumulating and only after the Sat 11-07 pull.

### 2b. Item-level simulation: what the register can say by 2027-06-30 if the data flows
Method: each item's own fixed rule (the spec's kill / pass thresholds), the spec's own event rate and noise, 20,000 draws; "pass" is an UPPER BOUND (only the statistical criterion is simulated; the other pass criteria (correlation, stack Calmar, placebo details, trade counts for GC) would lower it). Horizon: weeks from 2026-11-09 (33 reads; MBT from 11-01, CL from 10-17, RTY 34 weeks). Inputs and sources:
- MONDAY: Monday sd 120.6 bps; kill n >= 8 cum <= -2 x 120.6 x sqrt(n) or 13 consecutive weekly reads with cum <= 0; pass z >= 1.28 on the excess at n = 26; excess +12.2 bps (full sample) or +28.4 (2023+) or 0 (WATCH_MONDAY_LONG_SPEC.md sections 2-3).
- RTY: 8 events/quarter; per-trade sd of F 119.4 ticks = se 11.654 x sqrt(105) from the base node q .9, buffer 0, latency 1 s, hold 1800 s (deep_surface.csv, row RTY pre 1800: n 105, F +13.37, spread 4.0 + fee 0.97 ticks, net +8.40); H1 = F +13.37 (in-sample) or half of it; kill (i) at the first 20 trades: mean net <= 0 and mean F <= 0; kill (ii) cum net <= -$6,000 assuming 6 lots at $5/tick (ASSUMPTION; ignores stop truncation, so it overstates how often (ii) fires).
- CL: weekly sd $26,761/sqrt(52) = $3.71k, weekly mean $195 (13-year $132,164 over 676 weeks), K1 DD >= $47,782, K2 cum <= -$26,761 (WATCH_CL_DONCHIAN_SPEC.md); the fixed 24-month read is beyond the horizon.
- MBT: 39 trades/year, trade sd 1.0 R, kill t <= -1.0 at any n >= 20; H1 +0.07 R (the spec's shrunk prior) or +0.151 (in-sample); PERSISTS needs n = 60 (about 18 months) so it cannot occur by 2027-06 (WATCH_BTCM_KELTNER_SPEC.md section 4).
- NQ_PDL: 3.3 trades/week, sd $12.91 per MNQ, kill n >= 20 cum <= -2 x 12.91 x sqrt(n), final read at 60 trades or 26 weeks, pass z >= 1.28; H1 = +$2.00 per trade (the spec's own power example), H0 history = -$1.69 per trade (bar-based replay) (WATCH_NQ_PDL_SPEC.md sections 2-3).
- GC: weekly sd $4,162; K1 cum <= -$12,588, K2 DD >= $25,176, K3 mean < -$1,616 at 13 weeks, K4 mean < 0 at 26 weeks; PASS-WATCH at 26 weeks: mean >= $278, cum > 0, DD < $25,176, >= 55% positive 4-week blocks; true mean $557 (HOLD), $278, 0 or -$270 (PRE) (WATCH_GC_TREND_SPEC.md).

| item | scenario | P(kill fires by 2027-06-30) | P(pass candidate, upper bound) | other |
|--|--|--|--|--|
| MONDAY_LONG | no excess | 0.46 | 0.10 | no decision 0.44 |
| MONDAY_LONG | excess +12.2 bps | 0.29 | 0.22 | no decision 0.49 |
| MONDAY_LONG | excess +28.4 bps (2023+) | 0.12 | 0.46 | no decision 0.41 |
| RTY_PREMARKET (if L2 flowed) | F = 0 / half / in-sample | 0.68 / 0.60 / 0.52 any kill (kill (i) 0.30 / 0.24 / 0.19) | 0.0002 (PASS needs N >= 40) | only 61% of draws reach the 20 trades |
| CL_DONCHIAN | mean +$195 / 0 / -$400 per week | 0.13 / 0.20 / 0.41 | cannot pass (kill-only) | continue-eligibility is at 36 months |
| MBT_KELTNER | +0.07 R / +0.151 / 0 / -0.10 | 0.13 / 0.07 / 0.21 / 0.37 | 0 (PERSISTS needs n = 60) | 89% reach n = 20 by 2027-06 |
| NQ_PDL | +$2.00 / 0 / -$1.69 per trade | 0.01 / 0.11 / 0.45 | 0.48 / 0.10 / 0.01 | final-read null or not testable 0.51 / 0.79 / 0.54 |
| GC_TREND | +$557 / +$278 / 0 / -$270 per week | 0.38 / 0.51 / 0.63 / 0.75 | 0.44 / 0.31 / 0.22 / 0.14 | |
Reading: (i) the Monday, RTY, GC and CL kill rules fire at rates that are close under "real" and "no edge" (e.g. GC 0.38 vs 0.63; RTY kill (ii) 0.52 vs 0.67): a kill by 2027-06 mostly reflects noise, not absence of an effect. (ii) The only discriminating item by 2027-06 is NQ_PDL (pass 0.48 if the +$2 edge is real vs 0.10 at zero, kill 0.45 if the bar-based history is the truth) and Monday if the 2023+ excess persists (0.46 vs 0.10). (iii) RTY cannot reach a PASS by 2027-06 under any scenario and has no data.

### 2c. The register as a whole (independent items, from the table above; /mnt/l2/l2vast/find_b/pack/register_level.json)
| world | P(at least one item reaches a PASS candidate, upper bound) | P(at least one KILL fires) |
|--|--|--|
| every item has no edge | 0.37 | 0.96 (expected 2.3 kills) |
| every item has half of its in-sample effect | 0.72 | 0.90 (expected 1.7 kills) |
| only items with a feed today (Monday after the Sat pull, GC top-up) | null 0.30 / half-effect 0.46 | null 0.80 / half-effect 0.66 |
So by 2027-06 the register will almost certainly kill something whatever is true, and in an all-null world it throws up a pass-candidate about one time in three (before the extra pass criteria). A single item's pass-candidate must not be promoted on its own p; use Holm across the active items (per-item level .10/k for k active items) or the pooled test below. Probability that the register tells us anything by 2027-06 depends on one input the user controls: whether the NQ ohlcv-1s weekly pull (about $1.14/week, about $37 for 33 weeks) runs. With it, NQ_PDL gives a decisive read (kill or pass) with probability about 0.46 under the bar-based history, 0.49 if the +$2 edge is real, and 0.21 under zero edge (kill 0.11 + pass 0.10); without it, only Monday and GC can say anything.

### 2d. Pooled sequential-evidence plan (pre-registered here, boundaries fixed now)
Pool only items that share one hypothesis. Two groups exist:
1. **Prior-day-level touch continuation: NQ_PDL (30 s, NQ) + RTY_PREMARKET (30 min, RTY).** One SPRT on standardised per-trade outcomes y = net / sd (NQ_PDL: sd $12.91; RTY: F / 119.4 ticks), each trade adds LLR = d1 y - d1^2 / 2 with d1 = 0.155 for NQ_PDL (+$2 / $12.91) and 0.056 for RTY (half of 13.37 / 119.4); H0: d = 0; boundaries alpha .05, beta .20: accept H1 at LLR >= ln(.8/.05) = 2.77, accept H0 at LLR <= ln(.2/.95) = -1.56. Simulated 2026-11-09 to 2027-06-28 (/mnt/l2/l2vast/find_b/pack/pool_sim.json):
| stream | true effect | P(accept H1) | P(accept H0) | P(undecided by 2027-06) | median weeks if decided |
|--|--|--|--|--|--|
| NQ_PDL alone | +$2 per trade | 0.24 | 0.10 | 0.66 | 23 |
| NQ_PDL alone | zero | 0.01 | 0.57 | 0.42 | 18 |
| NQ_PDL alone | bar-based history -$1.69 | 0.0003 | 0.93 | 0.07 | 13 |
| RTY alone | any | 0 | 0 | 1.00 | none (about 21 trades with sd 119 ticks carry almost no information) |
| POOLED NQ_PDL + RTY | +$2 / +6.7 ticks | 0.25 | 0.10 | 0.65 | 23 |
| POOLED | zero | 0.01 | 0.58 | 0.41 | 17 |
Result: pooling the two adds nothing measurable by 2027-06 (RTY contributes 0.62 trades/week at a per-trade signal-to-noise of 0.06); the pooled test is NQ_PDL in practice. The SPRT is a better stopping rule than the spec's fixed 60-trade / 26-week read (it decides in a median 13-23 weeks when it decides) but only decides in about 35-60% of paths.
2. **Equity Monday long (NQ only in the watch).** Pooling with ES/RTY/YM Mondays would need new tables (a metadata cost quote only, default no buy; WATCH_MONDAY_LONG_SPEC.md section 1), so no pooling is available at zero cost. Plan: keep the spec's fixed kill rules, and replace the "13 consecutive weekly reads with cum <= 0" kill (it fires 46% under no edge and 29% under a real +12.2 bps excess in the simulation above) with a one-sided SPRT on weekly excess: H0 0 vs H1 +28.4 bps (2023+), sd 120.6 bps, same alpha .05 / beta .20. Expected-sample-size table for the SPRT: to be produced only if the user wants the change (the spec is frozen until then; no change is made here).
3. **Items with no shared hypothesis (CL Donchian, MBT Keltner, GC trend).** Keep their frozen kill rules; the simulation shows they are kill-tests with low power (MBT cannot reach its PERSISTS read before about 18 months; CL's first fixed read is 24 months).
Multiplicity across the register: any promotion needs Holm at level .10 over the active items, plus the spec's own criteria (corr to the NQ stack <= .3, stack Calmar not lower). All six are best-of-F or REGIME items (DS3_FIND_FINAL.md section 2); none is established.

---------------------------------------------------------------------------------------------------
## PART 3. Open user decisions (one list; consequence of yes/no; what work waits; the default taken while waiting)
Source for most rows: USER_BRIEF_20261105_v2.md section 5, MORNING_FLAGS.md, QUESTIONS.md, MONDAY_PREFLIGHT_20261109.md. "Default" = what the box does until you answer, stated in the cited file; where no default is stated I mark it (proposed) and the lead should confirm.
| # | decision | if YES / option A | if NO / option B | work that waits | default while waiting |
|--|--|--|--|--|--|
| 1 | **Saturday 11-07 NQ pull** (ohlcv-1s, window 2026-11-01T23:00Z to 11-07T00:00Z, about $1.14, cap $2.00; manual `hm_feed.py --execute` with the confirm string; FEED_RUNBOOK_20261107.md) | Monday 11-09 table has outcome data; HM anchor replay possible; NQ_PDL and the Monday-long watch can start; $1.14/week recurring (about $37 to 2027-06) | Monday table reads "no data yet" with a FEED / TAPE 'NO TAPE' row (MONDAY_PREFLIGHT_20261109.md); NQ_PDL and RTY watches stay NO-DATA; Monday-long week 1 cannot be read | Monday table, watch register, HM anchor replay, Shadow outcomes 11-04..11-06 | no purchase (nothing schedules it) |
| 2 | **MONDAY_START** (env; runners ignore signals logged before 2026-11-04; the feed and tape cover 11-02) | set MONDAY_START to include 11-02/11-03 signals if the box logged any | keep 2026-11-04 | which Shadow signals appear in the Monday table (PF-9 OPEN in MONDAY_PREFLIGHT_20261109.md) | 2026-11-04 (runbook intent) - lead to confirm |
| 3 | **Pre-2023 L2** (ES/RTY mbp-10 history; NQ before 2023-02) | one metadata cost quote first (DS3_FIND_FINAL.md section 3 item 1); would give the first pre-2023 evidence for any tick-scale item; price not in our files | every tick-scale row stays "no pre-2023 evidence"; the 1-min proxy failed calibration (weekly corr 0.56-0.77 vs 0.90 gate; deep_proxy_calib.csv) | RTY pre-market watch, NQ/ES prior-day-level items | no purchase (quote only on request) |
| 4 | **Entry-window question V0-V3** (is 09:00-09:59 blocked? 18:00-18:04 or 18:05? tested at signal or fill time for P7? do windows apply to Shadow lines?) | each answer fixes the base: only 18:00 blocked -> HOLD maxDD $103.3k, mean $17.5k (V1); both -> $91.2k, $16.5k, P(>$150k) .05 (V2); neither -> V0 $122.0k, $17.7k | unanswered: every drawdown figure is quoted under V0 and V2 | restating all engine-based headlines on one base (DIS-BJ/BR); NY-AM fade bundle label (clears per cell only under W1/V2); Shadow lines N_REL_rev, Q13, DIS-Q fully blocked under W1 | report V0 and V2 beside each other (USER_BRIEF section 5 item 1) |
| 5 | **Stop order type**: native stop-market vs join-then-market | native 1.28 pt (8 stops) vs join 2.45 pt (21 stops): +$3,097/week on six books (PE +$1,711), only +$0.6k if native is really 2.20; native on all books, the A/B stops | A/B continues; needs about 200 stops per arm, otherwise 6-8 weeks | stop A/B (FORWARD_STOP_AB.md), cost model of every engine run (2.45 used) | engine uses 2.45; A/B continues |
| 6 | **Order structure**: OCO? exchange-resting stop/target, kept or cancelled on disconnect? stop-market vs stop-limit? which exits are box-side (TH cut, time exit, 16:55 flat)? | answers choose the outage row: about $110/hour vs -$38k to -$79k per hour / Asia session (DS3_OUTAGE.md); box-side exits are 57% of trades | outage figures stay as a range | outage tail line, the TH-L2-as-resting-stop question | range reported |
| 7 | **Logging, 5-file minimum set** (fills, signals, d6_stops, th_cuts, control_pnl; D7_LOGGING_REQUEST.md; ES bars source; delivery folder and cadence; per-lot P&L must divide by lots_final since 11-02) | the TH-L2 cut's real cost, the stop A/B, fees (NQ fees are a proxy), live-vs-model gap become measurable | TH-L2 sign stays hostage to an unmeasured cost (post-cap gain +$18.1k/wk on the 10-s grid; $9.9k/wk if evaluated every second; zero at +3.5 pt slippage; DS3_TH_CLOCK.md / DS3_TH_COST.md) | live-vs-model reconciliation, TH-L2 clock and cost, Shadow tracking vs live | no logs, no reconciliation |
| 8 | **Risk dials** (appetite; no research number picks one) | PE x0.5: HOLD maxDD $122.0k -> $82.4k at -23% of the mean (DS3_BOOK_WEIGHTS.md); net-lot cap 8/10/12/14 costs 21.6/13.4/6.7/2.9% of total P&L; frontier extreme PE x0.5 + cap 8 + 1R gate: mean $11.3k, worst-of maxDD $58.3k (V0; V2 $10.39k and $39.3k) (DS3_RISK_FRONTIER.md v3) | stack stays as is (V0 HOLD maxDD $122.0k) | nothing waits on it; it sets drawdown tolerance and the capital line in Part 1 | none changed |
| 9 | **HM VWAP anchor**: ET midnight or fixed UTC-4 (23:00 EST in winter)? Is the platform clock ET? | replicas follow your answer | one winter week of HM fills settles it (11-02..11-06 can be replayed with both anchors once logs/fills exist) | HM replica; about 10% of HM entries differ in winter; last winter A-B -$16.8k over 18 weeks at live lots (weekly sd $4.7k) (HM_VWAP_ANCHOR.md; DST_AUDIT_20261105.md) | EDT identical; unresolved for winter |
| 10 | **Weekly L2 extension NQ+ES+RTY about $36-38/week** (about 18 weeks of the $711.74) vs NQ-only $1.15/week | refreshes the L2-dependent caches (TH-L2 inputs, DIS-E RF, ES/RTY) and RTY pre-market data; December refit gets new data | caches and the 2026-12-01 ledger refit stay at 2026-10-30 | TH-L2 re-fit/validation on post-11-01 data, RTY watch, L2 features | no purchase (CACHE_REFRESH_PLAN.md) |
| 11 | **Next-step choice for the intraday-index search** (DS3_FIND_FINAL.md section 3 item 3) | (a) close the intraday-index discovery and run only the forward WATCH items; | (b) point effort at something that changes the cost wall (fee/rebate tier, longer pre-2023 L2, other products); more searching on the same data adds multiplicity, not evidence | all new discovery programs | box runs the WATCH items and standing programs |
| 12 | **Monday long as a Shadow watch from 2026-11-09, and its relation to the stack's entry windows** (DS3_FIND_FINAL.md section 3 item 2) | costs nothing if the feed arrives; fixed kill rule; book corr to stack at most .12; enters 18:00 Sunday while V1/V2 block 18:00-18:04/05 | no Monday watch | the watch has no live path anyway | Shadow watch starts at week 1 = 2026-11-09 |
| 13 | **MBO seven**: live MNQ fills after 2026-02-06 (if any) and the fit period of the frozen Stage-6 scores | the seven can be scored on windows overlapping the stack (DS3_MBO7.md: weekly corr -0.02; at 1/3 size stack mean +13%, Calmar .121 -> .137, maxDD flat; file ends 2026-02-06) | the leg stays unscorable on recent windows and possibly selection-contaminated | MBO7 recent-window score | reading taken: whole file possibly selection-contaminated |
| 14 | **18 stopped processes / pid 1117680 and the root disk (96% full)** (MORNING_FLAGS.md USER ACTION 3 and 2) | free 30.6 GB RAM and ~10 locks | untouched | nothing in research waits | untouched |
| 15 | **Early closes and windows already scheduled**: Thu 2026-11-26 13:00 ET and Fri 2026-11-27 13:15 ET; Tue 12-01 02:00Z ledger refit (same data unless caches refreshed); about 12-15 December roll | none required | | | USER_BRIEF section 6 |

---------------------------------------------------------------------------------------------------
## PART 4. One-page honest summary of what the box found since 2026-11-05 19:30Z
**Bottom line: it found a lot of character and no new book.** Every claim below traces to the file named.
1. **T-INSTR-2 (12 instruments, own grids; DS3_INSTR2_FINAL.md).** Joint null over 2,129,018 eligible cells: nothing clears the diversifier bar on ES, RTY, YM, GC, CL, 6E, 6J, ZN, ZB, BTC, MBT, NKD. Tolerant-gate passers exist in large numbers (e.g. GC 1,756 of 141,120; ES 8,149 of 456,498) but every one is best-of-F or REGIME (positive in 2026 only; GC 40 finalists all negative 2013-2023, 0-6 of 11 pre-2023 years positive). ZN, ZB, NKD are NULL; BTC standard and NKD are CAP-BREACH (under 1 contract per 5 minutes inside the 1.7% cap).
2. **T-FIND (what each instrument does; DS3_FIND_FINAL.md, DS3_FIND_CHARACTER.md).** Almost all structure is mean reversion at 1-30 minutes plus last-print bid-ask bounce, and it is smaller than the cost of trading it: 0 of 13 instruments produce a clearing book on 1-minute bars, on 1-second book data (taker and maker) and at the daily horizon. Examples: ZN 5-minute autocorrelation -0.06 to -0.147 and level bounces 54-64%, but room is only 1.2x-2.8x the $52 round trip and all 420 map-book cells lose in HOLD; ES maker per order -0.35 ticks, RTY -0.94, NQ -1.73 (corrected figures, QA block). What survives is six small forward-only WATCH items (Part 2); none is established.
3. **My blocks (CHAR-B).** GC, CL, ZN, ZB maps and 2,142 map-generated book cells plus 2,268 learned-rule candidates: 0 clear (best family p books GC .59, CL .38, ZB .61, ZN 1.00; learned rules .26/.38/.22/.18; DS3_FIND.md CHAR-B section). Event windows (EIA, expiry week, NFP/CPI, auctions, London fix, 15:00 settle; 25 tests): none beats a random-day null (Bonferroni 1.00; DS3_FIND_CHARACTER.md event table). Relative-value spreads ES-RTY, ES-YM, RTY-YM, 6E-6J (1,554 cells): 0 clear, median cell loses $730-$1,508/wk in HOLD because both legs' costs exceed the spread's reversion; ZN-ZB spread room is 0.6-0.8x its $254 cost so no book is generated; GC-CL correlation 0.04-0.07 with a year-flipping sign (DS3_FIND.md RV section; prereg sha fa5c5c13..).
4. **NQ 13-year parameter map (DS3_NQ13.md).** No walk-forward parameter selector beats the fixed live parameters on 2023-26; no params_policy refit rule is proposed. The 1-minute object correlates 0.49-0.84 weekly with the 1-second engine (below the 0.90 rule), so pre-2023 results are descriptive only.
5. **MBO seven (DS3_MBO7.md).** The 3-year reconstructed file is on the box (4,314 trades to 2026-02-06). Uncorrelated with the stack (weekly -0.02), very drawdown-heavy alone ($229k at one NQ-equivalent per setup vs the stack's $88k over the same 149 weeks); at one third size it lifts the stack mean about 13% and Calmar .121 -> .137 with maxDD flat. Not a cleared diversifier: no window overlaps the last six months, no live fills after 2026-02-06 are on the box.
6. **Corrections that matter (so nobody trusts a number twice).** The 1-s tick-scale books were produced with a simulator that exited 60 seconds early; corrected (1S-FIX): no tick-scale cell clears, NQ NY-AM prior-day-level 30 s became a new WATCH (placebo p_book .16-.73, family .54-1.00). 6E/6J 1-min prints from 2013-2015 carry bad prints (~2% of bars); repaired copies are used and the "negative every year before 2023" reading of nine 6E cells was withdrawn (DATA_BAD_PRINTS.md; MORNING_FLAGS.md CHAR-C flag). The RTY 30-minute pre-market autocorrelation -0.101 is a 2023+ feature (-0.026 before). DST audit applied (DST_AUDIT_20261105.md).
7. **What is solid and what is not.** Solid: structure exists and is measurable per instrument and session; costs eat it at every scale tested; nothing replicates before 2023 where history exists; the live stack's 2026 gain leans on TH-L2 (post-cap +$18.1k/wk on the 10-s grid, about $9.9k/wk if evaluated every second, zero at +3.5 pt slippage; DS3_TH_CLOCK.md) and PE (53% of HOLD P&L, $104k of the $122k HOLD drawdown; DS3_CONCENTRATION.md), and those engine figures were restated several times after audits (USER_BRIEF "Process caveat"). Not solid: any WATCH item (best-of-F, 2026-regime), any 13-year 1-minute proxy (calibration below 0.90 for several objects), the margin proxies in Part 1 (labelled).
8. **What the box cannot tell you without your input:** the entry-window base (V0 $122.0k vs V2 $91.2k HOLD maxDD), live stop type and order structure, live TH-L2 evaluation clock and fills, NQ fees, account equity and broker margin, and whether to fund forward data (Saturday pull $1.14/week; weekly L2 $36-38/week). Everything else is waiting on those answers or on time (Part 2: most watches cannot reach a PASS before 2027-06 at their event rates).

---------------------------------------------------------------------------------------------------
## ADDENDUM (S4a, 2026-11-06, appended): ZS / LE overnight drift 'needs a measured spread' (no purchase)
DAILY-R6 (DS3_FIND_DAILY.md, DS3_INSTR2_FINAL.md): the constant-sign night legs of soybeans (ZS night long, z 4.3) and live cattle (LE night long, z 5.0) beat the 1,000-world random-side family maximum (family p < .001 in the 578-cell and in the 1,020-cell family); the direction of the overnight move (anchor close to day-session open) is not random. They are NOT books: at the PROXY cost of 1 tick per leg plus $4.84 the 13-year net is negative (ZS -$20k, LE -$68k) because the gross edge ($57 and $42 per day at the cells' lots) is about the size of the round-trip cost ($25-30 per lot); at a half-tick per leg ZS would be +$72k and LE +$17k over 13 years. Everything depends on the true spread at the anchor and at the open, which we do not own for ZS, LE, HE or 6C (1-s OHLCV and bars only; the cost proxies are unmeasured). Needed to decide: a measured spread table for those products (quotes at the anchor and at the day-session open); NO purchase is proposed in this pack, the item stays as an unresolved note; default: ignore until measured costs exist. Base for every number: percent-frame daily books, equal-$ vol lots, DAILY-R6 definitions.
