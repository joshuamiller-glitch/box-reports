T-SESSION-DISCOVER — find more of what the session re-score found, with session as the design axis from the start (2026-10-28)

Research only. No live, execution-server or chart change. UNTOUCHED never read. Redact account ids. Session rule in force (score by entry session; never kill for one-session; best-of-F a label; SESSION-CANDIDATE/PASS tiers). Fill bases as T-SESSION-2: stored / MEASURED (tier basis, at the cell's own lot level) / conservative (label). Runs after T-SESSION-2 A on the replay queue; CPU screens run now.

What the re-score found: the survivors are ICT-structure cells on sub-minute bars (IF_30s_eb in ASIA, IF_15s_eb in NY-AM), a CRT 15-min cell in LONDON, and the trend books carried by ASIA (PE/DN/KB) and NY-PM (KB). Those are the seeds. Every prior search chose cells on the pooled number; this program chooses per session from the first step, and tunes per session.

1. Neighbourhoods of the survivors, per session (first; CPU-only screens)

For each seed family (IF / iFVG, FVG, OB, BOS/MSS, sweep-and-reclaim, CRT, silver-bullet/killzone variants — the IC and SF families' full definitions on disk), re-screen the family's whole parameter grid INSIDE each session separately: bar sizes 5-s / 10-s / 15-s / 30-s / 1-min / 2-min / 500-tick (sub-minute is where the survivors live), the family's own parameters (gap size, displacement, lookback, confirmation), brackets 20/20 .. 60/60 and the structure pair the family uses, flat at session end vs run to bracket. Prereg per family x session (PRE selection, one HOLD look per family-session). Report per session the top 10 by MEASURED effect vs random-in-session (random minute in the same session, same bracket) with MDE and the 2023 span; the plain line per session: "ASIA likes X on 30-s bars; NY-AM likes Y on 15-s; LONDON likes CRT at 15-min; nothing survives in PRE/CLOSE".

2. Session-native re-search of the big entry families

T-ENTRY (191), T-TREND TR1 (133), T-CHOP (267), Footprint (169), PRO (264), T-PB (158), and the D4 engines (MAMA, Donchian, momentum vote, CRT H4): re-screen each family's grid per session with per-session parameters (the Asia-optimal Keltner multiple is not the NY one), same prereg discipline. The live books' engines included (KB/SM/PE/ST/HM/WT): does a session-tuned parameter set beat the live one in its carrier session (e.g. KB in ASIA with its own ATR period/multiple), paired on weeks.

3. Session structure as the signal (the sessions hand each other levels)

Cells built from the previous session's range, per session: ASIA range (18:00-02:00) high/low as sweep-and-reverse and as break-and-go at the LONDON open (02:00-05:00); LONDON range high/low the same at the NY open (08:30-11:00); the ICT "killzone" clocks (London 02:00-05:00, NY-AM 08:30-11:00, NY-PM 13:30-16:00, Asia 20:00-00:00) as windows; the first-hour-of-session range break and fade; previous session's VWAP and POC as levels; the "Judas swing" (first 30-min move of the session reversed); the session open price as a magnet (return to the session open after a 1x median-range excursion). Each with the family's reaction triggers (hold candle, sweep-and-reclaim, FVG) and the 20-60 bracket grid, per session, random-in-session placebo.

4. Cross-session conditioning

Gates known at the session open: the previous session's range vs median (quiet/wide), its direction, whether it swept the prior session's high/low, its close vs VWAP, the overnight gap; the ASIA-range-size gate from T-SESSION-2 C generalised to every session; day-of-week by session. Applied to the top 5 cells per session, PRE-selected, one HOLD look. Also "LONDON outcome -> NY-AM lots" style conditioning (size the NY-AM cells by the London result) as sizing cells.

5. Session-specific brackets and management

On the top 5 cells per session: the bracket grid 15/15 .. 60/60 and the structure pairs, flat-at-session-end vs run-to-bracket vs carry into the next session with a tightened stop (the handoff), per session. The 60/60-everywhere result came from the live trend books; sub-minute ICT cells may want 20/30. Per-session verdict.

6. Session regimes and trend books together

The ASIA carriers (PE/DN/KB) and the ASIA ICT survivors: does the trend regime (5-min Supertrend / 10-min) as a filter on the ICT cell, or the ICT structure as a trigger inside the trend book's regime, beat either alone in ASIA; same for NY-AM (MV + IF_15s). Combination cells <= 10 per session.

7. The six-session book (feeds D6)

Per session the best 1-3 cells at equal risk on the MEASURED basis with the lock engine; the six-session series: weekly mean, SD, maxDD, worst week, worst-20-weeks $, correlation to the live stack, stack-add at 10/20/30% risk, 2023 span; the handoff rule between sessions (flat vs carry); and the one-line D6 configuration: "ASIA = ..., LONDON = ..., PRE = ..., NYAM = ..., NYPM = ..., CLOSE = ...", each with PASS/CANDIDATE label, lots at $1,000 risk, and the slippage break-even.

8. Specs

For every session cell that makes the book: exact rule, bar type and size, parameters, session window ET, bracket in ticks, flat/handoff rule, lots, costs assumed, PASS/CANDIDATE, plain paragraph; codeable into DS6 without reading the study (sub-minute bars: state the NT8 bar type and the identity check needed; 5-s/10-s cells must say whether NT8 can build them from the Rithmic feed).

Reporting

DS3_SDISC_1_<family>.md per family (per-session tables), DS3_SDISC_2.md, _3.md, _4.md, _5.md, _6.md, DS3_SDISC_7_BOOK.md (the D6 line), MORNING.md every 2 h, DS3_SDISC_FINAL.md with one verdict line per session. Never-empty-handed: top 10 per session regardless of verdict with failed gate, MDE, and the three fill bases.
