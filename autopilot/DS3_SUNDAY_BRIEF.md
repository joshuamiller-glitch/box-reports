# DS3_SUNDAY_BRIEF — DRAFT v1 (lead, 2026-10-31 ~01:00Z; rewritten every 4 h from Sat 18:00Z; deadline Sun 2026-11-01 12:00 ET = 17:00Z)

Status: C2 (sub-minute confirmation 2) and CF-SUBMIN not yet reported; CF-COMBO book chain still running. Nothing below is a PASS. Numbers are research lots (live ≈ ÷2.35, unconfirmed), lock-engine stack, $k/wk vs the stack as it is, windows L3M / L6M / HOLD / PRE / X'. Everything selected after seeing L6M/HOLD/L3M is marked post-hoc.

## 1. ON for Sunday 18:00 ET (user decides; each is CANDIDATE-RECENT at best)
| Rule | D6 vocabulary | Evidence | Caveat |
|---|---|---|---|
| 70/30 risk-capped split, dip 3 pt (S73) | `entry * * dip_X=3 basis=i confirmations_N=1 gates=default8 veto_imb5=-0.40 chase_Y=off split_F=0.7 limit_join_s=0 eval=1s` (already line in THP_POLICY v2; market-entry lines for PE/DN/MA/CR above it) | stack +20.2 / +17.6 / +18.4 / +3.8 / +2.2 (≈ +7.5k/wk live L6M); beats random-dip placebo; positive all windows on M, N, LIVE-CAL | structure (bracket geometry); fails placebo/PRE CI/RC; breaks even at +1 pt (PRE) / +2.3 pt (L6M) extra cost per remainder fill — the live add-fill slippage decides it |
Alternative base if the live add costs > ~0.5 pt/lot: 90/10-at-8 (`split_F=0.9 dip_X=8 confirmations_N=0`): equal at measured cost, keeps +14.9k/+10.6k L6M at +1/+2 pt per fill vs +8.6k/+3.9k for 70/30.

## 2. SHADOW (paper) — numbers to beat, 13+ forward weeks
| Rule | D6 mapping | L3M/L6M/HOLD/PRE/X' stack | Why shadow |
|---|---|---|---|
| First book stopped → cut the rest 50% when the stopped book was entered in Asia (on S73) | `stack stopped_book_session=ASIA -> cut_rest 50` | +11.9 / +13.2 / +11.4 / +2.0 / +2.8 (MKT +17.5/+20.2/+16.5/+0.9/+3.7) | 1 of 202 cell-scopes; post-hoc; 92% of gain since 2025-10-01; 76% of the pooled gain is lock-engine re-entry (not live-reproducible) |
| ER(20) 5-min sizer (×1.5 at ≥0.3, ×0.5 below; ST HM WT KB SM PE) | `entry book regime trend(ER20,5m) >= 0.3 -> lotmult 1.5; below -> lotmult 0.5` | +13.3 L6M, +14.6 HOLD, −10.9 PRE, +7.5 X' (inside MDE 41k) | trade-level fact (+1.40/planned lot, rank 1/301) but stack negative in PRE; depends on whether D6 governors use planned-lot R or sized-lot R (≈ +7k/wk vs ≈ 0) |
| ES-led-NQ sizer (×1.5 if ES led by ≥1.5 bp/30 s, ×0.5 if NQ led) | needs ES 30-s return in D6 | ≥ 0 all 6 windows, +3.8 L6M (≈ +$1.6k/wk live) | inside MDE 22k; post-hoc |
| Stop-join: Native stop-market instead of 3 s JoinThenMarket (ST, HM) | order type (execution), not a research rule | join fills 8/21 (0.38) vs replay 0.78; join 2.45 vs Native 1.28 pts/stop; ≈ +$4.4k/wk at 10 lots (CI −1.0k..+9.9k), p 0.055 | run a two-week ST-vs-HM split; DS5/DS6 joins rejected 6/13 — check platform |
| 5-min ER(20) ≥ 0.3 as a skip (TG-1) | `entry book regime trend(ER20,5m) >= 0.3 -> take` | +3.30/contract L6M; stack +17.3k L6M, −7.5k PRE | volume loss; use the sizer instead |
| Skip same-direction re-entry within 30 min after a loser (N1) | stack/entry rule | +11.3 L6M, +14.9 L3M; −5.4 PRE | same shape as the cut rule; post-hoc |
| KB skip when book leaned our way ≥3 min (N1) | imb10 run-length | KB stack −0.7 L6M, −3.0 PRE | per-book, best-of-12 |
| HM skip when an unmitigated opposing 15m/1h/4h FVG lies between entry and target within 60 pts | needs daily HTF FVG file | +0.89/signal L6M below MDE; stack +11.5k L6M, 60% in 3 weeks | HM only; post-hoc |
| PE: 45-s three-bar (two down 45-s candles then an up candle closing above the previous high; short mirrored), limit at the confirming candle's body mid, pure wait (no 70/30, no confirmation = no trade) | `entry P6 * ...` order spec in DS3_THL2_NEEDS.md (CF2 section); needs 45-s candles in D6 | per planned lot vs the plain 70/30 dip floor: +2.42 L6M (MDE 3.2), +2.14 HOLD, +3.08 L3M, +0.97 PRE, +0.75 X'; fires on ~30 of 43 signals/wk; placebo rank 1/201 (L6M, HOLD); holds at 3-s delay (+2.56) and +1 tick (+2.23); stack +1.5k L6M, +0.65k HOLD, −1.4k PRE, +2.4k X' (≈ +10k/wk per-signal figure overstates it) | LEAD, shadow only; gain in NY-AM/NY-PM, Asia and pre-market negative; "positive in all windows" is post-hoc; WF chain lands on this cell for PE (+0.36 OOS, p 0.09 vs random-cell chain); cumulative p 1.0 |
| DN: HA 30-s second-up-candle add (market) instead of the 3-pt dip | (C2 §DN) | +1.13 L6M (MDE 1.4), +1.14 HOLD, +0.42 PRE | DN anchored chain earned −1.32 OOS: unstable |
| HM: 15-s four-up-closes after a dip | | +1.06 L6M, +1.37 HOLD; stack +12k/+10k; PRE −0.15 | gone at 3-s delay (+0.07): OFF |

