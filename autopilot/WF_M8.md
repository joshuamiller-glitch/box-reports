# WF_M8: HOURS (drop the worst third of session hours of the trailing 52 weeks) (W-WF78, 2026-11-27 02:57 UTC). Research only, post-hoc on exact trades, nothing live.

## ANSWER FIRST

Primary PASS cells (of 24 = 4 sessions x 2 subjects x 3 steps): 5. PASS: S1/NY/13w, S1/NP/2w, S2/NP/4w, S2/LO/2w, S2/LO/4w

Rule: PASS = (forward max DD shallower in >= 2/3 of periods AND mean $/wk >= 90% of untouched) OR (income higher in >= 2/3 AND mean DD not deeper). 2/3 of 12/39/77 periods. Drawdown first below; "chain" = all forward periods chained into one out-of-sample daily curve, max DD untouched -> treated. Luck: 24 primary cells here (and 240 cells across the programme at 3 steps), 12 day types / ~10 hours chosen per period are many looks; the live books were picked on the same weeks, so the untouched subject is flattered.


## S1 live mixes (exact trades) (primary; 2-week step shown first)

| session | step | n | chain max DD U -> T | mean per-period max DD U -> T | shallower periods | good periods (shallower, or higher income and not deeper) | worst week chain U -> T | $/wk U -> T | trades kept | L3M max DD / income U -> T | L6M max DD / income U -> T | random-skip null: P(good >= observed) | plain p (sign, shallower) | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 2 | 77 | -67,941 -> -63,345 | -15,764 -> -12,630 | 58/77 | 58/77 | -37,409 -> -39,491 | 5,537 -> 4,365 | 69% | -21,250 / 11,934 -> -27,096 / 8,993 | -37,750 / 15,460 -> -35,416 / 10,741 | 0.09 | 0.000 | **FAIL** |
| Asia | 4 | 39 | -67,941 -> -65,635 | -23,319 -> -19,809 | 31/39 | 31/39 | -37,409 -> -39,491 | 5,388 -> 4,309 | 70% | -21,250 / 11,934 -> -27,096 / 8,993 | -37,750 / 16,600 -> -35,416 / 11,134 | 0.10 | 0.000 | **FAIL** |
| Asia | 13 | 12 | -67,941 -> -85,539 | -38,271 -> -34,026 | 8/12 | 8/12 | -37,409 -> -36,797 | 5,513 -> 4,262 | 69% | -23,953 / 10,371 -> -39,416 / 5,789 | -37,750 / 15,460 -> -39,416 / 11,485 | 0.64 | 0.194 | **FAIL** |
| NY AM | 2 | 77 | -200,647 -> -200,578 | -43,982 -> -40,709 | 44/77 | 48/77 | -110,130 -> -120,628 | 19,825 -> 19,571 | 77% | -69,974 / 55,173 -> -51,482 / 45,378 | -69,974 / 53,912 -> -59,583 / 54,279 | 0.78 | 0.127 | **FAIL** |
| NY AM | 4 | 39 | -200,647 -> -200,578 | -62,580 -> -56,017 | 25/39 | 26/39 | -110,130 -> -120,628 | 19,562 -> 19,185 | 77% | -69,974 / 55,173 -> -51,482 / 45,378 | -69,974 / 60,959 -> -59,583 / 56,832 | 0.60 | 0.054 | **FAIL** |
| NY AM | 13 | 12 | -200,647 -> -200,578 | -101,653 -> -87,193 | 10/12 | 10/12 | -110,130 -> -120,628 | 20,215 -> 19,794 | 77% | -69,974 / 60,454 -> -51,482 / 52,280 | -69,974 / 53,912 -> -59,583 / 54,279 | 0.09 | 0.019 | **PASS** |
| NY PM | 2 | 77 | -134,363 -> -152,013 | -20,215 -> -17,911 | 52/77 | 52/77 | -44,139 -> -35,667 | 5,954 -> 5,463 | 79% | -20,350 / 13,621 -> -22,612 / 12,972 | -30,613 / 12,962 -> -31,610 / 10,600 | 0.12 | 0.001 | **PASS** |
| NY PM | 4 | 39 | -134,363 -> -152,013 | -29,172 -> -27,350 | 23/39 | 23/39 | -44,139 -> -35,667 | 5,181 -> 4,929 | 79% | -20,350 / 13,621 -> -22,612 / 12,972 | -30,613 / 13,684 -> -31,584 / 11,817 | 0.73 | 0.168 | **FAIL** |
| NY PM | 13 | 12 | -134,363 -> -152,013 | -49,090 -> -47,287 | 7/12 | 7/12 | -44,139 -> -35,667 | 5,843 -> 5,018 | 78% | -26,269 / 12,337 -> -23,273 / 13,507 | -30,613 / 12,962 -> -31,584 / 11,255 | 0.79 | 0.387 | **FAIL** |
| London | 2 | 77 | -224,333 -> -211,942 | -24,151 -> -22,389 | 36/77 | 37/77 | -107,350 -> -108,062 | 5,188 -> 4,444 | 75% | -39,760 / 18,615 -> -38,206 / 15,717 | -39,760 / 17,963 -> -46,155 / 11,301 | 0.98 | 0.753 | **FAIL** |
| London | 4 | 39 | -224,333 -> -237,835 | -37,290 -> -35,052 | 20/39 | 20/39 | -107,350 -> -108,062 | 5,393 -> 4,265 | 75% | -39,760 / 18,615 -> -38,206 / 15,717 | -39,760 / 18,993 -> -46,155 / 11,273 | 0.98 | 0.500 | **FAIL** |
| London | 13 | 12 | -224,333 -> -265,830 | -65,753 -> -61,817 | 7/12 | 7/12 | -107,350 -> -108,062 | 5,430 -> 3,860 | 74% | -39,760 / 18,416 -> -38,206 / 15,068 | -39,760 / 17,963 -> -45,934 / 11,402 | 0.91 | 0.387 | **FAIL** |

