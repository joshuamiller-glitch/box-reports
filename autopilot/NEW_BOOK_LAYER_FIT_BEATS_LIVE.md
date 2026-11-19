# NEW_BOOK_LAYER_FIT_BEATS_LIVE - own fitted layers of every D8 candidate that beats a live book (W-LAYERS, refreshed 2026-11-19 21:25Z)

Generator: code/th_layers/layer_gen.py (verified: reproduces all 81 XA3 sets byte-identically), cron code/th_layers/layer_cron.py every 30 min. Basis: each layer setting is the new book's own REPLACE row (base) + ONE layer on the exact engine vs TODAY's stack, fitted on the last 6 months (3 months beside), every live layer stays ON; prior years / 30 layered controls / 2-week roll still to run; provisional until Asia, London are decided (clock order). Columns = layered set minus its base row: stack ulcer (negative = better), worst week, max DD, mean $/wk (engine base lots, $4.84 RT proxy); a setting must keep trades >= 80% of the base.

## Progress and engine hours (read from autopilot/HEALTH.md at every refresh, never a fixed rate)
- engine rate: 8462 set-months/h (HEALTH.md at 21:25Z); layer queue (tag NYL, quota 5) landed 1105 set-months in the last hour, 2085 in 3 h; fast-path share of engine slots (W-FASTLADDER): 90%
- layer set-months queued 11995, landed 7329, remaining 4630; hours at the HEALTH rate (whole fleet) 0.5 h; at the measured NYL rate 4 h; at the fast-path rate: once W-FASTLADDER reports >= 90% of engine slots on the fast path the same remaining work counts at the fast-path speed-up (2.3x measured on one Asia ADD month; NY AM / REPLACE not yet timed)

| label | layer set-months queued | landed |
|---|---|---|
| Lda55d973xA7 | 918 | 461 |
| L5c9e11b3xA7 | 795 | 788 |
| La5b5d03axA7 | 752 | 432 |
| Ledfbf4d2xA7 | 746 | 740 |
| Lcb276f27xA7 | 752 | 440 |
| Lf77e374bxA7 | 432 | 99 |
| L7c368a4fxA7 | 1004 | 492 |
| L1edb9fabxA7 | 432 | 400 |
| L6a25b155xK7 | 561 | 561 |
| L01811caaxK7 | 906 | 906 |
| L21f079b6xK7 | 623 | 432 |
| L4d206c8cxA7 | 432 | 59 |
| Ldcdb0b6exA7 | 390 | 390 |
| L86781ac0xA7 | 348 | 347 |
| Lc4e74264xA7 | 348 | 108 |
| L7ea48296xA7 | 348 | 104 |
| L548972b6xA7 | 348 | 49 |
| Lb44a3e99xK7 | 348 | 343 |
| L678ebaddxK7 | 348 | 69 |
| L6c84f416xK7 | 348 | 32 |
| L641a7c4dxK7 | 348 | 48 |
| Lfea1c9fcxA7 | 432 | 29 |

## D8 gates per candidate: ENGINE rule B (order 1122Z)
Rule B: the stack WITH the new book (REPLACE row) vs TODAY'S stack in the SAME prior year. Sign convention: every percentage is "% WORSE than today's stack" (positive = worse): stack ulcer higher, max DD deeper, worst week lower, mean $/wk lower; negative = better. RED if any > 30%, AMBER 15-30%, else GREEN; persistence = share of 2-week windows where the new stack is not below today's (engine weekly difference). Until a candidate has engine prior years its tier is PENDING (never fail); the screen rule A (bare stream) is shown only as a note and orders the queue. Gate (order 1324Z, Josh): L6M + L3M beat (the candidate rows) + no RED prior year (rule B) + ENGINE persistence >= 0.58 (share of 2-week windows where the new stack is not worse than today's); persistence not yet published = PENDING, never fail (W-LAYERS' own pooled prior-year value is shown as provisional and is not used to fail). Tier -1/FIRST = coordinator-ordered first tier, 0 = gate pass, 2 = pending, 3 = rule-B RED / persistence fail / duplicate stream; Asia before NY inside a tier.

