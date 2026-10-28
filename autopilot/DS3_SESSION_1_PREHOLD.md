# DS3_SESSION_1_PREHOLD - D3SS1 pre-holdout text (WFPRE 2024-02-01..2025-06-30 ONLY; HOLD and X not computed). 2026-10-28
Prereg l2vast/ds3/prereg/SS1_prereg.md sha256 7a8777305548edb2d1765e8f613257787b720e8327936737385e2bb909ccb32c. Selection rules S1 (block: lowest PRE weekly-mean session with >=100 PRE trades, mean<0) and S2 (carrier: >=100 PRE trades, PRE weekly-mean bootstrap CI above 0) applied to the 11 books ST, HM, WT, KB, SM, PE, MV, MA, DN, CR, PBS (B3, RSI2T are 100% CLOSE, no cell). F = 66.
Books with no block cell: ST (no session with >=100 PRE trades has a negative PRE mean), KB, SM, MA (idem). ST/HM/WT/KB/SM/PE CLOSE has 0 PRE trades (live block); MV 8, MA 11, PBS 4 CLOSE trades: ineligible.

## Block cells (7), PRE only. delta = $/wk change in the stack (stack books, exact engine; PE exact; HM identity with first order) or in the book's own 10-lot $ (Sim books, first-order)
| book | blocked session (ET entry) | n PRE trades | PRE session mean $/wk | PRE delta (first order) [95% CI] | PRE delta (exact, stack books) [CI] | PRE-significant (CI above 0) |
|---|---|---|---|---|---|---|
| HM | NY-PM | 242 | -471 | 471 [-3,288, 4,115] | 471 [-3,288, 4,115] | NO |
| WT | NY-PM | 355 | -1,227 | 1,227 [-1,283, 3,688] | 1,340 [-1,215, 3,863] | NO |
| PE | LONDON | 422 | -900 | 900 [-2,407, 4,141] | -428 [-4,320, 3,369] | NO |
| MV | PRE | 190 | -1,854 | 1,854 [-2,145, 5,884] | n/a | NO |
| DN | NY-PM | 183 | -688 | 688 [-2,854, 4,141] | n/a | NO |
| CR | LONDON | 428 | -1,506 | 1,506 [-833, 3,704] | n/a | NO |
| PBS | NY-PM | 440 | -2,163 | 2,163 [-2,905, 7,138] | n/a | NO |

None of the 7 block cells is PRE-significant (every PRE delta CI includes 0, MDE 3.3k-7.2k per week against deltas 0.5-2.2k): they cannot reach SESSION-CANDIDATE under the prereg tier definition and are carried to the one holdout look for reporting (HOLD, X, by year, placebo rank), as the user's rule says nothing is dropped.

## Carrier cells (7): PRE session mean CI above 0 and >=100 PRE trades
| book | session | n PRE | PRE mean $/wk | CI | MDE |
|---|---|---|---|---|---|
| KB | ASIA | 703 | 4,272 | [184, 8,550] | 5,953 |
| KB | NY-PM | 259 | 3,608 | [1,295, 5,983] | 3,412 |
| PE | ASIA | 666 | 4,219 | [246, 8,331] | 5,837 |
| MV | ASIA | 747 | 9,877 | [1,638, 18,126] | 11,786 |
| MV | NY-AM | 796 | 10,517 | [1,819, 18,919] | 12,242 |
| DN | ASIA | 423 | 7,035 | [1,169, 13,065] | 8,629 |
| DN | NY-AM | 367 | 7,520 | [1,787, 13,137] | 8,167 |

KB ASIA/NY-PM, PE ASIA are stack-weighted $; MV, DN are own 10-lot $ (MV pre-lock approximation).

## Plan for the single look
One logged look (tracks D3SS1 and D3SS1_SPAN2): HOLD 2025-07-01..2026-02-06 and X 2023-04-01..2024-01-31 are read for these 14 cells, the 287-shift placebos of the 7 block cells (each shift re-selects on PRE), and for the descriptive book x session tables of all 11 books (no re-selection).
