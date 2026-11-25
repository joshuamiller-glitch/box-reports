# MORNING SUMMARY 2026-11-25 (written by LEAD, first edition ~11:35Z; second edition ~12:25Z below; refresh when prior years / walk-forward for the new eight land)

Research and shadow only: nothing was touched on the execution server or any live chart.

## What you need to decide before the NY AM open (14:30Z)
The file (build v30/v31) carries **JT91 on the delivered nine NY AM books** (WEAK-BUT-POSITIVE, RED 2023, null failed). A new eight-book NY AM stack is being fitted; its gated pick cannot be ready by 14:30Z.
1. **Which NY AM pick does the file trade today?** (A, default) JT91 on the nine as fitted. (B) the PROVISIONAL L6M-only pick on the new eight if it exists by ~13:30Z, labelled BEST-AVAILABLE-NOT-PROVEN (no walk-forward, prior years vs bare only). The fully gated pick on the new eight is ~17:00Z at the earliest.
2. **DLB9 at the file's size** (QUESTIONS_FOR_JOSH.md): at 6/3/1 the pick without the stack day-loss halt beats the pick with it (L6M ulcer 21,978 vs 34,552, max DD -$58,458 vs -$91,745, $/wk $32,273 vs $23,368); at 6/3/2 it is ulcer-neutral and costs ~$6,900/wk. Options: A ship JT91 as fitted (default); B re-fit at the file's size (~10,164 rows per size, ~3.5 h each); C ship with DLB9 off (not a fitted pick).
3. **Store holes** (engine store has no 20261102-04): parity pages and fitted results use the engine AS STORED; live follows complete data. Default stands unless you say otherwise (PRF5 POC 29561.25 as stored vs 28320.0 hole-filled on 20261110; L39287638 vsess_50 threshold 5,266 vs 5,672; renko box for Lca8ca9cb 43 vs 46 ticks).
4. **The 7.9 MB NY AM raw tape page** was moved out of the mirror (outputs/autopilot_nomirror/, stub left) because two lines contain a digit run equal to a configured account-id string (false positive); the box-reports gate was not changed. How should the tape reach the relay?

## NY AM, plainly
- **Equal five (BF2_JT68):** WEAK-BUT-POSITIVE (null 1 of 3).
- **Weighted nine, JT91 (native 4/2/1 basis, delivered 01:56Z):** L6M bare -> pick: ulcer 28,581 -> 9,465, max DD -$99,970 -> -$25,973, $/wk $51,363 -> $17,388 (-66%); walk-forward 0.775; 2023 RED (the pick loses money that year), 2024/2025 GREEN; null FAILED (0 of 2 draws, stop after the second miss). At the file's lots (6/3/1 or 6/3/2): L6M max DD -$91,745 / -$64,115, $/wk $23,368 / $25,395 (page: NYAM_WEIGHTED_FILE_SIZE.md). Keys/defaults: D8_LAYER_KEYS_NYAM_NYAMW_JT91.md / D8_LAYER_DEFAULTS_NYAM_NYAMW_JT91.md.
- **The NY AM pool grew 39 -> 40 -> 42 books** after that. The weighted re-pick on pool 42 (FINAL 10:08Z, provisional) is a different stack: eight books, L39287638 and L64390867 drop out, a new member Lca8ca9cb x0.25 comes in (it trades both sides). Bare 1-lot units: L6M ulcer 4,743 / max DD -$18,636 / $13,444 per wk; persistence 0.68.
- **Fit of the new eight (TL3_ALN_NY_STKd8w42, delivered nine untouched):** one hour was lost to a missing identity-set file (found and fixed 11:05Z). Now: R0 6/6, identity IDENTICAL, screen 947 of 3,114 at 11:27Z. ETA (W-LAYERS2): screen ~12:05-12:50Z, PROVISIONAL pick ~12:15-13:30Z, full 42-month joint and gated verdict ~17:00Z, null later.
- **Corrections to the layer pages (not to the fits):** CAP is a static median-book-R dollar value with a loss and a profit side, per book same value; DLB9 = -$4,000 x lots of the smallest-lot book not yet halted; SC1 acts in session 3. Correction sections were appended to 13 keys + 13 defaults pages + 2 Asia reference pages. Fitted results do not change.

## Coding specs (all hand-verified against the engine on full stored bars)
Eight NY AM spec pages (L43f0cbfb, B7bfd33b7, Bf428c4a1, Le4fede95, L39287638, L4407508c, L64390867, Lca8ca9cb) with parity packs for 20261027 and 20261110; the relay's five-plus readings were answered in the pages (EMAs run on one continuous series, sopen_cross state is not reset at session change, LVN = two lowest smoothed values, bucket edges use ts_event). Index: NYAM_WEIGHTED_CODING_INDEX.md. Open: TRADES for 20261110 (engine month 202611 not landed), td 20261125 constants (td 20261124 day file arrived with the 01:30Z top-up; completeness to be checked).

## Asia and other sessions
- **Asia fade L1acc170a:** passes the L6M gates bare at 1 lot, but with the fitted layers on (JT110 at 6 lots) it FAILS: ulcer +9.6% worse, max DD worse, walk-forward 55.4%, controls 12 of 30. The four-book Asia build stands; fade stays OFF.
- **NY PM and London nulls** restarted, wired as the last two queue lines (tail priority), ~16:00-20:00Z. London STC-free joint verdict pending. NY AM fade add rows (8,684) and NY AM ladder advance (18,118) wait behind the NY AM fits.
- **Queue:** ~97k unstarted set-months across the queue files at ~4.9k/h (~20 h).

## Plumbing and fixes today
- Weighted-nine fit rows were parked by the 2-lot rule; restored by LEAD (park exemption for the weighted names, parked file intact).
- The weighted selection loop stalled twice on candidate sets sitting behind the follow-up files; W-GRIDOPS front-loaded them and runs a 5-min niced watcher (<tmp> stop file STOP).
- Mirror outage 20:35Z-21:35Z (account-id gate false positive); fixed by moving the tape page, no gate change.
- Data: nightly top-up 01:30Z, quote $0.0000.

## Slips (honest)
The weighted nine was ordered "ready for NY AM tomorrow"; it was delivered 01:56Z (target met) but the pool then grew and the stack changed, so what is ready for today's open is JT91 (weak, null failed). The new eight will not be gated before 14:30Z. A clock-skew note: three of my entries between 03:22Z and 03:27Z carried later stamps than the real time.

## UPDATE 12:25Z (second edition)
- **New NY AM eight-book stack: PROVISIONAL pick JT154 exists** (screen done 11:51Z, joint L6M rows landed ~12:15Z). L6M at the native x4 basis, ulcer / max DD / $ per wk: bare 27,178 / -$97,355 / $51,505 -> JT154 14,720 / -$46,473 / $19,159; L3M ulcer 28,739 -> 10,716. Pages with a PROVISIONAL banner: BAREFIT_NY_STKd8w42_PROV.md, D8_LAYER_KEYS_NYAM_W42_PROV.md, D8_LAYER_DEFAULTS_NYAM_W42_PROV.md. No walk-forward, prior-year bands pending (36 rows queued, ~1-2 h), null pending.
- **Side by side with the delivered nine (JT91):** JT91 ulcer 9,465 / max DD -$25,973 / $17,388; JT154 earns ~$1,800 a week more but its ulcer is 56% higher and its max DD 79% higher. Drawdown first, JT91 is better on L6M. LEAD default for the 14:30Z open stays A: JT91 on the nine (your call).
- Full gated verdict for the new eight (walk-forward on all 242 combos x 42 months, ~8,400 rows open): ~15:30Z.
