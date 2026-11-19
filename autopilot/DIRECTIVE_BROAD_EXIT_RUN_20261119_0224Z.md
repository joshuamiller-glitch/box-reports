# ORDER 20261119_0224Z: NO SHORTCUTS (Josh, 02:15Z): full exit run, all four machines at 100%

Research only. Josh: "we have 4 BOXES! huge amount of Horsepower and cores - no shortcuts - let's get the
absolute best tech and run them 100%."

1. THE BROAD EXIT RUN IS ON: all 68 exit recipes (all 7 families), whole grid, all params your pass-2
   coverage supports (state the coverage; coarse first, then the fine params on cells alive on any recipe),
   real entries + null draws on the same footing as EXIT_YIELD, own-stop version of the exits built
   (the per-trade records it needs) so exits are ranked on the same rule as brackets.
   ORDER OF WORK inside it: Asia, NY AM, London, NY PM (if the simulation cannot be split by session, order
   the (row, module) pairs by their Asia / NY AM screen value so those sessions' answers land first).
   This is a QUEUE, not a deadline: it must never slow the D8 critical path (item 2).
2. PRIORITY LADDER on every machine (highest first):
   a. engine: D8 candidates Asia, then NY AM (REPLACE / ADD rows, exit-recipe engine rows, prior years,
      controls, layers);
   b. exit run on the D8 candidates (order 0213Z);
   c. real pass 1 + the forced level re-run (real cells);
   d. engine + candidate exits for London, then NY PM;
   e. R3 stages, calibration by family, pass 2;
   f. null draws 1-2 (incl. the level re-run of the null);
   g. the broad exit run (item 1);
   h. null draws 3-5.
   If g or h would starve for more than 12 h, say so in a LEAD NOTE with the hours (Josh decides on machines).
3. 100%: HEALTH.md 02:05Z shows Frankfurt 96% and Singapore 93% after the cut to 61 grid workers. No machine
   below 98% busy while any queue above has work: fill the freed threads with ENGINE workers first
   (the engine queue is 55 h deep and is what sets the D8 date), then exit-run workers. Measure, do not
   oversubscribe beyond what the 30-min tests showed is productive; log workers per type per machine.
4. BEST TOOLS: if any stage is slow for a reason better engineering removes (vectorised / compiled path
   simulator for the exit recipes, caching bar and feature stores in RAM on the 1.4 TB machines, the fast
   replay where it is validated), do it when the speed-up pays back within the run, with an identity test
   before any number from the faster path is used. One LEAD NOTE listing what was sped up and by how much.
5. Publish in one LEAD NOTE: start time and ETA of the broad exit run per session, the worker split per
   machine, and the D8 spec date for Asia + NY AM under orders 0210Z / 0213Z / 0220Z.
