# T-CROSS (user, 2026-11-11 21:50Z) — other markets as clues for NQ, on BOTH sides and at entry
Standing rules 1/2/2a, T-JOINT method, one set per job, exact for finalists, live panel base + JN04. Queue behind the P7 FIX exact sets; do not starve them of RAM.
Sources: ES and RTY 1-s state base (MBP-10); MNQ and MES if owned; 1-min for YM, NKD, 6J, 6E, ZN, ZB, GC, CL, MBT. Quote in MORNING.md (do not buy above $100 without the user): L1/1-s for YM, NKD, 6J, ZN, VX; and 1-s trades for the top NQ weights (NVDA, MSFT, AAPL, AMZN, META, GOOGL, AVGO, TSLA) for RTH.
Features, per second or per minute, signed WITH the NQ trade:
 1. ES/RTY own state: pulled_mult, delta_mult, sweep, imbalance, wall ahead, absorption — same definitions as NQ, on their books.
 2. CONFIRMATION/DIVERGENCE: NQ at a new extreme and ES not (and the reverse); NQ adverse move with ES flat or with the trade; 2-of-3 and 3-of-3 index agreement; NQ-minus-beta x ES residual and its z-score (NQ-only move = likely to revert; shared move = real).
 3. LEAD/LAG: ES or RTY breaks its own 1/5/15-min swing before NQ; lead time distribution by session; who led the move that put the trade in profit/in loss.
 4. RELATIVE STRENGTH: NQ/ES and NQ/RTY ratio trend over 5/30/120 min.
 5. ASIA DRIVERS: NKD and 6J direction, range and trend over 15/60 min at the signal and during the trade; NKD cash open/lunch/close clock.
 6. RATES/DOLLAR/VOL: ZN and ZB 5-30 min move, 6E, VX level and change (if bought), as regime and as shock flags.
 7. MEGACAPS (RTH, if bought): weighted top-8 return vs NQ, count of the 8 at new session high/low, leaders rolling over before the index.
 8. MICRO vs MINI: MNQ delta vs NQ delta.
Uses — each a family, then JOINT with everything live:
 A. LOSS CUT: the NQ state cut ON only when ES (or 2-of-3) confirms the adverse move; OFF when NQ is alone. P7 first, then K7, U7. Replay every live cut on 11-02..05 and 11-09..11: would it have kept the 6 saves and skipped the 2 recoveries?
 B. EARLY CUT: cross-market break against the trade inside the first N s / first 25-50% of the stop as the early-exit trigger; versus the random-later-exit control.
 C. NEAR-ZONE: extends family r — ES/RTY stall or reversal while NQ is in the zone -> take/floor; ES still pushing -> hold.
 D. ENTRY: skip/half when the cross-market state disagrees at the signal; scored properly through the EsLeadSize hook.
 E. P7 ASIA RE-ENTRY: allow the with-trend re-entry inside 30 min only when NKD/6J/ES agree; block otherwise. Versus the blunt blackout, on trend weeks and chop weeks separately.
 F. REGIME DIAL: index agreement / NQ-residual / VX as the chop-vs-trend flag for T-WORKS B1; does any separate last week from the choppy weeks where the NQ-only flags did not?
 G. LEARNED: add all of the above to the near-zone and early-cut GBDTs; report whether cross-market features enter the top 5.
Deliver DS3_CROSS.md, first page 2026-11-12 03:00Z, every 4 h, FINAL 2026-11-12 21:00Z: per use, the best cell with four windows + WF, the behavioural scorecard a-e before/after, the live-cut replay table, the data quote, and the v1.8 feature names needed in the policy grammar (es_delta_mult, es_confirm, idx_agree, nq_resid_z, nkd_trend ...). Say plainly if a family is null.

## ADDENDUM (user, 2026-11-11 21:55Z) — MEGACAPS as a full family, not a quote line
Buy 1-s trades + L1 for NVDA, MSFT, AAPL, AMZN, META, GOOGL, AVGO, TSLA, L6M first (PRE-APPROVED if under $100; otherwise quote and start with the 4 largest weights). QQQ and SMH 1-s as cheap proxies in the same buy.
Features, RTH and pre-market from 04:00 ET, signed with the NQ trade: weighted top-8 return vs NQ (residual + z-score); count of the 8 at a new session/30-min high or low; concentration (share of the NQ move explained by the single largest contributor); leaders rolling over (top-2 weights break their 5-min swing while NQ holds); dispersion across the 8; QQQ and SMH vs NQ basis and lead/lag; per-stock aggressor delta if the trades carry a side.
Score in uses A-G exactly as the index features (loss cut confirm, early cut, near-zone take/hold, entry skip/half, regime flag, learned exits), NY-AM and NY-PM books only. Report lead/lag honestly: do the stocks lead NQ at all at 1-s, or only confirm? State what live feed the features would need.
(Lead: the buy is authorised ONLY as one combined purchase with total quoted cost <= $100 (stocks + QQQ + SMH, L6M); if the combined quote is over $100 buy the 4 largest weights + QQQ if that is <= $100, else quote only and tell the lead. Record the spend in SPEND.json append-only with the quote id; key only via env, never printed.)

## SPEND AUTHORITY (user, 2026-11-11 21:50Z) — supersedes the $100 line in T-CROSS and its megacap addendum
The box may spend up to $1,000 TOTAL on data for T-CROSS without asking: megacap 1-s trades + L1 (8 stocks, QQQ, SMH), and L1/1-s for YM, NKD, 6J, ZN, VX. This raises the research data budget by whatever is needed to cover it (about $672 was left; the cap is now that plus the shortfall, for T-CROSS only).
Rules: buy and start work at once — do NOT wait for a reply; log every purchase in MORNING.md (dataset, symbols, date range, cost, running total) before the download starts. Order of purchase: megacaps L6M first, then NKD + 6J (the Asia drivers), then the rest. If a single quote would take the total past $1,000, buy the largest subset that fits (fewer symbols or a shorter window, L6M before older history) and keep working; list what was left out and its price. Nothing above $1,000 without the user. The Databento key stays in the env var only.
A missing dataset never stops T-CROSS: the ES/RTY families run now on owned data.
