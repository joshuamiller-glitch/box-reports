# D8 NEWS WINDOWS (family NW): entry blocks around releases and open-trade rules

Research only, 2 lots per book, written 2026-11-23 20:56 UTC by code/th_nw/nw_score.py (hook nw_hooks.py, builder nw_gen.py, queue nw_next.py, scorer nw_score.py, calendar nw_cal.py). Order: DIRECTIVE_NEWS_WINDOWS_20261123_1825Z.md (Josh: "if in open trade it could get taken for a huge ride").

**Calendar**: /mnt/l2/l2vast/_calendar/events.csv has events from **2024-10-01** (first row ISM manufacturing 10:00 ET) to 2026-12-23. Months 2023-04 to 2024-09 have NO events: they are NOT SCORED for NW (an NW set equals its pick there by construction; shown as "no calendar", never as evidence). So prior years here = 2024-10..2025-12 and 2026-01..04 (18 months, 2025-11 has no data) and L6M = 2026-05..10, L3M = 2026-08..10; data end 2026-10. 54 calendar rows are rule-derived (ISM dates), 1 UNVERIFIED, the rest verified. The calendar has no FOMC press-conference row: FOMC press = every FOMC decision date at 14:30 ET (synthetic). NOT in the calendar, so not tested: JOLTS, consumer confidence, new home sales and other 10:00 releases, Treasury auctions (in the file as AUC_* but not in the order).

**Rules as applied (hook nw_hooks.py)**: ENTRY BLOCK (A before, B after the release): a new-entry signal of a governed book is skipped when its order time is in [release-A min, release+B min); an unfilled resting limit entry at release-A is cancelled. OPEN-TRADE RULE at release-A for every trade open then: CLOSE = closed at market (exit name NWClose, market walk at 2 lots, measured basis, like every exit); BE = if the open profit marked at the liquidation side is > 0 the stop moves to break-even (entry price, never loosened), target stays, trade runs on, else closed at market. LEAVE ALONE = the pick row (reference). Rows "open rule" = rule only (re-entry after the close is allowed); rows "combo" = open rule at release-A plus the entry block [-A, +B). Groups: NY AM R10 = ISM mfg + ISM services + 10:00 PCE + chair speeches 09:00-12:00; NY PM G1 = FOMC decision 14:00, G2 = FOMC press 14:30, G3 = FOMC minutes 14:00 + chair speeches 12:00-16:00; London R830 = CPI PPI NFP GDP retail sales PCE + chair 08:30 (the London book is flat at 08:30:01, B is moot; A=5 / A=2 close rows are the 08:25 / 08:28 flatten tests, entry A=30 is the 08:00 block); Asia CH_EVE = the 3 chair speeches at 19:30-23:30 ET (the Asia book is flat at 02:00, so 08:30 / 10:00 / 14:00 releases never overlap it). NY AM versus the 08:30 releases: the longest block (B=60) ends at 09:30, so not tested. Sets are ALL books of the stack in one run (per-book numbers are the per-book trades of that run, exact per-book sets only for winners later); per release type numbers are the trades of that type's release days inside the group run (days differ by type, so exact up to week-state coupling; same-day releases are listed under each type).

Windows and definitions: daily series house convention (exit ET date +7h, p484 = gross - 4.84 x lots), zero-filled on the pick's trading days; ulcer = RMS drawdown (primary); "release day" = trading date of the release; worst single trade = lowest p484 of one trade whose exit trading date is a release day; worst day = lowest daily sum over release days of the group. Verdict: pick on L6M ulcer with L3M not worse, walk-forward >= 0.58, prior years not RED (>30% worse at equal-risk $/wk), best-of-many null 4 of 5 (placebo release dates, emulation). Selection rule: refit with the next joint.

Rows landed: 30 of 171 sets complete (all scored months). Verdict and null use complete sets only.

