# DS3_SDISC_2B - session-tuned vs live parameter sets in the live books' carrier sessions (D3SD2B, SDISC item 2 part, 2026-10-28)
Research only; nothing live. Prereg `l2vast/ds3/prereg/SD2B_prereg.md` sha256 `79fefb882170942fe83b4b7d3699ad7fba66e09060deaf52cb161862763ec3cf` + addendum A1 (DN, CR) `SD2B_prereg_add1.md` sha256 `818a592268d220cdd0cb6a8c656ec8326798ea33720e4a5786ba33e98852848f`; PREHOLD `autopilot/DS3_SDISC_2B_PREHOLD.md` sha256 `41711d2d629d6efd75b957693cf133cfaea853a4ddb23c98c31eefeb1cb7caa4` (all in DECISIONS.md, each logged BEFORE the statistics it guards). Code `l2vast/ds3/code/sd2b/` (sd2b_lib, grids, grids_add, s1 screen, s2 lock stage, mk_winners, s3 HOLD/X looks, s4 stack-add, mk_surv, rep); outputs `l2vast/ds3/out/sd2b/` (s1_*, s2_*, s3_all/s3_summary.csv, s4_all, pre_top10.csv, looks.jsonl, survivors_for_A.parquet, summary.json). UNTOUCHED (after 2026-02-06) never read.

## Verdict (plain)
- **A session-tuned parameter set does NOT beat the live one.** 10 engines x 4 sessions = 40 book-sessions, each with a PRE-selected winner out of {live + a PRE-only grid of 25-320 configs, top 30 through the exact lock engine}. In PRE the winner beats live by +2,883/wk on average (by construction); in the ONE HOLD look the same winners are **-1,745/wk vs live on average (median -1,448); only 9 of 40 are positive** (sign test, tuned worse than a coin flip: p = 0.0003); **0 of 40 beat live by their MDE** (HOLD delta MDE averages 9,597/wk; every delta is inside it; the CI excludes zero on the NEGATIVE side for 2: ST LONDON and DN ASIA). On the 2023 span the mean delta is +110/wk (23 of 40 positive: chance). Persistence inside PRE (best on PRE half 1, delta vs live on half 2): 17 of 40 positive: chance. The gain the screen finds in PRE is selection noise of a max over 25-320 configs, not a session-specific parameter effect.
- **The directive's examples:**
- **HM NY-AM**: tuned `f=20,s=35,ema=100` vs live: PRE +4,828/wk (the selection), HOLD -1,091 [-8,302, 6,231] (MDE 10,390), 2023 span +1,286, by year +1,608 / +3,566 / +2,537 / -401; in-session HOLD $/wk tuned -5,823 vs live -4,732.
- **KB ASIA**: tuned `k=2,n=30,m=1.5,na=14` vs live: PRE +6,489/wk (the selection), HOLD -6,008 [-17,939, 6,093] (MDE 17,459), 2023 span +278, by year +630 / +8,254 / -3,098 / +1,474; in-session HOLD $/wk tuned -2,426 vs live 3,583.
- **KB NY-PM**: tuned `k=2,n=30,m=2.0,na=20` vs live: PRE +1,530/wk (the selection), HOLD -2,331 [-9,662, 4,497] (MDE 10,191), 2023 span -587, by year -81 / -951 / +134 / +10,133; in-session HOLD $/wk tuned -2,671 vs live -340.
- **PE ASIA**: tuned `R=3,P=1,ptype=1,ttype=1` vs live: PRE +2,865/wk (the selection), HOLD -4,143 [-18,175, 10,300] (MDE 20,626), 2023 span +1,111, by year +2,127 / +1,612 / -2,094 / +12,306; in-session HOLD $/wk tuned -509 vs live 3,634.
- **MV NY-AM**: tuned `lbs=(5, 10, 20, 40, 80),thr=0.25,k=3` vs live: PRE +2,336/wk (the selection), HOLD -1,416 [-11,147, 7,913] (MDE 13,818), 2023 span +5,087, by year +6,022 / +3,101 / -408 / -3,986; in-session HOLD $/wk tuned 3,399 vs live 4,815.
- **DN ASIA**: tuned `k=3,n=30` vs live: PRE +5,534/wk (the selection), HOLD -13,068 [-24,249, -1,601] (MDE 16,573), 2023 span -3,922, by year -2,829 / +3,202 / -1,538 / -25,589; in-session HOLD $/wk tuned -6,267 vs live 6,801.
- **Tuned winners that are themselves SESSION-CANDIDATE (PRE CI > 0, HOLD > 0 in both HOLD years, MEASURED):** 2 - KB NY-AM (k=10,n=14,m=0.5,na=20): PRE CI low 749, HOLD 2,599 (live 4,889), H25 2,729, H26 1,583, X -1,375, HOLD one-sided p 0.165 ; MV NY-AM (lbs=(5, 10, 20, 40, 80),thr=0.25,k=3): PRE CI low 993, HOLD 3,399 (live 4,815), H25 2,103, H26 8,667, X -3,270, HOLD one-sided p 0.224. Both are NY-AM cells of engines whose LIVE set is already a SESSION-CANDIDATE carrier in the same session with a higher HOLD mean (KB NY-AM live 4,889 vs tuned 2,599; MV NY-AM live 4,815 vs 3,399). **New session books found: ASIA 0, LONDON 0, NY-AM 0 (2 candidates that duplicate existing carriers at a lower HOLD), NY-PM 0.** SESSION-PASS (HOLD one-sided p <= 0.05/40 = 0.00125) none.
- **Stack-add (MEASURED P for the swapped book, other five books unchanged, 8 stack-book winners incl. the disclosed non-tier extras):** no HOLD add has a CI above zero or exceeds its MDE (KB NY-AM -626 [-5,269, 4,204]; KB ASIA -4,677; PE ASIA -5,330; the positive ones, PE NY-AM +3,519, PE NY-PM +1,889, KB LONDON +1,219, SM LONDON +1,249, WT NY-PM +1,480, are inside MDE 4.5-6.6k and not tier-eligible). Table 3.
- **Survivors for the replay:** 6 winners are tier-alive on the STORED basis (PRE stored CI > 0, n >= 100, stored HOLD > 0 in both HOLD years) and are in `out/sd2b/survivors_for_A.parquet` (HM ASIA 1,278 entries, KB NY-PM 1,018, MA NY-AM 579, MV NY-AM 2,132, PE NY-PM 1,390, PE ASIA 952; entries.parquet schema + cell + session; lc 10, 240/240 ticks). On the analytic MEASURED basis 2 of them are positive in HOLD in both years (MV NY-AM, PE NY-PM) and none beats its live twin; the replay is the check, not a promotion.
- **What it means for the live books:** nothing in this search supports changing KB/SM/PE/ST/HM/WT/MA/MV/DN/CR parameters for a session. The live parameter sets are not obviously PRE-optimal (PRE deltas are large and positive for the max-of-30) but that edge does not survive HOLD: ASIA is the worst place to tune (mean HOLD delta -3,802/wk, DN ASIA -13,068), NY-AM the least bad (-396).

