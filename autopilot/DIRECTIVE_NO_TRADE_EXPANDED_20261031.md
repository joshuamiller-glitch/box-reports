# T-NO-TRADE-EXPANDED — user directive pasted 2026-10-31 (verbatim)

T-NO-TRADE-EXPANDED — every PLACE and STATE where a valid signal should not be taken: price, time, volatility, book, structure, after-events, crowding, day type; alone, combined, learned (2026-10-31)

Research only. Same rules as PLAN36 (measured + live-cal fills; per contract first; recent-first; session column; QUANT-LAYER; prereg per section; dead cells; RECENT_WINS rows). Base = the 70/30 split (and market). Every rule reports the SKIPPED signals' P&L beside the kept signals' gain and trades/week — a filter that throws away winners is scored as such. Actions for every rule: skip / size 50% / size 25% / delay (hold the signal for N minutes then take it if still valid) / re-target. Placebos: random skips at the same rate per book × session; shuffled-day states; time-shifted states. Runs after the follow-up orders; interim table within 6 h; feeds the Sunday brief only if a rule is ≥ 0 in L6M and HOLD on the stack with the placebo beaten.

A. The no-trade map (descriptive first): for every state below, P(target) and pts per contract of signals fired IN that state vs out of it, per book / session / window; ranked by how much the state lowers P(target); the plain line per state "KB signals fired within 10 min of an 8:30 release reach the target X% vs Y% otherwise (last 6 months, n)".

B. The states (each parameterised and swept)

PRICE / LOCATION (beyond the 11-line set)
no-man's land: the signal fires in the middle third of the prior-day range / the overnight range / the opening range / the session range / the 1-h and 4-h dealing ranges (equilibrium, no edge to lean on); between two set lines less than 15 pts apart (sandwiched).
extension / late: price more than k ATR (1 / 1.5 / 2 / 3) from the 20 / 50 / 200 EMA on 1 m / 5 m / 15 m at the signal; more than k σ from the session VWAP; at / within 5 pts of the day's high (for a long) or low (for a short) after a run of ≥ N pts since the open; the N-th consecutive signal in the same direction (chasing); the signal after the move has already travelled ≥ 70% of the day's median range.
the wrong side of the day: a long below the day's VWAP / below the open / below the prior close (and mirrored); against the 15-m / 1-h / 4-h structure (lower highs for a long); against the daily Supertrend / 200 EMA; in the premium third of the daily range for a long.
into the void: a long whose target crosses a volume-profile LVN / a liquidity void / an unfilled gap; a long whose stop sits in an HVN (will be defended against you) — the profile lines the live set lacks, used here as states.
round-number and level clusters: the target lies within 3 pts beyond a x00 / x50 with ≥ 2 other lines within 5 pts (a cluster), vs a single line.
TIME
scheduled releases: the signal within 5 / 10 / 15 / 30 min BEFORE a scheduled release (8:30 US data, 10:00, 14:00 FOMC, 13:00 auctions, 16:00 earnings nights) and within 2 / 5 / 10 min AFTER; FOMC day whole; CPI / NFP mornings.
session edges: the first 2 / 5 / 10 min after each session open (Asia 18:00, London 02:00, pre 08:30, RTH 09:30, PM 12:00) and the last 10 / 20 / 30 min before each session close and before the 16:55 flatten; the 09:00-10:00 block already live (score it as a state too); the lunch window 11:30-13:30; the 15:50-16:00 MOC window; the 17:00-18:00 break edges.
calendar: Friday after 12:00; day before / after holidays; month-end last 2 days; opex and quad witching; the first / last trading day of the month; the Monday Asia session after a gap weekend.
macro windows (ICT): xx:50-xx:10; silver bullets; the killzone END (the last 10 min of a killzone).
VOLATILITY / TAPE STATE
vol spike: the last 1-min range > k × (median 1-min range of the session) (k = 2 / 3 / 5) — the signal fired inside a spike bar; the last 5 min realised vol > 2 / 3 × its 20-day median for that minute of day; the bar that fired is > 2 ATR.
vol collapse: range of the last 15 / 30 min < 0.5 × median (dead tape); prints per second < 0.5 × median; the Bollinger squeeze ON (no energy).
spread / book: spread > 1 tick at the signal second; 10-level depth < 0.5 × its same-minute median (thin book); a wall ahead ≥ 5 / 10 × median within 10 pts; absorption against the signal in the last 30 s; a sweep against in the last 60 s; aggressor delta against ≥ 2 σ over 60 s; imb10 against the signal ≤ −0.3 for ≥ 5 min (the KB book-lean skip generalised to every book).
cross-market: ES moved the OPPOSITE way over the prior 15 / 30 / 60 s (the inverse of the ES-lead sizer); ES/RTY/NQ disagreement count ≥ 2; VIX futures up > k% on the day (if on disk).
AFTER-EVENT STATES
after a large bar: within N minutes after a 1-min bar ≥ 3 / 5 ATR (either direction); after a gap at a session open ≥ 20 pts; after a sweep of a session high/low (within 5 / 15 min); after a failed breakout (the OR edge broken and reclaimed within 15 min).
after the book's own losers: within 10 / 20 / 30 min after a loser (the N1 lead, per book and pooled, as a STATE here); after 2 / 3 losers in a row; after a stop in the same direction within 30 min (re-entry into the same failure).
after a big winner: within 10 / 20 min after the book's own target (the next signal is the chase); after the stack's day reaches +X R (the quit-when-up state, as a state).
CROWDING / STACK STATE
the stack already holds ≥ N same-side lots (6 / 8 / 10 / 12 live) — the signal adds to a crowded position; ≥ 2 books already on the same side; a book on the OTHER side (netting); the signal fires within 1 / 3 min of another book's identical signal (confluence, scored both ways: skip the duplicate vs size it).
DAY TYPE / REGIME
chop day ex-ante (first-hour range < 0.6 × median, ER < 0.3, Choppiness > 61.8) for the trend books; trend day for the fade books; the day's vol tercile the book loses in (from its own PRE+X' map); day after a > 2 % day; the second consecutive inside day.
ENGINE-SPECIFIC
KB: the Keltner break bar closed < 25 % beyond the band (weak break); the signal within N bars of the opposite flip (whipsaw); ST/SM: the Supertrend flip within 3 bars of the previous flip; HM: the HMA slope < k; PE/PB: the pullback deeper than 62 % / shallower than 23 %; MV: the vote at its minimum threshold; all: the signal bar's volume < 0.5 × median.