| label | tier | rule B verdict (and screen note) | 2023 d ulcer / d DD / d worst wk / d $/wk (% worse) colour | 2024 | 2025 | engine persistence |
|---|---|---|---|---|---|---|
| L01811caaxK7 | FIRST | FIRST (coordinator order 1156Z, position 1) | GATE PASS: 3 prior years none RED (AMBER 2023), engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.577 | -21% / +10% / +19% / -20% AMBER | -14% / -4% / +6% / -12% GREEN | -12% / -10% / -12% / -7% GREEN | 0.58 |
| L6a25b155xK7 | FIRST | FIRST (coordinator order 1156Z, position 2) | GATE PASS: 3 prior years none RED, engine persistence 0.590 >= 0.58 | W-NYENG pooled 43-month engine persistence 0.59 (REPLACE base); W-LAYERS 2023-25-only 0.577 | -4% / +13% / +5% / -25% GREEN | +10% / -3% / -3% / -14% GREEN | +3% / +3% / +0% / -7% GREEN | 0.58 |
| Lfea1c9fcxA7 | FIRST | FIRST (Asia gate-pass rank 1 by engine persistence) | W-ASIA PASS LIST: pass (pick REPLACE, pooled engine persistence 0.85 >= 0.58, 3 prior years no RED) | n/a | n/a | n/a | 0.85 |
| Ld9ea2776xK7 | FIRST | OWN-MERIT rank 1.0 (score 0.9449126094523477) | strict criterion (column only, not a gate): FAIL - L6M ulcer +533 mean +3080 worst wk -1545 max DD -1539 NOT strict; L3M ulcer +608 mean +1912 worst wk -1545 max DD -1539 NOT strict | n/a | n/a | n/a | n/a |
| Ldcdb0b6exA7 | FIRST | OWN-MERIT rank 2.0 (score 0.7681206556417058) | strict criterion (column only, not a gate): FAIL - L6M ulcer -373 mean +1317 worst wk -214 max DD +1570 NOT strict; L3M ulcer -65 mean +1637 worst wk -214 max DD +1570 NOT strict | n/a | n/a | n/a | n/a |
| Lb44a3e99xK7 | FIRST | OWN-MERIT rank 2.0 (score 0.9070675250511713) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1113 mean +1878 worst wk -3333 max DD -5791 NOT strict; L3M ulcer +1583 mean +1307 worst wk -3333 max DD -5791 NOT strict | n/a | n/a | n/a | n/a |
| L86781ac0xA7 | FIRST | OWN-MERIT rank 3.0 (score 0.6690035881353938) | strict criterion (column only, not a gate): FAIL - L6M ulcer +177 mean +1476 worst wk -4887 max DD -1151 NOT strict; L3M ulcer +900 mean +1342 worst wk -4887 max DD -1151 NOT strict | n/a | n/a | n/a | n/a |
| L678ebaddxK7 | FIRST | OWN-MERIT rank 3.0 (score 0.771150530259519) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1043 mean +2899 worst wk -100 max DD -5954 NOT strict; L3M ulcer +1538 mean +2236 worst wk -100 max DD -5954 NOT strict | n/a | n/a | n/a | n/a |
| Lc4e74264xA7 | FIRST | OWN-MERIT rank 4.0 (score 0.6666239680742703) | strict criterion (column only, not a gate): FAIL - L6M ulcer -926 mean +3168 worst wk -313 max DD +3113 NOT strict; L3M ulcer -1029 mean +3456 worst wk -313 max DD +3113 NOT strict | n/a | n/a | n/a | n/a |
| L6c84f416xK7 | FIRST | OWN-MERIT rank 4.0 (score 0.7642737637410547) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1220 mean +2271 worst wk -5696 max DD -4913 NOT strict; L3M ulcer +2088 mean +1786 worst wk -5696 max DD -4913 NOT strict | n/a | n/a | n/a | n/a |
| L7ea48296xA7 | FIRST | OWN-MERIT rank 5.0 (score 0.5884590646074138) | strict criterion (column only, not a gate): FAIL - L6M ulcer +69 mean +1310 worst wk +1250 max DD -3031 NOT strict; L3M ulcer +647 mean +2328 worst wk +1250 max DD -3031 NOT strict | n/a | n/a | n/a | n/a |
| L641a7c4dxK7 | FIRST | OWN-MERIT rank 5.0 (score 0.7098514261738971) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1021 mean +3183 worst wk -8053 max DD -5669 NOT strict; L3M ulcer +1781 mean +2647 worst wk -8053 max DD -5669 NOT strict | n/a | n/a | n/a | n/a |
| L548972b6xA7 | FIRST | OWN-MERIT rank 6.0 (score 0.5703005754703793) | strict criterion (column only, not a gate): FAIL - L6M ulcer -2 mean +865 worst wk +943 max DD +3530 ok; L3M ulcer +93 mean +599 worst wk +943 max DD +3530 NOT strict | n/a | n/a | n/a | n/a |
| L2176f633xK7 | FIRST | OWN-MERIT rank 6.0 (score 0.680083914322267) | strict criterion (column only, not a gate): FAIL - L6M ulcer +970 mean +2340 worst wk -4330 max DD -5390 NOT strict; L3M ulcer +1410 mean +1786 worst wk -4330 max DD -5390 NOT strict | n/a | n/a | n/a | n/a |
| Lbe8a8e54xA7 | FIRST | OWN-MERIT rank 7.0 (score 0.5514247458488498) | strict criterion (column only, not a gate): FAIL - L6M ulcer -703 mean +2236 worst wk -338 max DD +2173 NOT strict; L3M ulcer -847 mean +3188 worst wk -338 max DD +2173 NOT strict | n/a | n/a | n/a | n/a |
| L39470318xK7 | FIRST | OWN-MERIT rank 7.0 (score 0.6462296600537362) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1860 mean +1741 worst wk -9015 max DD -12215 NOT strict; L3M ulcer +2706 mean +1613 worst wk -9015 max DD -12215 NOT strict | n/a | n/a | n/a | n/a |
| L7c368a4fxA7 | FIRST | OWN-MERIT rank 8.0 (score 0.5512267213349934) | strict criterion (column only, not a gate): PASS - L6M ulcer -199 mean +1810 worst wk +464 max DD +1810 ok; L3M ulcer -1260 mean +3199 worst wk +2228 max DD +5312 ok | n/a | n/a | n/a | n/a |
| L86efc549xK7 | FIRST | OWN-MERIT rank 8.0 (score 0.61005458081942) | strict criterion (column only, not a gate): FAIL - L6M ulcer +255 mean +2505 worst wk +1651 max DD +664 NOT strict; L3M ulcer +303 mean +2638 worst wk +1651 max DD +664 NOT strict | n/a | n/a | n/a | n/a |
| L224050e7xA7 | FIRST | OWN-MERIT rank 9.0 (score 0.5169715780807336) | strict criterion (column only, not a gate): FAIL - L6M ulcer +28 mean +1436 worst wk -6936 max DD +522 NOT strict; L3M ulcer -316 mean +198 worst wk -3549 max DD +522 NOT strict | n/a | n/a | n/a | n/a |
| L4eba93d7xK7 | FIRST | OWN-MERIT rank 9.0 (score 0.5746168074599439) | strict criterion (column only, not a gate): FAIL - L6M ulcer +68 mean +2261 worst wk -3830 max DD +1432 NOT strict; L3M ulcer -510 mean +2536 worst wk -2835 max DD +1432 NOT strict | n/a | n/a | n/a | n/a |
| L2010fec9xK7 | FIRST | OWN-MERIT rank 10.0 (score 0.5435876160066083) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1560 mean +2259 worst wk -7800 max DD -8250 NOT strict; L3M ulcer +2475 mean +1662 worst wk -7800 max DD -8250 NOT strict | n/a | n/a | n/a | n/a |
| Lfb608c7bxA7 | FIRST | OWN-MERIT rank 11.0 (score 0.5013264017849397) | strict criterion (column only, not a gate): FAIL - L6M ulcer +600 mean +1478 worst wk -4124 max DD -8588 NOT strict; L3M ulcer +1721 mean +1908 worst wk -4124 max DD -8588 NOT strict | n/a | n/a | n/a | n/a |
| L582ae3cbxK7 | FIRST | OWN-MERIT rank 11.0 (score 0.5354879582398785) | strict criterion (column only, not a gate): FAIL - L6M ulcer +240 mean +2329 worst wk -4905 max DD +952 NOT strict; L3M ulcer +250 mean +2403 worst wk -4905 max DD +952 NOT strict | n/a | n/a | n/a | n/a |
| L15f14debxA7 | FIRST | OWN-MERIT rank 12.0 (score 0.4646530089269369) | strict criterion (column only, not a gate): FAIL - L6M ulcer +261 mean +707 worst wk -110 max DD -3605 NOT strict; L3M ulcer +672 mean +610 worst wk -110 max DD -3605 NOT strict | n/a | n/a | n/a | n/a |
| L03be4d27xK7 | FIRST | OWN-MERIT rank 12.0 (score 0.5271844063424663) | strict criterion (column only, not a gate): FAIL - L6M ulcer +194 mean +2845 worst wk -3120 max DD -217 NOT strict; L3M ulcer +184 mean +2867 worst wk -3120 max DD -217 NOT strict | n/a | n/a | n/a | n/a |
| Lda55d973xA7 | FIRST | OWN-MERIT rank 13.0 (score 0.46197594464680475) | strict criterion (column only, not a gate): PASS - L6M ulcer -1222 mean +911 worst wk +1631 max DD +1609 ok; L3M ulcer -1416 mean +2143 worst wk +1631 max DD +1609 ok | n/a | n/a | n/a | n/a |
| L2b8ccd55xK7 | FIRST | OWN-MERIT rank 13.0 (score 0.5040629192567844) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1665 mean +1362 worst wk -4130 max DD -9942 NOT strict; L3M ulcer +2820 mean +950 worst wk -4130 max DD -9942 NOT strict | n/a | n/a | n/a | n/a |
| L1edb9fabxA7 | FIRST | OWN-MERIT rank 14.0 (score 0.4503009121703421) | strict criterion (column only, not a gate): PASS - L6M ulcer -142 mean +1606 worst wk +464 max DD +98 ok; L3M ulcer -1252 mean +3083 worst wk +2203 max DD +5307 ok | n/a | n/a | n/a | n/a |
| Lc338b47bxK7 | FIRST | OWN-MERIT rank 14.0 (score 0.5003735518658498) | strict criterion (column only, not a gate): FAIL - L6M ulcer +823 mean +2487 worst wk -2915 max DD -2071 NOT strict; L3M ulcer +1145 mean +3152 worst wk -2915 max DD -2071 NOT strict | n/a | n/a | n/a | n/a |
| Ledfbf4d2xA7 | FIRST | OWN-MERIT rank 15.0 (score 0.4362018680339954) | strict criterion (column only, not a gate): PASS - L6M ulcer -459 mean +384 worst wk +4405 max DD +1029 ok; L3M ulcer -548 mean +1331 worst wk +4405 max DD +1029 ok | n/a | n/a | n/a | n/a |
| L4ed22711xK7 | FIRST | OWN-MERIT rank 15.0 (score 0.49907026914664) | strict criterion (column only, not a gate): FAIL - L6M ulcer +336 mean +1980 worst wk -3010 max DD +1537 NOT strict; L3M ulcer +63 mean +2912 worst wk +690 max DD +1537 NOT strict | n/a | n/a | n/a | n/a |
| L40bde9eaxA7 | FIRST | OWN-MERIT rank 16.0 (score 0.4237138464311408) | strict criterion (column only, not a gate): FAIL - L6M ulcer -398 mean +679 worst wk -116 max DD +2281 NOT strict; L3M ulcer -813 mean +3433 worst wk -116 max DD +2281 NOT strict | n/a | n/a | n/a | n/a |
| L4fd10b76xK7 | FIRST | OWN-MERIT rank 16.0 (score 0.4932034271304264) | strict criterion (column only, not a gate): FAIL - L6M ulcer +808 mean +2255 worst wk -5920 max DD -1844 NOT strict; L3M ulcer +848 mean +2149 worst wk -5920 max DD -1844 NOT strict | n/a | n/a | n/a | n/a |
| Lbd4b5635xA7 | FIRST | OWN-MERIT rank 17.0 (score 0.4153874312308409) | strict criterion (column only, not a gate): FAIL - L6M ulcer -511 mean +1149 worst wk -15565 max DD -5156 NOT strict; L3M ulcer -676 mean +1061 worst wk -15565 max DD -5156 NOT strict | n/a | n/a | n/a | n/a |
| Ldae2fbc4xK7 | FIRST | OWN-MERIT rank 17.0 (score 0.4813580047901726) | strict criterion (column only, not a gate): FAIL - L6M ulcer +362 mean +2726 worst wk +1131 max DD -612 NOT strict; L3M ulcer +579 mean +1965 worst wk +1131 max DD -612 NOT strict | n/a | n/a | n/a | n/a |
| Leee81e35xA7 | FIRST | OWN-MERIT rank 18.0 (score 0.40966532712237425) | strict criterion (column only, not a gate): FAIL - L6M ulcer -992 mean +1085 worst wk +1572 max DD -1475 NOT strict; L3M ulcer -895 mean +1573 worst wk +1572 max DD -1475 NOT strict | n/a | n/a | n/a | n/a |
| Lddba3fabxK7 | FIRST | OWN-MERIT rank 18.0 (score 0.4674360665287113) | strict criterion (column only, not a gate): FAIL - L6M ulcer +768 mean +2112 worst wk -1718 max DD -2545 NOT strict; L3M ulcer +995 mean +2282 worst wk -1718 max DD -2545 NOT strict | n/a | n/a | n/a | n/a |
| Lcae177baxA7 | FIRST | OWN-MERIT rank 19.0 (score 0.40484639940234185) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1446 mean +400 worst wk -5456 max DD -6597 NOT strict; L3M ulcer +2130 mean +1078 worst wk -5456 max DD -6597 NOT strict | n/a | n/a | n/a | n/a |
| L33bc9e87xK7 | FIRST | OWN-MERIT rank 19.0 (score 0.46687984214416717) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1054 mean +2250 worst wk -5925 max DD -3637 NOT strict; L3M ulcer +1329 mean +2450 worst wk -5925 max DD -3637 NOT strict | n/a | n/a | n/a | n/a |
| Lc754cf58xA7 | FIRST | OWN-MERIT rank 20.0 (score 0.40215316476999013) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1233 mean -743 worst wk -1541 max DD -4487 NOT strict; L3M ulcer +1507 mean +10 worst wk -370 max DD -4487 NOT strict | n/a | n/a | n/a | n/a |
| Lee3f074exK7 | FIRST | OWN-MERIT rank 20.0 (score 0.4609082202628904) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2061 mean +3014 worst wk -9779 max DD -12747 NOT strict; L3M ulcer +3339 mean +2331 worst wk -9779 max DD -12747 NOT strict | n/a | n/a | n/a | n/a |
| Lcb276f27xA7 | FIRST | OWN-MERIT rank 21.0 (score 0.38148584550243286) | strict criterion (column only, not a gate): PASS - L6M ulcer -1146 mean +1567 worst wk +3471 max DD +1415 ok; L3M ulcer -811 mean +1085 worst wk +3471 max DD +1415 ok | n/a | n/a | n/a | n/a |
| L0e94fadexK7 | FIRST | OWN-MERIT rank 21.0 (score 0.4554116774975572) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1741 mean +1602 worst wk -2560 max DD -9826 NOT strict; L3M ulcer +2739 mean +1101 worst wk -2560 max DD -9826 NOT strict | n/a | n/a | n/a | n/a |
| L1756b913xA7 | FIRST | OWN-MERIT rank 22.0 (score 0.37967773072202926) | strict criterion (column only, not a gate): FAIL - L6M ulcer +567 mean +803 worst wk +1990 max DD -1437 NOT strict; L3M ulcer +596 mean +4391 worst wk +1990 max DD -1437 NOT strict | n/a | n/a | n/a | n/a |
| L12e67af0xK7 | FIRST | OWN-MERIT rank 22.0 (score 0.4429086329080398) | strict criterion (column only, not a gate): n/a - not DONE | n/a | n/a | n/a | n/a |
| L973b5c8axA7 | FIRST | OWN-MERIT rank 23.0 (score 0.3713834498614412) | strict criterion (column only, not a gate): FAIL - L6M ulcer +798 mean +533 worst wk -2114 max DD -4527 NOT strict; L3M ulcer +1267 mean +1382 worst wk -2114 max DD -4527 NOT strict | n/a | n/a | n/a | n/a |
| L11a12538xK7 | FIRST | OWN-MERIT rank 23.0 (score 0.4419591387086143) | strict criterion (column only, not a gate): FAIL - L6M ulcer +650 mean +2960 worst wk +1446 max DD -5881 NOT strict; L3M ulcer +1156 mean +3591 worst wk +1446 max DD -5881 NOT strict | n/a | n/a | n/a | n/a |
| L29b1bc3fxA7 | FIRST | OWN-MERIT rank 24.0 (score 0.3613019307683299) | strict criterion (column only, not a gate): FAIL - L6M ulcer +99 mean +770 worst wk -737 max DD -2723 NOT strict; L3M ulcer +581 mean +1940 worst wk -737 max DD -2723 NOT strict | n/a | n/a | n/a | n/a |
| Lf6becac4xK7 | FIRST | OWN-MERIT rank 24.0 (score -0.017409941217030482) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1565 mean +150 worst wk -6780 max DD -9158 NOT strict; L3M ulcer +1991 mean +995 worst wk -6780 max DD -9158 NOT strict | n/a | n/a | n/a | n/a |
| M7423c0d9xA7 | FIRST | OWN-MERIT rank 25.0 (score 0.3585228485442376) | strict criterion (column only, not a gate): FAIL - L6M ulcer -1263 mean +151 worst wk -10117 max DD -157 NOT strict; L3M ulcer -1470 mean +591 worst wk -10117 max DD -157 NOT strict | n/a | n/a | n/a | n/a |
| Le0d40091xK7 | FIRST | OWN-MERIT rank 25.0 (score 0.4259976837049936) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1210 mean +2380 worst wk -3130 max DD -7162 NOT strict; L3M ulcer +1816 mean +833 worst wk -3130 max DD -7162 NOT strict | n/a | n/a | n/a | n/a |
| La5b5d03axA7 | FIRST | OWN-MERIT rank 26.0 (score 0.34926460991473435) | strict criterion (column only, not a gate): PASS - L6M ulcer -1197 mean +1547 worst wk +3509 max DD +1430 ok; L3M ulcer -892 mean +1038 worst wk +3509 max DD +1430 ok | n/a | n/a | n/a | n/a |
| Ld37dea46xK7 | FIRST | OWN-MERIT rank 26.0 (score 0.4255191240208243) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1104 mean +1849 worst wk -5404 max DD -4565 NOT strict; L3M ulcer +1727 mean +1977 worst wk -5404 max DD -4565 NOT strict | n/a | n/a | n/a | n/a |
| L6cff0af0xA7 | FIRST | OWN-MERIT rank 27.0 (score 0.3483638662867898) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1472 mean +455 worst wk -9001 max DD -3555 NOT strict; L3M ulcer +2341 mean +1157 worst wk -9001 max DD -3555 NOT strict | n/a | n/a | n/a | n/a |
| L1b44d5f3xK7 | FIRST | OWN-MERIT rank 27.0 (score 0.41880488141354294) | strict criterion (column only, not a gate): FAIL - L6M ulcer +859 mean +1797 worst wk -2396 max DD -3404 NOT strict; L3M ulcer +1123 mean +2192 worst wk -2396 max DD -3404 NOT strict | n/a | n/a | n/a | n/a |
| L2ccc12bfxA7 | FIRST | OWN-MERIT rank 28.0 (score 0.3411052281038711) | strict criterion (column only, not a gate): FAIL - L6M ulcer +440 mean +177 worst wk -2246 max DD -1121 NOT strict; L3M ulcer +424 mean +1918 worst wk -2246 max DD -1121 NOT strict | n/a | n/a | n/a | n/a |
| L34d66961xK7 | FIRST | OWN-MERIT rank 28.0 (score 0.4161058587997617) | strict criterion (column only, not a gate): FAIL - L6M ulcer -86 mean +2540 worst wk -3700 max DD +2662 NOT strict; L3M ulcer -685 mean +2740 worst wk -3700 max DD +3072 NOT strict | n/a | n/a | n/a | n/a |
| Lb68a132dxA7 | FIRST | OWN-MERIT rank 29.0 (score 0.33994007971209445) | strict criterion (column only, not a gate): FAIL - L6M ulcer -325 mean +35 worst wk -982 max DD -14 NOT strict; L3M ulcer -399 mean +1508 worst wk -982 max DD -14 NOT strict | n/a | n/a | n/a | n/a |
| Ld5cdb3c6xK7 | FIRST | OWN-MERIT rank 29.0 (score 0.4058070454054776) | strict criterion (column only, not a gate): FAIL - L6M ulcer +716 mean +1544 worst wk -5684 max DD -1359 NOT strict; L3M ulcer +1067 mean +1426 worst wk -5684 max DD -1359 NOT strict | n/a | n/a | n/a | n/a |
| Lbe5ac95bxA7 | FIRST | OWN-MERIT rank 30.0 (score 0.3329952109219714) | strict criterion (column only, not a gate): FAIL - L6M ulcer +560 mean +291 worst wk +258 max DD -4449 NOT strict; L3M ulcer +1044 mean +1460 worst wk +258 max DD -4449 NOT strict | n/a | n/a | n/a | n/a |
| L06eab808xK7 | FIRST | OWN-MERIT rank 30.0 (score 0.40284308289326426) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1756 mean +1425 worst wk -2560 max DD -9826 NOT strict; L3M ulcer +2739 mean +1101 worst wk -2560 max DD -9826 NOT strict | n/a | n/a | n/a | n/a |
| L59536e17xA7 | FIRST | OWN-MERIT rank 31.0 (score 0.33269563805275976) | strict criterion (column only, not a gate): FAIL - L6M ulcer +621 mean +1477 worst wk -9160 max DD -4965 NOT strict; L3M ulcer +1436 mean +413 worst wk -9160 max DD -4965 NOT strict | n/a | n/a | n/a | n/a |
| L21f079b6xK7 | FIRST | OWN-MERIT rank 31.0 (score 0.3979540608919033) | strict criterion (column only, not a gate): FAIL - L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict | n/a | n/a | n/a | n/a |
| L81e89115xA7 | FIRST | OWN-MERIT rank 32.0 (score 0.3207592767265385) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1861 mean +117 worst wk -6077 max DD -8014 NOT strict; L3M ulcer +3111 mean +564 worst wk -6077 max DD -8014 NOT strict | n/a | n/a | n/a | n/a |
| L2393e6acxK7 | FIRST | OWN-MERIT rank 32.0 (score 0.391530423578674) | strict criterion (column only, not a gate): FAIL - L6M ulcer +975 mean +1044 worst wk -433 max DD -4105 NOT strict; L3M ulcer +1336 mean +974 worst wk -433 max DD -4105 NOT strict | n/a | n/a | n/a | n/a |
| L358e61bexA7 | FIRST | OWN-MERIT rank 33.0 (score 0.3205372240301783) | strict criterion (column only, not a gate): FAIL - L6M ulcer +697 mean +1156 worst wk -5020 max DD -8849 NOT strict; L3M ulcer +2096 mean -627 worst wk -5020 max DD -8849 NOT strict | n/a | n/a | n/a | n/a |
| L56a50dc8xK7 | FIRST | OWN-MERIT rank 33.0 (score 0.3911120832098903) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1610 mean +1805 worst wk -3913 max DD -8447 NOT strict; L3M ulcer +2499 mean +1014 worst wk -3913 max DD -8447 NOT strict | n/a | n/a | n/a | n/a |
| Lc44703e7xA7 | FIRST | OWN-MERIT rank 34.0 (score 0.31559207259846017) | strict criterion (column only, not a gate): FAIL - L6M ulcer +362 mean +1467 worst wk -4318 max DD -5148 NOT strict; L3M ulcer +972 mean +3375 worst wk -4318 max DD -5148 NOT strict | n/a | n/a | n/a | n/a |
| L7678a6c4xK7 | FIRST | OWN-MERIT rank 34.0 (score 0.37767610883067076) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1170 mean +2643 worst wk -263 max DD -6553 NOT strict; L3M ulcer +1766 mean +1861 worst wk -263 max DD -6553 NOT strict | n/a | n/a | n/a | n/a |
| L4d206c8cxA7 | FIRST | OWN-MERIT rank 35.0 (score 0.31075413134502095) | strict criterion (column only, not a gate): FAIL - L6M ulcer -164 mean +834 worst wk +2169 max DD -1938 NOT strict; L3M ulcer -254 mean +664 worst wk +2169 max DD -1938 NOT strict | n/a | n/a | n/a | n/a |
| L0dc67ba7xK7 | FIRST | OWN-MERIT rank 35.0 (score 0.3775099900449968) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1082 mean +1825 worst wk -5260 max DD -937 NOT strict; L3M ulcer +1249 mean +1475 worst wk -5260 max DD -937 NOT strict | n/a | n/a | n/a | n/a |
| L023ff9ffxA7 | FIRST | OWN-MERIT rank 36.0 (score 0.30565496083535704) | strict criterion (column only, not a gate): FAIL - L6M ulcer -252 mean +1064 worst wk +1744 max DD -1372 NOT strict; L3M ulcer -278 mean +3269 worst wk +3429 max DD -1372 NOT strict | n/a | n/a | n/a | n/a |
| L9e98b767xK7 | FIRST | OWN-MERIT rank 36.0 (score 0.3723670310574653) | strict criterion (column only, not a gate): FAIL - L6M ulcer +895 mean +2131 worst wk -2697 max DD -538 NOT strict; L3M ulcer +861 mean +2194 worst wk -2697 max DD -526 NOT strict | n/a | n/a | n/a | n/a |
| L7a477a4axA7 | FIRST | OWN-MERIT rank 37.0 (score 0.3034624549598965) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1059 mean +702 worst wk -13006 max DD -5407 NOT strict; L3M ulcer +901 mean +333 worst wk -1590 max DD -5407 NOT strict | n/a | n/a | n/a | n/a |
| Lfe9994ffxK7 | FIRST | OWN-MERIT rank 37.0 (score 0.367981546438227) | strict criterion (column only, not a gate): FAIL - L6M ulcer +269 mean +2186 worst wk -3585 max DD +941 NOT strict; L3M ulcer -87 mean +2466 worst wk -3405 max DD +941 NOT strict | n/a | n/a | n/a | n/a |
| Mcee3865cxA7 | FIRST | OWN-MERIT rank 38.0 (score 0.303040336687815) | strict criterion (column only, not a gate): FAIL - L6M ulcer +530 mean -378 worst wk -7316 max DD -4374 NOT strict; L3M ulcer +1378 mean +246 worst wk -7316 max DD -4374 NOT strict | n/a | n/a | n/a | n/a |
| L3bbe44f5xK7 | FIRST | OWN-MERIT rank 38.0 (score 0.3574469340078878) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1893 mean +1115 worst wk -6396 max DD -9938 NOT strict; L3M ulcer +3015 mean +1008 worst wk -6396 max DD -9938 NOT strict | n/a | n/a | n/a | n/a |
| L3ee2d289xA7 | FIRST | OWN-MERIT rank 39.0 (score 0.2988151571608225) | strict criterion (column only, not a gate): FAIL - L6M ulcer -307 mean +633 worst wk -86 max DD +1535 NOT strict; L3M ulcer -414 mean +2184 worst wk -86 max DD +1535 NOT strict | n/a | n/a | n/a | n/a |
| Lc9217645xK7 | FIRST | OWN-MERIT rank 39.0 (score 0.35527092507784086) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1229 mean +1999 worst wk -6870 max DD -4582 NOT strict; L3M ulcer +1565 mean +2049 worst wk -6870 max DD -4582 NOT strict | n/a | n/a | n/a | n/a |
| M3f6f752cxA7 | FIRST | OWN-MERIT rank 40.0 (score 0.29557155011191016) | strict criterion (column only, not a gate): FAIL - L6M ulcer -385 mean -331 worst wk -1346 max DD -568 NOT strict; L3M ulcer -321 mean +1084 worst wk -1346 max DD -568 NOT strict | n/a | n/a | n/a | n/a |
| L92e46167xK7 | FIRST | OWN-MERIT rank 40.0 (score 0.3548581541729466) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1787 mean +1987 worst wk -5970 max DD -10687 NOT strict; L3M ulcer +2954 mean +851 worst wk -5970 max DD -10687 NOT strict | n/a | n/a | n/a | n/a |
| L5c9e11b3xA7 | FIRST | OWN-MERIT rank 41.0 (score 0.29491743031450207) | strict criterion (column only, not a gate): PASS - L6M ulcer -603 mean +1062 worst wk +3289 max DD +4781 ok; L3M ulcer -1151 mean +3460 worst wk +3289 max DD +4781 ok | n/a | n/a | n/a | n/a |
| L1ba33a2bxK7 | FIRST | OWN-MERIT rank 41.0 (score 0.35308690533949966) | strict criterion (column only, not a gate): FAIL - L6M ulcer +555 mean +1717 worst wk -705 max DD -1068 NOT strict; L3M ulcer +857 mean +1648 worst wk -705 max DD -1068 NOT strict | n/a | n/a | n/a | n/a |
| Md2a3a7d6xA7 | FIRST | OWN-MERIT rank 42.0 (score 0.2946106908599057) | strict criterion (column only, not a gate): FAIL - L6M ulcer -264 mean -642 worst wk -4180 max DD -1113 NOT strict; L3M ulcer +66 mean +274 worst wk -4180 max DD -1113 NOT strict | n/a | n/a | n/a | n/a |
| La62168e0xK7 | FIRST | OWN-MERIT rank 42.0 (score 0.3524590530284324) | strict criterion (column only, not a gate): FAIL - L6M ulcer +35 mean +2301 worst wk -3570 max DD +1857 NOT strict; L3M ulcer -508 mean +2315 worst wk -3060 max DD +2291 NOT strict | n/a | n/a | n/a | n/a |
| L00391b70xA7 | FIRST | OWN-MERIT rank 43.0 (score 0.29299830756413003) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2404 mean +781 worst wk -8186 max DD -17478 NOT strict; L3M ulcer +4415 mean -431 worst wk -8186 max DD -17478 NOT strict | n/a | n/a | n/a | n/a |
| L1af20032xK7 | FIRST | OWN-MERIT rank 43.0 (score 0.3502006641409061) | strict criterion (column only, not a gate): FAIL - L6M ulcer +361 mean +1842 worst wk -3010 max DD +1537 NOT strict; L3M ulcer +107 mean +2626 worst wk +690 max DD +1537 NOT strict | n/a | n/a | n/a | n/a |
| L2d89766exA7 | FIRST | OWN-MERIT rank 44.0 (score 0.29068037123969603) | strict criterion (column only, not a gate): FAIL - L6M ulcer +605 mean -278 worst wk -3787 max DD -2376 NOT strict; L3M ulcer +1325 mean +798 worst wk -3787 max DD -2376 NOT strict | n/a | n/a | n/a | n/a |
| L6be98834xK7 | FIRST | OWN-MERIT rank 44.0 (score 0.3485805255838504) | strict criterion (column only, not a gate): FAIL - L6M ulcer +409 mean +2335 worst wk -3815 max DD +996 NOT strict; L3M ulcer +148 mean +1607 worst wk -3080 max DD +996 NOT strict | n/a | n/a | n/a | n/a |
| Lb2f695b9xA7 | FIRST | OWN-MERIT rank 45.0 (score 0.28712663710704545) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1370 mean +302 worst wk -4436 max DD -10285 NOT strict; L3M ulcer +2327 mean +209 worst wk -4436 max DD -10285 NOT strict | n/a | n/a | n/a | n/a |
| L5ccb2d77xK7 | FIRST | OWN-MERIT rank 45.0 (score 0.34558500107323875) | strict criterion (column only, not a gate): FAIL - L6M ulcer +776 mean +2622 worst wk -2808 max DD -1849 NOT strict; L3M ulcer +1389 mean +1802 worst wk -2808 max DD -1849 NOT strict | n/a | n/a | n/a | n/a |
| L8c18be1cxA7 | FIRST | OWN-MERIT rank 46.0 (score 0.2812697368454018) | strict criterion (column only, not a gate): FAIL - L6M ulcer +76 mean -1142 worst wk -2340 max DD -4343 NOT strict; L3M ulcer +838 mean -1782 worst wk -2340 max DD -4343 NOT strict | n/a | n/a | n/a | n/a |
| L79cd626bxK7 | FIRST | OWN-MERIT rank 46.0 (score 0.34525742527484304) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1013 mean +1797 worst wk -6540 max DD -4437 NOT strict; L3M ulcer +1212 mean +2530 worst wk -6540 max DD -4437 NOT strict | n/a | n/a | n/a | n/a |
| Lb0bab78fxA7 | FIRST | OWN-MERIT rank 47.0 (score 0.2787143791118344) | strict criterion (column only, not a gate): FAIL - L6M ulcer -488 mean -207 worst wk -229 max DD -1611 NOT strict; L3M ulcer -70 mean +327 worst wk -229 max DD -1611 NOT strict | n/a | n/a | n/a | n/a |
| L15a07e54xK7 | FIRST | OWN-MERIT rank 47.0 (score 0.3449796156520747) | strict criterion (column only, not a gate): FAIL - L6M ulcer +644 mean +1360 worst wk -2270 max DD -2865 NOT strict; L3M ulcer +672 mean +489 worst wk -1495 max DD -2865 NOT strict | n/a | n/a | n/a | n/a |
| Le50c8ff3xA7 | FIRST | OWN-MERIT rank 48.0 (score 0.27545582403649305) | strict criterion (column only, not a gate): FAIL - L6M ulcer +359 mean +1054 worst wk -3396 max DD -4276 NOT strict; L3M ulcer +863 mean +377 worst wk -3396 max DD -4276 NOT strict | n/a | n/a | n/a | n/a |
| L082c912dxK7 | FIRST | OWN-MERIT rank 48.0 (score 0.3429347749935375) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2381 mean +2736 worst wk -7720 max DD -12802 NOT strict; L3M ulcer +3910 mean +1005 worst wk -7720 max DD -12802 NOT strict | n/a | n/a | n/a | n/a |
| Mac97d189xA7 | FIRST | OWN-MERIT rank 49.0 (score 0.2698116375544272) | strict criterion (column only, not a gate): FAIL - L6M ulcer -320 mean +102 worst wk -5785 max DD -872 NOT strict; L3M ulcer +67 mean +629 worst wk -5785 max DD -872 NOT strict | n/a | n/a | n/a | n/a |
| L3ab0746cxK7 | FIRST | OWN-MERIT rank 49.0 (score 0.3429225321442264) | strict criterion (column only, not a gate): FAIL - L6M ulcer +716 mean +1541 worst wk -4285 max DD -4276 NOT strict; L3M ulcer +1096 mean +1960 worst wk -4285 max DD -4276 NOT strict | n/a | n/a | n/a | n/a |
| L85abf719xA7 | FIRST | OWN-MERIT rank 50.0 (score 0.26603914469679957) | strict criterion (column only, not a gate): FAIL - L6M ulcer -217 mean -1155 worst wk -2190 max DD -1899 NOT strict; L3M ulcer +365 mean -1709 worst wk -2190 max DD -1899 NOT strict | n/a | n/a | n/a | n/a |
| L5e9c702bxK7 | FIRST | OWN-MERIT rank 50.0 (score 0.341182528776662) | strict criterion (column only, not a gate): FAIL - L6M ulcer +866 mean +2154 worst wk -4825 max DD -2470 NOT strict; L3M ulcer +1237 mean +2540 worst wk -4825 max DD -2470 NOT strict | n/a | n/a | n/a | n/a |
| L54f4c7dfxA7 | FIRST | OWN-MERIT rank 51.0 (score 0.26503441181236026) | strict criterion (column only, not a gate): FAIL - L6M ulcer +682 mean +1407 worst wk -2986 max DD -8589 NOT strict; L3M ulcer +1897 mean +1602 worst wk -2986 max DD -8589 NOT strict | n/a | n/a | n/a | n/a |
| Lcb97bb95xK7 | FIRST | OWN-MERIT rank 51.0 (score 0.33811080711035524) | strict criterion (column only, not a gate): FAIL - L6M ulcer +397 mean +2143 worst wk -3130 max DD -2449 NOT strict; L3M ulcer +554 mean +2238 worst wk -3130 max DD -2449 NOT strict | n/a | n/a | n/a | n/a |
| L7c4a36abxA7 | FIRST | OWN-MERIT rank 52.0 (score 0.26458861055985666) | strict criterion (column only, not a gate): FAIL - L6M ulcer +696 mean +267 worst wk -4487 max DD -5851 NOT strict; L3M ulcer +858 mean +1161 worst wk -4487 max DD -5851 NOT strict | n/a | n/a | n/a | n/a |
| Lfa8c13c0xK7 | FIRST | OWN-MERIT rank 52.0 (score 0.3254150657461218) | strict criterion (column only, not a gate): FAIL - L6M ulcer +266 mean +2264 worst wk -4905 max DD +952 NOT strict; L3M ulcer +272 mean +2381 worst wk -4905 max DD +952 NOT strict | n/a | n/a | n/a | n/a |
| L252e1154xA7 | FIRST | OWN-MERIT rank 53.0 (score 0.263390518108737) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1855 mean -112 worst wk -4285 max DD -11163 NOT strict; L3M ulcer +2795 mean +1698 worst wk -4285 max DD -11163 NOT strict | n/a | n/a | n/a | n/a |
| L9c7289bdxK7 | FIRST | OWN-MERIT rank 53.0 (score 0.32391760779312007) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1125 mean +1417 worst wk -4905 max DD -3779 NOT strict; L3M ulcer +1153 mean +2391 worst wk -3400 max DD -3779 NOT strict | n/a | n/a | n/a | n/a |
| L9b2dd5a0xA7 | FIRST | OWN-MERIT rank 54.0 (score 0.262709421385512) | strict criterion (column only, not a gate): FAIL - L6M ulcer -719 mean +1836 worst wk -2975 max DD +3933 NOT strict; L3M ulcer -971 mean +1301 worst wk -2975 max DD +3933 NOT strict | n/a | n/a | n/a | n/a |
| Lb939a293xK7 | FIRST | OWN-MERIT rank 54.0 (score 0.32380380976972084) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1039 mean +774 worst wk -4059 max DD -4015 NOT strict; L3M ulcer +1342 mean +937 worst wk -4059 max DD -4015 NOT strict | n/a | n/a | n/a | n/a |
| L05e7379bxA7 | FIRST | OWN-MERIT rank 55.0 (score 0.26152920406126584) | strict criterion (column only, not a gate): FAIL - L6M ulcer +589 mean +1636 worst wk -9135 max DD -4865 NOT strict; L3M ulcer +1394 mean +416 worst wk -9135 max DD -4865 NOT strict | n/a | n/a | n/a | n/a |
| Lb66c583exK7 | FIRST | OWN-MERIT rank 55.0 (score 0.32097406927096866) | strict criterion (column only, not a gate): FAIL - L6M ulcer +126 mean +2222 worst wk -3780 max DD +1857 NOT strict; L3M ulcer -446 mean +2312 worst wk -3000 max DD +2276 NOT strict | n/a | n/a | n/a | n/a |
| L26b8e434xA7 | FIRST | OWN-MERIT rank 56.0 (score 0.2612284962318172) | strict criterion (column only, not a gate): FAIL - L6M ulcer -431 mean -406 worst wk -7141 max DD -2404 NOT strict; L3M ulcer -973 mean +981 worst wk -7141 max DD -2404 NOT strict | n/a | n/a | n/a | n/a |
| Ldcfbef89xK7 | FIRST | OWN-MERIT rank 56.0 (score 0.316909723702875) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1363 mean +1861 worst wk -4760 max DD -9339 NOT strict; L3M ulcer +2166 mean +1740 worst wk -4760 max DD -9339 NOT strict | n/a | n/a | n/a | n/a |
| M72e48d4axA7 | FIRST | OWN-MERIT rank 57.0 (score 0.25906132092139483) | strict criterion (column only, not a gate): FAIL - L6M ulcer -313 mean -549 worst wk -4665 max DD -1687 NOT strict; L3M ulcer -68 mean +761 worst wk -4665 max DD -1687 NOT strict | n/a | n/a | n/a | n/a |
| L19abb182xK7 | FIRST | OWN-MERIT rank 57.0 (score 0.31180419206341314) | strict criterion (column only, not a gate): FAIL - L6M ulcer +413 mean +2434 worst wk +1007 max DD -972 NOT strict; L3M ulcer +541 mean +2017 worst wk +2066 max DD -972 NOT strict | n/a | n/a | n/a | n/a |
| M7cd27a3dxA7 | FIRST | OWN-MERIT rank 58.0 (score 0.258513049908933) | strict criterion (column only, not a gate): FAIL - L6M ulcer -227 mean -756 worst wk -4140 max DD -1108 NOT strict; L3M ulcer +141 mean +122 worst wk -4140 max DD -1108 NOT strict | n/a | n/a | n/a | n/a |
| L3c6da67fxK7 | FIRST | OWN-MERIT rank 58.0 (score 0.30625047231875635) | strict criterion (column only, not a gate): FAIL - L6M ulcer +494 mean +1431 worst wk -2650 max DD -3220 NOT strict; L3M ulcer +811 mean +1481 worst wk -2650 max DD -3220 NOT strict | n/a | n/a | n/a | n/a |
| L4f7bebffxA7 | FIRST | OWN-MERIT rank 59.0 (score 0.25523473470206604) | strict criterion (column only, not a gate): FAIL - L6M ulcer +886 mean +793 worst wk +565 max DD -5059 NOT strict; L3M ulcer +1732 mean +544 worst wk +565 max DD -5059 NOT strict | n/a | n/a | n/a | n/a |
| L0f98a9afxK7 | FIRST | OWN-MERIT rank 59.0 (score 0.30260458283177266) | strict criterion (column only, not a gate): FAIL - L6M ulcer +307 mean +2330 worst wk -3935 max DD -627 NOT strict; L3M ulcer +469 mean +2811 worst wk -3935 max DD -627 NOT strict | n/a | n/a | n/a | n/a |
| L46925cebxK7 | FIRST | OWN-MERIT rank 60.0 (score 0.3009967573020707) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2299 mean +2675 worst wk -2863 max DD -11830 NOT strict; L3M ulcer +3816 mean +528 worst wk -2863 max DD -11830 NOT strict | n/a | n/a | n/a | n/a |
| Ld6f168f8xA7 | FIRST | OWN-MERIT rank 61.0 (score 0.24972880186168672) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2220 mean -346 worst wk -10449 max DD -12342 NOT strict; L3M ulcer +3849 mean +745 worst wk -10449 max DD -12342 NOT strict | n/a | n/a | n/a | n/a |
| Le4fede95xK7 | FIRST | OWN-MERIT rank 61.0 (score 0.3007572228773432) | strict criterion (column only, not a gate): FAIL - L6M ulcer +171 mean +1765 worst wk +2078 max DD +1070 NOT strict; L3M ulcer +133 mean +2598 worst wk +2078 max DD +1069 NOT strict | n/a | n/a | n/a | n/a |
| M05838df6xA7 | FIRST | OWN-MERIT rank 62.0 (score 0.24936537815538654) | strict criterion (column only, not a gate): FAIL - L6M ulcer -715 mean +449 worst wk -2135 max DD +1772 NOT strict; L3M ulcer -618 mean +327 worst wk -2135 max DD +1772 NOT strict | n/a | n/a | n/a | n/a |
| Lba92ea98xK7 | FIRST | OWN-MERIT rank 62.0 (score 0.2966155845872248) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1907 mean +1846 worst wk -4873 max DD -9327 NOT strict; L3M ulcer +3103 mean +560 worst wk -4873 max DD -9327 NOT strict | n/a | n/a | n/a | n/a |
| Lf20f58a0xA7 | FIRST | OWN-MERIT rank 63.0 (score 0.24690964011715938) | strict criterion (column only, not a gate): FAIL - L6M ulcer +651 mean -1051 worst wk -5047 max DD +1639 NOT strict; L3M ulcer -238 mean +202 worst wk -584 max DD +1639 NOT strict | n/a | n/a | n/a | n/a |
| L94b48ae1xK7 | FIRST | OWN-MERIT rank 63.0 (score 0.29351882369063786) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2324 mean +1709 worst wk -4883 max DD -10784 NOT strict; L3M ulcer +3565 mean +1156 worst wk -4883 max DD -10784 NOT strict | n/a | n/a | n/a | n/a |
| Lbbb442f8xA7 | FIRST | OWN-MERIT rank 64.0 (score 0.24338851872772127) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2013 mean -950 worst wk -11586 max DD -5515 NOT strict; L3M ulcer +2067 mean -70 worst wk +183 max DD -5515 NOT strict | n/a | n/a | n/a | n/a |
| L8e5a7466xK7 | FIRST | OWN-MERIT rank 64.0 (score 0.29037530882121115) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1611 mean +928 worst wk -5116 max DD -8959 NOT strict; L3M ulcer +2502 mean +596 worst wk -5116 max DD -8959 NOT strict | n/a | n/a | n/a | n/a |
| Lde4f100bxA7 | FIRST | OWN-MERIT rank 65.0 (score 0.24184272164544224) | strict criterion (column only, not a gate): FAIL - L6M ulcer +133 mean +516 worst wk -2057 max DD +406 NOT strict; L3M ulcer -218 mean +2197 worst wk +773 max DD +406 ok | n/a | n/a | n/a | n/a |
| L4a797fb6xK7 | FIRST | OWN-MERIT rank 65.0 (score 0.2872506834763638) | strict criterion (column only, not a gate): n/a - not DONE | n/a | n/a | n/a | n/a |
| L31f57f58xA7 | FIRST | OWN-MERIT rank 66.0 (score 0.2399729843792461) | strict criterion (column only, not a gate): FAIL - L6M ulcer +211 mean +323 worst wk -256 max DD -1288 NOT strict; L3M ulcer +391 mean -583 worst wk -256 max DD -1288 NOT strict | n/a | n/a | n/a | n/a |
| Laf0d78abxK7 | FIRST | OWN-MERIT rank 66.0 (score 0.2863496266933274) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1049 mean +1871 worst wk -1770 max DD -7835 NOT strict; L3M ulcer +1675 mean +2019 worst wk -1770 max DD -7835 NOT strict | n/a | n/a | n/a | n/a |
| L35596060xA7 | FIRST | OWN-MERIT rank 67.0 (score 0.2369134270330623) | strict criterion (column only, not a gate): FAIL - L6M ulcer +618 mean +314 worst wk -3234 max DD -5375 NOT strict; L3M ulcer +1034 mean +1251 worst wk -3234 max DD -5375 NOT strict | n/a | n/a | n/a | n/a |
| Lc5665194xK7 | FIRST | OWN-MERIT rank 67.0 (score 0.284638525715788) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2452 mean +1397 worst wk -6628 max DD -10430 NOT strict; L3M ulcer +3447 mean +101 worst wk -6628 max DD -10430 NOT strict | n/a | n/a | n/a | n/a |
| M040bca61xA7 | FIRST | OWN-MERIT rank 68.0 (score 0.23111165071905015) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1006 mean -791 worst wk -8352 max DD -5341 NOT strict; L3M ulcer +1585 mean -446 worst wk -8352 max DD -5341 NOT strict | n/a | n/a | n/a | n/a |
| Ld30932f7xK7 | FIRST | OWN-MERIT rank 68.0 (score 0.2843709058097329) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1802 mean +2161 worst wk -8184 max DD -8732 NOT strict; L3M ulcer +2674 mean +1049 worst wk -8184 max DD -8732 NOT strict | n/a | n/a | n/a | n/a |
| Lf77e374bxA7 | FIRST | OWN-MERIT rank 69.0 (score 0.22943333474447752) | strict criterion (column only, not a gate): PASS - L6M ulcer -403 mean +1440 worst wk +116 max DD +1728 ok; L3M ulcer -202 mean +2270 worst wk +116 max DD +1728 ok | n/a | n/a | n/a | n/a |
| Ld61ffe03xK7 | FIRST | OWN-MERIT rank 69.0 (score 0.28299833562937193) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1385 mean +1086 worst wk -4002 max DD -7405 NOT strict; L3M ulcer +2254 mean +1213 worst wk -4002 max DD -7405 NOT strict | n/a | n/a | n/a | n/a |
| M1525fc29xA7 | FIRST | OWN-MERIT rank 70.0 (score 0.22826411838956692) | strict criterion (column only, not a gate): FAIL - L6M ulcer +661 mean +342 worst wk -11294 max DD -6740 NOT strict; L3M ulcer +1772 mean -42 worst wk -11294 max DD -6740 NOT strict | n/a | n/a | n/a | n/a |
| L0f2d7c91xK7 | FIRST | OWN-MERIT rank 70.0 (score 0.2812087401679533) | strict criterion (column only, not a gate): n/a - not DONE | n/a | n/a | n/a | n/a |
| L4c9a1a50xA7 | FIRST | OWN-MERIT rank 71.0 (score 0.2274627041330824) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2151 mean -729 worst wk -5002 max DD -11102 NOT strict; L3M ulcer +3175 mean -1021 worst wk -5002 max DD -11102 NOT strict | n/a | n/a | n/a | n/a |
| L252a89c9xK7 | FIRST | OWN-MERIT rank 71.0 (score 0.2811387328183575) | strict criterion (column only, not a gate): FAIL - L6M ulcer +137 mean +2049 worst wk -1962 max DD -2585 NOT strict; L3M ulcer +180 mean +1276 worst wk -1962 max DD -2585 NOT strict | n/a | n/a | n/a | n/a |
| L8a2453c8xA7 | FIRST | OWN-MERIT rank 72.0 (score 0.22482232992944776) | strict criterion (column only, not a gate): FAIL - L6M ulcer +521 mean +89 worst wk -7231 max DD +1372 NOT strict; L3M ulcer -220 mean +1080 worst wk -6610 max DD +1372 NOT strict | n/a | n/a | n/a | n/a |
| Lf5c3d8edxK7 | FIRST | OWN-MERIT rank 72.0 (score 0.2799947572184834) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1129 mean +626 worst wk -4039 max DD -4160 NOT strict; L3M ulcer +1786 mean -24 worst wk -4039 max DD -4160 NOT strict | n/a | n/a | n/a | n/a |
| La6f6f7adxA7 | FIRST | OWN-MERIT rank 73.0 (score 0.22280121552746224) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2321 mean -475 worst wk -8927 max DD -10337 NOT strict; L3M ulcer +2553 mean +312 worst wk -8927 max DD -10337 NOT strict | n/a | n/a | n/a | n/a |
| Lf3ab2350xK7 | FIRST | OWN-MERIT rank 73.0 (score 0.2793009352172177) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1129 mean +2243 worst wk -1962 max DD -2958 NOT strict; L3M ulcer +1509 mean -33 worst wk -1962 max DD -2958 NOT strict | n/a | n/a | n/a | n/a |
| Lc7889984xA7 | FIRST | OWN-MERIT rank 74.0 (score 0.22236786000166822) | strict criterion (column only, not a gate): PASS - L6M ulcer -1168 mean +1490 worst wk +1343 max DD +3365 ok; L3M ulcer -1479 mean +2893 worst wk +1343 max DD +3365 ok | n/a | n/a | n/a | n/a |
| L69c2a000xK7 | FIRST | OWN-MERIT rank 74.0 (score 0.2754920017307358) | strict criterion (column only, not a gate): FAIL - L6M ulcer +476 mean +1545 worst wk -2955 max DD -493 NOT strict; L3M ulcer +624 mean +1718 worst wk -2955 max DD -493 NOT strict | n/a | n/a | n/a | n/a |
| M0303c2bfxA7 | FIRST | OWN-MERIT rank 75.0 (score 0.22224143280259237) | strict criterion (column only, not a gate): FAIL - L6M ulcer +216 mean -185 worst wk -10067 max DD -5069 NOT strict; L3M ulcer +854 mean +164 worst wk -10067 max DD -5069 NOT strict | n/a | n/a | n/a | n/a |
| L41724a15xK7 | FIRST | OWN-MERIT rank 75.0 (score 0.27417587403967764) | strict criterion (column only, not a gate): n/a - not DONE | n/a | n/a | n/a | n/a |
| L3743d6caxA7 | FIRST | OWN-MERIT rank 76.0 (score 0.2220269889804927) | strict criterion (column only, not a gate): FAIL - L6M ulcer +1240 mean +885 worst wk +352 max DD -9915 NOT strict; L3M ulcer +2478 mean +695 worst wk +352 max DD -9915 NOT strict | n/a | n/a | n/a | n/a |
| L11631333xK7 | FIRST | OWN-MERIT rank 76.0 (score 0.273645783474347) | strict criterion (column only, not a gate): FAIL - L6M ulcer +758 mean +1556 worst wk -6570 max DD -4545 NOT strict; L3M ulcer +1083 mean +2339 worst wk -6570 max DD -4545 NOT strict | n/a | n/a | n/a | n/a |
| M3a2258bdxA7 | FIRST | OWN-MERIT rank 77.0 (score 0.2219773844013615) | strict criterion (column only, not a gate): FAIL - L6M ulcer +559 mean +183 worst wk -8499 max DD -4746 NOT strict; L3M ulcer +1090 mean -613 worst wk -8499 max DD -4746 NOT strict | n/a | n/a | n/a | n/a |
| L8123d039xK7 | FIRST | OWN-MERIT rank 77.0 (score 0.27260054257687016) | strict criterion (column only, not a gate): FAIL - L6M ulcer +315 mean +2014 worst wk -3000 max DD -796 NOT strict; L3M ulcer +217 mean +2347 worst wk -3000 max DD -796 NOT strict | n/a | n/a | n/a | n/a |
| L1a4596eexA7 | FIRST | OWN-MERIT rank 78.0 (score 0.22169651583301422) | strict criterion (column only, not a gate): FAIL - L6M ulcer +470 mean -1478 worst wk -5417 max DD -5080 NOT strict; L3M ulcer +317 mean +1208 worst wk -5417 max DD -5080 NOT strict | n/a | n/a | n/a | n/a |
| M7444c588xA7 | FIRST | OWN-MERIT rank 79.0 (score 0.22117854466774753) | strict criterion (column only, not a gate): FAIL - L6M ulcer -573 mean +695 worst wk -6845 max DD +868 NOT strict; L3M ulcer -429 mean +1201 worst wk -6845 max DD +868 NOT strict | n/a | n/a | n/a | n/a |
| L7f91b649xK7 | FIRST | OWN-MERIT rank 79.0 (score 0.2706789068844912) | strict criterion (column only, not a gate): FAIL - L6M ulcer +2669 mean +2152 worst wk -7665 max DD -14015 NOT strict; L3M ulcer +4251 mean +1152 worst wk -7665 max DD -14015 NOT strict | n/a | n/a | n/a | n/a |
| L345e7019xA7 | FIRST | OWN-MERIT rank 80.0 (score 0.21881653192080014) | strict criterion (column only, not a gate): FAIL - L6M ulcer +645 mean +315 worst wk -6504 max DD -683 NOT strict; L3M ulcer +1510 mean +692 worst wk -6504 max DD -683 NOT strict | n/a | n/a | n/a | n/a |
| L59efe6b3xK7 | FIRST | OWN-MERIT rank 80.0 (score 0.27054791071204837) | strict criterion (column only, not a gate): n/a - not DONE | n/a | n/a | n/a | n/a |
| M028d0c03xA7 | FIRST | OWN-MERIT rank 81.0 (score 0.21790494390427279) | strict criterion (column only, not a gate): FAIL - L6M ulcer -509 mean -535 worst wk -2486 max DD +2014 NOT strict; L3M ulcer -668 mean +704 worst wk -2486 max DD +2014 NOT strict | n/a | n/a | n/a | n/a |
| L1ef22fa7xK7 | FIRST | OWN-MERIT rank 81.0 (score 0.26949256403787414) | strict criterion (column only, not a gate): n/a - not DONE | n/a | n/a | n/a | n/a |
| L3c4f3969xA7 | FIRST | OWN-MERIT rank 82.0 (score 0.21732972017052618) | strict criterion (column only, not a gate): FAIL - L6M ulcer +640 mean +337 worst wk -6529 max DD -784 NOT strict; L3M ulcer +1518 mean +637 worst wk -6529 max DD -784 NOT strict | n/a | n/a | n/a | n/a |
| L598ad596xA7 | FIRST | OWN-MERIT rank 83.0 (score 0.21712751116807388) | strict criterion (column only, not a gate): FAIL - L6M ulcer +347 mean -548 worst wk -812 max DD -1930 NOT strict; L3M ulcer -188 mean +1566 worst wk -812 max DD -1930 NOT strict | n/a | n/a | n/a | n/a |
| L0a809c2exA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| M05ab6fe0xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L3ec39f56xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L63ff9ae8xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| M32bddb74xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L17ce266fxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L5d9e7166xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L05222ff9xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| M15f14debxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L411f8593xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L0509f37cxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L32db3e8bxA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L0b1d7882xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| Lb7ac1fa5xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| Mc817d9e3xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| L30aad100xA7 | 2 | reference / pending: not on W-ASIA's REPLACE pass list (pass_replace.json); REPLACE ONLY (order 1407Z): nothing started, lines wait behind the Asia ladder | n/a | n/a | n/a | n/a |
| Le3193838xK7 | 2 | strict PASS but not gate pass yet: strict criterion computed by W-LAYERS (L6M ulcer -269 mean +2068 worst wk +396 max DD +4136 ok; L3M ulcer -349 mean +1697 worst wk +396 max DD +4136 ok) | B FAIL: RED in 2023 | +41% / +38% / +26% / +12% RED | +23% / +6% / +6% / -7% AMBER | +10% / +16% / +4% / -0% AMBER | 0.54 |
| L4560e541xK7 | 2 | strict PASS but not gate pass yet: strict criterion computed by W-LAYERS (L6M ulcer -207 mean +642 worst wk +1832 max DD +549 ok; L3M ulcer -334 mean +967 worst wk +1832 max DD +549 ok) | FAIL: engine persistence 0.507 < 0.58 (order 1324Z) | -15% / +1% / +16% / +15% AMBER | -2% / +1% / -6% / -5% GREEN | -7% / -9% / -0% / -3% GREEN | 0.51 |
| L9513708bxK7 | 2 | strict PASS but not gate pass yet: strict criterion computed by W-LAYERS (L6M ulcer -61 mean +1033 worst wk +45 max DD +1752 ok; L3M ulcer -316 mean +1518 worst wk +45 max DD +1825 ok) | FAIL: engine persistence 0.465 < 0.58 (order 1324Z) | +16% / +24% / +21% / +3% AMBER | -12% / -0% / +5% / -13% GREEN | +4% / -1% / -5% / +11% GREEN | 0.46 |
| Lac37d7ebxK7 | 2 | NOT first tier: strict criterion not available yet (strict criterion computed by W-LAYERS (not DONE)) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L5a49e86dxK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -418 mean +713 worst wk +2050 max DD -5582 NOT strict; L3M ulcer -1885 mean +3361 worst wk +4777 max DD +6800 ok) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L96205086xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -26 mean +1294 worst wk -1155 max DD +1427 NOT strict; L3M ulcer -460 mean +2376 worst wk +1815 max DD +1427 ok) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L7295a253xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -155 mean +1091 worst wk +705 max DD -1391 NOT strict; L3M ulcer -197 mean +1845 worst wk +705 max DD -1391 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L09ae66e3xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -178 mean +919 worst wk -1005 max DD +1164 NOT strict; L3M ulcer -620 mean +1301 worst wk -1005 max DD +1164 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L0f097450xK7LO | 3 | NOT first tier: strict criterion FAIL - W-NYENG strict table | FAIL: engine persistence 0.563 < 0.58 (order 1324Z) | -14% / +3% / +22% / +2% AMBER | -8% / -2% / -3% / -15% GREEN | +11% / +10% / +15% / +12% GREEN | 0.56 |
| Lf967df3bxK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| Lbbb39855xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| L0bd23639xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | B FAIL: RED in 2023 | -9% / +9% / +31% / +7% RED | -7% / -14% / +2% / -13% GREEN | -17% / -18% / -20% / +2% GREEN | 0.61 |
| L77a763afxK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| Le728b0a3xK7 | 3 | NOT first tier: strict criterion FAIL - strict criterion computed by W-LAYERS (L6M ulcer -58 mean +2291 worst wk -3120 max DD +1857 NOT strict; L3M ulcer -504 mean +2902 worst wk -3120 max DD +2281 NOT strict) | pending: no engine prior year landed yet | n/a | n/a | n/a | n/a |
| L0f097450xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L3701b464xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L3701b464xK7LO | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| M41ef5c77xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Mdcdb0b6exA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Mac4916e6xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| M98c7ae1dxA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L34e2c5abxA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lb5e883f6xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| La4bf1d85xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L8fbea98exA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L798a7cc7xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L45cf0183xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L0b2562c4xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L5026acdcxA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Mb328c0d1xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L8e794e4dxA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L70969366xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| La4dd3ce9xA7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L2b25565axK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lc739d497xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L908c5381xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Ld45733dbxK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lf82cdf44xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lfa1de080xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L59b66d32xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L04aaa969xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L37c9625axK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lb92ba8f9xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L1d0ec711xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L4604d23bxK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L33d4983bxK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L3a102d84xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L1c19f73fxK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Ld14659a9xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L6dd56729xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Ld4b5bd12xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lea670f79xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Led06426axK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lca8ca9cbxK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Ld213a0b4xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lff43bc43xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L4702b598xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| Lce9be405xK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L8af7ec3fxK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L997f871exK7 | 3 | not in the current candidate list (superseded / demoted): queued after the Asia ladder | n/a | n/a | n/a | n/a |
| L01811caa | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L6a25b155 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L0f097450 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Lda55d973 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| M41ef5c77 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Mdcdb0b6e | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L4d206c8c | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Mac4916e6 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| M98c7ae1d | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L34e2c5ab | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| Lb5e883f6 | 9 | ADD-base programme PARKED (REPLACE ONLY, order 1407Z): lines moved to _layers/pending_parked_add.txt, not in QUEUES.txt; landed ADD results untouched | n/a | n/a | n/a | n/a |
| L96205086xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L01811caaxP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L5a49e86dxM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L6a25b155xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L96205086xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L5a49e86dxP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L6a25b155xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L01811caaxM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L6a25b155xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L34d66961xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L01811caaxH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L11631333xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L96205086xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L5a49e86dxH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L34d66961xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L34d66961xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L59b66d32xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L6ff237d4xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L4fd10b76xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L11631333xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L4fd10b76xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L9f026abcxP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L9f026abcxM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L9f026abcxH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L0f097450xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L21f079b6xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lf967df3bxP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lbbb39855xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L0bd23639xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L77a763afxP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L0f097450xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L21f079b6xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lf967df3bxM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lbbb39855xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L0bd23639xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L77a763afxM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L09ae66e3xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L0f097450xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L21f079b6xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lf967df3bxH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lbbb39855xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L0bd23639xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L09ae66e3xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lbbdd1236xP7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L09ae66e3xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| Lbbdd1236xM7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |
| L4ed22711xH7 | 9 | PARKED: other-slot variant (same cell vs another live book) - order 1806Z own-merit: the book's own first form is REPLACE-K7 / REPLACE-A7; layers are refitted jointly on the final stacks by W-COMBO | n/a | n/a | n/a | n/a |