## Method in one paragraph
Hybrid book = the live engine's own events outside the session plus a candidate parameter set's events inside it, one shared busy chain, regenerated through the exact generators (identity with the live rows checked: ST/HM/WT/KB/SM bk_lib rows, PE books.pkl (ei, side), MA/MV tr1 lists, DN d4a/don_T), 1-s path, live bracket (60/60; WT 45 / 0.75R), live entry windows. Basis MEASURED (tier): entry +1 tick (DN: the measured stop-market entry slip), stop exits raw - slip(year, lots) with NO mapped stop credit, target exits + year Target correction, time exits + year correction; STORED (screen label) = raw + mapping for every exit; CONSERVATIVE (label) = MEASURED with 0.5 pt more on stops and 0.25 more on all. Stage 1 (PRE 2024-02..2025-06 only; HOLD/X days zeroed before storing): unlocked weekly in-session MEASURED mean for all 2920 hybrid books (657 + 73 configs x 4 sessions). Stage 2: top 30 per book-session through sl_lib.run_book (the stack lock engine) and the PRE winner. One HOLD (2025-07-01..2026-02-06) and one X (2023-04..2024-01) look per winner (`looks.jsonl`, 40 lines, F_look = 40, best-of-F threshold 0.00125, a label). MDE = 2.8 SD/sqrt(weeks) of the paired weekly difference; CI = 10,000-draw weekly bootstrap. Session = ENTRY session (ASIA 18:00-02:00, LONDON 02:00-08:30, NY-AM 09:30-12:00, NY-PM 12:00-15:00; PRE/CLOSE not tuned).

