# MGMT_DESIGN (W-DYNC, step E1 of order 1643Z): three whole trade-management designs, written BEFORE any result. 27 Nov 16:50Z. Research only.
Status: DESIGN ONLY. Nothing here has been scored. Each design is tested ONCE as written. No grid over thresholds. If a design is changed after any result it is logged below under CHANGES and counted. Base for every row: an EDGE-BEYOND-DRIFT book's bare entry (no layers, no Trade Health), a safety stop at entry (1.5 x the book's own stop: a property of the book, not a fixed point), no fixed target.

## 0. The vocabulary (everything self-adjusting)
- "typical move" of an instrument over horizon h (sigma_i(h)): the standard deviation of that instrument's own h-second changes over the previous 2 hours, sampled every 30 s, refreshed every 10 minutes, scaled by sqrt(h/60) for horizons that are not sampled directly. Every distance and every threshold below is a multiple of a typical move. NQ's typical 5-minute move is written s5; its typical 15-minute move s15. No point, tick or dollar number appears in any rule.
- "against" / "with": a market has moved AGAINST my trade when its change since my entry, in the direction of my trade, is below minus z of its own typical move over the time since entry (at least 60 s); WITH when above plus z.
- "the others": the session's other markets. Index futures (ES, RTY, YM) always; plus by session: Asia NKD and 6J (yen up = risk-off); NY ZN (bond rally = risk-off) and, when the feed exists, NYSE TICK. London / NY PM: ES and RTY only until the feeds exist. "N of M agree": N of the M valid others are against (or with). A market whose quote is stale (feed age beyond its own limit) is not counted; fewer than 2 valid others = the loss rules abstain and log "blind".
- "NQ has followed": NQ's own move against my trade, in its typical moves, is at least half of the others' average move against, in their typical moves. "NQ has not followed" is the opposite. "NQ is leading back": NQ's last-minute move with the trade is above one fifth of s5.
- "dip": my trade is under water by more than one half of s5 (a dip bigger than a typical half-5-minute wiggle). "winner": my trade is up by more than the arm level of the design, in s5.
- "range used": the session's NQ range so far is at or above the 80th percentile of the ranges at the same elapsed time over the last 20 sessions of the same session type (a rank, not a size).
- "level just ahead": a held liquidity pool (W-DYNL pool state: swings, equal highs/lows, prior-day/overnight levels, profile levels) closer ahead than 0.5 s5 and not yet traded through.
- "a part" is one half of the open lots rounded to a whole lot (at least one lot); a 1-lot position cannot take a part: it takes ALL where a part is called for (stated rounding).
All three designs use the same vocabulary; they differ only in how many others must agree, how strongly, and how much they do.

## 1. THE THREE DESIGNS IN PLAIN SENTENCES
Rule numbers are shared; a design lists the value of each knob. Every rule acts at most once per trade unless stated; decisions are evaluated every 15 s; orders: marketable for exits, a stop move for tightening, at most 6 order changes per minute.

### LOSS SIDE (only while on a dip)
L1  "Most of the others have turned against my trade and NQ has not followed yet -> leave (cautious), take a part and tighten the rest to the book's own stop (middle), take a third and tighten (active)."
    Fires when: dip AND the share of valid others against by more than a_z is at least a_share AND NQ has not followed AND NQ is not leading back.
    cautious: a_z 2.0, a_share all (>= 2 valid), action ALL.   middle: a_z 1.5, a_share all (>= 2 valid), action PART (half) then tighten the rest to the book's own stop (XI1 primary).   active: a_z 1.0, a_share at least half (>= 2 valid), action PART (a third of the lots, rounded, minimum 1) then tighten the rest to the book's own stop.
L2  "The others have NOT moved on this dip -> hold."  Fires (as a logged decision, no order) when: dip AND fewer than one third of valid others are against by more than 0.5 of their typical move AND NQ's own dip is within 1 s5. Meaning: the wide safety stop stays; no rule below may cut or tighten on this dip alone. Same in all three designs (not a knob).
L3  "I have been stuck and am still not a winner -> stop waiting." Fires when: time in trade is beyond the 90th percentile of this book's own previous winners' time-to-win (causal, last 300 winners) AND my best open profit never reached the arm level AND I am under water. Action: cautious ALL; middle tighten to the book's own stop; active ignore (active lets stuck trades run to the stop). [Reused from loop A2 L3 with the 0.15 R fixed number removed.]