## Identity (inert hook = base row, trade for trade)
- Asia: PASS 9/9 inert sets equal to TL3_ASI_Lda55d973_RA7 on 202610,202608 trade for trade
- NYAM: PASS 9/9 inert sets equal to TL3_NYE_L6a25b155_RK7 on 202610,202608 trade for trade
- NYAM-ADD: PASS 9/9 inert sets equal to TL3_NYW_L01811caa_ADD on 202610,202608 trade for trade
- Asia-ADD: PASS 9/9 inert sets equal to TL3_ASI_Lda55d973_ADD on 202610,202608 trade for trade

## Candidates
| label | session | replaced book | variant | layer base set (REPLACE = default; ADD only when the three-row rule picks it) | stage | fit sets | L6M scored | top-2 prior-year sets | joint sets |
|---|---|---|---|---|---|---|---|---|---|
| M05ab6fe0xA7 | Asia | A7 | long | TL3_ASI_M05ab6fe0_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lfea1c9fcxA7 | Asia | A7 | both | TL3_ASI_Lfea1c9fc_RA7 | fit queued | 72 | - | 0 | 0 |
| L0509f37cxA7 | Asia | A7 | both | TL3_ASI_L0509f37c_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Mc817d9e3xA7 | Asia | A7 | long | TL3_ASI_Mc817d9e3_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L3ec39f56xA7 | Asia | A7 | both | TL3_ASI_L3ec39f56_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0a809c2exA7 | Asia | A7 | both | TL3_ASI_L0a809c2e_RA7 | scored | 72 | 2026-11-19 13:55Z | 6 | 3 |
| L32db3e8bxA7 | Asia | A7 | both | TL3_ASI_L32db3e8b_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L17ce266fxA7 | Asia | A7 | both | TL3_ASI_L17ce266f_RA7 | scored | 72 | 2026-11-19 16:25Z | 6 | 3 |
| L5d9e7166xA7 | Asia | A7 | both | TL3_ASI_L5d9e7166_RA7 | scored | 72 | 2026-11-19 12:55Z | 6 | 3 |
| L05222ff9xA7 | Asia | A7 | both | TL3_ASI_L05222ff9_RA7 | scored | 72 | 2026-11-19 13:23Z | 7 | 5 |
| L63ff9ae8xA7 | Asia | A7 | both | TL3_ASI_L63ff9ae8_RA7 | scored | 72 | 2026-11-19 18:05Z | 7 | 5 |
| L30aad100xA7 | Asia | A7 | both | TL3_ASI_L30aad100_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| M15f14debxA7 | Asia | A7 | long | TL3_ASI_M15f14deb_RA7 | scored | 72 | 2026-11-19 17:45Z | 9 | 4 |
| M32bddb74xA7 | Asia | A7 | long | TL3_ASI_M32bddb74_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0b1d7882xA7 | Asia | A7 | both | TL3_ASI_L0b1d7882_RA7 | fit queued | 72 | - | 0 | 0 |
| L411f8593xA7 | Asia | A7 | both | TL3_ASI_L411f8593_RA7 | fit queued | 72 | - | 0 | 0 |
| Lb7ac1fa5xA7 | Asia | A7 | both | TL3_ASI_Lb7ac1fa5_RA7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Ldcdb0b6exA7 | Asia | A7 | both | TL3_ASI_Ldcdb0b6e_RA7 | scored | 58 | 2026-11-19 20:25Z | 0 | 7 |
| L86781ac0xA7 | Asia | A7 | both | TL3_ASI_L86781ac0_RA7 | fit queued | 58 | - | 0 | 0 |
| Lc4e74264xA7 | Asia | A7 | both | TL3_ASI_Lc4e74264_RA7 | fit queued | 58 | - | 0 | 0 |
| L7ea48296xA7 | Asia | A7 | both | TL3_ASI_L7ea48296_RA7 | fit queued | 58 | - | 0 | 0 |
| L548972b6xA7 | Asia | A7 | both | TL3_ASI_L548972b6_RA7 | fit queued | 58 | - | 0 | 0 |
| Lbe8a8e54xA7 | Asia | A7 | both | TL3_ASI_Lbe8a8e54_RA7 | new | 0 | - | 0 | 0 |
| L7c368a4fxA7 | Asia | A7 | both | TL3_ASI_L7c368a4f_RA7 | scored | 72 | 2026-11-19 18:05Z | 14 | 9 |
| L224050e7xA7 | Asia | A7 | both | TL3_ASI_L224050e7_RA7 | new | 0 | - | 0 | 0 |
| Lfb608c7bxA7 | Asia | A7 | both | TL3_ASI_Lfb608c7b_RA7 | new | 0 | - | 0 | 0 |
| L15f14debxA7 | Asia | A7 | both | TL3_ASI_L15f14deb_RA7 | new | 0 | - | 0 | 0 |
| Lda55d973xA7 | Asia | A7 | both | TL3_ASI_Lda55d973_RA7 | scored | 72 | 2026-11-19 14:07Z | 12 | 7 |
| L1edb9fabxA7 | Asia | A7 | both | TL3_ASI_L1edb9fab_RA7 | fit queued | 72 | - | 0 | 0 |
| Ledfbf4d2xA7 | Asia | A7 | both | TL3_ASI_Ledfbf4d2_RA7 | scored | 72 | 2026-11-19 13:05Z | 8 | 3 |
| L40bde9eaxA7 | Asia | A7 | both | TL3_ASI_L40bde9ea_RA7 | new | 0 | - | 0 | 0 |
| Lbd4b5635xA7 | Asia | A7 | both | TL3_ASI_Lbd4b5635_RA7 | new | 0 | - | 0 | 0 |
| Leee81e35xA7 | Asia | A7 | both | TL3_ASI_Leee81e35_RA7 | new | 0 | - | 0 | 0 |
| Lcae177baxA7 | Asia | A7 | both | TL3_ASI_Lcae177ba_RA7 | new | 0 | - | 0 | 0 |
| Lc754cf58xA7 | Asia | A7 | both | TL3_ASI_Lc754cf58_RA7 | new | 0 | - | 0 | 0 |
| Lcb276f27xA7 | Asia | A7 | both | TL3_ASI_Lcb276f27_RA7 | scored | 72 | 2026-11-19 18:05Z | 8 | 4 |
| L1756b913xA7 | Asia | A7 | both | TL3_ASI_L1756b913_RA7 | new | 0 | - | 0 | 0 |
| L973b5c8axA7 | Asia | A7 | both | TL3_ASI_L973b5c8a_RA7 | new | 0 | - | 0 | 0 |
| L29b1bc3fxA7 | Asia | A7 | both | TL3_ASI_L29b1bc3f_RA7 | new | 0 | - | 0 | 0 |
| M7423c0d9xA7 | Asia | A7 | long | TL3_ASI_M7423c0d9_RA7 | new | 0 | - | 0 | 0 |
| La5b5d03axA7 | Asia | A7 | both | TL3_ASI_La5b5d03a_RA7 | scored | 72 | 2026-11-19 16:45Z | 8 | 4 |
| L6cff0af0xA7 | Asia | A7 | both | TL3_ASI_L6cff0af0_RA7 | new | 0 | - | 0 | 0 |
| L2ccc12bfxA7 | Asia | A7 | both | TL3_ASI_L2ccc12bf_RA7 | new | 0 | - | 0 | 0 |
| Lb68a132dxA7 | Asia | A7 | both | TL3_ASI_Lb68a132d_RA7 | new | 0 | - | 0 | 0 |
| Lbe5ac95bxA7 | Asia | A7 | both | TL3_ASI_Lbe5ac95b_RA7 | new | 0 | - | 0 | 0 |
| L59536e17xA7 | Asia | A7 | both | TL3_ASI_L59536e17_RA7 | new | 0 | - | 0 | 0 |
| L81e89115xA7 | Asia | A7 | both | TL3_ASI_L81e89115_RA7 | new | 0 | - | 0 | 0 |
| L358e61bexA7 | Asia | A7 | both | TL3_ASI_L358e61be_RA7 | new | 0 | - | 0 | 0 |
| Lc44703e7xA7 | Asia | A7 | both | TL3_ASI_Lc44703e7_RA7 | new | 0 | - | 0 | 0 |
| L4d206c8cxA7 | Asia | A7 | both | TL3_ASI_L4d206c8c_RA7 | fit queued | 72 | - | 0 | 0 |
| L023ff9ffxA7 | Asia | A7 | both | TL3_ASI_L023ff9ff_RA7 | new | 0 | - | 0 | 0 |
| L7a477a4axA7 | Asia | A7 | both | TL3_ASI_L7a477a4a_RA7 | new | 0 | - | 0 | 0 |
| Mcee3865cxA7 | Asia | A7 | long | TL3_ASI_Mcee3865c_RA7 | new | 0 | - | 0 | 0 |
| L3ee2d289xA7 | Asia | A7 | both | TL3_ASI_L3ee2d289_RA7 | new | 0 | - | 0 | 0 |
| M3f6f752cxA7 | Asia | A7 | long | TL3_ASI_M3f6f752c_RA7 | new | 0 | - | 0 | 0 |
| L5c9e11b3xA7 | Asia | A7 | both | TL3_ASI_L5c9e11b3_RA7 | scored | 72 | 2026-11-19 12:55Z | 9 | 5 |
| Md2a3a7d6xA7 | Asia | A7 | long | TL3_ASI_Md2a3a7d6_RA7 | new | 0 | - | 0 | 0 |
| L00391b70xA7 | Asia | A7 | both | TL3_ASI_L00391b70_RA7 | new | 0 | - | 0 | 0 |
| L2d89766exA7 | Asia | A7 | both | TL3_ASI_L2d89766e_RA7 | new | 0 | - | 0 | 0 |
| Lb2f695b9xA7 | Asia | A7 | both | TL3_ASI_Lb2f695b9_RA7 | new | 0 | - | 0 | 0 |
| L8c18be1cxA7 | Asia | A7 | both | TL3_ASI_L8c18be1c_RA7 | new | 0 | - | 0 | 0 |
| Lb0bab78fxA7 | Asia | A7 | both | TL3_ASI_Lb0bab78f_RA7 | new | 0 | - | 0 | 0 |
| Le50c8ff3xA7 | Asia | A7 | both | TL3_ASI_Le50c8ff3_RA7 | new | 0 | - | 0 | 0 |
| Mac97d189xA7 | Asia | A7 | long | TL3_ASI_Mac97d189_RA7 | new | 0 | - | 0 | 0 |
| L85abf719xA7 | Asia | A7 | both | TL3_ASI_L85abf719_RA7 | new | 0 | - | 0 | 0 |
| L54f4c7dfxA7 | Asia | A7 | both | TL3_ASI_L54f4c7df_RA7 | new | 0 | - | 0 | 0 |
| L7c4a36abxA7 | Asia | A7 | both | TL3_ASI_L7c4a36ab_RA7 | new | 0 | - | 0 | 0 |
| L252e1154xA7 | Asia | A7 | both | TL3_ASI_L252e1154_RA7 | new | 0 | - | 0 | 0 |
| L9b2dd5a0xA7 | Asia | A7 | both | TL3_ASI_L9b2dd5a0_RA7 | new | 0 | - | 0 | 0 |
| L05e7379bxA7 | Asia | A7 | both | TL3_ASI_L05e7379b_RA7 | new | 0 | - | 0 | 0 |
| L26b8e434xA7 | Asia | A7 | both | TL3_ASI_L26b8e434_RA7 | new | 0 | - | 0 | 0 |
| M72e48d4axA7 | Asia | A7 | long | TL3_ASI_M72e48d4a_RA7 | new | 0 | - | 0 | 0 |
| M7cd27a3dxA7 | Asia | A7 | long | TL3_ASI_M7cd27a3d_RA7 | new | 0 | - | 0 | 0 |
| L4f7bebffxA7 | Asia | A7 | both | TL3_ASI_L4f7bebff_RA7 | new | 0 | - | 0 | 0 |
| Ld6f168f8xA7 | Asia | A7 | both | TL3_ASI_Ld6f168f8_RA7 | new | 0 | - | 0 | 0 |
| M05838df6xA7 | Asia | A7 | long | TL3_ASI_M05838df6_RA7 | new | 0 | - | 0 | 0 |
| Lf20f58a0xA7 | Asia | A7 | both | TL3_ASI_Lf20f58a0_RA7 | new | 0 | - | 0 | 0 |
| Lbbb442f8xA7 | Asia | A7 | both | TL3_ASI_Lbbb442f8_RA7 | new | 0 | - | 0 | 0 |
| Lde4f100bxA7 | Asia | A7 | both | TL3_ASI_Lde4f100b_RA7 | new | 0 | - | 0 | 0 |
| L31f57f58xA7 | Asia | A7 | both | TL3_ASI_L31f57f58_RA7 | new | 0 | - | 0 | 0 |
| L35596060xA7 | Asia | A7 | both | TL3_ASI_L35596060_RA7 | new | 0 | - | 0 | 0 |
| M040bca61xA7 | Asia | A7 | long | TL3_ASI_M040bca61_RA7 | new | 0 | - | 0 | 0 |
| Lf77e374bxA7 | Asia | A7 | both | TL3_ASI_Lf77e374b_RA7 | fit queued | 72 | - | 0 | 0 |
| M1525fc29xA7 | Asia | A7 | long | TL3_ASI_M1525fc29_RA7 | new | 0 | - | 0 | 0 |
| L4c9a1a50xA7 | Asia | A7 | both | TL3_ASI_L4c9a1a50_RA7 | new | 0 | - | 0 | 0 |
| L8a2453c8xA7 | Asia | A7 | both | TL3_ASI_L8a2453c8_RA7 | new | 0 | - | 0 | 0 |
| La6f6f7adxA7 | Asia | A7 | both | TL3_ASI_La6f6f7ad_RA7 | new | 0 | - | 0 | 0 |
| Lc7889984xA7 | Asia | A7 | both | TL3_ASI_Lc7889984_RA7 | new | 0 | - | 0 | 0 |
| M0303c2bfxA7 | Asia | A7 | long | TL3_ASI_M0303c2bf_RA7 | new | 0 | - | 0 | 0 |
| L3743d6caxA7 | Asia | A7 | both | TL3_ASI_L3743d6ca_RA7 | new | 0 | - | 0 | 0 |
| M3a2258bdxA7 | Asia | A7 | long | TL3_ASI_M3a2258bd_RA7 | new | 0 | - | 0 | 0 |
| L1a4596eexA7 | Asia | A7 | both | TL3_ASI_L1a4596ee_RA7 | new | 0 | - | 0 | 0 |
| M7444c588xA7 | Asia | A7 | long | TL3_ASI_M7444c588_RA7 | new | 0 | - | 0 | 0 |
| L345e7019xA7 | Asia | A7 | both | TL3_ASI_L345e7019_RA7 | new | 0 | - | 0 | 0 |
| M028d0c03xA7 | Asia | A7 | long | TL3_ASI_M028d0c03_RA7 | new | 0 | - | 0 | 0 |
| L3c4f3969xA7 | Asia | A7 | both | TL3_ASI_L3c4f3969_RA7 | new | 0 | - | 0 | 0 |
| L598ad596xA7 | Asia | A7 | both | TL3_ASI_L598ad596_RA7 | new | 0 | - | 0 | 0 |
| L6a25b155xK7 | NYAM | K7 | both | TL3_NYE_L6a25b155_RK7 | scored | 72 | 2026-11-19 12:55Z | 3 | 3 |
| L96205086xP7 | NYAM | P7 | both | TL3_NYE_L96205086_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Ld9ea2776xK7 | NYAM | K7 | both | TL3_NYE_Ld9ea2776_RK7 | new | 0 | - | 0 | 0 |
| Lb44a3e99xK7 | NYAM | K7 | both | TL3_NYE_Lb44a3e99_RK7 | fit queued | 58 | - | 0 | 0 |
| L01811caaxP7 | NYAM | P7 | both | TL3_NYE_L01811caa_RP7 | scored | 72 | 2026-11-19 15:55Z | 9 | 3 |
| L5a49e86dxM7 | NYAM | M7 | both | TL3_NYE_L5a49e86d_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L678ebaddxK7 | NYAM | K7 | both | TL3_NYE_L678ebadd_RK7 | fit queued | 58 | - | 0 | 0 |
| L01811caaxK7 | NYAM | K7 | both | TL3_NYE_L01811caa_RK7 | scored | 72 | 2026-11-19 12:45Z | 12 | 5 |
| L6a25b155xP7 | NYAM | P7 | both | TL3_NYE_L6a25b155_RP7 | fit queued | 72 | - | 0 | 0 |
| L96205086xM7 | NYAM | M7 | both | TL3_NYE_L96205086_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L5a49e86dxP7 | NYAM | P7 | both | TL3_NYE_L5a49e86d_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L6c84f416xK7 | NYAM | K7 | both | TL3_NYE_L6c84f416_RK7 | fit queued | 58 | - | 0 | 0 |
| L641a7c4dxK7 | NYAM | K7 | both | TL3_NYE_L641a7c4d_RK7 | fit queued | 58 | - | 0 | 0 |
| L6a25b155xM7 | NYAM | M7 | both | TL3_NYE_L6a25b155_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L2176f633xK7 | NYAM | K7 | both | TL3_NYE_L2176f633_RK7 | new | 0 | - | 0 | 0 |
| L01811caaxM7 | NYAM | M7 | both | TL3_NYE_L01811caa_RM7 | scored | 72 | 2026-11-19 16:15Z | 11 | 5 |
| L39470318xK7 | NYAM | K7 | both | TL3_NYE_L39470318_RK7 | new | 0 | - | 0 | 0 |
| L6a25b155xH7 | NYAM | H7 | both | TL3_NYE_L6a25b155_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L34d66961xP7 | NYAM | P7 | both | TL3_NYE_L34d66961_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L86efc549xK7 | NYAM | K7 | both | TL3_NYE_L86efc549_RK7 | new | 0 | - | 0 | 0 |
| L01811caaxH7 | NYAM | H7 | both | TL3_NYE_L01811caa_RH7 | scored | 72 | 2026-11-19 17:25Z | 9 | 4 |
| L4eba93d7xK7 | NYAM | K7 | both | TL3_NYE_L4eba93d7_RK7 | new | 0 | - | 0 | 0 |
| L5a49e86dxK7 | NYAM | K7 | both | TL3_NYE_L5a49e86d_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L2010fec9xK7 | NYAM | K7 | both | TL3_NYE_L2010fec9_RK7 | new | 0 | - | 0 | 0 |
| L11631333xP7 | NYAM | P7 | both | TL3_NYE_L11631333_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L582ae3cbxK7 | NYAM | K7 | both | TL3_NYE_L582ae3cb_RK7 | new | 0 | - | 0 | 0 |
| L96205086xH7 | NYAM | H7 | both | TL3_NYE_L96205086_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L03be4d27xK7 | NYAM | K7 | both | TL3_NYE_L03be4d27_RK7 | new | 0 | - | 0 | 0 |
| L2b8ccd55xK7 | NYAM | K7 | both | TL3_NYE_L2b8ccd55_RK7 | new | 0 | - | 0 | 0 |
| L96205086xK7 | NYAM | K7 | both | TL3_NYE_L96205086_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lc338b47bxK7 | NYAM | K7 | both | TL3_NYE_Lc338b47b_RK7 | new | 0 | - | 0 | 0 |
| L5a49e86dxH7 | NYAM | H7 | both | TL3_NYE_L5a49e86d_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L4ed22711xK7 | NYAM | K7 | both | TL3_NYE_L4ed22711_RK7 | new | 0 | - | 0 | 0 |
| L4fd10b76xK7 | NYAM | K7 | both | TL3_NYE_L4fd10b76_RK7 | new | 0 | - | 0 | 0 |
| L34d66961xM7 | NYAM | M7 | both | TL3_NYE_L34d66961_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Ldae2fbc4xK7 | NYAM | K7 | both | TL3_NYE_Ldae2fbc4_RK7 | new | 0 | - | 0 | 0 |
| L34d66961xH7 | NYAM | H7 | both | TL3_NYE_L34d66961_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lddba3fabxK7 | NYAM | K7 | both | TL3_NYE_Lddba3fab_RK7 | new | 0 | - | 0 | 0 |
| L33bc9e87xK7 | NYAM | K7 | both | TL3_NYE_L33bc9e87_RK7 | new | 0 | - | 0 | 0 |
| Lee3f074exK7 | NYAM | K7 | both | TL3_NYE_Lee3f074e_RK7 | new | 0 | - | 0 | 0 |
| Le3193838xK7 | NYAM | K7 | both | TL3_NYE_Le3193838_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0e94fadexK7 | NYAM | K7 | both | TL3_NYE_L0e94fade_RK7 | new | 0 | - | 0 | 0 |
| L59b66d32xM7 | NYAM | M7 | both | TL3_NYE_L59b66d32_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L12e67af0xK7 | NYAM | K7 | both | TL3_NYE_L12e67af0_RK7 | new | 0 | - | 0 | 0 |
| L11a12538xK7 | NYAM | K7 | both | TL3_NYE_L11a12538_RK7 | new | 0 | - | 0 | 0 |
| L4560e541xK7 | NYAM | K7 | both | TL3_NYE_L4560e541_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lf6becac4xK7 | NYAM | K7 | both | TL3_NYE_Lf6becac4_RK7 | new | 0 | - | 0 | 0 |
| Le0d40091xK7 | NYAM | K7 | both | TL3_NYE_Le0d40091_RK7 | new | 0 | - | 0 | 0 |
| Ld37dea46xK7 | NYAM | K7 | both | TL3_NYE_Ld37dea46_RK7 | new | 0 | - | 0 | 0 |
| L6ff237d4xM7 | NYAM | M7 | both | TL3_NYE_L6ff237d4_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L1b44d5f3xK7 | NYAM | K7 | both | TL3_NYE_L1b44d5f3_RK7 | new | 0 | - | 0 | 0 |
| L7295a253xK7 | NYAM | K7 | both | TL3_NYE_L7295a253_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L34d66961xK7 | NYAM | K7 | both | TL3_NYE_L34d66961_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L4fd10b76xP7 | NYAM | P7 | both | TL3_NYE_L4fd10b76_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L9513708bxK7 | NYAM | K7 | both | TL3_NYE_L9513708b_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Ld5cdb3c6xK7 | NYAM | K7 | both | TL3_NYE_Ld5cdb3c6_RK7 | new | 0 | - | 0 | 0 |
| L11631333xM7 | NYAM | M7 | both | TL3_NYE_L11631333_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L06eab808xK7 | NYAM | K7 | both | TL3_NYE_L06eab808_RK7 | new | 0 | - | 0 | 0 |
| L21f079b6xK7 | NYAM | K7 | both | TL3_NYE_L21f079b6_RK7 | scored | 72 | 2026-11-19 15:15Z | 5 | 1 |
| L2393e6acxK7 | NYAM | K7 | both | TL3_NYE_L2393e6ac_RK7 | new | 0 | - | 0 | 0 |
| L56a50dc8xK7 | NYAM | K7 | both | TL3_NYE_L56a50dc8_RK7 | new | 0 | - | 0 | 0 |
| L7678a6c4xK7 | NYAM | K7 | both | TL3_NYE_L7678a6c4_RK7 | new | 0 | - | 0 | 0 |
| L0dc67ba7xK7 | NYAM | K7 | both | TL3_NYE_L0dc67ba7_RK7 | new | 0 | - | 0 | 0 |
| L9e98b767xK7 | NYAM | K7 | both | TL3_NYE_L9e98b767_RK7 | new | 0 | - | 0 | 0 |
| Lfe9994ffxK7 | NYAM | K7 | both | TL3_NYE_Lfe9994ff_RK7 | new | 0 | - | 0 | 0 |
| L4fd10b76xM7 | NYAM | M7 | both | TL3_NYE_L4fd10b76_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L3bbe44f5xK7 | NYAM | K7 | both | TL3_NYE_L3bbe44f5_RK7 | new | 0 | - | 0 | 0 |
| Lc9217645xK7 | NYAM | K7 | both | TL3_NYE_Lc9217645_RK7 | new | 0 | - | 0 | 0 |
| L92e46167xK7 | NYAM | K7 | both | TL3_NYE_L92e46167_RK7 | new | 0 | - | 0 | 0 |
| L1ba33a2bxK7 | NYAM | K7 | both | TL3_NYE_L1ba33a2b_RK7 | new | 0 | - | 0 | 0 |
| La62168e0xK7 | NYAM | K7 | both | TL3_NYE_La62168e0_RK7 | new | 0 | - | 0 | 0 |
| L1af20032xK7 | NYAM | K7 | both | TL3_NYE_L1af20032_RK7 | new | 0 | - | 0 | 0 |
| L6be98834xK7 | NYAM | K7 | both | TL3_NYE_L6be98834_RK7 | new | 0 | - | 0 | 0 |
| L5ccb2d77xK7 | NYAM | K7 | both | TL3_NYE_L5ccb2d77_RK7 | new | 0 | - | 0 | 0 |
| L79cd626bxK7 | NYAM | K7 | both | TL3_NYE_L79cd626b_RK7 | new | 0 | - | 0 | 0 |
| L15a07e54xK7 | NYAM | K7 | both | TL3_NYE_L15a07e54_RK7 | new | 0 | - | 0 | 0 |
| L082c912dxK7 | NYAM | K7 | both | TL3_NYE_L082c912d_RK7 | new | 0 | - | 0 | 0 |
| L3ab0746cxK7 | NYAM | K7 | both | TL3_NYE_L3ab0746c_RK7 | new | 0 | - | 0 | 0 |
| L5e9c702bxK7 | NYAM | K7 | both | TL3_NYE_L5e9c702b_RK7 | new | 0 | - | 0 | 0 |
| Lcb97bb95xK7 | NYAM | K7 | both | TL3_NYE_Lcb97bb95_RK7 | new | 0 | - | 0 | 0 |
| Lfa8c13c0xK7 | NYAM | K7 | both | TL3_NYE_Lfa8c13c0_RK7 | new | 0 | - | 0 | 0 |
| L9c7289bdxK7 | NYAM | K7 | both | TL3_NYE_L9c7289bd_RK7 | new | 0 | - | 0 | 0 |
| Lb939a293xK7 | NYAM | K7 | both | TL3_NYE_Lb939a293_RK7 | new | 0 | - | 0 | 0 |
| Lb66c583exK7 | NYAM | K7 | both | TL3_NYE_Lb66c583e_RK7 | new | 0 | - | 0 | 0 |
| Ldcfbef89xK7 | NYAM | K7 | both | TL3_NYE_Ldcfbef89_RK7 | new | 0 | - | 0 | 0 |
| L19abb182xK7 | NYAM | K7 | both | TL3_NYE_L19abb182_RK7 | new | 0 | - | 0 | 0 |
| L3c6da67fxK7 | NYAM | K7 | both | TL3_NYE_L3c6da67f_RK7 | new | 0 | - | 0 | 0 |
| L0f98a9afxK7 | NYAM | K7 | both | TL3_NYE_L0f98a9af_RK7 | new | 0 | - | 0 | 0 |
| L46925cebxK7 | NYAM | K7 | both | TL3_NYE_L46925ceb_RK7 | new | 0 | - | 0 | 0 |
| Le4fede95xK7 | NYAM | K7 | both | TL3_NYE_Le4fede95_RK7 | new | 0 | - | 0 | 0 |
| Lba92ea98xK7 | NYAM | K7 | both | TL3_NYE_Lba92ea98_RK7 | new | 0 | - | 0 | 0 |
| L94b48ae1xK7 | NYAM | K7 | both | TL3_NYE_L94b48ae1_RK7 | new | 0 | - | 0 | 0 |
| L8e5a7466xK7 | NYAM | K7 | both | TL3_NYE_L8e5a7466_RK7 | new | 0 | - | 0 | 0 |
| L4a797fb6xK7 | NYAM | K7 | both | TL3_NYE_L4a797fb6_RK7 | new | 0 | - | 0 | 0 |
| Laf0d78abxK7 | NYAM | K7 | both | TL3_NYE_Laf0d78ab_RK7 | new | 0 | - | 0 | 0 |
| Lc5665194xK7 | NYAM | K7 | both | TL3_NYE_Lc5665194_RK7 | new | 0 | - | 0 | 0 |
| Ld30932f7xK7 | NYAM | K7 | both | TL3_NYE_Ld30932f7_RK7 | new | 0 | - | 0 | 0 |
| Ld61ffe03xK7 | NYAM | K7 | both | TL3_NYE_Ld61ffe03_RK7 | new | 0 | - | 0 | 0 |
| L0f2d7c91xK7 | NYAM | K7 | both | TL3_NYE_L0f2d7c91_RK7 | new | 0 | - | 0 | 0 |
| L252a89c9xK7 | NYAM | K7 | both | TL3_NYE_L252a89c9_RK7 | new | 0 | - | 0 | 0 |
| Lf5c3d8edxK7 | NYAM | K7 | both | TL3_NYE_Lf5c3d8ed_RK7 | new | 0 | - | 0 | 0 |
| Lf3ab2350xK7 | NYAM | K7 | both | TL3_NYE_Lf3ab2350_RK7 | new | 0 | - | 0 | 0 |
| L69c2a000xK7 | NYAM | K7 | both | TL3_NYE_L69c2a000_RK7 | new | 0 | - | 0 | 0 |
| L41724a15xK7 | NYAM | K7 | both | TL3_NYE_L41724a15_RK7 | new | 0 | - | 0 | 0 |
| L11631333xK7 | NYAM | K7 | both | TL3_NYE_L11631333_RK7 | new | 0 | - | 0 | 0 |
| L8123d039xK7 | NYAM | K7 | both | TL3_NYE_L8123d039_RK7 | new | 0 | - | 0 | 0 |
| L7f91b649xK7 | NYAM | K7 | both | TL3_NYE_L7f91b649_RK7 | new | 0 | - | 0 | 0 |
| L59efe6b3xK7 | NYAM | K7 | both | TL3_NYE_L59efe6b3_RK7 | new | 0 | - | 0 | 0 |
| L1ef22fa7xK7 | NYAM | K7 | both | TL3_NYE_L1ef22fa7_RK7 | new | 0 | - | 0 | 0 |
| L9f026abcxP7 | NYAM | P7 | both | TL3_NYE_L9f026abc_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L9f026abcxM7 | NYAM | M7 | both | TL3_NYE_L9f026abc_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L9f026abcxH7 | NYAM | H7 | both | TL3_NYE_L9f026abc_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0f097450xP7 | NYAM | P7 | both | TL3_NYE_L0f097450_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L21f079b6xP7 | NYAM | P7 | both | TL3_NYE_L21f079b6_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lf967df3bxP7 | NYAM | P7 | both | TL3_NYE_Lf967df3b_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lbbb39855xP7 | NYAM | P7 | both | TL3_NYE_Lbbb39855_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0bd23639xP7 | NYAM | P7 | both | TL3_NYE_L0bd23639_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L77a763afxP7 | NYAM | P7 | both | TL3_NYE_L77a763af_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0f097450xM7 | NYAM | M7 | both | TL3_NYE_L0f097450_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L21f079b6xM7 | NYAM | M7 | both | TL3_NYE_L21f079b6_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lf967df3bxM7 | NYAM | M7 | both | TL3_NYE_Lf967df3b_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lbbb39855xM7 | NYAM | M7 | both | TL3_NYE_Lbbb39855_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0bd23639xM7 | NYAM | M7 | both | TL3_NYE_L0bd23639_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L77a763afxM7 | NYAM | M7 | both | TL3_NYE_L77a763af_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L09ae66e3xP7 | NYAM | P7 | both | TL3_NYE_L09ae66e3_RP7 | fit queued | 72 | - | 0 | 0 |
| L0f097450xH7 | NYAM | H7 | both | TL3_NYE_L0f097450_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L21f079b6xH7 | NYAM | H7 | both | TL3_NYE_L21f079b6_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lf967df3bxH7 | NYAM | H7 | both | TL3_NYE_Lf967df3b_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lbbb39855xH7 | NYAM | H7 | both | TL3_NYE_Lbbb39855_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0bd23639xH7 | NYAM | H7 | both | TL3_NYE_L0bd23639_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L09ae66e3xM7 | NYAM | M7 | both | TL3_NYE_L09ae66e3_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lbbdd1236xP7 | NYAM | P7 | both | TL3_NYE_Lbbdd1236_RP7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L09ae66e3xH7 | NYAM | H7 | both | TL3_NYE_L09ae66e3_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lbbdd1236xM7 | NYAM | M7 | both | TL3_NYE_Lbbdd1236_RM7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L4ed22711xH7 | NYAM | H7 | both | TL3_NYE_L4ed22711_RH7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L09ae66e3xK7 | NYAM | K7 | both | TL3_NYE_L09ae66e3_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lac37d7ebxK7 | NYAM | K7 | both | TL3_NYE_Lac37d7eb_RK7 | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| L0f097450xK7LO | NYAM | K7 | long | TL3_NYE_L0f097450_RK7LO | waiting for the gate (pending / fail): no fit programme started | 0 | - | 0 | 0 |
| Lf967df3bxK7 | NYAM | K7 | both | TL3_NYE_Lf967df3b_RK7 | scored | 72 | 2026-11-19 15:35Z | 5 | 1 |
| Lbbb39855xK7 | NYAM | K7 | both | TL3_NYE_Lbbb39855_RK7 | fit queued | 72 | - | 0 | 0 |
| L0bd23639xK7 | NYAM | K7 | both | TL3_NYE_L0bd23639_RK7 | fit queued | 72 | - | 0 | 0 |
| L77a763afxK7 | NYAM | K7 | both | TL3_NYE_L77a763af_RK7 | fit queued | 72 | - | 0 | 0 |
| Le728b0a3xK7 | NYAM | K7 | both | TL3_NYE_Le728b0a3_RK7 | fit queued | 72 | - | 0 | 0 |

