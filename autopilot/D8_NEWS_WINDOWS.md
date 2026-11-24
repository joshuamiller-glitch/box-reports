# D8 NEWS WINDOWS (family NW): entry blocks around releases and open-trade rules

Research only, 2 lots per book, written 2026-11-24 13:08 UTC by code/th_nw/nw_score.py (hook nw_hooks.py, builder nw_gen.py, queue nw_next.py, scorer nw_score.py, calendar nw_cal.py). Order: DIRECTIVE_NEWS_WINDOWS_20261123_1825Z.md (Josh: "if in open trade it could get taken for a huge ride").

**Calendar**: /mnt/l2/l2vast/_calendar/events.csv has events from **2024-10-01** (first row ISM manufacturing 10:00 ET) to 2026-12-23. Months 2023-04 to 2024-09 have NO events: they are NOT SCORED for NW (an NW set equals its pick there by construction; shown as "no calendar", never as evidence). So prior years here = 2024-10..2025-12 and 2026-01..04 (18 months, 2025-11 has no data) and L6M = 2026-05..10, L3M = 2026-08..10; data end 2026-10. 54 calendar rows are rule-derived (ISM dates), 1 UNVERIFIED, the rest verified. The calendar has no FOMC press-conference row: FOMC press = every FOMC decision date at 14:30 ET (synthetic). NOT in the calendar, so not tested: JOLTS, consumer confidence, new home sales and other 10:00 releases, Treasury auctions (in the file as AUC_* but not in the order).

**Rules as applied (hook nw_hooks.py)**: ENTRY BLOCK (A before, B after the release): a new-entry signal of a governed book is skipped when its order time is in [release-A min, release+B min); an unfilled resting limit entry at release-A is cancelled. OPEN-TRADE RULE at release-A for every trade open then: CLOSE = closed at market (exit name NWClose, market walk at 2 lots, measured basis, like every exit); BE = if the open profit marked at the liquidation side is > 0 the stop moves to break-even (entry price, never loosened), target stays, trade runs on, else closed at market. LEAVE ALONE = the pick row (reference). Rows "open rule" = rule only (re-entry after the close is allowed); rows "combo" = open rule at release-A plus the entry block [-A, +B). Groups: NY AM R10 = ISM mfg + ISM services + 10:00 PCE + chair speeches 09:00-12:00; NY PM G1 = FOMC decision 14:00, G2 = FOMC press 14:30, G3 = FOMC minutes 14:00 + chair speeches 12:00-16:00; London R830 = CPI PPI NFP GDP retail sales PCE + chair 08:30 (the London book is flat at 08:30:01, B is moot; A=5 / A=2 close rows are the 08:25 / 08:28 flatten tests, entry A=30 is the 08:00 block); Asia CH_EVE = the 3 chair speeches at 19:30-23:30 ET (the Asia book is flat at 02:00, so 08:30 / 10:00 / 14:00 releases never overlap it). NY AM versus the 08:30 releases: the longest block (B=60) ends at 09:30, so not tested. Sets are ALL books of the stack in one run (per-book numbers are the per-book trades of that run, exact per-book sets only for winners later); per release type numbers are the trades of that type's release days inside the group run (days differ by type, so exact up to week-state coupling; same-day releases are listed under each type).

Windows and definitions: daily series house convention (exit ET date +7h, p484 = gross - 4.84 x lots), zero-filled on the pick's trading days; ulcer = RMS drawdown (primary); "release day" = trading date of the release; worst single trade = lowest p484 of one trade whose exit trading date is a release day; worst day = lowest daily sum over release days of the group. Verdict: pick on L6M ulcer with L3M not worse, walk-forward >= 0.58, prior years not RED (>30% worse at equal-risk $/wk), best-of-many null 4 of 5 (placebo release dates, emulation). Selection rule: refit with the next joint.

## Best per session (verdict = gate AND L6M ulcer lower AND L3M not higher; null = best-of-N settings, real beats k of the first 5, needs 4)

