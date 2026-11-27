# ALGO_BARE_X (W-DYNC): cross-market management rules for BARE entries, version BX1 (order 1529Z). 27 Nov ~16:10Z. Research only; NO P&L reported here (order 1527Z: management goes straight to the exact engine).
Class: code/th_dync/algo_bare.py, class BareX, path code/th_dync, module algo_bare. Feeds (inst1s, lag 1 s): NQ, ES, RTY (+ YM, ZN, ZB, CL, GC, 6E, 6J, NKD when present in the hook config; rules whose feeds are missing abstain and count in self.miss). Decision every 15 s (param dec_s). No model, no fitting: thresholds fixed in advance.

## ANSWER FIRST
1. The learned model is not a source of rules: W-DYNML withdrew loop C (replay bug, corrected quick screen: no edge). My Asia MF1 "plain rules from loop C" (RulesBook AS1, ALGO_LOOP_A.md PER-BOOK RULES) were read off the invalid model and are WITHDRAWN with it; my own counterfactual had already shown no relation between its predicted advantage and the realised saving. So BX1 is written from the trader's picture, not from a model: "leave a losing trade when the other charts have turned against it and NQ has not followed yet".
2. BX1 RULES (loss side; rows B and D, and C):
 X1 LEADERS HAVE TURNED: ES and RTY 300-s moves against the trade both >= 2.5 own-sigma (sigma of 300-s moves over the previous 2 h) AND trade >= 0.50 R0 under water (R0 = the book's own stop) -> ALL (marketable).
 X2 NQ IS THE LAGGARD: leaders (mean of ES, RTY, YM when present) 300-s move against >= 2.0 sigma AND still against over the last 60 s (>= 0.5 sigma) AND NQ's own 300-s move against is less than half of the leaders' AND trade >= 0.50 R0 under water -> ALL.
 X3 RISK-OFF CONFIRMATION (off in BX1; long books only when switched on): ZN 300-s rally >= 1.5 sigma with ES against >= 0.5 sigma and trade >= 0.30 R0 under water -> ALL. Off because the bond sign is not validated on bare data.
 Profit side (row C only): arm at +1.0 R0; trail 1.0 R0 behind the best (ratchet, never below breakeven once armed); loosen to 1.5 R0 while ES and RTY both confirm (>= +0.5 sigma with the trade); tighten to 0.5 R0 when both are against <= -1.0 sigma; exit 15 min before session end in profit.
 Each rule acts at most once per trade; order changes <= 6 per minute; one decision per 15 s.
3. FIRING SHARES (the only number reported, from a walk of safety-stop-only paths of the live-book entries as a stand-in for bare entries until W-DYNH's bare events exist; 100 trades each; 15-s steps; first fire per trade; Asia MF1 / NY AM MF5). Written target before the run: X1 <= 12%, X2 <= 12%, combined <= 25%.
 - first draft (X1 1.5 sigma, 0.30 R0; X2 1.0 sigma): X1 42% / 33%, X2 10% / 9%: TOO OFTEN.
 - notch 1 (2.0 / 1.5): X1 33% / 23%, X2 7% / 6%: still too often.
 - notch 2 = BX1 defaults (2.5 sigma, 0.50 R0; X2 2.0 sigma): X1 20% / 12%, X2 2% / 3%: combined ~22% / 15%: within the target for NY, Asia X1 20% (over its 12% line, within the combined 25%).
 Profit side: trail arms on 50% / 42% of trades, the 15-min clock exit fires on 49% / 53% (the clock is common: most trades are still open in profit near the session end on a safety-only path).
 Thresholds were moved ONLY on the firing share, never on P&L; count of versions tried: 3 loss-side, 1 profit-side.
4. ASIA FEED HOLE: in Asia the ES/RTY per-second series have gaps: 8,497 to 10,263 blind decisions in 100 Asia MF1 trades (NQ_SS/ES/RTY seconds missing > 5 s) against 16 to 18 in NY. X1 for Asia books should lead with ES + NKD (or YM when it exists) instead of RTY; the class takes RTY missing as abstain, so Asia X1 is partly blind. W-DYNX8 to say what second-level Asia-hours series exist (NKD, 6J, ES overnight).
5. LABEL / FEATURE NOTE for W-DYNML: no learned part in BX1; if the corrected loop C is retrained on bare paths (15-s states), BX1 is the readable baseline it must beat on the same rows.

## ROWS for W-DYNH (bare entries: R0 events: no layers, no Trade Health, one position per book; 1 lot and live lots)
 A  bare + book bracket, no manager.
 B  safety 1.5 x own stop + own target + BareX {loss:true, profit:false}.
 C  safety 1.5 x own stop, no target + BareX {loss:true, profit:true}.
 D  own stop (safety_mult 1.0) + own target + BareX {loss:true, profit:false, safety_mult:1.0}  (the loop only cuts earlier).
 E  fitted live book as run (reference).
 manager config: {'path':'code/th_dync','module':'algo_bare','cls':'BareX','params':{'safety_mult':1.5,'loss':True,'profit':False}}; feeds: NQ, ES, RTY (+ YM, ZN when available), kind inst1s, sym = name, lag 1. Random-management null (same share and timing as X1+X2 on the best row), re-entry rows L0 and L1, pessimistic fills, hook health counters (algo_nmiss) must show < 5% missing-feature minutes, else the set is data-starved.
 Rarity reference for the null: code/th_dync/bare_share_loss3.json (shares) - delays to be taken from the exact rows.