C. Combinations and the learned no-trade model
Pairs / triples of the top-30 states (PRE+X' ranked), any-of-k, the four-legged (location + time + volatility/book + after-event), nested with the 8-line set (a set line ahead AND a state); the learned model: walk-forward classifier of P(target) from ALL states at the signal second (plus signal quality and HTF), policy skip / 50 % / full by predicted P(target) buckets, 3-month weekly re-fit, shuffled-feature placebo, calibration curve, the extracted ≤ 6-rule tree with retained gain; per book and pooled; the stack line for every rule with locks; the equal-risk frame labelled structure.

D. The opposite side (so the map is complete)
The same states as TAKE-ONLY / size-up where the map shows a HIGHER P(target) in the state (e.g. after a large bar WITH the signal; thick book behind; ES already moving the same way) — reported in the same table so the user sees both edges of each state.

E. Report and publish
DS3_NO_TRADE_MAP_2.md (section A, ranked, recent-first, both edges), DS3_NO_TRADE_RULES_2.md (B + C per rule; kept vs skipped; trades/week; stack line), DS3_NO_TRADE_FINAL_2.md: one verdict per family and the plain sentences "not taking KB within 10 min before an 8:30 release keeps N % of trades and adds X pts per contract in the last 6 months (MDE Y)"; "the states that most reliably precede a failed signal in this market are …"; "the learned no-trade model keeps Z % of signals and adds W at equal risk (factor V)". Anything ≥ 0 per contract in L6M and HOLD, placebo-beaten, stack ≥ 0: an entry rule in THP_POLICY.txt (entry book regime state(name, param) -> skip | lotmult x | delay N) with each state's definition exact for D6 (release calendar as a daily file; the rest computable live), named in DS3_THL2_NEEDS.md; rows to RECENT_WINS.md; MORNING.md every 2 h.
