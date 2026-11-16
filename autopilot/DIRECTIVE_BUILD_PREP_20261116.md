# USER ORDER 2026-11-16 (verbatim): BUILD PREP for D7 v2.0. Priority over all other work.
1. LS1_MP and LS125_MP: write the exact live spec to
   autopilot/SPEC_LONDON_RANGE_MP.md: bars used, session bounds (ET), the
   own-bar range forecast formula with every constant, how "range used"
   is measured and when, the k threshold, which signals are skipped (M7,
   P7, London only), what happens to an open trade, and 5 worked examples
   with timestamps and numbers from the engine that I can check the code
   against. State which version (k=1 or k=1.25) you recommend and why.
2. Re-run on JN05W2JL2, all six windows, with 3 placebos and 3 matched
   random controls each: A7 Asia 40x40, U7 Asia 40x40, K7 NY AM 40x40 and
   40x60, K7 London 40x60. Report drawdown first. These run before
   anything else in D10.
3. For each of the five bracket cells, give the exact policy line as the
   engine applied it (bracket <book> <session> target= stop=) and say
   whether cuts, trails and caps were left at their live values.
4. DRAWDOWN TARGET: HOLD window (Nov 2025 to Apr 2026) max DD is 74.4k
   base on JL2 against 22.6k in L6M. Decompose that drawdown by book,
   session and day type, and score every current lead (London skip,
   the five bracket cells, L3 item, P7 Asia set, AL hold/cut) on that
   window specifically. Page DS3_DD_HOLD.md.