- Asia (AS_STKd8106b26ef_JT19): best CH_EVE_EBa2b5, L6M ulcer +0.0% (L3M +0.0%), verdict NO-EFFECT; null not run in this scoring (no null draws in nw_null.json).
- London (LO_L19201dfc_R0BRF90_30_BASE): best R830_EBa30, L6M ulcer -3.7% (L3M -1.9%), verdict PASS; null not run in this scoring (no null draws in nw_null.json).
- NYPM (NP_STKd893133bd8_BASE): best G3_EBa5b5, L6M ulcer -3.6% (L3M +0.0%), verdict PASS; null not run in this scoring (no null draws in nw_null.json).
- NYAM (NY_STKd8b76ecd35_JT68): best R10_OBa2, L6M ulcer +1.1% (L3M -1.7%), verdict FAIL; null not run in this scoring (no null draws in nw_null.json).

Rows landed: 171 of 171 sets complete (all scored months). Verdict and null use complete sets only.

## Asia (AS_STKd8106b26ef_JT19, pick TL3_SR_AS_STKd8106b26ef_BF2_JT19)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| CH_EVE | 1 | -1270 | 4092 | 4092 | -1410 | -5692 |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| CH_EVE_EBa2b5 | +0.0 | +0.0 | 9849 | -8694 | -3660 | -7635 | -1270 / -1270 | 4092 / 4092 | 0 | 0 | +0 / +0 / +0 | 1.00 | NO-EFFECT |
| CH_EVE_EBa2b15 | +0.0 | +0.0 | 9808 | -8694 | -3660 | -7635 | -1270 / -1270 | 2961 / 4092 | 1 | 0 | +0 / -0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa2b30 | +0.0 | +0.0 | 9768 | -8694 | -3660 | -7635 | -1270 / -1270 | 1891 / 4092 | 2 | 0 | +0 / -0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa2b60 | +0.0 | +0.0 | 9815 | -8694 | -3660 | -7635 | -841 / -1270 | 3161 / 4092 | 3 | 0 | +0 / +0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa5b5 | +0.0 | +0.0 | 9849 | -8694 | -3660 | -7635 | -1270 / -1270 | 4092 / 4092 | 0 | 0 | +0 / +0 / +0 | 1.00 | NO-EFFECT |
| CH_EVE_EBa5b15 | +0.0 | +0.0 | 9808 | -8694 | -3660 | -7635 | -1270 / -1270 | 2961 / 4092 | 1 | 0 | +0 / -0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa5b30 | +0.0 | +0.0 | 9768 | -8694 | -3660 | -7635 | -1270 / -1270 | 1891 / 4092 | 2 | 0 | +0 / -0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa5b60 | +0.0 | +0.0 | 9815 | -8694 | -3660 | -7635 | -841 / -1270 | 3161 / 4092 | 3 | 0 | +0 / +0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa15b5 | +0.0 | +0.0 | 9849 | -8694 | -3660 | -7635 | -1270 / -1270 | 4092 / 4092 | 0 | 0 | +0 / +0 / +0 | 1.00 | NO-EFFECT |
| CH_EVE_EBa15b15 | +0.0 | +0.0 | 9808 | -8694 | -3660 | -7635 | -1270 / -1270 | 2961 / 4092 | 1 | 0 | +0 / -0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa15b30 | +0.0 | +0.0 | 9768 | -8694 | -3660 | -7635 | -1270 / -1270 | 1891 / 4092 | 2 | 0 | +0 / -0 / +0 | 0.96 | NO-EFFECT |
| CH_EVE_EBa15b60 | +0.0 | +0.0 | 9815 | -8694 | -3660 | -7635 | -841 / -1270 | 3161 / 4092 | 3 | 0 | +0 / +0 / +0 | 0.96 | NO-EFFECT |

