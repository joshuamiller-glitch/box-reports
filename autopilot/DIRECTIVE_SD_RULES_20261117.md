RESEARCH ORDER (relay, 11-17 23:57Z): the user (a supply / demand trader first) asks "what is the methodology for supply and demand zones?" Publish the EXACT rules of trig_levels_sd5 / sd15 / sd60 as coded, in plain words with numbers, on a short page autopilot/SD_ZONE_RULES.md (one screen, phone-readable), within 30 minutes; W-GRIDD owns it. State for each item the rule and the settings grid:
1. What bars zones are drawn from (5 / 15 / 60-minute; also say if zones can be drawn on the non-time bars) and how far back zones live.
2. BASE: how a base is recognised (number of bars, max body / range vs ATR or vs the impulse, overlap rule).
3. IMPULSE / departure: minimum size (x ATR or x base height), minimum speed (bars), must it close beyond the base, must it break a prior swing (structure break) to count.
4. ZONE LINES: proximal and distal line definitions (body vs wick: which convention), for demand and for supply; the four shapes (rally-base-rally, drop-base-rally, rally-base-drop, drop-base-drop) and how continuation vs reversal zones are tagged.
5. FRESHNESS: what counts as a test (touch of the proximal line? penetration %?), how many tests allowed, when a zone is dead (close beyond the distal line? by how much?).
6. QUALITY FEATURES computed (departure strength, time in base, freshness, structure break, location in the larger range = discount / premium, nesting inside a higher-timeframe zone, opposing-zone distance = room) and how each is scored.
7. ENTRIES tested: limit at the proximal line; confirmation (reject bar; order-flow turn = what exactly: delta flip, absorption, book wall); the 8 variants and 40 parameter sets listed.
8. STOP / TARGET: stop beyond the distal line + how many ticks; target = opposing zone proximal line, or fixed R multiples (which), and the "zone-aware bracket mode" status (built or not).
9. How this differs from D7's own PoiSet zones (one paragraph).
10. What is NOT yet built from order 2308Z (list), with times.
The user may correct the rules to match how he traded; code so the definitions are parameters (conventions switchable: wick-to-wick vs body-to-wick, test definition, departure threshold). Research only. No spend.
