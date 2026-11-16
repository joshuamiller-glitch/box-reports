# DS3_FLAT_VS_BOOK - flat stand-in vs book-based cut on the live-equivalent base TL3_EV_JN05W2JL2 (W-EV, user order 11-16)

**VERDICT (data ends 2026-10-30; FIRST PASS, running; 0 of 28 cells have a scored window; windows appear as months land; no PASS claimed).** Reference = TL3_EV_JN05W2JL2 (K7 flat 45 + K7 book cut; P7 book cut (ctx fresh 45/5x/w5/p10, rechase 30/10x/w5/p2) and NO P7 flat). Drawdown first.

## What is live-computable today and what is not
- LIVE TODAY (v1.9b, blind book): the flat stand-ins (K7 -0.75 x stop = 45, P7 -0.70 = 42; price-only, win=1 persist=1) are computable live; the book-based lines (K7 45/10x/w2/p3, P7 40/5x/w5/p3 or the F3 context cells) were NOT, because live read no book on 79% of losing seconds.
- With v1.9c (primary-series book) the clean book the engine uses becomes available: (b) book-based only and the book arm moves (e) are then live-computable; (a) book + flat and the flat level moves (d) are computable now and after v1.9c; (c) flat only is what live effectively ran.
- Engine note: the engine book is the clean one, so engine (b) is what v1.9c should do. Live results of (a)/(c) before v1.9c are NOT comparable to the engine (blind book, section 14 of DS3_ENGINE_VS_LIVE.md).

## Cell map
- ID = JN05W2JL2 with K7 flat re-expressed through la_hooks (must equal JL2); A_* = book + flat (K7 45 live, P7 42 stand-in); B_* = flat off (book only); C_* = flat only (that book cut off by la_hooks scut nocut); D_* = flat level moved (K7 39/51, P7 36/48; both together diagonal); E_* = book arm -10/+10 pts (K7 all sessions floor 15; P7 fresh and rechase); PC_* = persistent random-trigger flats (bucket 300, one draw per 5-min bucket per book and side, never re-drawn) REPLACING that book flat, q 0.05/0.10/0.20: the nonsense rate beside every flat row. Units: 60-pt stop; K7 -0.65/-0.75/-0.85 = 39/45/51 pts, P7 -0.60/-0.70/-0.80 = 36/42/48.
Columns: dd_cut / dd44_cut = max-drawdown cut % vs JL2 (all weeks / W44 removed), ww = worst week $, best5 = share of the reference best-5 weeks kept, w2l = winning weeks turned losing, d_mean / d_mean_484 = $/wk vs JL2 base lots (live x1.75; $4.84 repriced), flat_wk = LaFlat exits per week, flat_usd_wk vs same_entries_noflat_usd_wk = the cut trades vs the same entries without the flat (path effect caution), t / p = weekly-cluster t and sign-flip p.

## L3M
(no cell has all months of this window yet)

## L6M
(no cell has all months of this window yet)

## HOLD
(no cell has all months of this window yet)

## GAP
(no cell has all months of this window yet)

## PRE
(no cell has all months of this window yet)

## X'
(no cell has all months of this window yet)