## London (LO_L19201dfc_R0BRF90_30_BASE, pick TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_BASE)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| R830 | 22 | -3625 | -3679 | 17482 | -3630 | -5321 |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| R830_EBa30 | -3.7 | -1.9 | 3318 | -7836 | -4903 | -6629 | -3625 / -3625 | -3679 / -3679 | 3 | 0 | +0 / +5 / +3 | 0.94 | PASS |
| R830_EBa15 | -3.7 | -1.9 | 3318 | -7836 | -4903 | -6629 | -3625 / -3625 | -3679 / -3679 | 3 | 0 | -0 / +8 / -0 | 0.96 | PASS |
| R830_CBa15 | -2.9 | -0.8 | 3232 | -7836 | -4903 | -6629 | -3625 / -3625 | -3625 / -3679 | 3 | 3 | -8 / -8 / -2 | 0.80 | PASS |
| R830_CCa15 | -2.9 | -0.8 | 3232 | -7836 | -4903 | -6629 | -3625 / -3625 | -3625 / -3679 | 3 | 3 | -8 / -6 / -2 | 0.76 | PASS |
| R830_EBa5 | -1.2 | -1.9 | 3294 | -7836 | -5371 | -6629 | -3625 / -3625 | -3679 / -3679 | 2 | 0 | +0 / +0 / +0 | 1.00 | PASS |
| R830_EBa2 | -0.8 | -1.3 | 3271 | -7836 | -5371 | -6629 | -3625 / -3625 | -3679 / -3679 | 1 | 0 | +0 / +0 / +0 | 1.00 | PASS |
| R830_OBa15 | +0.8 | +1.1 | 3178 | -7836 | -5371 | -6629 | -3625 / -3625 | -3625 / -3679 | 0 | 3 | -8 / -15 / -2 | 0.81 | NO-GAIN |
| R830_OCa15 | +0.8 | +1.1 | 3178 | -7836 | -5371 | -6629 | -3625 / -3625 | -3625 / -3679 | 0 | 3 | -8 / -13 / -2 | 0.78 | NO-GAIN |
| R830_CCa2 | +2.1 | +0.6 | 3231 | -8043 | -5791 | -6629 | -3625 / -3625 | -3694 / -3679 | 1 | 5 | -3 / -21 / -1 | 0.76 | NO-GAIN |
| R830_CBa2 | +2.1 | +0.6 | 3213 | -8043 | -5791 | -6629 | -3625 / -3625 | -3694 / -3679 | 1 | 4 | -2 / -19 / -0 | 0.78 | NO-GAIN |
| R830_OCa2 | +2.9 | +1.9 | 3224 | -8043 | -5791 | -6629 | -3625 / -3625 | -3694 / -3679 | 0 | 5 | -3 / -21 / -1 | 0.76 | NO-GAIN |
| R830_OBa2 | +2.9 | +1.9 | 3206 | -8043 | -5791 | -6629 | -3625 / -3625 | -3694 / -3679 | 0 | 4 | -2 / -19 / -0 | 0.78 | NO-GAIN |

