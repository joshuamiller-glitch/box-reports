# Josh-fit-at-two-lots-only (research order, 2026-11-23 ~18:40Z)

Josh's words, verbatim (10:31 Mountain time = 17:31Z, 23 Nov), on the layer picks being different at 1, 2 and 4 lots per book:

> "no this is the bullshit i keep saying - this refitting is based on slippage - the box can't get that right - i want everythign fitted to the 2 lots"

Everything below is the relay's reading (relay = Claude, not typed by Josh).

1. (relay) From now on the layer fits (screen, joint, nulls, daily-loss, session-end, cross-session carry-over, and every "delivered pick") are made and reported on the 2-LOTS-PER-BOOK basis only. The 2-lot pick is THE pick of a session; the D8 file uses it at every account size (dollar rules scale per lot / per R, the settings do not change with size). Do not queue new 1-lot or 4-lot rows for these families; rows already landed stay as reference; rows already running may finish (nothing deleted). Say how many queued rows this removes and what it does to the ETAs.
2. (relay) The D8 file now carries: Asia = BF2_JT19, NY AM = BF2_JT68, London bare, NY PM bare (3 of 4 books). The Asia joint re-run with the daily-loss family and CGB (order 0640Z), the session-end test (0645Z), the carry-over rows (0750Z / 1725Z), the NY PM joint and the London pick: deliver each on the 2-lot basis, keys and defaults pages named for the 2-lot pick.
3. (relay) Where a pick's rule cannot be reproduced from a NinjaTrader feed (the STC state cut needs a 10-level cancel tape), keep it out of the joint's menu for the delivered pick, or deliver the best pick WITHOUT it beside the best pick with it, so the file can run exactly what was tested.
4. (relay) Not in this order: any spend, new machine or data purchase; no gate or pin change.

Research only. Nothing here touches the execution server, any live chart, credentials, spend authority or data deletion.
