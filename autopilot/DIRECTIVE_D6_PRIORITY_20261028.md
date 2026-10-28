PRIORITY NOW — D6 goes live tonight: all cores on the session book (2026-10-28, ~19:30Z)  [verbatim]

Research only; no live, execution-server or chart change; UNTOUCHED never read; redact account ids. This supersedes every queue order given today. Every other program (T-ZEN remaining items, T-STACK E/F, CONFIRM leftovers, DIV follow-ups) is PAUSED — not killed; markers stay — until items 1-4 below are delivered. Use all 32 slots and the full replay allowance the memguard permits; replay governor PRIO_ALLOW the T-SESSION-2 A workers now (backup first). MORNING.md every 30 minutes until done, one line per item with ETA.

1. SPECS FIRST (CPU-only, deliver within 60 minutes, in this order; each one its own file the moment it is done, do not batch)

Codeable NT8 specs in the DS3_SPEC_TE6 format (bars, exact rule bar by bar, entry order type, stop/target in ticks, session window ET, flat rule, lots at $1,000 risk, costs, identity test vs the library rows, what could kill it):

IF_30s_eb (ASIA; also PRE) and IF_15s_eb (NY-AM): the inverse-FVG rule exactly — FVG measured on bodies or wicks, min gap 8 ticks, inversion rule (what makes a gap "inverted"), retest definition, limit at the midpoint, stop = gap/OB far edge + 5 ticks, target = "nearest liquidity >= 1R else 2R" with the liquidity definition, expiry of a pending limit, one-at-a-time rule, and whether NT8 15-s / 30-s bars reproduce the library bars.
CRT_M15_M1_close_ib and CRT_M15_M1_close (LONDON): the 15-min candle-range rule with the 1-min close-back-inside confirmation, the "_ib" variant defined, stop/target, range-candle validity, gap rule; and CRT_H1_30s_close.
ba2/KB_t60_s75 (ASIA), ba2/HM_t75_s90 (NY-AM), ba2/SM_t60_sst (ASIA): confirm these are the live KB / HM / SM engines with the bracket stated (target/stop in pts; "sst" = Supertrend-line stop, define exactly), nothing else changed.
PB7_PB5_depth_atr0.5_W15_s+0 (ASIA): the pullback cell's exact parameters in PbEngine terms (regime, level, depth 0.5 ATR of what period, W15 window, s+0, trigger, bracket).
E1A_RENKOC5_A3_r48, TB4B_tick_26_tick_250_ST3_SW62_T2, TB4W_03_time_15s_ST3_E20_1_T2 (ASIA): the generating rule if it is on disk; otherwise one line saying it is not reconstructible.

2. LIVE-LATENCY REPLAY of the D6 legs (replay, all allowed workers, deliver within 2 hours)

The T-SESSION-2 A replay, restricted to exactly the cells in item 1 in their sessions (plus the 27 pairs' legs if time allows), three fill bases (STORED / MEASURED at the cell's own lot level — the tier basis / CONSERVATIVE as a stress label), 0-s and 1-s delay. Report DS3_SESSION2_A_D6.md: per leg the MEASURED $/wk and pts/trade with CI and MDE, HOLD, 2023 span, break-even slippage, survives-stress yes/no, and the one-line sizing advice per leg (full / half / minimum / do not run).

3. THE D6 LINE (deliver within 2.5 hours, from 1 + 2)

Per session the best 1-3 legs at equal risk with the lock engine on the MEASURED basis; the six-session series (weekly mean, SD, maxDD, worst week, worst-20-weeks $, correlation to the live stack, stack-add at 10/20/30% risk, 2023 span); the handoff rule (flat at session end vs run to bracket); and the single configuration line: "ASIA = ..., LONDON = ..., PRE = ..., NYAM = ..., NYPM = ..., CLOSE = ..." with lots at a 30-NQ-lot book scale, PASS/CANDIDATE label and break-even slippage per leg. DS3_SESSION2_D_D6LINE.md.

4. Then resume

T-SESSION-2 B (entry-clock re-runs, T-OPEN first), C (2023 gate), T-SESSION-DISCOVER, then the paused programs in their previous order.