## NYPM (NP_STKd893133bd8_BASE, pick TL3_SR_NP_STKd893133bd8_BF2_BASE)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| G1 | 4 | -4800 | -5060 | 26162 | -4800 | -9450 |
| G2 | 4 | -4800 | -5060 | 26162 | -4800 | -9450 |
| G3 | 4 | -2405 | -3248 | 1101 | -4820 | -8582 |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G3_EBa5b5 | -3.6 | +0.0 | 8908 | -24257 | -8566 | -16735 | -2405 / -2405 | -222 / -3248 | 3 | 0 | +2 / +1 / +0 | 0.93 | PASS |
| G3_EBa5b15 | -3.6 | +0.0 | 8908 | -24257 | -8566 | -16735 | -2405 / -2405 | -222 / -3248 | 4 | 0 | +2 / +9 / +0 | 0.89 | PASS |
| G3_EBa15b60 | -3.5 | +0.2 | 8776 | -24257 | -8566 | -16735 | -2405 / -2405 | -2272 / -3248 | 9 | 0 | -0 / -6 / -4 | 0.93 | NO-GAIN |
| G3_EBa15b5 | -2.8 | +0.0 | 8863 | -24257 | -8566 | -16735 | -2405 / -2405 | -1457 / -3248 | 4 | 0 | +2 / +1 / +0 | 0.89 | PASS |
| G3_EBa15b15 | -2.8 | +0.0 | 8863 | -24257 | -8566 | -16735 | -2405 / -2405 | -1457 / -3248 | 5 | 0 | +2 / +9 / +0 | 0.87 | PASS |
| G3_EBa5b60 | -2.8 | +0.2 | 8731 | -24257 | -8566 | -16735 | -2405 / -2405 | -2272 / -3248 | 8 | 0 | -0 / -6 / -4 | 0.91 | NO-GAIN |
| G1_OCa15 | -0.5 | -1.9 | 8951 | -24257 | -8566 | -16735 | -4800 / -4800 | 610 / -5060 | 0 | 6 | -18 / +1 / +22 | 0.83 | PASS |
| G2_EBa15b5 | -0.5 | -1.8 | 8889 | -24257 | -8566 | -16735 | -4800 / -4800 | -1511 / -5060 | 10 | 0 | +1 / -2 / -3 | 0.89 | PASS |
| G2_EBa5b5 | -0.5 | -1.8 | 8799 | -24257 | -8566 | -16735 | -4800 / -4800 | -1511 / -5060 | 5 | 0 | +1 / -1 / +1 | 0.89 | PASS |
| G2_EBa2b5 | -0.5 | -1.8 | 8843 | -24257 | -8566 | -16735 | -4800 / -4800 | -1511 / -5060 | 4 | 0 | +1 / -1 / +1 | 0.89 | PASS |
| G1_OBa15 | -0.4 | -1.4 | 8823 | -24257 | -8566 | -16735 | -4800 / -4800 | -2625 / -5060 | 0 | 3 | -17 / +1 / +28 | 0.83 | PASS |
| G2_EBa15b15 | -0.4 | -1.4 | 8620 | -24257 | -9072 | -16735 | -4800 / -4800 | -2701 / -5060 | 14 | 0 | -1 / -2 / -18 | 0.87 | PASS |

## NYAM (NY_STKd8b76ecd35_JT68, pick TL3_SR_NY_STKd8b76ecd35_BF2_JT68)

Reference (no rule = the pick), on release days of each group, L6M | all scored months:

| group | L6M release days | L6M worst single trade | L6M worst day | L6M $ on release days | all-months worst single trade | all-months worst day |
|--|--|--|--|--|--|--|
| R10 | 15 | -4050 | -3782 | 21534 | -4820 | -10819 |

Top settings by L6M ulcer (full list of every row in D8_NEWS_WINDOWS_ROWS.md):

