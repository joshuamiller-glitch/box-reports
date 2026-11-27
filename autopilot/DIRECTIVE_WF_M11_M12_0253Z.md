# Walk-forward programme: add M11 and M12, Unusual Whales as the REGIME input (order from Josh, relayed)

Josh, 27 Nov 02:53Z, verbatim: "and what about unusual whales ? anything we can test there we still have that setup"

(relay) My design. Research only; UW key only via the env var as now; nothing bought, no plan change. Your own pages say: UW as entry triggers / books / flow alerts = weak to none (DS3_UWBOOKS, DS3_UW_FLOWALERTS), but UW FORECASTS THE SESSION RANGE out of sample beyond ATR + IV + weekday (DS3_UWREGIME: IV term structure, gamma flip, walls; e.g. QQQ iv_term +19 pp at the prior-close reading). That forecast was never joined to sizing or brackets. So use UW for what it is good at.

M11. SIZE BY UW RANGE FORECAST. Input = the DS3_UWREGIME expanding-window range forecast for the coming session (prior-close reading for Asia and London; 08:30 and 09:30 readings for NY AM; 10:00+ for NY PM), refit every 10 trading days as on that page, strictly out of sample. Primary: session size full when the forecast range is inside the tercile where the subject earned best per unit drawdown on past data, half otherwise. Reference rows: the same using the no-UW benchmark forecast (ATR + IV + weekday) so the UW-specific gain is visible; skip instead of half; forecast quintiles.
M12. BRACKET AND STOP DISTANCE BY UW RANGE FORECAST. As M9, but the multiplier is (forecast session range / the book's fit-period median session range), clipped 0.6-1.6, lots scaled inversely so dollars at risk stay equal. Reference: the no-UW benchmark forecast; trailing-range version = M9.
Also for both: day-type reading where the page found a YES (iv_term for trend-vs-chop): reference row "breakout-type books full size on forecast trend days, fade-type books full size on forecast chop days, half otherwise" (state which live books are which).

Subjects, steps (2 / 4 / 13 weeks), PASS rule, drawdown-first tables, scoreboard and luck accounting exactly as the programme. Span = the UW history only (2024-10 to date): say how many forward periods that gives at each step. State the assumed UW delivery lag and keep it conservative.
STATUS LINE ALSO WANTED: is the UW live recorder still running and is the plan still active (yes/no, last file date); do not log in, renew or buy anything.
Pages WF_M11.md, WF_M12.md. Post counts and start.
