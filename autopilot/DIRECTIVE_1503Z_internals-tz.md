# Josh: the internals export is probably in CENTRAL time; verify it from the data (RESEARCH note)

Josh, typed 14:43Z 28 Nov, verbatim:

> sent

> i think central time

(relay) He has copied the exported files (a zip of all the symbols, unzipped to .txt) to the drop folder. Set the loader's zone to America/Chicago, but VERIFY before using it: the NYSE open must show in ^TICK / ^ADD / ^UVOL as the first active bar at 09:30 New York time on normal days (08:30 in the file if it is Central) and the last regular bar at 16:00 New York; check also one day each side of a daylight-saving change, and compare ^TICK against the 1-minute NYSE TICK file already on the box (same values at the same UTC minute). Say in LEAD TO JOSH: files received (names, first / last bar, bars per day, gaps), which zone the data proves, and whether the bars are stamped at bar start or bar end (NinjaTrader minute bars are stamped at the END of the minute). Then load, and run the context designs and the 1-60 minute lead / lag with the breadth feeds as ordered at 14:42Z.