## Variant notes (order 1014Z: every yes row counts, the engine is the judge)
| label | session | book | variant | note |
|---|---|---|---|---|
| M05ab6fe0xA7 | Asia | A7 | long | W-ASIA list: pick REPLACE, pooled engine persistence 0.54 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Lfea1c9fcxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.85 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L0509f37cxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.46 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Mc817d9e3xA7 | Asia | A7 | long | W-ASIA list: pick REPLACE, pooled engine persistence 0.38 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L3ec39f56xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.54 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L0a809c2exA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.56 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L32db3e8bxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.46 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L17ce266fxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L5d9e7166xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L05222ff9xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L63ff9ae8xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.54 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L30aad100xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.38 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| M15f14debxA7 | Asia | A7 | long | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| M32bddb74xA7 | Asia | A7 | long | W-ASIA list: pick REPLACE, pooled engine persistence 0.54 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L0b1d7882xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.46 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L411f8593xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.51 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Lb7ac1fa5xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.46 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Ldcdb0b6exA7 | Asia | A7 | both | own-merit rank 2 |
| L86781ac0xA7 | Asia | A7 | both | own-merit rank 3 |
| Lc4e74264xA7 | Asia | A7 | both | own-merit rank 4 |
| L7ea48296xA7 | Asia | A7 | both | own-merit rank 5 |
| L548972b6xA7 | Asia | A7 | both | own-merit rank 6 |
| Lbe8a8e54xA7 | Asia | A7 | both | own-merit rank 7 |
| L7c368a4fxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L224050e7xA7 | Asia | A7 | both | own-merit rank 9 |
| Lfb608c7bxA7 | Asia | A7 | both | own-merit rank 11 |
| L15f14debxA7 | Asia | A7 | both | own-merit rank 12 |
| Lda55d973xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.52 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L1edb9fabxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Ledfbf4d2xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L40bde9eaxA7 | Asia | A7 | both | own-merit rank 16 |
| Lbd4b5635xA7 | Asia | A7 | both | own-merit rank 17 |
| Leee81e35xA7 | Asia | A7 | both | own-merit rank 18 |
| Lcae177baxA7 | Asia | A7 | both | own-merit rank 19 |
| Lc754cf58xA7 | Asia | A7 | both | own-merit rank 20 |
| Lcb276f27xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.53 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L1756b913xA7 | Asia | A7 | both | own-merit rank 22 |
| L973b5c8axA7 | Asia | A7 | both | own-merit rank 23 |
| L29b1bc3fxA7 | Asia | A7 | both | own-merit rank 24 |
| M7423c0d9xA7 | Asia | A7 | long | own-merit rank 25 |
| La5b5d03axA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.52 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| L6cff0af0xA7 | Asia | A7 | both | own-merit rank 27 |
| L2ccc12bfxA7 | Asia | A7 | both | own-merit rank 28 |
| Lb68a132dxA7 | Asia | A7 | both | own-merit rank 29 |
| Lbe5ac95bxA7 | Asia | A7 | both | own-merit rank 30 |
| L59536e17xA7 | Asia | A7 | both | own-merit rank 31 |
| L81e89115xA7 | Asia | A7 | both | own-merit rank 32 |
| L358e61bexA7 | Asia | A7 | both | own-merit rank 33 |
| Lc44703e7xA7 | Asia | A7 | both | own-merit rank 34 |
| L4d206c8cxA7 | Asia | A7 | both | own-merit rank 35 |
| L023ff9ffxA7 | Asia | A7 | both | own-merit rank 36 |
| L7a477a4axA7 | Asia | A7 | both | own-merit rank 37 |
| Mcee3865cxA7 | Asia | A7 | long | own-merit rank 38 |
| L3ee2d289xA7 | Asia | A7 | both | own-merit rank 39 |
| M3f6f752cxA7 | Asia | A7 | long | own-merit rank 40 |
| L5c9e11b3xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.58 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| Md2a3a7d6xA7 | Asia | A7 | long | own-merit rank 42 |
| L00391b70xA7 | Asia | A7 | both | own-merit rank 43 |
| L2d89766exA7 | Asia | A7 | both | own-merit rank 44 |
| Lb2f695b9xA7 | Asia | A7 | both | own-merit rank 45 |
| L8c18be1cxA7 | Asia | A7 | both | own-merit rank 46 |
| Lb0bab78fxA7 | Asia | A7 | both | own-merit rank 47 |
| Le50c8ff3xA7 | Asia | A7 | both | own-merit rank 48 |
| Mac97d189xA7 | Asia | A7 | long | own-merit rank 49 |
| L85abf719xA7 | Asia | A7 | both | own-merit rank 50 |
| L54f4c7dfxA7 | Asia | A7 | both | own-merit rank 51 |
| L7c4a36abxA7 | Asia | A7 | both | own-merit rank 52 |
| L252e1154xA7 | Asia | A7 | both | own-merit rank 53 |
| L9b2dd5a0xA7 | Asia | A7 | both | own-merit rank 54 |
| L05e7379bxA7 | Asia | A7 | both | own-merit rank 55 |
| L26b8e434xA7 | Asia | A7 | both | own-merit rank 56 |
| M72e48d4axA7 | Asia | A7 | long | own-merit rank 57 |
| M7cd27a3dxA7 | Asia | A7 | long | own-merit rank 58 |
| L4f7bebffxA7 | Asia | A7 | both | own-merit rank 59 |
| Ld6f168f8xA7 | Asia | A7 | both | own-merit rank 61 |
| M05838df6xA7 | Asia | A7 | long | own-merit rank 62 |
| Lf20f58a0xA7 | Asia | A7 | both | own-merit rank 63 |
| Lbbb442f8xA7 | Asia | A7 | both | own-merit rank 64 |
| Lde4f100bxA7 | Asia | A7 | both | own-merit rank 65 |
| L31f57f58xA7 | Asia | A7 | both | own-merit rank 66 |
| L35596060xA7 | Asia | A7 | both | own-merit rank 67 |
| M040bca61xA7 | Asia | A7 | long | own-merit rank 68 |
| Lf77e374bxA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.48 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| M1525fc29xA7 | Asia | A7 | long | own-merit rank 70 |
| L4c9a1a50xA7 | Asia | A7 | both | own-merit rank 71 |
| L8a2453c8xA7 | Asia | A7 | both | own-merit rank 72 |
| La6f6f7adxA7 | Asia | A7 | both | own-merit rank 73 |
| Lc7889984xA7 | Asia | A7 | both | W-ASIA list: pick REPLACE, pooled engine persistence 0.62 (ADD pick = reference only; REPLACE ONLY order 1407Z) |
| M0303c2bfxA7 | Asia | A7 | long | own-merit rank 75 |
| L3743d6caxA7 | Asia | A7 | both | own-merit rank 76 |
| M3a2258bdxA7 | Asia | A7 | long | own-merit rank 77 |
| L1a4596eexA7 | Asia | A7 | both | own-merit rank 78 |
| M7444c588xA7 | Asia | A7 | long | own-merit rank 79 |
| L345e7019xA7 | Asia | A7 | both | own-merit rank 80 |
| M028d0c03xA7 | Asia | A7 | long | own-merit rank 81 |
| L3c4f3969xA7 | Asia | A7 | both | own-merit rank 82 |
| L598ad596xA7 | Asia | A7 | both | own-merit rank 83 |
| L96205086xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Ld9ea2776xK7 | NYAM | K7 | both | own-merit rank 1 |
| Lb44a3e99xK7 | NYAM | K7 | both | own-merit rank 2 |
| L678ebaddxK7 | NYAM | K7 | both | own-merit rank 3 |
| L96205086xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L6c84f416xK7 | NYAM | K7 | both | own-merit rank 4 |
| L641a7c4dxK7 | NYAM | K7 | both | own-merit rank 5 |
| L2176f633xK7 | NYAM | K7 | both | own-merit rank 6 |
| L39470318xK7 | NYAM | K7 | both | own-merit rank 7 |
| L34d66961xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L86efc549xK7 | NYAM | K7 | both | own-merit rank 8 |
| L4eba93d7xK7 | NYAM | K7 | both | own-merit rank 9 |
| L2010fec9xK7 | NYAM | K7 | both | own-merit rank 10 |
| L11631333xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) [twin of Ld14659a9 here: same stream, one programme] |
| L582ae3cbxK7 | NYAM | K7 | both | own-merit rank 11 |
| L96205086xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L03be4d27xK7 | NYAM | K7 | both | own-merit rank 12 |
| L2b8ccd55xK7 | NYAM | K7 | both | own-merit rank 13 |
| L96205086xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) [twin of L9f026abc here: same stream, one programme] |
| Lc338b47bxK7 | NYAM | K7 | both | own-merit rank 14 |
| L4ed22711xK7 | NYAM | K7 | both | own-merit rank 15 |
| L4fd10b76xK7 | NYAM | K7 | both | own-merit rank 16 |
| L34d66961xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Ldae2fbc4xK7 | NYAM | K7 | both | own-merit rank 17 |
| L34d66961xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lddba3fabxK7 | NYAM | K7 | both | own-merit rank 18 |
| L33bc9e87xK7 | NYAM | K7 | both | own-merit rank 19 |
| Lee3f074exK7 | NYAM | K7 | both | own-merit rank 20 |
| L0e94fadexK7 | NYAM | K7 | both | own-merit rank 21 |
| L59b66d32xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L12e67af0xK7 | NYAM | K7 | both | own-merit rank 22 |
| L11a12538xK7 | NYAM | K7 | both | own-merit rank 23 |
| L4560e541xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf6becac4xK7 | NYAM | K7 | both | own-merit rank 24 |
| Le0d40091xK7 | NYAM | K7 | both | own-merit rank 25 |
| Ld37dea46xK7 | NYAM | K7 | both | own-merit rank 26 |
| L6ff237d4xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L1b44d5f3xK7 | NYAM | K7 | both | own-merit rank 27 |
| L7295a253xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L34d66961xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L4fd10b76xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Ld5cdb3c6xK7 | NYAM | K7 | both | own-merit rank 29 |
| L11631333xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) [twin of Ld14659a9 here: same stream, one programme] |
| L06eab808xK7 | NYAM | K7 | both | own-merit rank 30 |
| L21f079b6xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L2393e6acxK7 | NYAM | K7 | both | own-merit rank 32 |
| L56a50dc8xK7 | NYAM | K7 | both | own-merit rank 33 |
| L7678a6c4xK7 | NYAM | K7 | both | own-merit rank 34 |
| L0dc67ba7xK7 | NYAM | K7 | both | own-merit rank 35 |
| L9e98b767xK7 | NYAM | K7 | both | own-merit rank 36 |
| Lfe9994ffxK7 | NYAM | K7 | both | own-merit rank 37 |
| L4fd10b76xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L3bbe44f5xK7 | NYAM | K7 | both | own-merit rank 38 |
| Lc9217645xK7 | NYAM | K7 | both | own-merit rank 39 |
| L92e46167xK7 | NYAM | K7 | both | own-merit rank 40 |
| L1ba33a2bxK7 | NYAM | K7 | both | own-merit rank 41 |
| La62168e0xK7 | NYAM | K7 | both | own-merit rank 42 |
| L1af20032xK7 | NYAM | K7 | both | own-merit rank 43 |
| L6be98834xK7 | NYAM | K7 | both | own-merit rank 44 |
| L5ccb2d77xK7 | NYAM | K7 | both | own-merit rank 45 |
| L79cd626bxK7 | NYAM | K7 | both | own-merit rank 46 |
| L15a07e54xK7 | NYAM | K7 | both | own-merit rank 47 |
| L082c912dxK7 | NYAM | K7 | both | own-merit rank 48 |
| L3ab0746cxK7 | NYAM | K7 | both | own-merit rank 49 |
| L5e9c702bxK7 | NYAM | K7 | both | own-merit rank 50 |
| Lcb97bb95xK7 | NYAM | K7 | both | own-merit rank 51 |
| Lfa8c13c0xK7 | NYAM | K7 | both | own-merit rank 52 |
| L9c7289bdxK7 | NYAM | K7 | both | own-merit rank 53 |
| Lb939a293xK7 | NYAM | K7 | both | own-merit rank 54 |
| Lb66c583exK7 | NYAM | K7 | both | own-merit rank 55 |
| Ldcfbef89xK7 | NYAM | K7 | both | own-merit rank 56 |
| L19abb182xK7 | NYAM | K7 | both | own-merit rank 57 |
| L3c6da67fxK7 | NYAM | K7 | both | own-merit rank 58 |
| L0f98a9afxK7 | NYAM | K7 | both | own-merit rank 59 |
| L46925cebxK7 | NYAM | K7 | both | own-merit rank 60 |
| Le4fede95xK7 | NYAM | K7 | both | own-merit rank 61 |
| Lba92ea98xK7 | NYAM | K7 | both | own-merit rank 62 |
| L94b48ae1xK7 | NYAM | K7 | both | own-merit rank 63 |
| L8e5a7466xK7 | NYAM | K7 | both | own-merit rank 64 |
| L4a797fb6xK7 | NYAM | K7 | both | own-merit rank 65 |
| Laf0d78abxK7 | NYAM | K7 | both | own-merit rank 66 |
| Lc5665194xK7 | NYAM | K7 | both | own-merit rank 67 |
| Ld30932f7xK7 | NYAM | K7 | both | own-merit rank 68 |
| Ld61ffe03xK7 | NYAM | K7 | both | own-merit rank 69 |
| L0f2d7c91xK7 | NYAM | K7 | both | own-merit rank 70 |
| L252a89c9xK7 | NYAM | K7 | both | own-merit rank 71 |
| Lf5c3d8edxK7 | NYAM | K7 | both | own-merit rank 72 |
| Lf3ab2350xK7 | NYAM | K7 | both | own-merit rank 73 |
| L69c2a000xK7 | NYAM | K7 | both | own-merit rank 74 |
| L41724a15xK7 | NYAM | K7 | both | own-merit rank 75 |
| L11631333xK7 | NYAM | K7 | both | own-merit rank 76 |
| L8123d039xK7 | NYAM | K7 | both | own-merit rank 77 |
| L7f91b649xK7 | NYAM | K7 | both | own-merit rank 79 |
| L59efe6b3xK7 | NYAM | K7 | both | own-merit rank 80 |
| L1ef22fa7xK7 | NYAM | K7 | both | own-merit rank 81 |
| L9f026abcxP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L9f026abcxM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L9f026abcxH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0f097450xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) [twin of L3701b464 here: same stream, one programme] |
| L21f079b6xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf967df3bxP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lbbb39855xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0bd23639xP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L77a763afxP7 | NYAM | P7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0f097450xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) [twin of L3701b464 here: same stream, one programme] |
| L21f079b6xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf967df3bxM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lbbb39855xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0bd23639xM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L77a763afxM7 | NYAM | M7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0f097450xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) [twin of L3701b464 here: same stream, one programme] |
| L21f079b6xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lf967df3bxH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lbbb39855xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0bd23639xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L4ed22711xH7 | NYAM | H7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0f097450xK7LO | NYAM | K7 | long |  [twin of L3701b464 here: same stream, one programme] |
| Lf967df3bxK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Lbbb39855xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L0bd23639xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| L77a763afxK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |
| Le728b0a3xK7 | NYAM | K7 | both | both-side variant of a long cell (engine-tested; judged by the engine, order 1014Z) |