## 3. OFF (tested; do not run)
All exits keyed on price, path, time, signal state, forecast or mirrored confirmations (SD-A/B/C, RC-1; losses saved ≈ wins forfeited, stack −11k..−65k/wk); brackets (30–90, liquidity targets); trade-health/L2 profit rules (gain = target-fill artefact, flips negative on N/LIVE-CAL); bar types as the base for the live engines (BAR-ENG, BARS-CAND 1+2, B2; after PAIRFIX the paired "wins" are within noise; TB4W 10-min Asia and TE6 5-min NY-AM NOT confirmed); POI/zones as location or no-trade (NTZ-1, FZ-1, Z2: the 11-line set fails forward, WF chain −0.26/signal); entry timing at the first 15-s close; session-open drift; first-hour selector; per-session or per-ER add size; limit-at-arming; split on a confirmation base; first-target mirror; all-session same-side caps; stack partials on profit; HTF arrays as location.

## 4. Stack line for the ON set vs the stack as it is
S73 alone: L3M +20.2k / L6M +17.6k / HOLD +18.4k / PRE +3.8k / X' +2.2k per week (research lots; N basis; the RC vs the market stack is p 0.002 but that is the known split gain; vs S73 alone every add-on is p ≥ 0.7). Weekly mean/SD/maxDD/worst-20 per line: DS3_SPLIT_2.md §6c and DS3_STACK_2.md. Equal-risk (structure): S73 at 1.06× lots +22.6k L6M.

## 5. Open questions (answers change numbers)
1. Live remainder (add) fill slippage per lot — decides 70/30@3 vs 90/10@8.
2. Live lots per book (SP2/S2/T2 assume research ÷ 2.35; your 11:40 example stack P6 5, K6 3, M6 3, H6 1).
3. D6 governors (day entry test +5R/−2R, day arm 2R keep 50%, week floor 12R): planned-lot R or sized-lot R? Decides whether any sizer is worth ≈ +7k/wk or ≈ 0.
4. Can the live L2/TH cut trigger times be replayed ("L2/TH counts as a stop" is untestable otherwise)?
5. HALT-RESUME, RISK-OFF, QUIT-WHEN-UP directives never reached the lead — please re-paste.
6. HM forward register starts 2026-11-01 18:00 ET: November 1-s feed (free quote first; any buy needs your OK); MBO pull decision; mask-audit decisions (MORNING.md).
7. Zones: run the 11-line set as a shadow arm (needs a rolling file for D6) or close the line? Options positioning/VIX files for the trend gate.

Sources: DS3_SPLIT_2, DS3_STACK_2, DS3_TREND_2, DS3_ZONES_2, DS3_BARS_2, DS3_PAIRFIX, DS3_NEW_IDEAS, LIVE_STOP_JOIN, DS3_TREND_FINAL, DS3_STACK_PARTIALS, DS3_CONFIRM_COMBOS (CF-COMBO still running).
