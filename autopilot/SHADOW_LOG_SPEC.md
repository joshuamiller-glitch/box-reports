# SHADOW_LOG_SPEC - one line per management decision, for the relay's shadow logger (W-DYNA for W-DYNC / MGMT_DESIGN.md; order 1643Z section D)

Version 0.1 2026-11-27. SPEC = what the logger must write; the same line format is written by the box replay (exact engine / quick screen) so a shadow day can be compared line by line with a replay of the same day. One design = one file per day: `shadow_<design>_<YYYYMMDD>.csv` (UTC trading day starting 22:00Z), UTF-8, header line, comma separated, fields containing commas or quotes in double quotes, floats with up to 6 decimals, NaN / missing = empty field, no spaces after commas, timestamps in UTC nanoseconds plus the ET string for reading.

## 1. WHEN A LINE IS WRITTEN
```
ENTRY      the entry fill (state PROBE), action ENTRY
TICK       every decision evaluation of an open trade: every 15 s for designs that decide per 15 s, every 60 s for per-minute designs (the evaluation cadence of the design, whichever it is; never less often than once per minute while a trade is open) - action HOLD when nothing is done
ACTION     every action request (TIGHTEN, PART, ALL, TRAIL, RELEASE, READD, HOLD_STOP): the request line, and one more line when the order is acknowledged / filled (action = FILL, same trade_id, order_id, fill_px, fill_lots, fill_ts)
STATE      every state transition (state_from != state_to) even when the action is HOLD
EXIT       the trade ends for any reason (stop, target, bell, hard flat, own action, day halt): action EXIT, exit_name, exit_px, final_pts, final_R
GAP        a feed went missing or came back (action FEED, reason = which feed and for how long)
HEARTBEAT  every hour with no open trade (action NONE) so a silent logger is detectable
```
Volume: about 240 TICK lines per trade-hour at 15 s; a 9-book session day is well under 50k lines.