## L0a809c2exA7 (Asia, replaces A7; base TL3_ASI_L0a809c2e_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 30 min | +7 | +0 | +420 | -202 | 0.96 | -2 / +2 | n/a | n/a | n/a |
| CP | own day loss cap 4 stops ($4800 base), profit cap 12,000 | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +6 | -38 | +0 | -2 | 1.00 | +11 / -3 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | -390 | +477 | -298 | +455 | 1.02 | -797 / +1934 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +20 | -189 | -780 | -360 | +538 | 1.03 | +143 / +731 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -268 | +4141 | -1595 | +497 | 1.09 | +217 / +845 | n/a | n/a | n/a |
| NT | no new entries 1830-1900 ET | -246 | +639 | +1059 | +12 | 0.96 | -275 / +119 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +165 | -75 | -1369 | -165 | 0.99 | +242 / -192 | n/a | n/a | n/a |

## L17ce266fxA7 (Asia, replaces A7; base TL3_ASI_L17ce266f_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +40 | +0 | +0 | -47 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -231 | -2757 | +930 | -397 | 0.75 | -600 / -540 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | +753 | -6771 | -4814 | -441 | 1.05 | +1437 / -186 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | -417 | +2045 | +1505 | +93 | 1.00 | -721 / +222 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -49 | +3584 | +1100 | -1397 | 1.16 | -69 / -737 | n/a | n/a | n/a |
| NT | no new entries 1930-2000 ET | +52 | +0 | -615 | -421 | 0.99 | +9 / +82 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | -442 | +1880 | +1380 | +123 | 1.00 | -683 / +183 | n/a | n/a | n/a |