### PROFIT SIDE (only once the trade is a winner)
P1  "I am up -> protect it behind price at a distance that fits the market's own noise."  Arm: best open profit above t_arm (in s5). Trail distance t_k (in s5) behind the best price, ratchet only, never below breakeven once armed.
    cautious: t_arm 1.0, t_k 1.5.   middle: t_arm 1.0, t_k 2.0.   active: t_arm 1.5, t_k 3.0.
P2  "The others confirm the trend (N of M with me) -> let it breathe."  Fires while the share of valid others WITH me by more than 0.5 of their typical move is at least 2/3 and the range is not used: trail distance multiplied by loosen (cautious 1.0 = no loosening; middle 1.5; active 2.0). Guard (all designs): the stop never gives back more than 50% of the peak open profit.
P3  "The others turn against my winner -> tighten, and take something off."  Fires when: winner AND at least half of the valid others are against by more than 1.0 of their typical move over the last 5 minutes. Action: trail distance becomes tight (cautious 0.5 s5, middle 1.0 s5, active 1.0 s5) and take a part: cautious half, middle a third, active none (tighten only).
P4  "The session's range is used up -> stop asking for more."  Fires when range used. cautious: leave ALL while in profit; middle: freeze P2 loosening and tighten the trail to 1.0 s5; active: freeze P2 loosening only.
P5  "A level just ahead -> take it there."  Fires when a level is just ahead and I am a winner. cautious ALL at the level; middle a part at the level; active none (it rides through unless P3/P4 fire).
P6  "Strong agreement after a part -> add the part back (once)." ACTIVE ONLY. After a part was taken, if at least 2/3 of the valid others are WITH me by more than 1.0 of their typical move since the part, NQ is making new highs in my direction, I am a winner and in profit by more than the part exit price: add the banked part back once at market; never above the original size; never under water.
T1  "Near the close, do not carry open profit into the bell." 15 minutes before the session end: cautious and middle leave ALL if in profit; active tightens to 1.0 s5.
S   Safety stop at entry (1.5 x the book's own stop): never widened; the only resting order apart from stops moved by P1-P3, L1, L3.

## 2. KNOB LIST (every number in the designs)
| knob | cautious | middle | active | what it means |
|---|---|---|---|---|
| a_z (others against beyond, own-vol units) | 2.0 | 1.5 | 1.0 | L1 |
| a_share (share of valid others) | all (>=2) | all (>=2) | half (>=2) | L1 |
| L1 action | ALL | PART half + tighten to own stop | PART third + tighten to own stop | L1 |
| dip depth | 0.5 s5 | 0.5 s5 | 0.5 s5 | common |
| NQ followed test | 0.5 of others | 0.5 | 0.5 | common |
| NQ leading back | 0.2 s5 per minute | same | same | common |
| L3 stuck quantile | 90th of own winners' times | same | off | L3 |
| t_arm | 1.0 s5 | 1.0 | 1.5 | P1 |
| t_k | 1.5 s5 | 2.0 | 3.0 | P1 |
| loosen factor (P2) | 1.0 | 1.5 | 2.0 | P2 |
| P2 agreement | 2/3 with, > 0.5 own move | same | same | P2 |
| give-back guard | 50% of peak | 50% | 50% | P2 |
| P3 against | half, > 1.0 own move, 5 min | same | same | P3 |
| P3 tight trail | 0.5 s5 | 1.0 s5 | 1.0 s5 | P3 |
| P3 part | half | third | none | P3 |
| range used rank | 0.8 | 0.8 | 0.8 | P4 |
| P4 action | ALL in profit | freeze loosen + trail 1.0 s5 | freeze loosen | P4 |
| level ahead distance | 0.5 s5 | 0.5 s5 | off | P5 |
| P5 action | ALL | part | none | P5 |
| P6 re-add | off | off | on (2/3 with > 1.0, once) | P6 |
| clock | ALL in profit | ALL in profit | tighten 1.0 s5 | T1 |
| decision step | 15 s | 15 s | 15 s | common |
| order change cap | 6 / min | 6 / min | 6 / min | common |
Count: 21 knob rows, but only 7 are design-defining (a_z, a_share, L1 action, t_arm, t_k, loosen, P3/P4/P5/P6 action sets); the rest are shared constants fixed by the vocabulary. No knob is searched.

## 3. WHICH ROWS (for W-DYNH; exact engine)
Rows per book, each design tested ONCE: A bare entry + book bracket (reference); D1 cautious; D2 middle; D3 active; E the fitted live book (reference). Manager classes: D2 = XI1 primary (class algo_xi.XI, params k 1.5, action 'half'+'own') with the vocabulary above; D1, D3 and the profit side need the new class code/th_dync/algo_mgmt.py (class MGMT, param design in {cautious, middle, active}), written next and announced by LEAD NOTE; the rows wait for it. NY AM and Asia books first, then London and NY PM (feeds permitting: see ALGO_BARE_X.md XI1 section). Re-entry policy L0 (free) as the engine runs; slot effects (extra entries freed by early exits) are shown explicitly in the report. Judged by the scorecard of order 1643Z section C (smoothness first), at the three income floors; PASS rules are Josh's.
Inputs needed that do not exist yet: NYSE TICK in the hook (hyphenated file names); range-rank table per session type (to be built from NQ 1-s: range to date by elapsed minute for the previous 20 sessions: a small table, built by W-DYNC on server C); typical-move tables (computed inside the class from the feed history, no file). The pool state needs W-DYNL's tables on the engine host (loud fail, not abstain).

## 4. SHADOW LOG FORMAT (one line per DECISION, tab-separated; every action AND every logged hold of L2; at most one line per 15 s per trade). Proposed to W-DYNA for the ALGO_SPEC keys-page standard.
ts_utc | book | trade_id (entry epoch s + side) | design (D1/D2/D3) | state (PROBE / CONFIRMED / RUNNING / DEFENDING / OUT) | open_s5 (open profit in s5 units) | best_s5 | dip_s5 | others: M list of "ES:-1.7,RTY:-2.1,YM:-0.4,NKD:na,6J:+0.3" (signed own-vol moves with the trade, na = stale) | N_against/M_valid | N_with/M_valid | nq_move_own (NQ's own signed move) | nq_followed (0/1) | nq_leading_back (0/1) | range_rank | level_ahead_s5 (distance or na) | rule (L1 L2 L3 P1..P6 T1 S) | action (hold, part, all, tighten, loosen, add) | qty | stop_px_after | reason (one plain sentence) | order_changes_last_min
Example: 2026-11-27T14:42:15Z NY_AM_MF4 1790862135+1 D2 DEFENDING -0.8 +0.1 0.8 ES:-1.7,RTY:-2.1,YM:-1.6 3/3 0/3 -0.5 0 0 0.42 na L1 part 2 20312.25 "others (3 of 3) are beyond 1.5 of their own typical move against; NQ has followed only 0.3 of that; taking a part and tightening to the book's own stop" 2
The same line format is what the engine hook writes in the replay (algo_log), so a live shadow line can be matched with a replay line for the same trade.

## 5. WHAT THIS PAGE DOES NOT DO
- It picks no threshold from data. The lead finder (W-DYNA) is background only.
- It does not report income. The scorecard (smoothness first, income as a floor at 10 / 20 / 30% below the fixed bracket) is applied to the rows when they exist.
- Design inputs known to be missing or blind today: London and NY PM feeds, TICK, UW from the US morning only (not used in these designs), range-rank table.

## 6. ADDED 17:10Z (order 1648Z): CALENDAR RULES AND THE TOOLS EACH RULE NEEDS
CALENDAR (in EVERY design; the calendar feed is built by W-DYNX8; class reads code/th_dync/calendar_events.json [{ts, impact, name}] and abstains when it is absent, logging 'blind'):
C1  "A scheduled high-impact event (CPI, jobs, FOMC decision, Fed chair speech) is minutes away and my trade is not a winner -> do not carry it through the number": cautious: leave ALL; middle: tighten to the book's own stop if on a dip; active: no action. Window: from 5 minutes before the event.
C2  "Inside the event window (5 minutes before to 5 minutes after) the other markets are moving on the number, not on my trade -> evidence rules (L1, P2, P3) are suspended; winners keep the stop they have; the book's own safety stop stays." Same in all three designs.
C3  "Holiday half-days and early closes: the session end for T1 is the actual early close." (calendar feed field 'close_ts'.) Opex, megacap earnings after the bell and auctions: logged as context in the shadow line (field event_tag), no rule yet; a rule needs evidence, none is invented here.
SESSION STRUCTURE (inputs; all self-adjusting): prior-day and overnight high/low, opening range, Globex VWAP, round numbers are LEVELS for P5 (level just ahead) through W-DYNL's pool state (kinds p1/p5/p20, pd, on, ib, hl); the session range used vs typical is P4 (rank table built: code/th_dync/range_table.json from NQ 1-s, Asia 412 and NY AM 954 session-days; rank needs 10 prior sessions).
TOOLS PER RULE (what each rule reads; refresh rate the rule needs; this is the rule-by-rule half of the 'tool -> use -> on box -> live' table; W-DYNX8 adds the live-availability column):
| rule | reads | refresh needed | on the box (history) |
|---|---|---|---|
| vocabulary: typical moves | the instrument's own prices, previous 2 h | recomputed every 10 min | all listed below |
| L1 / L2 / P2 / P3 / P6 "the others" | ES, RTY quote mids (1 s); YM, NKD, 6J, ZB 1-min bars; ZN 1-s trades; NY: TICK 1-min (tick_ma5), megacap basket (NVDA MSFT AAPL AMZN META GOOGL AVGO TSLA, 1-min, +120 s), Unusual Whales Market Tide net premium (1-min, +120 s) as further members of 'the others' (sign: with the index). Others worth having, not on the box today: CL and GC in Asia (1-s trades, sparse), 6E, 6A, HG, BTC, SI | 15 s decisions on 1-s feeds; 60 s on bar feeds; UW 60-120 s | ES/RTY from 2023-08 (quotes), YM/NKD/6J/ZB/6E 1-min from 2023-01, ZN/CL/GC 1-s, TICK 2023-04, megacaps and UW from 2024-10; 6A HG BTC SI NO |
| NQ followed / leading back | NQ quote mid 1 s | 15 s | yes |
| L3 stuck loser | this book's own history of winners' time-to-win (causal) | per trade | yes |
| P1 trail | NQ price, typical 5-min move | 15 s | yes |
| P4 range used | NQ session range to date vs last 20 sessions of the type | 60 s | yes (table) |
| P5 level just ahead | liquidity pools: swings, equal highs/lows, prior-day / overnight / IB / VWAP / profile levels; UW gamma walls and flip (EOD only before 13 Nov: 1 day stale; intraday on 9 recorder days) | levels: 1 min; UW walls: daily (history) / intraday (live recorder) | pools yes; UW intraday walls NO (9 days) |
| NQ tape and 10-level book | wall pulled / eaten, size behind, iceberg refills: NOT used by D1-D3 as written (attribution found no information; MBO not live-entitled). Available for the scorecard follow-up only | 1 s | tape and 10 levels yes; MBO to 13 Nov |
| C1 / C2 calendar | scheduled events with time and impact | static, loaded daily | NOT yet (W-DYNX8 building) |
| internals ADD / VOLD / VIX | would join 'the others' (TICK is the only one on the box) | 1-60 s | ADD VOLD VIX NO (Josh's second subscription may have them live: history needed for any test) |
The designs as written use the first column set the box has. Anything marked NO is not silently replaced: the rule runs with the members it has (at least 2 valid) and the shadow line says which members were blind.
UW options flow (tide, net premium ticks, gamma) enters as a member of 'the others' in NY sessions only (refresh 60 s, +120 s history lag, live stream 2.7 s): optional member, off in the first run of each design so that D1-D3 stay comparable across Asia and NY; it is not tuned.

## 7. STATUS OF THE CODE (17:30Z)
Class code/th_dync/algo_mgmt.py (class MGMT, params design = cautious / middle / active, book, session, others, extras, shadow_path) implements L1, L2 (log only), L3, P1-P6, T1, C1/C2 (when the calendar file exists). Sanity run only (25 safety-stop-only trades per book, 15-s steps; NOT a result, NOT used to change anything): first-fire shares per trade on Asia MF1 / NY AM MF5: cautious P1 68% / 44%, P3 60% / 36%, P4 12% / 16%, T1 24% / 32%, L1 0% / 0%; middle P1 76% / 56%, P3 72% / 52%, T1 28% / 40%, L1 0%; active P1 72% / 56%, L1 4% / 8%. Two things to look at before the rows run: (a) P3 fires on over half of the trades that reach the arm level (others turned against over 5 minutes by 1.0 of their own move is common): that is a property of the design as written; if it is changed after results it is logged under CHANGES; (b) Asia decisions are counted blind 3,582 of 15,201 (cautious) because the Asia range table has 412 session-days and the rank is missing for the rest, and fewer than two valid others on some bars; W-DYNH's health counter will say whether any set is data-starved (> 5%).
L1 never fired in the cautious / middle sanity run (a_z 2.0 / 1.5 with ALL others, a dip of 0.5 s5, NQ not followed, NQ not leading back, best < arm): the loss side is rare as written. Stated, not changed.

## CHANGES (counted; empty means every design is as first written)
(none)