## Asia (AS_STKd8106b26ef_JT19, pick TL3_SR_AS_STKd8106b26ef_BF2_JT19)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| CH_EVE | 1 | -1270 | 4092 | 4092 | -1410 | -5692 |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| CH_EVE_EBa2b5 | +0.0 | +0.0 | 9849 | -8694 | -3660 | -7635 | -1270 / -1270 | 4092 / 4092 | 0 | 0 | +0 / +0 / +0 | 1.00 | PASS |
| CH_EVE_EBa2b15 | +0.0 | +0.0 | 9808 | -8694 | -3660 | -7635 | -1270 / -1270 | 2961 / 4092 | 1 | 0 | +0 / -0 / +0 | 0.96 | PASS |
| CH_EVE_EBa2b30 | +0.0 | +0.0 | 9768 | -8694 | -3660 | -7635 | -1270 / -1270 | 1891 / 4092 | 2 | 0 | +0 / -0 / +0 | 0.96 | PASS |
| CH_EVE_EBa2b60 | +0.0 | +0.0 | 9815 | -8694 | -3660 | -7635 | -841 / -1270 | 3161 / 4092 | 3 | 0 | +0 / +0 / +0 | 0.96 | PASS |
| CH_EVE_EBa5b5 | +0.0 | +0.0 | 9849 | -8694 | -3660 | -7635 | -1270 / -1270 | 4092 / 4092 | 0 | 0 | +0 / +0 / +0 | 1.00 | PASS |
| CH_EVE_EBa5b15 | +0.0 | +0.0 | 9808 | -8694 | -3660 | -7635 | -1270 / -1270 | 2961 / 4092 | 1 | 0 | +0 / -0 / +0 | 0.96 | PASS |
| CH_EVE_EBa5b30 | +0.0 | +0.0 | 9768 | -8694 | -3660 | -7635 | -1270 / -1270 | 1891 / 4092 | 2 | 0 | +0 / -0 / +0 | 0.96 | PASS |
| CH_EVE_EBa5b60 | +0.0 | +0.0 | 9815 | -8694 | -3660 | -7635 | -841 / -1270 | 3161 / 4092 | 3 | 0 | +0 / +0 / +0 | 0.96 | PASS |
| CH_EVE_EBa15b5 | +0.0 | +0.0 | 9849 | -8694 | -3660 | -7635 | -1270 / -1270 | 4092 / 4092 | 0 | 0 | +0 / +0 / +0 | 1.00 | PASS |
| CH_EVE_EBa15b15 | +0.0 | +0.0 | 9808 | -8694 | -3660 | -7635 | -1270 / -1270 | 2961 / 4092 | 1 | 0 | +0 / -0 / +0 | 0.96 | PASS |
| CH_EVE_EBa15b30 | +0.0 | +0.0 | 9768 | -8694 | -3660 | -7635 | -1270 / -1270 | 1891 / 4092 | 2 | 0 | +0 / -0 / +0 | 0.96 | PASS |
| CH_EVE_EBa15b60 | +0.0 | +0.0 | 9815 | -8694 | -3660 | -7635 | -841 / -1270 | 3161 / 4092 | 3 | 0 | +0 / +0 / +0 | 0.96 | PASS |

## London (LO_L19201dfc_R0BRF90_30_BASE, pick TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_BASE)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| R830 | nan | nan | nan | nan | nan | nan |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|

## NYPM (NP_STKd893133bd8_BASE, pick TL3_SR_NP_STKd893133bd8_BF2_BASE)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| G1 | 4 | -4800 | -5060 | 26162 | -4800 | -5060 |
| G2 | nan | nan | nan | nan | nan | nan |
| G3 | nan | nan | nan | nan | nan | nan |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|

## NYAM (NY_STKd8b76ecd35_JT68, pick TL3_SR_NY_STKd8b76ecd35_BF2_JT68)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| R10 | nan | nan | nan | nan | nan | nan |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|

## Best NW setting per session (drawdown first; "none" = the pick, reference only)

No setting yet passes the pick filter (L6M and L3M ulcer both lower); see the tables.