## L5d9e7166xA7 (Asia, replaces A7; base TL3_ASI_L5d9e7166_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +40 | +0 | +0 | -47 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -231 | -2757 | +930 | -397 | 0.75 | -600 / -540 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | +753 | -6771 | -4814 | -441 | 1.05 | +1437 / -186 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | -417 | +2045 | +1505 | +93 | 1.00 | -721 / +222 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -49 | +3584 | +1100 | -1397 | 1.16 | -69 / -737 | n/a | n/a | n/a |
| NT | no new entries 1930-2000 ET | +52 | +0 | -615 | -421 | 0.99 | +9 / +82 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | -442 | +1880 | +1380 | +123 | 1.00 | -683 / +183 | n/a | n/a | n/a |

## L05222ff9xA7 (Asia, replaces A7; base TL3_ASI_L05222ff9_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +40 | +0 | +0 | -47 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -221 | -3962 | +930 | -453 | 0.75 | -612 / -528 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | +739 | -6781 | -4824 | +243 | 1.04 | +1436 / +65 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | -403 | +2050 | +1440 | +83 | 1.00 | -703 / +211 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+20 pts | -249 | +1993 | -1851 | +333 | 1.32 | -234 / +286 | n/a | n/a | n/a |
| NT | no new entries 1930-2000 ET | +38 | +0 | -610 | +151 | 0.98 | +8 / +92 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | -442 | +1955 | +1385 | +116 | 1.00 | -688 / +178 | n/a | n/a | n/a |

