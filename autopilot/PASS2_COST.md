# PASS2_COST - set-months per book and dates for pass 2 (W-P2P, first version 2026-11-19 18:50Z; updated hourly until pass 2 starts)

Unit: set-month = one engine run of one set (one book variant) for one calendar month (ENGINE_PLAN.md). Fleet rate read from HEALTH.md at 18:40Z: 4,506 set-months/h (DONE files x 2), 14.5 h of queue, fast share 96% (Dallas, Frankfurt, Singapore 100%, box 1 68%). ENGINE_PLAN NY AM line: fleet 4,652/h measured, low 4,000/h. Engine slots ~ 255 (box 1 31, Dallas 28, Frankfurt 99-100, Singapore 97-100) => about 17.6 set-months per slot-hour (~205 s each) at the fast path; exact-path jobs take 550-580 s (3x slower), so the fleet rate falls to ~1,850/h if pass-2 sets are NOT on the fast path.

## 1. Screen cost (per book, fast walker, grid side, not engine set-months)
Screen = about 700-900 settings per book (PREREG_PASS2 section 1.1) x matched random-skip null (200 draws; 1,000 and 10,000 only for the few kept). Per-book cpu-seconds from W-P2A's PASS2_COMBINER.md: NOT YET PUBLISHED (placeholder). Working assumption from the R3 ladder (stage A 0.010 core-h per cell for 30 draws; null draws on a per-trade vector are far cheaper than walker runs): about 0.3 core-h per book, i.e. ~4 set-month equivalents at 264 core-seconds per set-month. Negligible against the joint stage (0.2%); to be replaced by the W-P2A number.

## 2. Joint stage, exact engine: formula and numbers (per book)
Formula: sm_book = J1 x m_L6M + J2 x m_L6M + P x m_year x 3 + C_exact x m_L6M + R x (m_all - m_L6M), where m_L6M = 6 months, m_year = 12 months, m_all = 43 months (2023-04 to 2026-10, the landed history), J1 = 96, J2 = 24, P = 3 top settings, C_exact = 20 date-shift controls, R = 24 roll-set settings.

| item | settings x months | set-months |
|---|---|---|
| J1: 96 joint settings, L6M (L3M is inside it) | 96 x 6 | 576 |
| J2: 24 refinements, L6M | 24 x 6 | 144 |
| prior years 2023 / 2024 / 2025, top 3 settings | 3 x 36 | 108 |
| 20 exact date-shift controls on the final setting (10 more = selection repeats on the screen walker, PREREG amendment 1) | 20 x 6 | 120 |
| 2-week roll: 24 roll-set settings over the other 37 months | 24 x 37 | 888 |
| **total per book, full path** | | **1,836** |
| add for a LEAD-or-better book: 10 selection-repeat controls, 96 settings each, exact | 10 x 96 x 6 | +5,760 |

Funnel case: the roll (888, 48% of the cost) runs only for books that pass G3-G6 (drawdown-first, prior years, persistence); assume 60% of books go on (assumption, to be replaced by the measured pass rate of the first 20 books): 1,836 x 0.6 = about 1,100 per book. If hooks are screen-only for part of the books the number falls further.
Pass-2 totals per session (N books, full path): N=50: 91,800; N=100: 183,600; N=200: 367,200 set-months. Funnel case: 55,100 / 110,200 / 220,400. Extra for LEAD+ selection repeats: 5,760 per LEAD+ book (top ~10 per session at first = 57,600 per session).
Not counted: stack stage from empty (W-COMBO, ENGINE_PLAN section 2 uses ~1,000-3,400 per stack question), exit run of the 68 recipes through the exact engine (inside J1 once W-XB1/W-XB2 pass; its screen is separate).

## 3. Dates, top 50 / 100 / 200 books per session (Asia and NY AM both, same N each)
Share rule (order 1850Z): while first looks run pass 2 gets no engine beyond identity runs; Asia first look ends ~23:20Z (W-ASIA; HEALTH 4,506/h), NY AM first looks end 2026-11-20 07:18Z (base) / 09:24Z (low) (ENGINE_PLAN, W-NYENG 18:30Z); a finished session's freed first-look share goes to pass 2 for that session; ranked follow-ups keep 30%. Model: pass-2 pool = 70% of fleet; Asia gets 61% of it from 23:20Z (Asia's share of remaining first looks, ENGINE_PLAN split 61/39) until NY AM ends (09:24Z, the conservative low case); then 50/50 of the pool; when one session's N books are done the other takes the whole 70%. Assumes Asia pass 2 rate = 0.7 x 0.61 x fleet = 1,920/h at 4,500/h (before NY AM finishes).

| fleet rate | per-book cost | top 50: Asia / NY AM done | top 100: Asia / NY AM done | top 200: Asia / NY AM done |
|---|---|---|---|---|
| 4,500/h (fast path ~100%, today) | full 1,836 | 11-22 07Z / 11-22 13Z | 11-24 17Z / 11-25 00Z | 11-29 14Z / 11-29 20Z |
| 4,500/h | funnel 1,102 | 11-21 08Z / 11-21 14Z | 11-22 19Z / 11-23 01Z | 11-25 17Z / 11-25 23Z |
| 3,800/h (lower measured band) | full | 11-22 18Z / 11-23 00Z | 11-25 15Z / 11-25 21Z | 12-01 09Z / 12-01 15Z |
| 3,800/h | funnel | 11-21 14Z / 11-21 20Z | 11-23 08Z / 11-23 14Z | 11-26 18Z / 11-27 01Z |
| 1,850/h (hooks NOT on the fast path, exact 550 s) | full | 11-25 19Z / 11-26 01Z | 12-01 16Z / 12-01 23Z | 12-13 12Z / 12-13 18Z |
| 1,850/h | funnel | 11-23 10Z / 11-23 16Z | 11-26 23Z / 11-27 05Z | 12-04 01Z / 12-04 07Z |

Reading: top 50 per session in about 2-3 days at today's rate; top 200 in about 6-10 days. The first books' joint results land within the first 6 hours after 23:20Z (a book needs 1,836 set-months over its own ~ a few dozen slots). The biggest lever is the fast path: the 1,850/h row is the penalty if W-P2B's hooks (or W-XB exits) are not in FAST_KINDS; fl_autoadd must run each new kind's identity pair at once (order 1457Z item 1). Any follow-up share above 30% or slot cap changes (HEALTH) shifts the dates in proportion.
Not modelled: the other-book REPLACE rows of NY AM (148,248 set-months, parked 18:58Z per W-NYENG), further servers (none), the stack stage.

## 4. Hourly log
- 18:50Z first version. Inputs not yet available: W-P2A per-book cpu-seconds, W-P2B per-hook fast-path status.
- 18:48Z (auto) fleet 5588 sm/h (HEALTH), queue 65130 lines, fast share 87%; PASS2_COMBINER.md ABSENT | PASS2_HOOKS.md ABSENT; FAST_KINDS pass-2 related lines 0; Asia first look end ~23:20Z (order 1850Z; recheck W-ASIA), NY AM first looks end ?; dates (Asia/NY AM done, top N per session, full 1,836 sm/book): 50: 11-21 20Z/11-22 02Z; 100: 11-23 19Z/11-24 01Z; 200: 11-27 17Z/11-27 23Z; funnel 1,102: 50: 11-21 01Z/11-21 07Z; 100: 11-22 05Z/11-22 11Z; 200: 11-24 13Z/11-24 20Z. Screen cost and funnel still assumptions until W-P2A/B publish.
