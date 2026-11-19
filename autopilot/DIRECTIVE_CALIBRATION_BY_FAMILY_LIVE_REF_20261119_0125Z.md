# ORDER 20261119_0125Z: calibration: break it down by family, and run the LIVE books through the same test

Research only. Nothing stops; these are additions to the calibration work (W-SHORT), run beside it.

Read: 01:16Z first measured calibration (null draw 1 ~33%, stage A): no threshold reaches FDR <= 10%;
London and NY PM show no search-level signal; Asia weak; NY AM pending. That is a search-wide AVERAGE.
A search of 145 trigger modules x 493 bar rows can be mostly noise and still hold a few real families.

1. FDR BY FAMILY, per session, same footing as the 01:16Z table (real vs null family-bests, p_L6M):
   a. by TRIGGER family (levels / VWAP, zones, order book, tape, trend, mean reversion, cross-market,
      session structure ... use your module groups);
   b. by BAR family (time, tick, volume, range / renko-type, delta, imbalance, information-driven ...);
   c. the 10 (trigger family x bar family) blocks with the LOWEST measured FDR per session, with counts.
   A block with real >> null is where the engine and the deeper stages go first ("expand what hits");
   a block with null >= real is deprioritised (not dropped: it stays in the ladder, last).
   State the number of blocks tested so the best-of-many effect is visible (the 5 null draws check it).
2. LIVE BOOKS AS THE REFERENCE. Put each live D7 book in each session it trades (K7, M7, U7, P7, H7, A7,
   O7; bare trigger on its own bar, its live bracket, no layers) through EXACTLY the same test: R0, R1,
   stage A / B / C (30 / 200 / 1,000 same-bracket random-entry draws, p_L6M and weakest prior year).
   One table: book, session, L6M trades, R0 pass?, beats of 30, p at 200 / 1,000. This tells Josh
   what the test says about books that make money live, so he can judge how hard the bar is.
   (Research replay only: nothing on the execution server or the live chart is touched.)
3. DEEPER RUNGS: when stages B / C on real and null family-bests exist, add FDR at p <= 0.02 / 0.005 / 0.001
   per session to the CALIBRATION section (stage A with 30 draws cannot resolve below p 0.032).
   Also the same calibration on the OWN-STOP (R1) ranking once the arrays exist.
4. OVERSUBSCRIPTION: phase 2 says 60 grid workers on Frankfurt beat 96. Singapore's control moved by itself
   (x0.46: its real cells ran out?), so the comparison is not clean; run the same 30-min test on Singapore
   (99 -> 60) and keep the better setting there too.
5. One LEAD NOTE when 1 and 2 are on the page (target 04:00Z), and put both tables in MORNING_SUMMARY.md.