## L63ff9ae8xA7 (Asia, replaces A7; base TL3_ASI_L63ff9ae8_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +40 | +0 | +0 | -47 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -221 | -3962 | +930 | -453 | 0.75 | -612 / -528 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | +739 | -6781 | -4824 | +243 | 1.04 | +1436 / +65 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | -403 | +2050 | +1440 | +83 | 1.00 | -703 / +211 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+20 pts | -249 | +1993 | -1851 | +333 | 1.32 | -234 / +286 | n/a | n/a | n/a |
| NT | no new entries 1930-2000 ET | +38 | +0 | -610 | +151 | 0.98 | +8 / +92 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | -442 | +1955 | +1385 | +116 | 1.00 | -688 / +178 | n/a | n/a | n/a |

## M15f14debxA7 (Asia, replaces A7; base TL3_ASI_M15f14deb_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +3 | +0 | +0 | -96 | 0.99 | +0 / +0 | n/a | n/a | n/a |
| CP | own day loss cap 4 stops ($4800 base), profit cap 12,000 | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -36 pts | -165 | +400 | +1438 | -574 | 1.09 | -483 / +617 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -48 | +0 | +0 | -175 | 1.00 | -213 / +471 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +30 | -332 | -173 | +1370 | +67 | 1.08 | -486 / +415 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -231 | +0 | +230 | -391 | 1.11 | -294 / +225 | n/a | n/a | n/a |
| NT | no new entries 1800-1830 ET | -428 | +670 | +990 | -57 | 0.94 | -709 / +1103 | n/a | n/a | n/a |
| TK | take at 65% of target after 5 s without a new extreme | -218 | +1717 | +2230 | -52 | 1.25 | -240 / +350 | n/a | n/a | n/a |