## Table 1 - per book-session: live vs PRE-chosen winner (in-session post-lock MEASURED $/wk at 10 lots, WT 7)
| book | session | live params | winner (tuned) params | live PRE | winner PRE | PRE delta [CI] (MDE) | live HOLD | winner HOLD | HOLD delta [CI] (MDE) | X (2023 span) delta | H25 / H26 delta | beats live | tier (winner as a session book) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | ASIA | per=120,mult=2.0,ema=200 | per=120,mult=1.0,ema=100 | 595 | 7,381 | 6,785 [-510, 13,714] (10,349) | -2,573 | -5,362 | -2,789 [-13,306, 8,107] (15,714) | -2,262 | -2,526 / -3,508 | no | none |
| ST | LONDON | per=120,mult=2.0,ema=200 | per=30,mult=1.5,ema=200 | -684 | 410 | 1,094 [-1,326, 3,608] (3,572) | 3,671 | 465 | -3,206 [-5,714, -1,093] (3,441) | 852 | -3,427 / -1,680 | no | none |
| ST | NY-AM | per=120,mult=2.0,ema=200 | per=120,mult=1.0,ema=200 | 546 | 5,462 | 4,917 [-381, 10,347] (7,731) | 2,074 | 2,557 | 483 [-5,385, 6,549] (8,708) | -1,696 | 1,436 / -3,887 | no | none |
| ST | NY-PM | per=120,mult=2.0,ema=200 | per=240,mult=1.0,ema=400 | 395 | 2,990 | 2,595 [-565, 5,809] (4,581) | 4,309 | 3,012 | -1,296 [-5,812, 3,157] (6,488) | 494 | 861 / -10,786 | no | none |
| HM | ASIA | f=20,s=55,ema=200 | f=15,s=35,ema=100 | 3,060 | 8,473 | 5,412 [-1,468, 12,391] (9,946) | 6,761 | 1,370 | -5,391 [-18,182, 7,885] (19,210) | -5,745 | -7,419 / 4,634 | no | none |
| HM | LONDON | f=20,s=55,ema=200 | f=30,s=120,ema=100 | -83 | 4,229 | 4,312 [-2,190, 10,572] (8,984) | -4,109 | -5,564 | -1,455 [-11,421, 7,884] (14,124) | 3,059 | -3,845 / 9,543 | no | none |
| HM | NY-AM | f=20,s=55,ema=200 | f=20,s=35,ema=100 | 1,013 | 5,841 | 4,828 [-951, 10,640] (8,237) | -4,732 | -5,823 | -1,091 [-8,302, 6,231] (10,390) | 1,286 | -1,204 / -401 | no | none |
| HM | NY-PM | f=20,s=55,ema=200 | f=30,s=55,ema=100 | -957 | 577 | 1,534 [-2,649, 5,776] (6,019) | -933 | -1,787 | -855 [-6,834, 4,934] (8,469) | -1,661 | -1,477 / 2,090 | no | none |
| WT | ASIA | an=20,mult=2.0,ema=100 | an=10,mult=1.5,ema=50 | 107 | 2,992 | 2,886 [-89, 5,821] (4,190) | -389 | -3,715 | -3,326 [-8,635, 1,908] (7,779) | 2,378 | -5,446 / 6,767 | no | none |
| WT | LONDON | an=20,mult=2.0,ema=100 | an=10,mult=2.0,ema=200 | -2,621 | -656 | 1,965 [-660, 4,701] (3,823) | -2,522 | -2,347 | 175 [-2,753, 2,815] (3,988) | -1,930 | 1,397 / -5,355 | no | none |
| WT | NY-AM | an=20,mult=2.0,ema=100 | an=40,mult=1.5,ema=50 | -541 | 870 | 1,411 [-1,244, 4,061] (3,764) | 2,650 | 1,661 | -989 [-4,927, 2,829] (5,753) | 392 | -567 / -2,723 | no | none |
| WT | NY-PM | an=20,mult=2.0,ema=100 | an=20,mult=1.5,ema=200 | -2,158 | -831 | 1,327 [-324, 3,009] (2,400) | -6,090 | -4,611 | 1,480 [-1,520, 4,951] (4,749) | -451 | 520 / 5,550 | no | none |
| KB | ASIA | k=3,n=14,m=1.0,na=10 | k=2,n=30,m=1.5,na=14 | 4,407 | 10,896 | 6,489 [-485, 13,697] (10,320) | 3,583 | -2,426 | -6,008 [-17,939, 6,093] (17,459) | 278 | -7,448 / 1,474 | no | none |
| KB | LONDON | k=3,n=14,m=1.0,na=10 | k=3,n=8,m=0.5,na=20 | 2,270 | 3,641 | 1,371 [-4,007, 6,715] (7,737) | 5,743 | 7,858 | 2,115 [-6,370, 11,189] (12,707) | -325 | 1,011 / 6,732 | no | none |
| KB | NY-AM | k=3,n=14,m=1.0,na=10 | k=10,n=14,m=0.5,na=20 | 1,289 | 4,926 | 3,638 [-1,420, 8,828] (7,391) | 4,889 | 2,599 | -2,290 [-12,583, 9,462] (16,203) | 419 | -3,454 / 3,329 | no | SESSION-CANDIDATE (not best-of-F) |
| KB | NY-PM | k=3,n=14,m=1.0,na=10 | k=2,n=30,m=2.0,na=20 | 2,917 | 4,447 | 1,530 [-2,640, 5,605] (5,877) | -340 | -2,671 | -2,331 [-9,662, 4,497] (10,191) | -587 | -5,015 / 10,133 | no | none |
| SM | ASIA | k=10,n=7,m=3.0 | k=5,n=10,m=5.0 | 4,797 | 4,858 | 62 [-3,479, 3,369] (4,933) | 209 | -1,516 | -1,725 [-9,244, 4,841] (10,258) | 1,064 | 973 / -13,578 | no | none |
| SM | LONDON | k=10,n=7,m=3.0 | k=10,n=10,m=3.0 | 149 | 3,312 | 3,162 [179, 6,261] (4,409) | 19 | 1,359 | 1,340 [-2,073, 4,969] (5,128) | 295 | 3,431 / -8,294 | no | none |
| SM | NY-AM | k=10,n=7,m=3.0 | k=20,n=10,m=2.0 | 1,969 | 4,927 | 2,958 [49, 5,882] (4,146) | -941 | -968 | -27 [-5,504, 5,371] (7,955) | 2,651 | 353 / -1,735 | no | none |
| SM | NY-PM | k=10,n=7,m=3.0 | k=5,n=7,m=3.0 | -729 | 1,502 | 2,230 [-2,335, 6,781] (6,595) | -201 | -1,375 | -1,174 [-7,513, 5,180] (9,389) | 4,540 | -1,691 / 1,346 | no | none |
| PE | ASIA | R=5,P=1,ptype=0,ttype=1 | R=3,P=1,ptype=1,ttype=1 | 4,489 | 7,355 | 2,865 [-6,188, 11,671] (12,707) | 3,634 | -509 | -4,143 [-18,175, 10,300] (20,626) | 1,111 | -7,645 / 12,306 | no | none |
| PE | LONDON | R=5,P=1,ptype=0,ttype=1 | R=3,P=1,ptype=1,ttype=0 | -4,403 | 3,548 | 7,951 [1,202, 14,732] (9,671) | 6,990 | 3,099 | -3,891 [-10,831, 2,937] (10,031) | 2,240 | -4,289 / -1,454 | no | none |
| PE | NY-AM | R=5,P=1,ptype=0,ttype=1 | R=3,P=1,ptype=0,ttype=0 | 2,891 | 4,811 | 1,919 [-2,702, 6,591] (6,612) | -154 | 3,973 | 4,127 [-3,315, 11,213] (10,515) | -1,767 | -170 / 22,776 | no | none |
| PE | NY-PM | R=5,P=1,ptype=0,ttype=1 | R=15,P=1,ptype=0,ttype=0 | 2,330 | 2,892 | 562 [-3,283, 4,473] (5,638) | -1,560 | 2,204 | 3,765 [-1,860, 10,226] (8,783) | 1,354 | 4,075 / 1,741 | no | none |
| MA | ASIA | k=10,fast=0.5,slow=0.05 | k=10,fast=0.5,slow=0.1 | 2,663 | 4,589 | 1,926 [-2,786, 6,512] (6,638) | -5,090 | -4,099 | 990 [-4,879, 6,870] (8,450) | -398 | 2,504 / -5,986 | no | none |
| MA | LONDON | k=10,fast=0.5,slow=0.05 | k=5,fast=0.25,slow=0.05 | 1,842 | 3,543 | 1,701 [-2,463, 6,065] (6,119) | 5,920 | 4,748 | -1,172 [-8,480, 5,916] (10,390) | 198 | -4,375 / 13,436 | no | none |
| MA | NY-AM | k=10,fast=0.5,slow=0.05 | k=10,fast=0.75,slow=0.05 | 3,041 | 6,537 | 3,496 [-666, 7,551] (5,840) | 845 | -595 | -1,441 [-7,067, 3,860] (7,845) | -3,225 | -2,847 / 5,128 | no | none |
| MA | NY-PM | k=10,fast=0.5,slow=0.05 | k=3,fast=0.5,slow=0.02 | -747 | 4,189 | 4,935 [-712, 10,258] (7,953) | 5,379 | 361 | -5,018 [-11,739, 1,945] (9,800) | -314 | -6,108 / 720 | no | none |
| MV | ASIA | lbs=(15, 30, 60, 120, 240),thr=0.5,k=4 | lbs=(30, 60, 120, 240, 480),thr=0.5,k=3 | 4,019 | 7,433 | 3,415 [-2,972, 10,104] (9,420) | -7,876 | -10,005 | -2,129 [-13,950, 8,332] (16,495) | 5,691 | 2,391 / -22,114 | no | none |
| MV | LONDON | lbs=(15, 30, 60, 120, 240),thr=0.5,k=4 | lbs=(30, 60, 120, 240, 480),thr=1.0,k=5 | -2,919 | 129 | 3,048 [-2,320, 8,321] (7,753) | 2,492 | -2,942 | -5,433 [-12,268, 1,248] (9,834) | 3,446 | -9,762 / 14,950 | no | none |
| MV | NY-AM | lbs=(15, 30, 60, 120, 240),thr=0.5,k=4 | lbs=(5, 10, 20, 40, 80),thr=0.25,k=3 | 5,427 | 7,763 | 2,336 [-2,976, 7,562] (7,726) | 4,815 | 3,399 | -1,416 [-11,147, 7,913] (13,818) | 5,087 | -792 / -3,986 | no | SESSION-CANDIDATE (not best-of-F) |
| MV | NY-PM | lbs=(15, 30, 60, 120, 240),thr=0.5,k=4 | lbs=(15, 30, 60, 120, 240),thr=0.25,k=4 | -358 | 3,567 | 3,925 [1,497, 6,682] (3,750) | -58 | -2,284 | -2,226 [-5,957, 1,153] (5,168) | -3,768 | -1,295 / -6,047 | no | none |
| DN | ASIA | k=15,n=20 | k=3,n=30 | 3,830 | 9,364 | 5,534 [-1,302, 12,444] (9,954) | 6,801 | -6,267 | -13,068 [-24,249, -1,601] (16,573) | -3,922 | -9,801 / -25,589 | no | none |
| DN | LONDON | k=15,n=20 | k=5,n=20 | -21 | 4,258 | 4,279 [-975, 9,836] (7,749) | -1,138 | -4,338 | -3,200 [-9,354, 3,164] (9,174) | -4,718 | -1,830 / -8,828 | no | none |
| DN | NY-AM | k=15,n=20 | k=10,n=30 | 6,935 | 8,010 | 1,075 [-2,605, 4,716] (5,228) | -3,087 | -5,088 | -2,001 [-6,522, 2,795] (6,917) | -932 | -1,116 / -5,648 | no | none |
| DN | NY-PM | k=15,n=20 | k=10,n=40 | -1,274 | -172 | 1,102 [-863, 3,085] (2,837) | 2,752 | 313 | -2,439 [-6,150, 181] (4,734) | 600 | -2,891 / 0 | no | none |
| CR | ASIA | htf=240,etf=5,etype=close,tmode=SO,buf=0 | htf=240,etf=5,etype=close,tmode=NB,buf=0 | -736 | -459 | 278 [-1,282, 1,897] (2,260) | -7,037 | -7,470 | -432 [-2,157, 1,355] (2,541) | 18 | -58 / -2,045 | no | none |
| CR | LONDON | htf=240,etf=5,etype=close,tmode=SO,buf=0 | htf=240,etf=5,etype=csd,tmode=SO,buf=5 | -3,045 | -810 | 2,235 [-337, 4,703] (3,652) | -974 | -3,838 | -2,865 [-7,173, 1,429] (6,313) | -1,106 | -2,834 / -2,526 | no | none |
| CR | NY-AM | htf=240,etf=5,etype=close,tmode=SO,buf=0 | htf=240,etf=15,etype=close,tmode=SO,buf=0 | -2,197 | -144 | 2,053 [-653, 4,872] (3,987) | -4,382 | -3,692 | 690 [-3,954, 4,959] (6,559) | 1,646 | 287 / 2,388 | no | none |
| CR | NY-PM | htf=240,etf=5,etype=close,tmode=SO,buf=0 | htf=240,etf=5,etype=close,tmode=NB,buf=0 | 972 | 1,165 | 193 [-878, 1,222] (1,523) | 470 | 339 | -131 [-1,047, 577] (1,204) | 116 | -299 / 645 | no | none |