## S2 Test 5 qualifier baskets (primary; 2-week step shown first)

| session | step | n | chain max DD U -> T | mean per-period max DD U -> T | shallower periods | good periods (shallower, or higher income and not deeper) | worst week chain U -> T | $/wk U -> T | trades kept | L3M max DD / income U -> T | L6M max DD / income U -> T | random-skip null: P(good >= observed) | plain p (sign, shallower) | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 2 | 76 | -15,347 -> -12,049 | -1,610 -> -1,313 | 59/76 | 59/76 | -5,422 -> -4,353 | 196 -> 155 | 70% | -4,745 / 45 -> -2,470 / 224 | -6,481 / 635 -> -4,873 / 692 | 1.00 | 0.000 | **FAIL** |
| Asia | 4 | 38 | -15,347 -> -13,794 | -2,446 -> -1,949 | 31/38 | 31/38 | -5,422 -> -4,353 | 228 -> 167 | 69% | -4,745 / 45 -> -2,470 / 274 | -6,481 / 487 -> -4,873 / 536 | 1.00 | 0.000 | **FAIL** |
| Asia | 13 | 11 | -15,347 -> -12,235 | -4,984 -> -4,263 | 9/11 | 9/11 | -5,422 -> -4,544 | 211 -> 170 | 74% | -4,852 / 207 -> -2,996 / 331 | -6,481 / 635 -> -5,316 / 653 | 1.00 | 0.033 | **FAIL** |
| NY AM | 2 | 76 | -18,432 -> -17,718 | -1,899 -> -1,598 | 53/76 | 53/76 | -6,016 -> -5,717 | 245 -> 218 | 73% | -4,955 / 239 -> -4,331 / 291 | -7,279 / 80 -> -7,529 / 72 | 1.00 | 0.000 | **FAIL** |
| NY AM | 4 | 38 | -18,432 -> -17,830 | -2,934 -> -2,372 | 24/38 | 24/38 | -6,016 -> -5,717 | 237 -> 225 | 73% | -4,955 / 239 -> -4,523 / 325 | -7,279 / 133 -> -7,707 / 113 | 1.00 | 0.072 | **FAIL** |
| NY AM | 13 | 11 | -18,432 -> -15,729 | -5,396 -> -5,039 | 7/11 | 7/11 | -6,016 -> -5,717 | 245 -> 203 | 77% | -5,127 / 398 -> -5,032 / 444 | -7,279 / 80 -> -5,659 / 159 | 1.00 | 0.274 | **FAIL** |
| NY PM | 2 | 76 | -22,890 -> -13,159 | -1,962 -> -1,794 | 50/76 | 50/76 | -4,207 -> -4,899 | 173 -> 138 | 73% | -6,360 / 54 -> -6,135 / 89 | -16,283 / 252 -> -9,507 / 147 | 1.00 | 0.004 | **FAIL** |
| NY PM | 4 | 38 | -22,890 -> -14,443 | -2,959 -> -2,709 | 26/38 | 26/38 | -4,207 -> -3,181 | 192 -> 181 | 75% | -6,360 / 54 -> -6,135 / 89 | -9,348 / 475 -> -6,135 / 275 | 1.00 | 0.017 | **PASS** |
| NY PM | 13 | 11 | -22,890 -> -15,844 | -6,696 -> -5,625 | 5/11 | 5/11 | -4,207 -> -4,128 | 204 -> 173 | 76% | -6,360 / 242 -> -6,411 / 184 | -16,283 / 252 -> -9,507 / 202 | 1.00 | 0.726 | **FAIL** |
| London | 2 | 76 | -14,554 -> -11,938 | -1,415 -> -1,031 | 53/76 | 54/76 | -8,788 -> -6,342 | -71 -> -47 | 54% | -6,053 / 66 -> -3,720 / -147 | -6,053 / 173 -> -3,720 / 75 | 0.99 | 0.000 | **PASS** |
| London | 4 | 38 | -14,505 -> -12,470 | -2,272 -> -1,511 | 31/38 | 31/38 | -8,788 -> -6,342 | -70 -> -36 | 54% | -6,053 / 66 -> -5,026 / -267 | -6,053 / 133 -> -5,026 / 5 | 0.79 | 0.000 | **PASS** |
| London | 13 | 11 | -14,464 -> -16,904 | -4,920 -> -4,057 | 9/11 | 9/11 | -8,788 -> -7,325 | -68 -> -99 | 63% | -6,053 / 159 -> -5,423 / -47 | -6,053 / 173 -> -5,866 / -51 | 0.90 | 0.033 | **FAIL** |