## Ldcdb0b6exA7 (Asia, replaces A7; base TL3_ASI_Ldcdb0b6e_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | -58 | +0 | +0 | -153 | 1.00 | -180 / +236 | n/a | n/a | n/a |
| CP | own day loss cap 3 stops ($3600 base), profit cap 12,000 | -82 | +0 | +0 | +139 | 1.00 | -136 / +289 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | -2 | +0 | +0 | -9 | 1.00 | +0 / -23 | n/a | n/a | n/a |
| CX | context cut (fresh) at -48 pts | +1171 | -6570 | -7563 | -504 | 1.03 | +1802 / -427 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+0 pts | -451 | +1056 | +2465 | +510 | 1.11 | -759 / +812 | n/a | n/a | n/a |
| NT | no new entries 1830-1900 ET | -137 | +0 | +0 | -74 | 1.01 | +64 / -207 | n/a | n/a | n/a |
| TK | take at 50% of target after 5 s without a new extreme | -350 | +285 | -2784 | -846 | 1.37 | -422 / -38 | n/a | n/a | n/a |

## L7c368a4fxA7 (Asia, replaces A7; base TL3_ASI_L7c368a4f_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +105 | -711 | -858 | -433 | 0.99 | +208 / +19 | n/a | n/a | n/a |
| CP | own day loss cap 3 stops ($3600 base), profit cap 12,000 | -137 | +652 | +2558 | +80 | 0.98 | +0 / +0 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | -4 | +0 | +0 | +4 | 1.00 | -2 / +1 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | -580 | +71 | +188 | -43 | 1.02 | -876 / -273 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -212 | +0 | +1560 | +415 | 1.00 | -71 / +379 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | -67 | -145 | +1027 | -14 | 1.00 | +16 / -100 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -630 | -966 | +910 | +530 | 1.15 | +579 / -868 | n/a | n/a | n/a |
| NT | no new entries 1800-1830 ET | -922 | -1823 | +4643 | +71 | 0.96 | -1149 / +1803 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | -67 | -145 | +1027 | -14 | 1.00 | +16 / -100 | n/a | n/a | n/a |

## Lda55d973xA7 (Asia, replaces A7; base TL3_ASI_Lda55d973_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 30 min | -43 | +1060 | +2162 | +306 | 0.98 | -473 / +405 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -416 | -1201 | +4785 | -562 | 0.76 | -1240 / +523 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -48 pts | +846 | -4863 | -500 | -272 | 1.02 | +1386 / -408 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -69 | +0 | +0 | +53 | 1.00 | -103 / +156 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 9000 | -247 | +0 | +3475 | -416 | 0.92 | -609 / +408 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+20 pts | -335 | -28 | +1684 | -1203 | 1.17 | -344 / -2685 | n/a | n/a | n/a |
| NT | no new entries 1830-1900 ET | -508 | +3162 | +6741 | +167 | 0.98 | -833 / +382 | n/a | n/a | n/a |
| TK | take at 65% of target after 15 s without a new extreme | -160 | +472 | +3544 | -308 | 1.19 | +224 / -1750 | n/a | n/a | n/a |

## Ledfbf4d2xA7 (Asia, replaces A7; base TL3_ASI_Ledfbf4d2_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +17 | +0 | +0 | -156 | 1.00 | -33 / +91 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($1200 base), profit cap 12,000 | -426 | -5894 | +282 | -526 | 0.76 | -639 / -814 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | -0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | +825 | -5733 | -3718 | +1120 | 1.05 | +1540 / +1199 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 6000 | -161 | -112 | -517 | +45 | 0.93 | -421 / +548 | n/a | n/a | n/a |
| LK | lock at 80% -> stop to entry+0 pts | -93 | +260 | +2485 | +52 | 1.03 | -238 / +658 | n/a | n/a | n/a |
| NT | no new entries 2000-2030 ET | -103 | -582 | +0 | -129 | 0.95 | -140 / +197 | n/a | n/a | n/a |
| TK | take at 65% of target after 30 s without a new extreme | -601 | -286 | +7319 | -897 | 1.18 | -1045 / -1011 | n/a | n/a | n/a |

## Lcb276f27xA7 (Asia, replaces A7; base TL3_ASI_Lcb276f27_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | -36 | -690 | +0 | -600 | 0.98 | -179 / -165 | n/a | n/a | n/a |
| CP | own day loss cap 3 stops ($2340 base), profit cap 12,000 | -141 | +0 | +0 | -1127 | 0.88 | -313 / -73 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -39 pts (1.0 x stop) | +1677 | +204 | -1999 | -2080 | 1.48 | +1447 / -1264 | n/a | n/a | n/a |
| CX | context cut (fresh) at -31 pts | +534 | -1372 | -1157 | -30 | 1.11 | +475 / -255 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -48 | +0 | +0 | -311 | 1.00 | -112 / +195 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +20 | -96 | -267 | +1662 | -882 | 1.05 | -295 / +145 | n/a | n/a | n/a |
| LK | lock at 80% -> stop to entry+0 pts | -136 | +28 | +1567 | -395 | 1.03 | -305 / +241 | n/a | n/a | n/a |
| NT | no new entries 1900-1930 ET | +133 | -1795 | +690 | -509 | 0.96 | +116 / -309 | n/a | n/a | n/a |
| TK | take at 95% of target after 5 s without a new extreme | +15 | -315 | -185 | +196 | 1.02 | +47 / -51 | n/a | n/a | n/a |

## La5b5d03axA7 (Asia, replaces A7; base TL3_ASI_La5b5d03a_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | -52 | +0 | +0 | -503 | 0.98 | -232 / +114 | n/a | n/a | n/a |
| CP | own day loss cap 3 stops ($2340 base), profit cap 12,000 | -91 | +0 | +0 | -1130 | 0.88 | -233 / -75 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -39 pts (1.0 x stop) | +1721 | +161 | -1999 | -1938 | 1.48 | +1524 / -1074 | n/a | n/a | n/a |
| CX | context cut (fresh) at -31 pts | +335 | -1410 | -63 | +82 | 1.11 | +141 / -14 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -49 | +0 | +0 | -311 | 1.00 | -112 / +195 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +20 | -91 | -320 | +1632 | -882 | 1.05 | -288 / +142 | n/a | n/a | n/a |
| LK | lock at 80% -> stop to entry+0 pts | -131 | +0 | +1562 | -397 | 1.03 | -302 / +242 | n/a | n/a | n/a |
| NT | no new entries 1900-1930 ET | +47 | +0 | +690 | -490 | 0.97 | -25 / -128 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +54 | -35 | -165 | -180 | 1.00 | +28 / -18 | n/a | n/a | n/a |

## L5c9e11b3xA7 (Asia, replaces A7; base TL3_ASI_L5c9e11b3_RA7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 30 min | +245 | -707 | -1068 | -38 | 0.96 | -71 / +124 | n/a | n/a | n/a |
| CP | own day loss cap 3 stops ($3600 base), profit cap 12,000 | -136 | +0 | +1013 | -188 | 0.97 | -213 / +103 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | +214 | -2413 | -2088 | -534 | 1.08 | +505 / -864 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -24 | +0 | +0 | -637 | 1.00 | -186 / +369 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +20 | -144 | +446 | +1235 | +17 | 1.08 | -118 / -470 | n/a | n/a | n/a |
| LK | lock at 80% -> stop to entry+0 pts | -202 | +0 | +525 | +11 | 1.05 | +29 / -550 | n/a | n/a | n/a |
| NT | no new entries 1830-1900 ET | -195 | +0 | +1013 | -64 | 0.97 | -262 / -115 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | -76 | -110 | +903 | -76 | 1.00 | -183 / +11 | n/a | n/a | n/a |

## L6a25b155xK7 (NYAM, replaces K7; base TL3_NYE_L6a25b155_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 15 min | +112 | +0 | +0 | -455 | 0.97 | +180 / -827 | n/a | n/a | n/a |
| CP | own day loss cap 2 stops ($4800 base), profit cap 12,000 | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -120 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -96 pts | +41 | +0 | +0 | -626 | 1.02 | +83 / -1138 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -56 | +551 | +551 | -2 | 0.98 | -43 / -352 | n/a | n/a | n/a |
| FR | W-FASTR pick: take 95%/30 s | +8 | -50 | +0 | -52 | 1.00 | +14 / -68 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+10 pts | -207 | +2165 | +692 | -30 | 1.14 | -156 / -260 | n/a | n/a | n/a |
| NT | no new entries 1100-1130 ET | +7 | -230 | -230 | +448 | 0.92 | +24 / +715 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +8 | -50 | +0 | -52 | 1.00 | +14 / -68 | n/a | n/a | n/a |

## L01811caaxP7 (NYAM, replaces P7; base TL3_NYE_L01811caa_RP7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | -96 | +845 | +0 | -559 | 0.89 | -120 / -470 | n/a | n/a | n/a |
| CP | own day loss cap 2 stops ($2400 base), profit cap 12,000 | -4 | +0 | +0 | -11 | 0.99 | -7 / -23 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | -13 | +252 | +0 | -30 | 1.01 | -0 / -573 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: no-follow-through: < +5 pts after 20 min | -28 | +0 | +0 | +326 | 1.03 | -60 / +217 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -7 | +1440 | +0 | -96 | 1.04 | +27 / +59 | n/a | n/a | n/a |
| NT | no new entries 1130-1200 ET | -24 | -350 | +0 | +12 | 0.89 | -46 / +151 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | +1 | +0 | +0 | -7 | 1.00 | +0 / -5 | n/a | n/a | n/a |

## L01811caaxK7 (NYAM, replaces K7; base TL3_NYE_L01811caa_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | -56 | +845 | +0 | -616 | 0.89 | -46 / -589 | n/a | n/a | n/a |
| CP | own day loss cap 2 stops ($2400 base), profit cap 12,000 | -4 | +0 | +0 | -11 | 0.99 | -7 / -23 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | -31 | -1351 | +0 | -14 | 1.01 | -13 / -590 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -29 | +0 | +0 | -265 | 0.97 | -43 / -769 | n/a | n/a | n/a |
| FR | W-FASTR pick: lock 80% -> +10 | -9 | +0 | +0 | -78 | 1.01 | +18 / -98 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -37 | +127 | +0 | -63 | 1.05 | -24 / +40 | n/a | n/a | n/a |
| NT | no new entries 1130-1200 ET | -8 | -350 | +0 | +18 | 0.89 | -20 / +164 | n/a | n/a | n/a |
| TK | take at 80% of target after 30 s without a new extreme | -4 | +610 | +0 | -145 | 1.03 | +8 / -90 | n/a | n/a | n/a |

## L01811caaxM7 (NYAM, replaces M7; base TL3_NYE_L01811caa_RM7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | -34 | +845 | +0 | -602 | 0.89 | -31 / -561 | n/a | n/a | n/a |
| CP | own day loss cap 2 stops ($2400 base), profit cap 12,000 | -3 | +0 | +0 | -11 | 0.99 | -5 / -23 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | -9 | -2023 | +0 | +9 | 1.02 | +17 / -543 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -1800 base (1.5R) | -30 | +0 | +551 | -274 | 0.97 | -85 / -329 | n/a | n/a | n/a |
| FR | W-FASTR pick: no-follow-through: < +5 pts after 20 min | -11 | -1389 | -56 | +263 | 1.02 | -37 / +210 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -60 | -544 | +185 | +6 | 1.05 | -27 / +25 | n/a | n/a | n/a |
| NT | no new entries 1130-1200 ET | -11 | -350 | -15 | -38 | 0.89 | -21 / +119 | n/a | n/a | n/a |
| TK | take at 80% of target after 15 s without a new extreme | -5 | +421 | -235 | -90 | 1.03 | +46 / -171 | n/a | n/a | n/a |

## L01811caaxH7 (NYAM, replaces H7; base TL3_NYE_L01811caa_RH7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | -92 | +845 | +0 | -575 | 0.89 | -106 / -504 | n/a | n/a | n/a |
| CP | own day loss cap 2 stops ($2400 base), profit cap 12,000 | -4 | +0 | +0 | -11 | 0.99 | -7 / -23 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -60 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -24 pts | -14 | +397 | +0 | -30 | 1.01 | -2 / -573 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: no-follow-through: < +5 pts after 20 min | -26 | +0 | -56 | +257 | 1.03 | -67 / +199 | n/a | n/a | n/a |
| LK | lock at 65% -> stop to entry+10 pts | -46 | +1440 | +185 | -184 | 1.05 | -71 / +12 | n/a | n/a | n/a |
| NT | no new entries 1130-1200 ET | -11 | -350 | -15 | -5 | 0.89 | -23 / +117 | n/a | n/a | n/a |
| TK | take at 95% of target after 15 s without a new extreme | +1 | +0 | +0 | -7 | 1.00 | +1 / -5 | n/a | n/a | n/a |

## L21f079b6xK7 (NYAM, replaces K7; base TL3_NYE_L21f079b6_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | +387 | +0 | -2606 | +260 | 0.99 | +849 / -514 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($2400 base), profit cap 12,000 | -23 | +0 | +0 | +40 | 0.99 | -42 / +82 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -120 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -96 pts | +412 | -2662 | -1669 | -420 | 1.04 | +743 / -356 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 9000 | -24 | +0 | +0 | +218 | 0.97 | -42 / +82 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+0 pts | -4 | +0 | +0 | -1402 | 1.30 | -95 / -663 | n/a | n/a | n/a |
| NT | no new entries 1100-1130 ET | -48 | +0 | +0 | -28 | 0.97 | -84 / +98 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +18 | +0 | +0 | +133 | 1.01 | +23 / -52 | n/a | n/a | n/a |

## Lf967df3bxK7 (NYAM, replaces K7; base TL3_NYE_Lf967df3b_RK7)
| layer | best setting (L6M ulcer) | d ulcer | d worst wk | d max DD | d mean $/wk | trades x base | L3M d ulcer / d mean | 2025 | 2024 | 2023 |
|---|---|---|---|---|---|---|---|---|---|---|
| BO | post-stop same-side blackout 60 min | +387 | +0 | -2606 | +260 | 0.99 | +849 / -514 | n/a | n/a | n/a |
| CP | own day loss cap 1 stops ($2400 base), profit cap 12,000 | -23 | +0 | +0 | +40 | 0.99 | -42 / +82 | n/a | n/a | n/a |
| CU | loss cut when unrealised <= -120 pts (1.0 x stop) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| CX | context cut (fresh) at -96 pts | +412 | -2662 | -1669 | -420 | 1.04 | +743 / -356 | n/a | n/a | n/a |
| DD | DAY-DONE: stack >= 22 closes and day <= -2400 base (2.0R) | +0 | +0 | +0 | +0 | 1.00 | +0 / +0 | n/a | n/a | n/a |
| FR | W-FASTR pick: own day cap loss $2400, profit 9000 | -24 | +0 | +0 | +218 | 0.97 | -42 / +82 | n/a | n/a | n/a |
| LK | lock at 50% -> stop to entry+0 pts | -4 | +0 | +0 | -1402 | 1.30 | -95 / -663 | n/a | n/a | n/a |
| NT | no new entries 1100-1130 ET | -48 | +0 | +0 | -28 | 0.97 | -84 / +98 | n/a | n/a | n/a |
| TK | take at 95% of target after 30 s without a new extreme | +18 | +0 | +0 | +133 | 1.01 | +23 / -52 | n/a | n/a | n/a |