## 2. FIELDS (in this order)
| # | field | type | meaning |
|---|---|---|---|
| 1 | ts_ns | int64 | decision time, UTC nanoseconds (the time the decision was taken, not the data time) |
| 2 | ts_et | str | `YYYY-MM-DD HH:MM:SS` Eastern |
| 3 | seq | int | line counter within the file (gap = lost line) |
| 4 | design | str | design name and version hash, e.g. `MGMT-A@3f9a21` |
| 5 | stem | str | live stem name from BOOK_STEMS.md, e.g. `NY-FIB` |
| 6 | session | str | AS / NY / LO / NP |
| 7 | mf | str | MF number inside the session, e.g. `MF1` |
| 8 | trade_id | str | `<stem>|<entry fill ts_ns>` |
| 9 | side | int | +1 long, -1 short |
| 10 | lots_open | int | lots open after this line's action |
| 11 | lots_orig | int | lots at entry |
| 12 | px | float | last trade price used by the decision |
| 13 | bid | float | best bid at decision (empty if unknown) |
| 14 | ask | float | best ask |
| 15 | entry_px | float | average entry fill |
| 16 | open_pts | float | side x (px - entry_px), points per lot |
| 17 | open_R | float | open_pts / S0 (R = the book's own stop distance in points; S0 in the book table) |
| 18 | peak_R | float | best open_R since entry |
| 19 | mae_R | float | worst open_R since entry (<= 0) |
| 20 | t_in_s | int | seconds since the entry fill |
| 21 | state_from | str | PROBE / CONFIRMED / RUNNING / DEFENDING / OUT |
| 22 | state_to | str | state after this line |
| 23 | markets | str | which markets agree: `ES:+1;RTY:0;YM:+1;ZN:-1;CL:NA;TICK:0;UW:0` per market: +1 with the trade, 0 neutral, -1 against, NA missing; the rule for +1/-1 (z threshold and window) is stated once in the design page |
| 24 | n_for | int | number of markets / evidence items with +1 |
| 25 | n_against | int | number with -1 |
| 26 | score | float | the design's score (n_for - n_against for count designs; empty if none) |
| 27 | inputs | str | JSON of the numeric inputs the design used, key order fixed by the design (e.g. `{"i1":0.12,"i2":-0.4,"es_z5":-1.1,"wall_a_sz":85}`), no spaces |
| 28 | input_age_ms | int | age of the OLDEST input used (data time to decision time) |
| 29 | stop_px | float | resting stop price after the line (empty = none) |
| 30 | target_px | float | resting target (empty = none) |
| 31 | action | str | ENTRY / HOLD / TIGHTEN / PART / ALL / TRAIL / RELEASE / READD / HOLD_STOP / FILL / EXIT / FEED / NONE |
| 32 | action_px | float | price asked (stop level, limit or the marketable price) |
| 33 | action_lots | int | lots affected |
| 34 | rule | str | rule id, e.g. `A.R3`, `B.score<=-3`, `SAFETY`, `CLOCK.flat1655`, `BELL` |
| 35 | reason | str | one plain sentence a trader can read (`ES and RTY broke against, 2 of 4 markets against, open +0.8 R: take half`) |
| 36 | order_id | str | order id of the request / fill (empty on HOLD) |
| 37 | fill_px | float | fill price (FILL / EXIT lines) |
| 38 | fill_lots | int | filled lots |
| 39 | fill_ts_ns | int64 | fill time UTC ns |
| 40 | exit_name | str | EXIT lines: Stop / Target / Bell / HardFlat / Algo... |
| 41 | final_pts | float | EXIT lines: points per lot of the whole trade |
| 42 | note | str | free text (feed missing, data gap, manual override) |
```
engine_version  is written once in the file header comment line:  # shadow_log v0.1 engine=<hash> design=<hash> books=<stems> S0=<stem:pts,...>
```
## 3. EXAMPLE LINES
```
ts_ns,ts_et,seq,design,stem,session,mf,trade_id,side,lots_open,lots_orig,px,bid,ask,entry_px,open_pts,open_R,peak_R,mae_R,t_in_s,state_from,state_to,markets,n_for,n_against,score,inputs,input_age_ms,stop_px,target_px,action,action_px,action_lots,rule,reason,order_id,fill_px,fill_lots,fill_ts_ns,exit_name,final_pts,note
1790172127000000000,2026-09-23 10:02:07,1,MGMT-A@3f9a21,NY-OFI,NY,MF5,NY-OFI|1790172127000000000,-1,2,2,30844.0,30843.75,30844.0,30844.0,0,0,0,0,0,PROBE,PROBE,ES:0;RTY:0;ZN:0;CL:0;TICK:0;UW:0,0,0,0,"{}",40,30904.0,,ENTRY,30844.0,2,ENTRY,entry fill: safety stop 60 pts,O1,30844.0,2,1790172127310000000,,,
1790172187000000000,2026-09-23 10:03:07,2,MGMT-A@3f9a21,NY-OFI,NY,MF5,NY-OFI|1790172127000000000,-1,2,2,30838.5,30838.25,30838.5,30844.0,5.5,0.09,0.09,-0.02,60,PROBE,PROBE,ES:+1;RTY:+1;ZN:0;CL:0;TICK:0;UW:0,2,0,2,"{""i1"":0.14,""i3"":0.2}",120,30904.0,,HOLD,,,A.hold,in profit 0.09 R and two markets agree: hold,,,,,,,
1790172475000000000,2026-09-23 10:07:55,24,MGMT-A@3f9a21,NY-OFI,NY,MF5,NY-OFI|1790172127000000000,-1,2,2,30808.0,30807.75,30808.0,30844.0,36.0,0.60,0.62,-0.02,348,RUNNING,DEFENDING,ES:-1;RTY:-1;ZN:0;CL:0;TICK:-1;UW:0,0,3,-3,"{""i1"":-0.2,""es_z5"":-1.8}",90,30838.0,,TIGHTEN,30838.0,2,B.score<=-3,3 of 6 markets against after +0.6 R: stop to +0.1 R,O7,,,,,,
1790172478725462858,2026-09-23 10:07:58,25,MGMT-A@3f9a21,NY-OFI,NY,MF5,NY-OFI|1790172127000000000,-1,0,2,30838.0,,,30844.0,6.0,0.10,0.62,-0.02,351,DEFENDING,OUT,ES:-1;RTY:-1;ZN:0;CL:0;TICK:-1;UW:0,0,3,-3,"{}",70,,,EXIT,30838.0,2,STOP_TIGHT,stop hit at 30838.0,O7,30838.0,2,1790172478725462858,Stop,6.0,
```
(The example numbers are illustrative of the format only.)
## 4. RULES FOR THE LOGGER
```
- one line per decision at the stated cadence, even when HOLD; a decision that is skipped (feed missing) is written as HOLD with note 'skipped: <feed>'
- a line is written BEFORE the order leaves (action line) and AGAIN at the fill (FILL line): the pair shows the decision-to-fill latency
- the markets field uses ONLY the markets the design uses; the rule that turns a market's move into +1/0/-1 is in the design page (z threshold and window), the logger writes the result, not the raw value (raw values go to inputs)
- timestamps: decision ts_ns from the engine clock synchronised to the exchange; input_age_ms = decision time - data time of the oldest input; a design that cannot state this does not log
- replay equivalence: the box replay writes the same columns with fill_* from the engine's fill model, so `diff` of a shadow day against its replay shows where live differs (latency, fills, missing feeds)
- file closed at the end of the UTC trading day; sha256 of the file posted next to it
```

## 5. AMENDMENTS (finalised with W-DYNC's MGMT_DESIGN section 4 proposal and the playbook; 2026-11-27)
```
add field 43 health   : the book's health vote (ninth screen): A / W / N / - (A = deeper (MAE) or longer under water than 90 percent of this book's past winners, or less early progress than 75 percent of winners by this minute; W = better than the median winner; - = fewer than 40 past winners): written on every TICK line, with health_mae_R, health_uw_min, health_mfe_R in the inputs JSON
add field 44 votes    : the playbook's 8 screen votes as an 8-character string, one character per screen in the order 1 NQ chart, 2 NQ tape/book, 3 ES/RTY/YM, 4 other markets, 5 TICK, 6 VIX, 7 megacaps/ETFs, 8 UW tide; A against, W with, N nothing, - abstains (the same string W-DYNH writes in algo_log as 'sec:vote:VVVVVVVV:openR'); on every TICK line (the engine writes it on change only: the logger repeats the last string)
fold in W-DYNC's design columns inside `inputs` (JSON keys): open_s5, best_s5, dip_s5, others {"ES":-1.7,"RTY":-2.1,...} (signed own-vol moves with the trade, null = stale), n_against, m_valid, n_with, nq_move_own, nq_followed (0/1), nq_leading_back (0/1), range_rank, level_ahead_s5, order_changes_last_min
tab-separated option: W-DYNC's proposal uses tabs; the relay may write TAB or comma separated files as long as the header line names the fields in this order
the engine replay writes the same fields from algo_log: algo_log item 'sec:kind:rule:openR' -> action/rule/open_R (open R in safety-stop units x1.5 -> open_R in R of the book stop)
```