## Reference versions (mark: reference; chain max DD U -> T / mean $/wk U -> T / shallower periods / verdict), S1 then S2

| subject | session | step | | subject | session | step | ref:half | ref:quarter | ref:26w | ref:meantrade |
|---|---|---|---|---|---|---|
| S1 | Asia | 2 | -67,941 -> -75,628 / 5,537 -> 3,792 / 56/77 / FAIL | -67,941 -> -77,837 / 5,537 -> 4,991 / 52/77 / PASS | -67,941 -> -65,404 / 5,537 -> 4,444 / 55/77 / FAIL | -67,941 -> -63,879 / 5,537 -> 3,686 / 55/77 / FAIL |
| S1 | Asia | 4 | -67,941 -> -75,167 / 5,388 -> 3,824 / 28/39 / FAIL | -67,941 -> -70,546 / 5,388 -> 4,758 / 27/39 / FAIL | -67,941 -> -53,266 / 5,388 -> 4,517 / 29/39 / FAIL | -67,941 -> -71,731 / 5,388 -> 3,456 / 29/39 / FAIL |
| S1 | Asia | 13 | -67,941 -> -98,324 / 5,513 -> 3,054 / 10/12 / FAIL | -67,941 -> -93,438 / 5,513 -> 4,754 / 10/12 / FAIL | -67,941 -> -56,712 / 5,513 -> 4,313 / 9/12 / FAIL | -67,941 -> -85,539 / 5,513 -> 4,063 / 8/12 / FAIL |
| S1 | NY AM | 2 | -200,647 -> -189,177 / 19,825 -> 14,225 / 53/77 / FAIL | -200,647 -> -200,578 / 19,825 -> 19,571 / 44/77 / FAIL | -200,647 -> -146,380 / 19,825 -> 19,341 / 45/77 / FAIL | -200,647 -> -200,578 / 19,825 -> 17,954 / 44/77 / FAIL |
| S1 | NY AM | 4 | -200,647 -> -189,177 / 19,562 -> 13,948 / 27/39 / FAIL | -200,647 -> -200,578 / 19,562 -> 19,185 / 25/39 / FAIL | -200,647 -> -188,316 / 19,562 -> 17,505 / 23/39 / FAIL | -200,647 -> -200,578 / 19,562 -> 17,384 / 25/39 / FAIL |
| S1 | NY AM | 13 | -200,647 -> -189,177 / 20,215 -> 14,999 / 9/12 / FAIL | -200,647 -> -200,578 / 20,215 -> 19,794 / 10/12 / PASS | -200,647 -> -208,779 / 20,215 -> 20,208 / 11/12 / PASS | -200,647 -> -200,578 / 20,215 -> 19,794 / 10/12 / PASS |
| S1 | NY PM | 2 | -134,363 -> -111,239 / 5,954 -> 4,634 / 55/77 / FAIL | -134,363 -> -152,013 / 5,954 -> 5,463 / 52/77 / PASS | -134,363 -> -153,951 / 5,954 -> 5,402 / 49/77 / FAIL | -134,363 -> -152,013 / 5,954 -> 5,391 / 51/77 / FAIL |
| S1 | NY PM | 4 | -134,363 -> -111,239 / 5,181 -> 4,636 / 29/39 / FAIL | -134,363 -> -152,013 / 5,181 -> 4,929 / 23/39 / FAIL | -134,363 -> -153,951 / 5,181 -> 4,670 / 24/39 / FAIL | -134,363 -> -152,013 / 5,181 -> 4,652 / 22/39 / FAIL |
| S1 | NY PM | 13 | -134,363 -> -111,239 / 5,843 -> 4,652 / 9/12 / FAIL | -134,363 -> -152,013 / 5,843 -> 5,018 / 7/12 / FAIL | -134,363 -> -152,013 / 5,843 -> 5,192 / 7/12 / FAIL | -134,363 -> -152,013 / 5,843 -> 5,018 / 7/12 / FAIL |
| S1 | London | 2 | -224,333 -> -164,891 / 5,188 -> 1,750 / 48/77 / FAIL | -224,333 -> -211,942 / 5,188 -> 4,444 / 36/77 / FAIL | -224,333 -> -227,729 / 5,188 -> 4,067 / 41/77 / FAIL | -224,333 -> -211,942 / 5,188 -> 4,209 / 35/77 / FAIL |
| S1 | London | 4 | -224,333 -> -127,406 / 5,393 -> 2,297 / 26/39 / FAIL | -224,333 -> -237,835 / 5,393 -> 4,265 / 20/39 / FAIL | -224,333 -> -236,259 / 5,393 -> 4,606 / 24/39 / FAIL | -224,333 -> -237,835 / 5,393 -> 4,289 / 21/39 / FAIL |
| S1 | London | 13 | -224,333 -> -116,201 / 5,430 -> 3,031 / 8/12 / FAIL | -224,333 -> -265,830 / 5,430 -> 3,860 / 7/12 / FAIL | -224,333 -> -231,582 / 5,430 -> 4,003 / 8/12 / FAIL | -224,333 -> -221,491 / 5,430 -> 4,456 / 9/12 / FAIL |
| S2 | Asia | 2 | -15,347 -> -18,203 / 196 -> 102 / 57/76 / FAIL | -15,347 -> -13,108 / 196 -> 174 / 64/76 / FAIL | -15,347 -> -10,858 / 196 -> 206 / 59/76 / PASS | -15,347 -> -12,054 / 196 -> 152 / 55/76 / FAIL |
| S2 | Asia | 4 | -15,347 -> -16,903 / 228 -> 129 / 31/38 / FAIL | -15,347 -> -12,536 / 228 -> 195 / 33/38 / FAIL | -15,347 -> -13,396 / 228 -> 191 / 31/38 / FAIL | -15,347 -> -13,390 / 228 -> 160 / 31/38 / FAIL |
| S2 | Asia | 13 | -15,347 -> -12,366 / 211 -> 162 / 9/11 / FAIL | -15,347 -> -12,536 / 211 -> 209 / 9/11 / PASS | -15,347 -> -13,489 / 211 -> 142 / 9/11 / FAIL | -15,347 -> -12,235 / 211 -> 168 / 9/11 / FAIL |
| S2 | NY AM | 2 | -18,432 -> -13,670 / 245 -> 312 / 60/76 / PASS | -18,432 -> -17,718 / 245 -> 218 / 53/76 / FAIL | -18,432 -> -15,407 / 245 -> 210 / 51/76 / FAIL | -18,432 -> -17,576 / 245 -> 215 / 51/76 / FAIL |
| S2 | NY AM | 4 | -18,432 -> -13,670 / 237 -> 310 / 31/38 / PASS | -18,432 -> -17,830 / 237 -> 225 / 24/38 / FAIL | -18,432 -> -14,735 / 237 -> 269 / 26/38 / PASS | -18,432 -> -15,481 / 237 -> 264 / 27/38 / PASS |
| S2 | NY AM | 13 | -18,432 -> -13,670 / 245 -> 306 / 7/11 / FAIL | -18,432 -> -15,729 / 245 -> 203 / 7/11 / FAIL | -18,432 -> -17,565 / 245 -> 200 / 6/11 / FAIL | -18,432 -> -15,913 / 245 -> 228 / 7/11 / FAIL |
| S2 | NY PM | 2 | -22,890 -> -12,319 / 173 -> 144 / 53/76 / FAIL | -22,890 -> -22,301 / 173 -> 160 / 46/76 / FAIL | -22,890 -> -14,300 / 173 -> 138 / 50/76 / FAIL | -22,890 -> -16,989 / 173 -> 192 / 48/76 / FAIL |
| S2 | NY PM | 4 | -22,890 -> -13,695 / 192 -> 195 / 26/38 / PASS | -22,890 -> -16,894 / 192 -> 196 / 23/38 / FAIL | -22,890 -> -14,300 / 192 -> 128 / 22/38 / FAIL | -22,890 -> -13,491 / 192 -> 217 / 24/38 / FAIL |
| S2 | NY PM | 13 | -22,890 -> -11,099 / 204 -> 217 / 7/11 / FAIL | -22,890 -> -21,076 / 204 -> 196 / 6/11 / FAIL | -22,890 -> -16,312 / 204 -> 78 / 5/11 / FAIL | -22,890 -> -21,076 / 204 -> 197 / 6/11 / FAIL |
| S2 | London | 2 | -14,554 -> -14,010 / -71 -> -70 / 61/76 / FAIL | -14,554 -> -11,938 / -71 -> -47 / 53/76 / PASS | -14,554 -> -13,526 / -71 -> -64 / 51/76 / PASS | -14,554 -> -13,306 / -71 -> -60 / 47/76 / FAIL |
| S2 | London | 4 | -14,505 -> -14,436 / -70 -> -62 / 33/38 / PASS | -14,505 -> -12,470 / -70 -> -36 / 31/38 / PASS | -14,505 -> -16,697 / -70 -> -65 / 27/38 / FAIL | -14,505 -> -15,775 / -70 -> -70 / 28/38 / FAIL |
| S2 | London | 13 | -14,464 -> -9,899 / -68 -> -47 / 11/11 / PASS | -14,464 -> -16,904 / -68 -> -99 / 9/11 / FAIL | -14,464 -> -15,338 / -68 -> -100 / 9/11 / FAIL | -14,464 -> -13,737 / -68 -> -64 / 7/11 / FAIL |