## Table 2 - by year, and the three fill bases (winner minus live, $/wk; years pool PRE/HOLD/X windows that fall in the year)
| book | session | 2023 | 2024 | 2025 | 2026 | HOLD MEAS delta | HOLD STORED delta | HOLD CONS delta | HOLD MEAS: winner / live | n HOLD trades winner / live |
|---|---|---|---|---|---|---|---|---|---|---|
| ST | ASIA | -4,670 | 5,915 | 3,959 | -3,508 | -2,789 | -5,625 | -2,797 | -5,362 / -2,573 | 304 / 288 |
| ST | LONDON | 961 | 1,044 | -1,242 | -1,680 | -3,206 | -4,913 | -3,205 | 465 / 3,671 | 130 / 133 |
| ST | NY-AM | -1,828 | 6,576 | 1,051 | -3,887 | 483 | -3,992 | -122 | 2,557 / 2,074 | 193 / 166 |
| ST | NY-PM | 296 | 2,445 | 1,857 | -10,786 | -1,296 | -1,695 | -1,329 | 3,012 / 4,309 | 73 / 57 |
| HM | ASIA | -7,095 | 6,765 | -2,434 | 4,634 | -5,391 | -8,372 | -5,535 | 1,370 / 6,761 | 299 / 268 |
| HM | LONDON | 1,803 | 3,710 | 1,646 | 9,543 | -1,455 | -4,120 | -1,400 | -5,564 / -4,109 | 126 / 149 |
| HM | NY-AM | 1,608 | 3,566 | 2,537 | -401 | -1,091 | -2,066 | -1,587 | -5,823 / -4,732 | 135 / 106 |
| HM | NY-PM | -1,432 | -768 | 1,861 | 2,090 | -855 | 2,736 | -850 | -1,787 / -933 | 82 / 73 |
| WT | ASIA | 2,121 | 3,954 | -2,232 | 6,767 | -3,326 | -2,116 | -3,346 | -3,715 / -389 | 456 / 434 |
| WT | LONDON | -1,240 | 1,133 | 1,669 | -5,355 | 175 | -607 | 132 | -2,347 / -2,522 | 262 / 256 |
| WT | NY-AM | 18 | 2,793 | -772 | -2,723 | -989 | -2,483 | -1,391 | 1,661 / 2,650 | 205 / 152 |
| WT | NY-PM | -691 | 1,837 | 440 | 5,550 | 1,480 | 2,472 | 1,557 | -4,611 / -6,090 | 150 / 125 |
| KB | ASIA | 630 | 8,254 | -3,098 | 1,474 | -6,008 | -6,643 | -6,089 | -2,426 / 3,583 | 296 / 308 |
| KB | LONDON | -262 | 498 | 1,880 | 6,732 | 2,115 | -1,717 | 1,282 | 7,858 / 5,743 | 143 / 144 |
| KB | NY-AM | 45 | 4,557 | -855 | 3,329 | -2,290 | 4,863 | -2,857 | 2,599 / 4,889 | 85 / 156 |
| KB | NY-PM | -81 | -951 | 134 | 10,133 | -2,331 | 38 | -1,713 | -2,671 / -340 | 69 / 84 |
| SM | ASIA | 1,180 | -367 | 966 | -13,578 | -1,725 | -1,032 | -1,717 | -1,516 / 209 | 105 / 110 |
| SM | LONDON | -281 | 3,843 | 2,831 | -8,294 | 1,340 | 2,086 | 1,327 | 1,359 / 19 | 95 / 89 |
| SM | NY-AM | 3,137 | 1,779 | 2,479 | -1,735 | -27 | -1,708 | -40 | -968 / -941 | 56 / 47 |
| SM | NY-PM | 3,864 | 3,320 | -100 | 1,346 | -1,174 | -691 | -1,298 | -1,375 / -201 | 68 / 25 |
| PE | ASIA | 2,127 | 1,612 | -2,094 | 12,306 | -4,143 | -7,163 | -3,960 | -509 / 3,634 | 215 / 303 |
| PE | LONDON | 3,112 | 3,675 | 4,962 | -1,454 | -3,891 | -2,667 | -3,801 | 3,099 / 6,990 | 100 / 134 |
| PE | NY-AM | -1,066 | 2,822 | -875 | 22,776 | 4,127 | -227 | 3,849 | 3,973 / -154 | 187 / 157 |
| PE | NY-PM | 2,940 | -1,277 | 3,109 | 1,741 | 3,765 | 5,768 | 3,738 | 2,204 / -1,560 | 82 / 74 |
| MA | ASIA | 183 | 200 | 3,336 | -5,986 | 990 | 2,822 | 973 | -4,099 / -5,090 | 171 / 164 |
| MA | LONDON | 1,153 | 2,311 | -2,816 | 13,436 | -1,172 | -4,585 | -1,186 | 4,748 / 5,920 | 98 / 93 |
| MA | NY-AM | -2,853 | -240 | 3,159 | 5,128 | -1,441 | -716 | -1,511 | -595 / 845 | 105 / 85 |
| MA | NY-PM | -1,568 | 5,424 | -659 | 720 | -5,018 | -5,037 | -5,168 | 361 / 5,379 | 121 / 48 |
| MV | ASIA | 4,600 | 9,175 | -1,785 | -22,114 | -2,129 | -445 | -2,108 | -10,005 / -7,876 | 254 / 269 |
| MV | LONDON | 3,166 | 2,168 | -2,298 | 14,950 | -5,433 | -5,033 | -5,330 | -2,942 / 2,492 | 79 / 149 |
| MV | NY-AM | 6,022 | 3,101 | -408 | -3,986 | -1,416 | 1,680 | -1,705 | 3,399 / 4,815 | 185 / 145 |
| MV | NY-PM | -3,616 | 3,227 | 1,201 | -6,047 | -2,226 | -2,513 | -2,218 | -2,284 / -58 | 64 / 55 |
| DN | ASIA | -2,829 | 3,202 | -1,538 | -25,589 | -13,068 | -8,921 | -13,301 | -6,267 / 6,801 | 280 / 203 |
| DN | LONDON | -4,899 | 3,773 | 1,037 | -8,828 | -3,200 | -5,529 | -3,400 | -4,338 / -1,138 | 202 / 137 |
| DN | NY-AM | -884 | 180 | 649 | -5,648 | -2,001 | -1,462 | -2,258 | -5,088 / -3,087 | 157 / 132 |
| DN | NY-PM | 350 | 828 | -501 | 0 | -2,439 | -2,929 | -2,469 | 313 / 2,752 | 46 / 40 |
| CR | ASIA | 189 | 908 | -668 | -2,045 | -432 | -779 | -414 | -7,470 / -7,037 | 205 / 199 |
| CR | LONDON | -1,013 | 2,225 | -678 | -2,526 | -2,865 | -6,569 | -2,435 | -3,838 / -974 | 58 / 166 |
| CR | NY-AM | 1,407 | 1,664 | 1,719 | 2,388 | 690 | -762 | 849 | -3,692 / -4,382 | 61 / 107 |
| CR | NY-PM | -54 | -107 | 363 | 645 | -131 | -136 | -128 | 339 / 470 | 64 / 64 |
Mean over the 40: delta 2023 +114, 2024 +2,619, 2025 +445, 2026 -262 (the 2024 positive is PRE, the selection window); HOLD delta MEASURED -1,745, STORED -2,020, CONSERVATIVE -1,824 (STORED positive in 8, CONSERVATIVE in 8 of 40): the conclusion does not depend on the basis.