| code | L6M ulcer % | L3M ulcer % | L6M $/wk | L6M maxDD | L6M worst wk | L6M worst day | L6M rel-day worst trade (rule / ref) | L6M rel-day worst day (rule / ref) | removed | closed early | prior yrs ulcer % (2024Q4 / 2025 / 2026a) | WF | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| R10_OBa2 | +1.1 | -1.7 | 5800 | -10218 | -4550 | -5504 | -4050 / -4050 | -4307 / -3782 | 3 | 7 | +27 / +2 / +13 | 0.65 | FAIL |
| R10_EBa5b60 | +7.5 | +14.8 | 6091 | -11022 | -4550 | -5504 | -2395 / -4050 | -2490 / -3782 | 77 | 0 | -11 / +3 / -32 | 0.65 | NO-GAIN |
| R10_EBa15b60 | +7.9 | +15.0 | 5764 | -11022 | -4550 | -5504 | -2395 / -4050 | -4339 / -3782 | 102 | 0 | -9 / -5 / -27 | 0.61 | FAIL |
| R10_OCa2 | +11.4 | +12.8 | 5447 | -11159 | -4550 | -5504 | -4050 / -4050 | -4307 / -3782 | 3 | 13 | +40 / +4 / +13 | 0.59 | FAIL |
| R10_EBa2b60 | +12.8 | +21.6 | 6118 | -12170 | -4550 | -5504 | -2395 / -4050 | -3136 / -3782 | 73 | 0 | -12 / +2 / -32 | 0.67 | NO-GAIN |
| R10_EBa5b5 | +12.9 | +18.5 | 5993 | -14134 | -4550 | -5504 | -4050 / -4050 | -5100 / -3782 | 12 | 0 | +3 / -0 / +1 | 0.72 | NO-GAIN |
| R10_EBa15b5 | +13.2 | +18.7 | 5937 | -14134 | -5084 | -5504 | -4050 / -4050 | -5100 / -3782 | 40 | 0 | +23 / +1 / +1 | 0.69 | FAIL |
| R10_CBa2b60 | +13.8 | +21.4 | 5559 | -11262 | -4550 | -5504 | -2395 / -4050 | -4339 / -3782 | 74 | 7 | -17 / +5 / -18 | 0.63 | FAIL |
| R10_OBa5 | +15.7 | +19.9 | 5595 | -12793 | -4550 | -5504 | -4050 / -4050 | -3782 / -3782 | 3 | 10 | +9 / +3 / +12 | 0.65 | NO-GAIN |
| R10_OCa5 | +16.6 | +21.1 | 5493 | -12793 | -4550 | -5504 | -4050 / -4050 | -3782 / -3782 | 3 | 16 | +13 / +8 / +12 | 0.59 | NO-GAIN |
| R10_EBa5b30 | +17.5 | +26.7 | 5984 | -13895 | -4550 | -5504 | -4050 / -4050 | -4860 / -3782 | 36 | 0 | -15 / +4 / -9 | 0.76 | NO-GAIN |
| R10_EBa2b5 | +17.9 | +25.3 | 5988 | -15282 | -5064 | -6248 | -4050 / -4050 | -6248 / -3782 | 8 | 0 | -1 / -0 / +1 | 0.74 | NO-GAIN |

## Best NW setting per session (drawdown first; "none" = the pick, reference only)

### London: R830_EBa30 [LEAD (null pending)]

L6M ulcer -3.7% (L3M -1.9%), $/wk L6M 3318 vs ref 3265, maxDD -7836 vs -7836, worst week -4903 vs -5371; release-day worst single trade -3625 vs ref -3625; release-day worst day -3679 vs ref -3679; prior years ulcer % +0 / +5 / +3; walk-forward 0.944 (PASS).
Exact ET clock rules (relay can code):

- release 08:30 ET: no new entry from 08:00 up to (not incl.) 08:35 (the London book is flat at 08:30:01 anyway)

### NYPM: G3_EBa5b15 [LEAD (null pending)]

L6M ulcer -3.6% (L3M +0.0%), $/wk L6M 8908 vs ref 8736, maxDD -24257 vs -24257, worst week -8566 vs -8566; release-day worst single trade -2405 vs ref -2405; release-day worst day -222 vs ref -3248; prior years ulcer % +2 / +9 / +0; walk-forward 0.889 (PASS).
Exact ET clock rules (relay can code):

- release 12:00 ET: no new entry from 11:55 up to (not incl.) 12:15
- release 12:20 ET: no new entry from 12:15 up to (not incl.) 12:35
- release 12:30 ET: no new entry from 12:25 up to (not incl.) 12:45
- release 12:35 ET: no new entry from 12:30 up to (not incl.) 12:50
- release 13:00 ET: no new entry from 12:55 up to (not incl.) 13:15
- release 13:30 ET: no new entry from 13:25 up to (not incl.) 13:45
- release 14:00 ET: no new entry from 13:55 up to (not incl.) 14:15
- release 14:40 ET: no new entry from 14:35 up to (not incl.) 14:55
- release 15:00 ET: no new entry from 14:55 up to (not incl.) 15:15