## HOW (read before trusting)
- Subjects: S1 = per-trade exact TRADES of the four live sets (TL3_SR_AS_STKd8da2eb47b_FSff6_PICKC, TL3_SR_LO_STKd8w42lo_FSffb8_BARE, TL3_SR_NY_STKd8cd0279ff_FSff6_PICKC, TL3_SR_NP_STKd893133bd8_FSf46_PICKC), net of $4.84/lot fee; S2 = equal-weight realised basket of the Test 5 primary qualifiers (bare R0 exact sets, 1/count per week weight), trades inside their hold weeks only.
- Decision dates: grid weeks 26, 26+step, ... up to week 182 (2023-10-02 to 2026-10-25), forward period = next step weeks; step 2/4/13 -> up to 78/39/12 periods; the four Nov-2025 weeks excluded everywhere (training and forward). Periods with < 30 training trades are dropped (S2 starts at week 28 because the qualifier baskets only have trades inside their holds, and the filter is learned from the earlier realised basket trades, never from future holds). One engine month (202511) missing, so n is 77/38/12 for S1 rather than 78/39/12 where a period lies wholly in Nov 2025.
- EARLY DATES: the 52-week trailing window is clipped at the data start (2023-04-03): the first decision (wk 26) trains on 26 weeks, wk 39 on 39, from wk 52 on a full 52. Nothing before 2023-04 exists, so no period was skipped for that reason.
- M7 day types (12): weekday x5; prior-session NQ range tercile x3 (previous trading day high-low from the NQ daily file); overnight-gap tercile x3 (|open - prior close| of the NQ trading-day file, Globex-open basis: this is a small gap, NOT the RTH-open gap; flagged weakness); scheduled event day (hi_day of /mnt/l2/l2vast/_calendar/event_flags.csv, FOMC/CPI/NFP etc.). THE CALENDAR EXISTS ONLY FROM 2024-10-01: the event type is eligible only when the whole trailing window lies inside the calendar (decision weeks >= 126, i.e. the last ~4 13-week periods); earlier periods choose among 11 types. Terciles from past NQ days only. Worst type = lowest total trailing net $ among types with >= 8 traded days; skipped only if that total is negative. Trades are assigned to the day type of their ENTRY trading date (18:00 ET roll).
- M8: hours = ET clock hour of entry; per hour trailing net $; hours with >= 5 trades ranked; worst third (rounded) dropped, even if positive.
- Q7 time-of-session resim tables (code/th_q7) are NOT on this server (/mnt/l2/l2vast/_q7 absent here); S2 uses the exact trades of the qualifier sets instead, which is at least as faithful.
- 'post-hoc approx': dropping trades does not re-run the one-position rule, stack caps or the daily-loss halts, so a dropped trade could in the engine have let another trade in. Direction of error unknown.
- Null: 200 draws skipping the same share of trades per period at random (independent); column gives the share of draws whose good-period count is >= the observed one.
- Chained curve DD: forward periods joined in time order on daily P&L; this is the only DD number comparable across steps. Per-period DD for 2-week periods is very noisy.
- Many looks: 12 day types or ~10 hours re-chosen at each date, 3 steps, 8 subject-sessions, 5-6 versions. Treat any PASS as a candidate only.
Selections in the last six 2-week decisions (S1 NY AM primary): [(170, [11]), (172, [11]), (174, [11]), (176, [11]), (178, [11]), (180, [11])]

## READING THE PASS CELLS (added by W-WF78)
- A per-period PASS is not a chained-curve improvement: check the "chain max DD" column. S1 NY PM at 2 weeks passes the count (52/77 shallower) but its chained OOS max DD goes -134,363 -> -152,013; S1 NY AM at 13 weeks (M8) 10/12 shallower but chain -200,647 -> -200,578 (flat) and worst week worse.
- S2 qualifier baskets have near-zero or negative income per week in some sessions (London about -70/wk, NY PM about 190/wk): a "PASS" there is a tiny-dollar basket that was already barely alive, and the basket is built from cells selected on the same trailing data (in-sample).
- Not done: pessimistic-fill re-score of PASS cells (label only, to be queued by LEAD), ALL-session combination, trade-level re-run through the engine (post-hoc approx). Candidates go to the forward register only if LEAD accepts them; nothing is called "works".