## Table 3 - stack-add (exact stack, book swapped live-hybrid -> winner-hybrid; MEASURED P for the swapped book)
| book | session | PRE add $/wk | HOLD add [CI] (MDE) | X add | HOLD maxDD base -> cand | HOLD worst-20-wk $ base -> cand | HOLD stack mean live-hybrid |
|---|---|---|---|---|---|---|---|
| KB | NY-AM | 3,622 [234, 7,276] | -626 [-5,269, 4,204] (6,869) | 2,389 [-3,007, 7,640] | 575,051 -> 582,445 | -754,847 -> -698,278 | 49,088 |
| KB | ASIA | 5,537 [1,277, 10,154] | -4,677 [-10,619, 1,351] (8,819) | -1,807 [-6,602, 3,071] | 575,051 -> 611,178 | -754,847 -> -785,683 | 49,088 |
| KB | LONDON | -1,209 [-5,081, 2,645] | 1,219 [-3,053, 5,464] (6,185) | 1,574 [-3,983, 7,537] | 575,051 -> 575,684 | -754,847 -> -705,119 | 49,088 |
| PE | ASIA | -47 [-6,430, 6,435] | -5,330 [-14,700, 4,799] (14,229) | 2,308 [-4,274, 8,922] | 610,371 -> 600,261 | -887,059 -> -974,469 | 43,798 |
| PE | NY-AM | 1,144 [-1,280, 3,612] | 3,519 [-1,150, 8,023] (6,594) | -2,359 [-7,173, 2,309] | 610,371 -> 609,688 | -887,059 -> -835,625 | 43,798 |
| PE | NY-PM | 111 [-2,000, 2,212] | 1,889 [-1,048, 5,188] (4,516) | 956 [-2,146, 4,048] | 610,371 -> 611,771 | -887,059 -> -853,179 | 43,798 |
| SM | LONDON | 1,334 [-1,054, 3,792] | 1,249 [-2,049, 4,451] (4,660) | 456 [-1,460, 2,420] | 605,295 -> 590,045 | -855,776 -> -851,425 | 46,990 |
| WT | NY-PM | 1,308 [-338, 2,967] | 1,480 [-1,520, 4,951] (4,749) | -451 [-2,249, 1,267] | 613,556 -> 613,901 | -962,189 -> -948,530 | 42,179 |
KB NY-AM is the only criterion-eligible row (tier-CANDIDATE winner); the others are disclosed extras (the directive's carriers KB ASIA and PE ASIA, and every stack-book winner with a positive HOLD delta). PRE adds for KB ASIA (+5,537 [1,277, ...]) and KB NY-AM (+3,622 [234, ...]) are the in-sample selection and reverse in HOLD (-4,677, -626).

## Table 4 - never empty-handed: the live set and the PRE top 10 (post-lock PRE in-session $/wk) in the six carrier cells (all 40 book-sessions: `out/sd2b/pre_top10.csv`)
| carrier | rank | cfg | n PRE | PRE mean (unlocked MEAS top-30 -> locked) | PRE delta vs live [CI] | MDE |
|---|---|---|---|---|---|---|
| KB ASIA | LIVE | k=3,n=14,m=1.0,na=10 | 669 | 4,407 | - | 11,053 |
| KB ASIA | 1 | k=2,n=30,m=1.5,na=14 | 648 | 10,896 | 6,489 [-485, 13,697] | 10,320 |
| KB ASIA | 2 | k=2,n=30,m=1.0,na=14 | 672 | 10,751 | 6,344 [-1,218, 14,158] | 11,097 |
| KB ASIA | 3 | k=2,n=30,m=1.5,na=20 | 652 | 10,657 | 6,250 [-1,537, 14,087] | 11,171 |
| KB ASIA | 4 | k=2,n=30,m=1.5,na=7 | 665 | 10,231 | 5,824 [-1,484, 13,365] | 10,761 |
| KB ASIA | 5 | k=2,n=30,m=1.0,na=20 | 675 | 9,505 | 5,098 [-2,655, 12,956] | 11,292 |
| KB ASIA | 6 | k=3,n=14,m=1.0,na=20 | 653 | 9,328 | 4,921 [-1,364, 11,211] | 9,005 |
| KB ASIA | 7 | k=3,n=14,m=0.5,na=10 | 680 | 9,212 | 4,805 [-3,287, 12,811] | 11,770 |
| KB ASIA | 8 | k=2,n=30,m=1.0,na=10 | 670 | 9,025 | 4,618 [-3,035, 12,562] | 11,385 |
| KB ASIA | 9 | k=2,n=30,m=2.0,na=20 | 640 | 9,023 | 4,616 [-3,355, 12,610] | 11,432 |
| KB ASIA | 10 | k=2,n=30,m=2.0,na=7 | 667 | 9,019 | 4,612 [-3,683, 13,083] | 12,033 |
| PE ASIA | LIVE | R=5,P=1,ptype=0,ttype=1 | 674 | 4,489 | - | 11,503 |
| PE ASIA | 1 | R=3,P=1,ptype=1,ttype=1 | 492 | 7,355 | 2,865 [-6,188, 11,671] | 12,707 |
| PE ASIA | 2 | R=3,P=2,ptype=0,ttype=0 | 652 | 5,703 | 1,213 [-6,494, 8,951] | 11,009 |
| PE ASIA | 3 | R=3,P=2,ptype=0,ttype=1 | 637 | 5,380 | 890 [-7,380, 9,462] | 12,045 |
| PE ASIA | 4 | R=3,P=2,ptype=1,ttype=1 | 471 | 4,992 | 503 [-9,606, 10,302] | 14,267 |
| PE ASIA | 5 | R=3,P=2,ptype=1,ttype=0 | 513 | 4,855 | 366 [-9,248, 9,813] | 13,677 |
| PE ASIA | 6 | R=3,P=1,ptype=0,ttype=0 | 712 | 4,774 | 285 [-8,205, 8,640] | 12,174 |
| PE ASIA | 7 | R=3,P=1,ptype=0,ttype=1 | 685 | 4,682 | 192 [-6,523, 7,274] | 9,918 |
| PE ASIA | 8 | R=5,P=3,ptype=0,ttype=1 | 585 | 3,540 | -950 [-6,996, 5,421] | 8,994 |
| PE ASIA | 9 | R=5,P=2,ptype=0,ttype=1 | 635 | 3,265 | -1,224 [-7,163, 4,682] | 8,534 |
| PE ASIA | 10 | R=3,P=1,ptype=1,ttype=0 | 536 | 3,055 | -1,435 [-10,323, 7,224] | 12,669 |
| DN ASIA | LIVE | k=15,n=20 | 423 | 3,830 | - | 8,796 |
| DN ASIA | 1 | k=3,n=30 | 632 | 9,364 | 5,534 [-1,302, 12,444] | 9,954 |
| DN ASIA | 2 | k=5,n=10 | 660 | 8,797 | 4,967 [-2,832, 12,594] | 11,225 |
| DN ASIA | 3 | k=5,n=20 | 630 | 8,703 | 4,873 [-1,611, 11,381] | 9,612 |
| DN ASIA | 4 | k=3,n=40 | 622 | 7,364 | 3,534 [-3,067, 10,253] | 9,577 |
| DN ASIA | 5 | k=10,n=10 | 604 | 6,882 | 3,052 [-3,749, 9,770] | 9,687 |
| DN ASIA | 6 | k=3,n=60 | 573 | 4,508 | 678 [-5,349, 6,685] | 8,780 |
| DN ASIA | 7 | k=30,n=10 | 387 | 4,506 | 676 [-2,688, 3,732] | 4,540 |
| DN ASIA | 8 | k=5,n=40 | 552 | 4,063 | 233 [-5,826, 6,476] | 8,973 |
| DN ASIA | 9 | k=5,n=60 | 455 | 3,620 | -210 [-3,398, 3,047] | 4,717 |
| DN ASIA | 10 | k=10,n=20 | 526 | 3,519 | -311 [-5,616, 4,900] | 7,590 |
| KB NY-PM | LIVE | k=3,n=14,m=1.0,na=10 | 205 | 2,917 | - | 6,957 |
| KB NY-PM | 1 | k=2,n=30,m=2.0,na=20 | 187 | 4,447 | 1,530 [-2,640, 5,605] | 5,877 |
| KB NY-PM | 2 | k=1,n=14,m=1.5,na=14 | 230 | 4,160 | 1,242 [-3,217, 5,821] | 6,417 |
| KB NY-PM | 3 | k=1,n=14,m=2.0,na=10 | 183 | 4,093 | 1,176 [-3,571, 6,198] | 7,013 |
| KB NY-PM | 4 | k=1,n=14,m=2.0,na=20 | 185 | 4,091 | 1,173 [-3,258, 5,901] | 6,556 |
| KB NY-PM | 5 | k=2,n=8,m=1.0,na=14 | 222 | 3,880 | 962 [-3,411, 5,429] | 6,268 |
| KB NY-PM | 6 | k=1,n=14,m=2.0,na=14 | 184 | 3,788 | 871 [-3,689, 5,690] | 6,774 |
| KB NY-PM | 7 | k=3,n=30,m=2.0,na=14 | 156 | 3,697 | 779 [-4,368, 5,918] | 7,442 |
| KB NY-PM | 8 | k=2,n=20,m=1.5,na=14 | 221 | 3,451 | 534 [-2,747, 3,929] | 4,830 |
| KB NY-PM | 9 | k=2,n=30,m=2.0,na=14 | 193 | 3,316 | 398 [-3,004, 3,824] | 4,934 |
| KB NY-PM | 10 | k=3,n=20,m=2.0,na=10 | 152 | 3,204 | 286 [-4,952, 5,432] | 7,452 |
| HM NY-AM | LIVE | f=20,s=55,ema=200 | 252 | 1,013 | - | 6,219 |
| HM NY-AM | 1 | f=20,s=35,ema=100 | 327 | 5,841 | 4,828 [-951, 10,640] | 8,237 |
| HM NY-AM | 2 | f=15,s=35,ema=100 | 319 | 5,457 | 4,444 [-694, 9,665] | 7,408 |
| HM NY-AM | 3 | f=15,s=35,ema=200 | 304 | 5,103 | 4,090 [-754, 9,056] | 7,035 |
| HM NY-AM | 4 | f=15,s=35,ema=400 | 294 | 4,968 | 3,955 [-1,165, 9,116] | 7,333 |
| HM NY-AM | 5 | f=20,s=35,ema=200 | 318 | 4,871 | 3,858 [-1,403, 9,366] | 7,649 |
| HM NY-AM | 6 | f=20,s=35,ema=400 | 310 | 4,441 | 3,428 [-1,845, 9,009] | 7,683 |
| HM NY-AM | 7 | f=20,s=80,ema=200 | 207 | 4,220 | 3,208 [-1,427, 7,910] | 6,589 |
| HM NY-AM | 8 | f=20,s=80,ema=400 | 191 | 4,182 | 3,169 [-1,188, 7,608] | 6,286 |
| HM NY-AM | 9 | f=20,s=80,ema=100 | 224 | 3,632 | 2,619 [-1,655, 6,879] | 6,079 |
| HM NY-AM | 10 | f=10,s=80,ema=100 | 251 | 3,510 | 2,497 [-2,705, 7,516] | 7,269 |
| MV NY-AM | LIVE | lbs=(15, 30, 60, 120, 240),thr=0.5,k=4 | 396 | 5,427 | - | 9,614 |
| MV NY-AM | 1 | lbs=(5, 10, 20, 40, 80),thr=0.25,k=3 | 492 | 7,763 | 2,336 [-2,976, 7,562] | 7,726 |
| MV NY-AM | 2 | lbs=(15, 30, 60, 120, 240),thr=0.75,k=3 | 400 | 6,631 | 1,204 [-3,765, 6,279] | 7,099 |
| MV NY-AM | 3 | lbs=(5, 10, 20, 40, 80),thr=0.25,k=5 | 472 | 6,468 | 1,041 [-4,686, 6,714] | 8,139 |
| MV NY-AM | 4 | lbs=(30, 60, 120, 240, 480),thr=0.5,k=5 | 298 | 5,575 | 148 [-4,927, 5,050] | 7,072 |
| MV NY-AM | 5 | lbs=(5, 10, 20, 40, 80),thr=1.0,k=5 | 305 | 4,749 | -678 [-6,232, 5,114] | 8,101 |
| MV NY-AM | 6 | lbs=(5, 10, 20, 40, 80),thr=1.0,k=3 | 493 | 4,581 | -846 [-5,970, 4,630] | 7,607 |
| MV NY-AM | 7 | lbs=(15, 30, 60, 120, 240),thr=0.25,k=5 | 410 | 4,503 | -924 [-5,284, 3,407] | 6,301 |
| MV NY-AM | 8 | lbs=(30, 60, 120, 240, 480),thr=0.75,k=4 | 313 | 4,334 | -1,093 [-7,022, 4,609] | 8,284 |
| MV NY-AM | 9 | lbs=(30, 60, 120, 240, 480),thr=0.25,k=5 | 334 | 4,187 | -1,240 [-6,009, 3,585] | 6,800 |
| MV NY-AM | 10 | lbs=(5, 10, 20, 40, 80),thr=1.0,k=4 | 421 | 3,896 | -1,531 [-7,107, 4,058] | 7,905 |

## Which direction the PRE screen moves the parameters (descriptive, not a finding)
The PRE winners are mostly FASTER / LOOSER versions of the live set (ST mult 1.0 instead of 2.0 in ASIA/NY-AM, HM s=35 ema=100 in ASIA/NY-AM, WT an=10 ASIA, KB 2-min bars, MV the short 5-80 min lookback set in NY-AM (the slower 30-480 set in ASIA/LONDON), DN 3/5-minute Donchian): more trades per week in a window where the MEASURED basis rewards frequency, then the HOLD window gives it back. There is no consistent session-specific parameter: the Asia-optimal Keltner is (k=2, n=30, m=1.5, ATR14), the NY-AM one (k=10, n=14, m=0.5, ATR20), LONDON (k=3, n=8, m=0.5, ATR20), NY-PM (k=2, n=30, m=2.0, ATR20) on PRE, and none is HOLD-positive against the live k=3/n=14/m=1.0/ATR10 (KB ASIA -6,008, LONDON +2,115, NY-AM -2,290, NY-PM -2,331; all inside MDE 10-17k).

## Specs
No cell makes a book (0 beats-live; the 2 tier-candidate winners are inferior to the live twin in the same session). The only parameter statements worth keeping: KB NY-AM tuned = 10-min Keltner, EMA 14, 0.5 x ATR(20) (monitoring/half lots, HOLD +2,599 vs live 4,889); MV NY-AM tuned = vol-normalised-return ensemble on lookbacks 5/10/20/40/80 min, threshold 0.25 sigma, 3 of 5 (HOLD +3,399 vs live 4,815, X -3,270). Neither is recommended over the live set.

## Disclosures and limits
- Basis: the 'live' in-session numbers here are the REGENERATED live rows on the MEASURED analytic basis through sl_lib.run_book (stack lock spec), not the stack's stored P9 series: they differ from DS3_SESSION_1_BOOKS (stored/audit table). The MEASURED stop slip is the 10-lot DN stop-market walk applied to every stop exit (lot curve for WT 7), not a per-trade replay; the survivor rows go to the replay queue. For DN the entry slip replaces the 1-tick entry (stop-market entry). CR scale-out ladders are scored by the row's exit class (combined points) and CR stops are short (median 11 pt): CR MEASURED is the least reliable basis here.
- PE is regenerated with pb3_core (identical (ei, side) to books.pkl PB); live entry-window blocks are applied BEFORE the busy chain for all five stack engines + PE (the stack masks them after), so the reference differs slightly from the stack's PE; the same convention is used for live and tuned. MA/MV use the tr1 gate with the engine WINMASK.
- Stage-1 ranking is UNLOCKED, the winner is picked on the LOCKED PRE number among the 30 (the lock engine changes the ranking: the DN test hybrid was -251k unlocked and +525k locked over the span). A config outside the unlocked top 30 that would win locked is never seen: a bias toward the unlocked ranking; it cannot create the HOLD collapse, which comes from the winners themselves.
- Weeks are iid-bootstrapped (autocorrelated books: CIs slightly narrow). 32 HOLD weeks, 2026 is 5-6 weeks: by-year columns for 2026 are noisy. The 40 winners are not independent (shared sessions, correlated engines): the sign test is descriptive.
- Smoke-test disclosures are in the prereg (whole-history unlocked sums, KB session split of the whole span, DN/CR plumbing tests). Past run bug avoided: argv captured before imports; DAYS has 958 label days in the lib and 953 in dvg_lib (s4 slices to 953).
