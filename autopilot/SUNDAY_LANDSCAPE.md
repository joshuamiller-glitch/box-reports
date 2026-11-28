# SUNDAY_LANDSCAPE: no fixed target, own stop, exit from the current landscape (W-SUNDAY-LS, exact engine, live mix)

Every set: one book of the live mix enters with its own stop and NO target (session flatten kept, live loss-side Trade Health kept, the book's profit-side Trade Health removed); everything else live as run. Numbers are WHOLE-MIX deltas vs the live mix as run on the same months (+ = better; dd gap + = shallower weekly max DD). Dollars after 4.84 x lots. Rule text and codes: code/th_ls/ls_build.py docstring and ls_mgr.py; rules: a set is scored on every month it has (xi: from 2023-09; live row cut to the same months). PASS = max DD and worst week not worse than the live bracket, L6M DD not worse, income >= 0.97 x live, and weekly DD better-or-equal in >= 2 of 3 full years. BEST landscape per book (drawdown first): the PASS set with the most income, else the set with the shallowest max DD among sets with income >= 0.90 x live, else the set with the smallest income loss; marked WEAK when not PASS.

Codes: so0 = stop-only to session end; gKKaAA = give-back cap: stop keeps KK% of the peak once peak >= AA% of the old target distance; trCC = trail CC% of the old target behind the best from +50%; xi10all/xi15all/xi10ext/xi10tight = ES RTY YM (+ZN ZB 6J 6E NKD CL GC) turning against a winner for 5 min (1.0 / 1.5 sigma): all = leave, tight = stop to 80% of peak, ext = also needs one extra instrument; rg80/rg100 = range used so far today >= 80/100% of the UW forecast range (acts only from 2025-03); lv07t/lv13t = resting take at the first landscape level >= 0.7 / 1.3 x old target; lv07p = half off there, runner trail 0.5 x target; xi/rg/lv codes sit on g67a50; x7 / l7 / cbA (combined) sit on g67a70 (x7 + xi10tight, l7 + lv13t, cbA + tr100 + xi10tight + lv13t).


## AS-NR7 (live bracket, same months: income +915k, max DD -68k, worst week -37k; L6M income +463k, L6M DD -25k, L3M income +154k)

**VERDICT WEAK: best landscape exit = `tr100` (TL3_DX_AS_MF1_ls_tr100_M)**: income -54k (-5.9%), max DD gap -5k, worst-week gap -2k, L6M income +4k / DD gap +11k, L3M income -30k / DD gap +8k, NQ-down weeks +329k vs +364k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| lv13t | 42 | -256k | +1k | +2k | -119k / +7k | -72k / +2k | -106k | -1k / -8k / -96k / -150k | WEAK |
| rg80 | 42 | -355k | -0k | +2k | -188k / +5k | -47k / +10k | -153k | -1k / -12k / -109k / -232k | WEAK |
| g67a50 | 42 | -270k | -0k | +2k | -119k / +7k | -74k / +2k | -103k | -1k / -12k / -99k / -157k | WEAK |
| rg100 | 42 | -283k | -0k | +4k | -178k / +8k | -46k / +13k | -131k | -1k / -12k / -61k / -208k | WEAK |
| g75a70 | 42 | -219k | -3k | -3k | -139k / -9k | -75k / +7k | -113k | +2k / -14k / -81k / -126k | WEAK |
| lv07t | 42 | -297k | -4k | +0k | -121k / +9k | -69k / +4k | -139k | -3k / -20k / -114k / -161k | WEAK |
| lv07p | 42 | -286k | -4k | +1k | -135k / +7k | -76k / +2k | -119k | +0k / -20k / -100k / -167k | WEAK |
| tr100 | 42 | -54k | -5k | -2k | +4k / +11k | -30k / +8k | -36k | -1k / -0k / -40k / -13k | WEAK |
| tr50 | 42 | -222k | -6k | +1k | -104k / +7k | -57k / +1k | -69k | +3k / -18k / -103k / -104k | WEAK |
| g75a50 | 42 | -234k | -8k | -0k | -105k / +4k | -77k / -1k | -97k | +5k / -17k / -97k / -125k | WEAK |
| xi15all | 36 | -311k | -17k | +2k | -120k / -1k | -72k / -6k | -78k | -11k / -10k / -116k / -175k | WEAK |
| l7 | 42 | -190k | -17k | -3k | -119k / +5k | -64k / +8k | -108k | +4k / -4k / -90k / -100k | WEAK |
| g67a70 | 42 | -225k | -21k | -3k | -123k / +3k | -66k / +9k | -116k | +4k / -2k / -99k / -128k | WEAK |
| g50a50 | 42 | -218k | -22k | +5k | -110k / +3k | -42k / +5k | -88k | -2k / -23k / -63k / -131k | WEAK |
| so0 | 42 | -217k | -31k | -2k | -160k / +2k | -42k / -3k | -178k | +2k / +5k / -30k / -194k | WEAK |
| xi10all | 36 | -382k | -40k | +4k | -147k / +3k | -72k / -2k | -105k | -13k / -32k / -146k / -191k | WEAK |
| xi10tight | 36 | -381k | -43k | +4k | -149k / +3k | -72k / -2k | -96k | -15k / -24k / -151k / -192k | WEAK |
| xi10ext | 36 | -395k | -44k | +2k | -135k / +4k | -71k / -2k | -111k | -14k / -41k / -150k / -189k | WEAK |
| cbA | 36 | -340k | -57k | +4k | -130k / +9k | -69k / +5k | -71k | -16k / -33k / -144k / -147k | WEAK |
| x7 | 36 | -328k | -67k | +2k | -131k / +6k | -65k / +5k | -57k | -16k / -17k / -154k / -141k | WEAK |
| g75a30 | 42 | -361k | -94k | -2k | -138k / +8k | -38k / +9k | -127k | +1k / -49k / -147k / -166k | WEAK |
| g67a30 | 42 | -312k | -99k | -2k | -134k / +8k | -36k / +5k | -75k | -8k / -21k / -152k / -131k | WEAK |
| g50a30 | 42 | -327k | -144k | -5k | -156k / +1k | -31k / +13k | -122k | +10k / -27k / -146k / -163k | WEAK |

## AS-RSI (live bracket, same months: income +915k, max DD -68k, worst week -37k; L6M income +463k, L6M DD -25k, L3M income +154k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_AS_MF2_ls_so0_M)**: income -42k (-4.5%), max DD gap +8k, worst-week gap +0k, L6M income -24k / DD gap -0k, L3M income -7k / DD gap +4k, NQ-down weeks +369k vs +364k, years better-DD 3 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| so0 | 42 | -42k | +8k | +0k | -24k / -0k | -7k / +4k | +4k | -2k / -17k / -53k / +30k | WEAK |
| rg100 | 42 | -85k | +4k | -1k | -45k / -5k | -7k / +10k | -8k | -3k / +4k / -27k / -58k | WEAK |
| g50a30 | 42 | -131k | +1k | -2k | -78k / -4k | -28k / -2k | -35k | +5k / -32k / -35k / -70k | WEAK |
| g67a30 | 42 | -126k | +1k | -3k | -76k / -4k | -25k / -2k | -46k | +5k / -29k / -26k / -77k | WEAK |
| g75a30 | 42 | -128k | +0k | -3k | -83k / -4k | -36k / -2k | -38k | +5k / -28k / -24k / -81k | WEAK |
| xi10ext | 37 | -31k | -4k | +0k | -21k / -4k | -2k / +7k | -7k | +7k / -18k / -10k / -10k | WEAK |
| xi10all | 37 | -38k | -4k | +0k | -21k / -4k | -3k / +7k | -13k | +8k / -19k / -14k / -12k | WEAK |
| xi10tight | 37 | -39k | -4k | +0k | -21k / -4k | -3k / +7k | -14k | +8k / -19k / -14k / -13k | WEAK |
| lv07t | 42 | -31k | -4k | -0k | -27k / -2k | -17k / +8k | +13k | -3k / -6k / -4k / -18k | WEAK |
| lv07p | 42 | -21k | -4k | -0k | -25k / -2k | -12k / +8k | +13k | -3k / -0k / -2k / -17k | WEAK |
| g67a50 | 42 | -22k | -4k | -0k | -26k / -2k | -11k / +7k | +10k | -3k / +4k / -4k / -19k | WEAK |
| lv13t | 42 | -10k | -4k | -0k | -26k / -2k | -11k / +8k | +18k | -3k / +11k / +1k / -19k | WEAK |
| xi15all | 37 | -24k | -4k | -0k | -28k / -2k | -12k / +7k | -5k | +6k / -9k / -2k / -20k | WEAK |
| rg80 | 42 | -139k | -4k | +0k | -71k / -5k | -25k / +10k | -20k | -3k / +4k / -42k / -98k | WEAK |
| tr100 | 42 | -18k | -4k | -2k | +34k / -3k | +13k / -1k | -11k | -3k / -19k / -31k / +36k | WEAK |
| g75a50 | 42 | -40k | -5k | -1k | -32k / -2k | -25k / +8k | +9k | -3k / -10k / -8k / -20k | WEAK |
| cbA | 37 | -34k | -5k | -1k | -6k / -4k | -1k / +10k | -22k | +8k / -22k / -12k / -8k | WEAK |
| x7 | 37 | -45k | -5k | -1k | -6k / -4k | +3k / +9k | -33k | +8k / -26k / -16k / -10k | WEAK |
| tr50 | 42 | -23k | -7k | -0k | -16k / -1k | -4k / +2k | +1k | -1k / +0k / -5k / -17k | WEAK |
| g50a50 | 42 | -68k | -8k | -1k | -51k / -3k | -22k / +3k | -3k | -1k / -15k / -8k / -44k | WEAK |
| g75a70 | 42 | +12k | -11k | -0k | +14k / +0k | -1k / +12k | +10k | +0k / -5k / -3k / +20k | WEAK |
| g67a70 | 42 | +5k | -12k | -0k | +8k / -0k | +4k / +13k | -1k | -1k / -2k / +4k / +4k | WEAK |
| l7 | 42 | +18k | -12k | -0k | +13k / -0k | +9k / +14k | +4k | -1k / +4k / +3k / +12k | WEAK |

## AS-VWAPBRK (live bracket, same months: income +916k, max DD -68k, worst week -37k; L6M income +463k, L6M DD -25k, L3M income +154k)

**VERDICT PASS: best landscape exit = `x7` (TL3_DX_AS_MF3_ls_x7_M)**: income +107k (+11.7%), max DD gap +19k, worst-week gap +1k, L6M income -22k / DD gap +1k, L3M income +1k / DD gap +9k, NQ-down weeks +388k vs +365k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| x7 | 37 | +107k | +19k | +1k | -22k / +1k | +1k / +9k | +23k | -22k / +13k / +78k / +38k | PASS |
| tr100 | 42 | +205k | +18k | -2k | -3k / +8k | -8k / +8k | +105k | -2k / +47k / +76k / +84k | WEAK |
| l7 | 42 | +175k | +17k | -4k | -28k / -6k | +14k / +4k | +85k | +7k / +52k / +109k / +8k | WEAK |
| g67a70 | 42 | +190k | +16k | -4k | -41k / -7k | +5k / +5k | +79k | +6k / +56k / +114k / +15k | WEAK |
| rg100 | 42 | +83k | +16k | -8k | +0k / +5k | +6k / +2k | +78k | -0k / +50k / -4k / +37k | WEAK |
| rg80 | 42 | +10k | +16k | -8k | -4k / +8k | +4k / +6k | +62k | -0k / +50k / -29k / -12k | WEAK |
| g50a50 | 42 | +192k | +13k | -11k | -18k / +4k | -5k / +4k | +115k | -11k / +22k / +129k / +51k | WEAK |
| xi15all | 37 | +139k | +12k | -8k | -9k / +4k | -12k / -1k | +24k | -22k / +18k / +89k / +54k | WEAK |
| cbA | 37 | +157k | +11k | -1k | +45k / +13k | +3k / +8k | +27k | -22k / +6k / +68k / +105k | WEAK |
| lv07p | 42 | +152k | +9k | -8k | +3k / +5k | -4k / -0k | +46k | +0k / +45k / +65k / +42k | WEAK |
| g75a70 | 42 | +140k | +8k | -2k | -37k / -7k | -8k / +8k | +52k | +23k / +40k / +78k / -1k | WEAK |
| g75a50 | 42 | +125k | +8k | -7k | +4k / +6k | -9k / +1k | +39k | +5k / +26k / +47k / +47k | WEAK |
| tr50 | 42 | +127k | +7k | -7k | -1k / -5k | +44k / +5k | +37k | -14k / +56k / +58k / +26k | WEAK |
| lv07t | 42 | +139k | +7k | -7k | -5k / +4k | -14k / -2k | +38k | -3k / +24k / +86k / +32k | WEAK |
| xi10all | 37 | +86k | +7k | -2k | -21k / +4k | -26k / -1k | +7k | -19k / +1k / +75k / +30k | WEAK |
| xi10tight | 37 | +97k | +7k | -2k | -21k / +3k | -26k / -2k | +9k | -19k / +4k / +77k / +35k | WEAK |
| g67a50 | 42 | +197k | +7k | -8k | -1k / +5k | -7k / -0k | +56k | -0k / +50k / +83k / +64k | WEAK |
| g67a30 | 42 | +2k | +6k | +7k | -27k / +9k | -8k / +4k | -15k | -28k / -6k / +12k / +24k | WEAK |
| lv13t | 42 | +163k | +5k | -8k | +6k / +4k | -3k / -2k | +52k | +1k / +47k / +74k / +41k | WEAK |
| xi10ext | 37 | +114k | +5k | -2k | -15k / +4k | -20k / -1k | +7k | -21k / +13k / +86k / +36k | WEAK |
| g50a30 | 42 | -37k | -2k | +4k | -73k / +5k | -3k / +7k | -3k | -33k / -22k / +31k / -13k | WEAK |
| g75a30 | 42 | -21k | -2k | +6k | -31k / +2k | -9k / -3k | -37k | -31k / -17k / +18k / +8k | WEAK |
| so0 | 42 | -25k | -45k | -11k | -176k / -10k | -50k / -6k | +148k | +2k / +82k / +49k / -158k | WEAK |

## LO-CRUDE (live bracket, same months: income +914k, max DD -213k, worst week -107k; L6M income +528k, L6M DD -21k, L3M income +234k)

**VERDICT WEAK: best landscape exit = `tr100` (TL3_DX_LO_MF1_ls_tr100_M)**: income -106k (-11.6%), max DD gap -149k, worst-week gap +36k, L6M income -176k / DD gap -29k, L3M income -4k / DD gap -5k, NQ-down weeks -199k vs -95k, years better-DD 0 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| rg100 | 42 | -508k | -14k | +20k | -366k / -21k | -138k / +5k | -69k | -79k / -36k / -76k / -318k | WEAK |
| l7 | 42 | -221k | -27k | +16k | -125k / -5k | -27k / -5k | -47k | -53k / -52k / -89k / -27k | WEAK |
| rg80 | 42 | -637k | -28k | +20k | -412k / -31k | -163k / +5k | -152k | -79k / -36k / -108k / -414k | WEAK |
| lv13t | 42 | -308k | -40k | +10k | -189k / -9k | -48k / -10k | +21k | -83k / -45k / -95k / -84k | WEAK |
| lv07p | 42 | -307k | -45k | +10k | -186k / -9k | -47k / -9k | +17k | -77k / -39k / -111k / -79k | WEAK |
| g75a70 | 42 | -244k | -46k | +17k | -148k / -4k | -33k / -4k | -37k | -43k / -40k / -104k / -57k | WEAK |
| g67a70 | 42 | -172k | -46k | +9k | -102k / -5k | -13k / -5k | -26k | -55k / -47k / -102k / +32k | WEAK |
| g67a30 | 42 | -444k | -47k | +4k | -228k / -7k | -66k / -8k | -97k | -79k / -95k / -101k / -169k | WEAK |
| g50a50 | 42 | -260k | -48k | +15k | -164k / -13k | -9k / -12k | -16k | -59k / -45k / -59k / -97k | WEAK |
| g67a50 | 42 | -304k | -49k | +8k | -179k / -9k | -36k / -10k | +10k | -79k / -36k / -109k / -79k | WEAK |
| xi10ext | 37 | -332k | -56k | -0k | -184k / -9k | -38k / -10k | -10k | -58k / -69k / -131k / -75k | WEAK |
| g75a50 | 42 | -303k | -56k | +8k | -202k / -8k | -58k / -8k | +37k | -62k / -44k / -110k / -87k | WEAK |
| lv07t | 42 | -337k | -57k | +12k | -197k / -8k | -61k / -9k | -3k | -70k / -42k / -125k / -99k | WEAK |
| g50a30 | 42 | -422k | -57k | +2k | -185k / -9k | -21k / -9k | -102k | -71k / -66k / -139k / -146k | WEAK |
| xi15all | 37 | -325k | -60k | +5k | -179k / -9k | -36k / -10k | -11k | -55k / -66k / -124k / -80k | WEAK |
| xi10all | 37 | -335k | -64k | -3k | -173k / -9k | -28k / -10k | -16k | -61k / -69k / -139k / -66k | WEAK |
| xi10tight | 37 | -337k | -66k | -3k | -174k / -9k | -28k / -10k | -17k | -62k / -69k / -140k / -66k | WEAK |
| g75a30 | 42 | -511k | -67k | +2k | -270k / -7k | -97k / -7k | -116k | -75k / -100k / -128k / -207k | WEAK |
| cbA | 37 | -423k | -79k | +8k | -192k / -11k | -63k / -11k | -115k | -54k / -93k / -179k / -97k | WEAK |
| tr50 | 42 | -149k | -80k | -19k | -191k / -42k | +15k / -13k | -54k | -16k / +29k / -56k / -106k | WEAK |
| x7 | 37 | -330k | -102k | -3k | -103k / -6k | +13k / -7k | -87k | -56k / -87k / -200k / +13k | WEAK |
| tr100 | 42 | -106k | -149k | +36k | -176k / -29k | -4k / -5k | -105k | +11k / -58k / -36k / -23k | WEAK |
| so0 | 42 | -139k | -160k | +9k | -94k / -46k | +104k / +0k | -79k | +4k / +7k / -25k / -125k | WEAK |

## LO-ZB (live bracket, same months: income +914k, max DD -213k, worst week -107k; L6M income +528k, L6M DD -21k, L3M income +234k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_LO_MF3_ls_so0_M)**: income -19k (-2.1%), max DD gap +19k, worst-week gap -4k, L6M income +3k / DD gap -1k, L3M income +16k / DD gap -1k, NQ-down weeks -100k vs -95k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| tr50 | 42 | -97k | +50k | +34k | -2k / +1k | +58k / +2k | -91k | -17k / -108k / +53k / -25k | WEAK |
| so0 | 42 | -19k | +19k | -4k | +3k / -1k | +16k / -1k | -6k | +2k / -59k / +55k / -17k | WEAK |
| g67a70 | 42 | -163k | +17k | +11k | -0k / +1k | +20k / +4k | -112k | -6k / -105k / -2k / -50k | WEAK |
| g75a70 | 42 | -121k | +11k | +11k | +15k / +3k | +9k / +6k | -44k | -4k / -88k / -8k / -22k | WEAK |
| tr100 | 42 | -27k | +2k | +19k | -5k / -2k | -6k / +2k | +30k | +3k / -38k / +11k / -3k | WEAK |
| l7 | 42 | -161k | +0k | +2k | +8k / -2k | -0k / -3k | -98k | -0k / -104k / -27k / -30k | WEAK |
| g50a50 | 42 | -204k | -3k | -3k | -58k / -8k | -19k / -8k | -91k | +24k / -104k / -8k / -117k | WEAK |
| g75a50 | 42 | -17k | -5k | -7k | -38k / -3k | -13k / -3k | -32k | +36k / -57k / +55k / -49k | WEAK |
| xi10ext | 37 | -251k | -8k | -1k | -49k / -6k | -8k / -6k | -85k | -17k / -127k / -20k / -87k | WEAK |
| xi10all | 37 | -270k | -9k | -1k | -50k / -6k | -6k / -7k | -92k | -18k / -122k / -44k / -86k | WEAK |
| g50a30 | 42 | -194k | -10k | +1k | -39k / -5k | -19k / -6k | -92k | +13k / -63k / -29k / -115k | WEAK |
| lv13t | 42 | -133k | -13k | -10k | -37k / -3k | -29k / -4k | -64k | +8k / -81k / +3k / -62k | WEAK |
| g75a30 | 42 | -196k | -15k | -0k | -15k / +3k | +5k / +2k | -138k | +9k / -73k / -46k / -86k | WEAK |
| g67a50 | 42 | -150k | -16k | -10k | -48k / -3k | -22k / -4k | -99k | +3k / -86k / +15k / -81k | WEAK |
| lv07p | 42 | -152k | -16k | -10k | -53k / -4k | -25k / -4k | -103k | +4k / -84k / +10k / -82k | WEAK |
| lv07t | 42 | -98k | -16k | -10k | -22k / -4k | -9k / -4k | -74k | +3k / -77k / +23k / -48k | WEAK |
| g67a30 | 42 | -148k | -17k | -1k | +2k / +3k | +9k / +2k | -119k | +13k / -64k / -46k / -51k | WEAK |
| xi10tight | 37 | -287k | -17k | -1k | -50k / -6k | -6k / -7k | -110k | -18k / -132k / -52k / -86k | WEAK |
| xi15all | 37 | -196k | -21k | -1k | -61k / -4k | -15k / -5k | -121k | -17k / -105k / +7k / -82k | WEAK |
| x7 | 37 | -277k | -29k | +12k | -19k / +2k | +30k / +1k | -95k | -25k / -131k / -56k / -66k | WEAK |
| cbA | 37 | -229k | -31k | +16k | -2k / -0k | +2k / -1k | -42k | -25k / -129k / -52k / -23k | WEAK |
| rg100 | 42 | -437k | -71k | +3k | -165k / +2k | -91k / +2k | -211k | +3k / -86k / -104k / -249k | WEAK |
| rg80 | 42 | -487k | -131k | +1k | -152k / +1k | -86k / +0k | -245k | +3k / -86k / -152k / -250k | WEAK |

## NP-CONF (live bracket, same months: income +1493k, max DD -98k, worst week -65k; L6M income +467k, L6M DD -17k, L3M income +248k)

**VERDICT WEAK: best landscape exit = `cbA` (TL3_DX_NP_CONF_ls_cbA_M)**: income -59k (-3.9%), max DD gap +18k, worst-week gap +19k, L6M income -37k / DD gap -3k, L3M income +11k / DD gap -3k, NQ-down weeks +720k vs +717k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| cbA | 37 | -59k | +18k | +19k | -37k / -3k | +11k / -3k | +3k | -23k / -28k / +57k / -65k | WEAK |
| x7 | 37 | -35k | +17k | +19k | -39k / -3k | +9k / -3k | +13k | -24k / -34k / +82k / -59k | WEAK |
| xi10tight | 37 | -32k | +10k | +20k | -30k / -5k | +15k / -2k | +25k | -28k / -49k / +94k / -50k | WEAK |
| xi10all | 37 | -32k | +10k | +20k | -30k / -5k | +15k / -2k | +25k | -29k / -48k / +95k / -50k | WEAK |
| xi10ext | 37 | -57k | +8k | +20k | -36k / -4k | +15k / -2k | +6k | -27k / -46k / +73k / -57k | WEAK |
| g67a30 | 42 | -96k | +6k | +17k | -53k / -9k | -8k / +0k | +0k | +11k / -51k / +30k / -86k | WEAK |
| g50a30 | 42 | -129k | +5k | +17k | -67k / -10k | -20k / -1k | -9k | +11k / -47k / +17k / -109k | WEAK |
| g75a30 | 42 | -129k | +4k | +17k | -52k / -8k | -8k / +0k | -19k | +8k / -51k / +12k / -98k | WEAK |
| xi15all | 37 | -76k | +2k | +19k | -38k / -4k | +10k / -2k | +10k | -32k / -45k / +51k / -51k | WEAK |
| g75a50 | 42 | -40k | +1k | +19k | -21k / -4k | +12k / -0k | +25k | +25k / -42k / +15k / -38k | WEAK |
| lv07t | 42 | -37k | +1k | +21k | -41k / -3k | -4k / -1k | +27k | +33k / -40k / +23k / -53k | WEAK |
| lv07p | 42 | -32k | +0k | +20k | -36k / -3k | +1k / -1k | +15k | +30k / -43k / +34k / -53k | WEAK |
| rg80 | 42 | -258k | +0k | +17k | -77k / -5k | -42k / +1k | -55k | +26k / -45k / -82k / -157k | WEAK |
| g67a50 | 42 | -30k | +0k | +21k | -36k / -2k | +3k / -1k | +10k | +26k / -45k / +39k / -50k | WEAK |
| lv13t | 42 | -33k | +0k | +21k | -33k / -1k | +4k / -1k | +8k | +30k / -45k / +36k / -55k | WEAK |
| tr100 | 42 | -154k | +0k | +22k | -35k / -12k | -31k / -12k | -14k | +13k / -70k / -62k / -35k | WEAK |
| l7 | 42 | -86k | -0k | +9k | -9k / +1k | +22k / +1k | -60k | +28k / -72k / -19k / -24k | WEAK |
| g75a70 | 42 | -69k | -2k | +9k | -0k / +2k | +28k / +2k | -42k | +20k / -60k / -28k / -0k | WEAK |
| g67a70 | 42 | -92k | -3k | +9k | -14k / +1k | +24k / +1k | -63k | +24k / -78k / -17k / -21k | WEAK |
| g50a50 | 42 | -124k | -8k | +18k | -54k / -6k | +4k / -2k | -40k | +34k / -57k / -18k / -82k | WEAK |
| tr50 | 42 | -78k | -11k | +16k | -43k / -5k | +4k / -5k | -43k | +36k / -62k / +15k / -67k | WEAK |
| so0 | 42 | -152k | -12k | +0k | +23k / -10k | +8k / +0k | -22k | +33k / -31k / -139k / -16k | WEAK |
| rg100 | 42 | -276k | -13k | +19k | -72k / -8k | -47k / -8k | -50k | +26k / -45k / -99k / -158k | WEAK |

## NP-MACD (live bracket, same months: income +1210k, max DD -153k, worst week -52k; L6M income +521k, L6M DD -28k, L3M income +252k)

**VERDICT WEAK: best landscape exit = `so0` (TL3_DX_NP_MACD_ls_so0_M)**: income +306k (+25.3%), max DD gap +17k, worst-week gap -21k, L6M income -98k / DD gap -28k, L3M income -21k / DD gap -20k, NQ-down weeks +624k vs +542k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| so0 | 42 | +306k | +17k | -21k | -98k / -28k | -21k / -20k | +82k | +22k / +143k / +98k / +44k | WEAK |
| g75a30 | 42 | -170k | +10k | -2k | -144k / -2k | -36k / +5k | +54k | -34k / -22k / -52k / -62k | WEAK |
| g67a30 | 42 | -123k | +9k | -2k | -135k / -2k | -33k / +5k | +101k | -46k / -9k / -18k / -50k | WEAK |
| g50a30 | 42 | -32k | +4k | -2k | -128k / -4k | -35k / +6k | +168k | +6k / +30k / -18k / -51k | WEAK |
| g67a50 | 42 | -118k | +2k | -9k | -113k / -7k | -42k / +0k | +22k | -26k / -23k / +33k / -102k | WEAK |
| rg80 | 42 | -198k | +2k | +0k | -191k / -11k | -64k / -2k | -6k | -26k / -23k / -58k / -91k | WEAK |
| xi15all | 37 | -63k | +2k | -6k | -113k / -7k | -42k / +0k | +43k | +11k / -12k / +39k / -102k | WEAK |
| rg100 | 42 | -207k | +2k | +0k | -205k / -15k | -73k / -0k | -12k | -26k / -23k / -39k / -119k | WEAK |
| xi10ext | 37 | -61k | +2k | -6k | -115k / -7k | -43k / +0k | +53k | +9k / -4k / +38k / -104k | WEAK |
| g75a50 | 42 | -203k | +1k | -9k | -122k / -6k | -45k / -1k | -28k | -19k / -46k / -23k / -115k | WEAK |
| lv07p | 42 | -136k | +1k | -8k | -113k / -7k | -43k / +0k | +12k | -27k / -31k / +25k / -103k | WEAK |
| lv13t | 42 | -154k | +1k | -9k | -108k / -7k | -40k / +0k | +3k | -40k / -35k / +17k / -95k | WEAK |
| lv07t | 42 | -186k | +0k | -8k | -112k / -7k | -43k / -0k | -10k | -37k / -38k / -8k / -103k | WEAK |
| xi10all | 37 | -63k | -0k | -6k | -113k / -7k | -40k / +0k | +53k | +7k / -9k / +42k / -102k | WEAK |
| xi10tight | 37 | -63k | -0k | -6k | -112k / -7k | -40k / +0k | +53k | +7k / -10k / +42k / -102k | WEAK |
| x7 | 37 | +9k | -1k | +0k | -42k / -5k | +7k / +3k | -3k | -6k / -35k / +70k / -20k | WEAK |
| cbA | 37 | -31k | -7k | +1k | -52k / -8k | -9k / +3k | +6k | -7k / -62k / +69k / -31k | WEAK |
| g75a70 | 42 | -134k | -9k | -3k | -68k / -12k | -9k / +2k | -72k | -42k / -59k / +19k / -52k | WEAK |
| l7 | 42 | -86k | -9k | -4k | -44k / -9k | -1k / +3k | -42k | -56k / -62k / +48k / -16k | WEAK |
| g67a70 | 42 | -63k | -10k | -5k | -49k / -5k | -3k / +3k | -33k | -43k / -57k / +62k / -25k | WEAK |
| g50a50 | 42 | -103k | -12k | -11k | -129k / -9k | -46k / +1k | +63k | -9k / +27k / +7k / -128k | WEAK |
| tr100 | 42 | -18k | -14k | -11k | -188k / -7k | -75k / -15k | -54k | -11k / +82k / +8k / -96k | WEAK |
| tr50 | 42 | +143k | -19k | -12k | -127k / -14k | -25k / -1k | +213k | +42k / +25k / +235k / -160k | WEAK |

## NP-YM (live bracket, same months: income +1047k, max DD -127k, worst week -44k; L6M income +386k, L6M DD -23k, L3M income +199k)

**VERDICT WEAK: best landscape exit = `x7` (TL3_DX_NP_MF3_ls_x7_M)**: income -95k (-9.0%), max DD gap +28k, worst-week gap -3k, L6M income -5k / DD gap -2k, L3M income -22k / DD gap -6k, NQ-down weeks +432k vs +488k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| x7 | 37 | -95k | +28k | -3k | -5k / -2k | -22k / -6k | -56k | -23k / +44k / -97k / -18k | WEAK |
| l7 | 42 | -77k | +20k | -3k | -12k / -2k | -17k / -3k | -21k | +13k / -2k / -68k / -20k | WEAK |
| g67a70 | 42 | -28k | +18k | -3k | -14k / -2k | -18k / -3k | -24k | +28k / +26k / -58k / -24k | WEAK |
| g75a70 | 42 | -43k | +16k | -3k | -30k / -1k | -18k / -2k | -17k | +21k / +24k / -52k / -36k | WEAK |
| tr50 | 42 | +34k | +12k | -3k | -11k / +3k | -40k / -1k | +45k | -29k / +88k / +6k / -31k | WEAK |
| cbA | 37 | -164k | +11k | -5k | -26k / -1k | -25k / -6k | -50k | -38k / +6k / -99k / -32k | WEAK |
| g67a30 | 42 | -170k | +8k | -13k | -65k / +3k | -48k / -2k | -59k | -10k / +13k / -86k / -86k | WEAK |
| g75a30 | 42 | -172k | +5k | -13k | -64k / +3k | -45k / -2k | -60k | -17k / +5k / -80k / -80k | WEAK |
| g50a30 | 42 | -135k | +4k | -11k | -67k / +2k | -46k / -3k | -44k | +5k / +9k / -67k / -82k | WEAK |
| xi10all | 37 | -218k | -8k | -3k | -36k / -3k | -39k / -8k | -60k | -34k / -5k / -147k / -31k | WEAK |
| xi10tight | 37 | -212k | -8k | -3k | -36k / -3k | -39k / -8k | -58k | -34k / -2k / -145k / -31k | WEAK |
| xi15all | 37 | -213k | -9k | -3k | -31k / -0k | -36k / -5k | -64k | -26k / -24k / -133k / -30k | WEAK |
| rg100 | 42 | -245k | -9k | -10k | -62k / +2k | -31k / -3k | -128k | -20k / -21k / -117k / -87k | WEAK |
| rg80 | 42 | -254k | -10k | -10k | -71k / +2k | -33k / -3k | -118k | -20k / -21k / -114k / -99k | WEAK |
| xi10ext | 37 | -231k | -10k | -3k | -33k / -0k | -36k / -5k | -69k | -34k / -18k / -147k / -33k | WEAK |
| g75a50 | 42 | -172k | -11k | -4k | -23k / -0k | -28k / -5k | -50k | -15k / -33k / -111k / -13k | WEAK |
| g67a50 | 42 | -181k | -11k | -3k | -30k / -0k | -34k / -5k | -55k | -20k / -21k / -112k / -29k | WEAK |
| lv07p | 42 | -184k | -13k | -3k | -30k / -0k | -34k / -5k | -54k | -20k / -24k / -108k / -31k | WEAK |
| lv13t | 42 | -193k | -14k | -3k | -31k / -0k | -35k / -5k | -59k | -31k / -14k / -116k / -31k | WEAK |
| g50a50 | 42 | -116k | -16k | -4k | +5k / +2k | -31k / -1k | -23k | -11k / -26k / -102k / +23k | WEAK |
| lv07t | 42 | -206k | -17k | -2k | -27k / -0k | -29k / -5k | -61k | -31k / -27k / -114k / -34k | WEAK |
| tr100 | 42 | -58k | -27k | +2k | -93k / -5k | -40k / -10k | -42k | -32k / -31k / +86k / -81k | WEAK |
| so0 | 42 | +205k | -29k | -1k | +63k / -13k | -51k / -18k | +96k | -35k / +32k / +179k / +29k | WEAK |

## NP-ZN (live bracket, same months: income +1129k, max DD -127k, worst week -44k; L6M income +386k, L6M DD -23k, L3M income +199k)

**VERDICT WEAK: best landscape exit = `xi15all` (TL3_DX_NP_MF2_ls_xi15all_M)**: income -21k (-2.0%), max DD gap +39k, worst-week gap +0k, L6M income -52k / DD gap -3k, L3M income +13k / DD gap +2k, NQ-down weeks +439k vs +488k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| g75a30 | 42 | -279k | +40k | -4k | -116k / +6k | -29k / +2k | -185k | -36k / +63k / -139k / -167k | WEAK |
| xi15all | 37 | -21k | +39k | +0k | -52k / -3k | +13k / +2k | -50k | -14k / +53k / +10k / -70k | WEAK |
| g67a30 | 42 | -243k | +38k | -2k | -94k / +6k | -23k / +2k | -171k | -27k / +50k / -116k / -150k | WEAK |
| lv07t | 42 | -30k | +32k | +0k | -102k / -3k | -34k / -0k | -30k | -21k / +80k / +30k / -119k | WEAK |
| xi10ext | 37 | -22k | +30k | -1k | -89k / -3k | -23k / +2k | -47k | -24k / +70k / +20k / -88k | WEAK |
| x7 | 37 | +39k | +30k | +0k | -73k / -8k | -13k / -0k | -86k | -10k / +41k / +93k / -85k | WEAK |
| cbA | 37 | +29k | +30k | +0k | -62k / -5k | -16k / -0k | -90k | -13k / +40k / +93k / -92k | WEAK |
| xi10all | 37 | -71k | +29k | -1k | -95k / -3k | -22k / -0k | -93k | -18k / +66k / +23k / -143k | WEAK |
| xi10tight | 37 | -70k | +29k | -1k | -95k / -3k | -22k / -0k | -92k | -18k / +70k / +20k / -143k | WEAK |
| lv07p | 42 | -45k | +23k | +0k | -52k / -1k | +7k / +2k | -49k | -42k / +58k / +17k / -79k | WEAK |
| rg80 | 42 | -324k | +21k | +0k | -169k / +7k | -91k / +2k | -245k | -31k / +54k / -88k / -258k | WEAK |
| g67a50 | 42 | -29k | +21k | +0k | -51k / -1k | +11k / +2k | -61k | -31k / +54k / +21k / -72k | WEAK |
| rg100 | 42 | -287k | +21k | +0k | -156k / +4k | -94k / -1k | -221k | -31k / +54k / -59k / -250k | WEAK |
| g75a50 | 42 | -10k | +21k | +0k | -38k / -3k | +20k / +2k | -60k | -48k / +80k / +33k / -74k | WEAK |
| lv13t | 42 | -6k | +21k | +0k | -48k / -1k | +9k / +2k | -56k | -43k / +53k / +54k / -69k | WEAK |
| g50a30 | 42 | -295k | +19k | -6k | -125k / -2k | -27k / +0k | -216k | -18k / +17k / -122k / -172k | WEAK |
| tr100 | 42 | -119k | +7k | +0k | -36k / +3k | -45k / +0k | -61k | +15k / +12k / -77k / -69k | WEAK |
| so0 | 42 | -164k | +6k | -27k | -57k / +3k | -36k / +0k | +9k | +17k / +12k / -137k / -56k | WEAK |
| g50a50 | 42 | -105k | +1k | +0k | -100k / -30k | -14k / +1k | -79k | -8k / +10k / -0k / -107k | WEAK |
| tr50 | 42 | -86k | -7k | +0k | -108k / -29k | -15k / +0k | -36k | -8k / +8k / +21k / -106k | WEAK |
| g75a70 | 42 | +2k | -7k | +0k | +9k / -5k | +38k / +0k | -51k | -25k / -15k / +48k / -5k | WEAK |
| g67a70 | 42 | +0k | -11k | +0k | -15k / -6k | +24k / +0k | -32k | +3k / -4k / +30k / -29k | WEAK |
| l7 | 42 | +8k | -11k | +0k | -9k / -6k | +22k / +0k | -58k | -19k / -11k / +59k / -21k | WEAK |

## NY-FIB (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT WEAK: best landscape exit = `g75a30` (TL3_DX_NY_MF1_ls_g75a30_M)**: income -152k (-4.4%), max DD gap +18k, worst-week gap +7k, L6M income -133k / DD gap -0k, L3M income -135k / DD gap -22k, NQ-down weeks +1381k vs +1353k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| g75a30 | 42 | -152k | +18k | +7k | -133k / -0k | -135k / -22k | +27k | -35k / -122k / +174k / -169k | WEAK |
| so0 | 42 | -21k | +9k | +0k | -91k / -4k | -52k / +1k | -55k | +9k / +53k / +23k / -106k | WEAK |
| tr100 | 42 | -264k | -5k | +0k | -263k / -20k | -41k / -21k | -287k | +20k / +28k / -31k / -281k | WEAK |
| tr50 | 42 | -621k | -8k | +0k | -225k / -40k | -29k / -36k | -683k | -11k / -132k / -157k / -321k | WEAK |
| g67a50 | 42 | -533k | -37k | +0k | -230k / -24k | -160k / -26k | -268k | -108k / -110k / -126k / -189k | WEAK |
| rg100 | 42 | -1239k | -37k | +0k | -575k / -14k | -212k / -26k | -551k | -108k / -110k / -360k / -661k | WEAK |
| rg80 | 42 | -1483k | -37k | +0k | -635k / -1k | -223k / -19k | -702k | -108k / -110k / -371k / -893k | WEAK |
| lv07p | 42 | -482k | -46k | +0k | -188k / -25k | -134k / -25k | -268k | -102k / -116k / -124k / -140k | WEAK |
| xi15all | 37 | -622k | -49k | +3k | -187k / -24k | -149k / -26k | -220k | -140k / -188k / -114k / -180k | WEAK |
| g75a70 | 42 | -243k | -52k | +0k | -63k / +8k | -94k / -13k | +48k | -21k / -59k / +67k / -230k | WEAK |
| lv13t | 42 | -565k | -68k | +0k | -137k / -24k | -187k / -26k | -293k | -108k / -174k / -186k / -98k | WEAK |
| g50a30 | 42 | -623k | -70k | +12k | -168k / +4k | -146k / -17k | -364k | -16k / -380k / -14k / -213k | WEAK |
| l7 | 42 | -502k | -71k | +0k | -54k / -2k | -116k / -23k | -282k | -77k / -135k / -60k / -230k | WEAK |
| xi10all | 37 | -629k | -73k | +4k | -129k / -24k | -110k / -29k | -265k | -126k / -285k / -86k / -133k | WEAK |
| xi10tight | 37 | -617k | -73k | +4k | -132k / -24k | -112k / -29k | -258k | -127k / -268k / -85k / -137k | WEAK |
| x7 | 36 | -802k | -75k | +4k | -71k / -44k | -38k / -3k | -419k | -97k / -314k / -126k / -265k | WEAK |
| g50a50 | 42 | -572k | -78k | +0k | -144k / +6k | -107k / -15k | -401k | -25k / -120k / -192k / -235k | WEAK |
| lv07t | 42 | -428k | -79k | -12k | -62k / -10k | -162k / -31k | -283k | -81k / -173k / +23k / -197k | WEAK |
| xi10ext | 37 | -649k | -91k | +4k | -167k / -24k | -150k / -29k | -282k | -129k / -279k / -54k / -186k | WEAK |
| cbA | 37 | -645k | -96k | +4k | +26k / -48k | -62k / -5k | -420k | -97k / -350k / -94k / -104k | WEAK |
| g75a50 | 42 | -25k | -103k | +0k | -101k / -17k | -118k / -39k | +239k | -31k / -129k / +84k / +52k | WEAK |

## NY-NODE (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT WEAK: best landscape exit = `g67a70` (TL3_DX_NY_MF4_ls_g67a70_M)**: income +117k (+3.3%), max DD gap +45k, worst-week gap -9k, L6M income -19k / DD gap -11k, L3M income +37k / DD gap +4k, NQ-down weeks +1257k vs +1353k, years better-DD 3 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| g67a70 | 42 | +117k | +45k | -9k | -19k / -11k | +37k / +4k | -96k | -12k / +99k / +88k / -58k | WEAK |
| tr50 | 42 | -88k | +31k | +28k | -228k / -21k | -59k / -42k | -170k | -25k / +67k / +102k / -231k | WEAK |
| g50a30 | 42 | -299k | +25k | +20k | -265k / +12k | -46k / +1k | -277k | -93k / -40k / -76k / -90k | WEAK |
| g75a70 | 42 | +5k | +25k | -4k | +2k / +2k | +37k / +5k | -117k | -37k / +46k / +85k / -90k | WEAK |
| cbA | 37 | +60k | +23k | -3k | -23k / -8k | +39k / +4k | +61k | +24k / +102k / +5k / -71k | WEAK |
| x7 | 37 | +157k | +23k | +9k | -20k / -11k | +45k / +2k | -10k | +1k / +144k / +64k / -52k | WEAK |
| l7 | 42 | +14k | +18k | -8k | -3k / -8k | +38k / +6k | -34k | -17k / +23k / +92k / -84k | WEAK |
| g67a30 | 42 | -381k | +8k | +17k | -250k / +7k | +11k / +3k | -323k | -53k / -63k / -129k / -136k | WEAK |
| g75a30 | 42 | -461k | +6k | +16k | -291k / +2k | -6k / -2k | -348k | -75k / -57k / -129k / -200k | WEAK |
| lv07p | 42 | -292k | -8k | +0k | -137k / -5k | +20k / +3k | -264k | -71k / -72k / +39k / -188k | WEAK |
| g67a50 | 42 | -254k | -9k | -1k | -127k / -5k | +29k / +3k | -263k | -69k / -47k / +44k / -182k | WEAK |
| rg80 | 42 | -833k | -9k | +17k | -477k / -4k | -135k / -15k | -546k | -69k / -47k / -180k / -537k | WEAK |
| rg100 | 42 | -692k | -9k | +12k | -399k / +11k | -96k / -10k | -448k | -69k / -47k / -74k / -501k | WEAK |
| xi10tight | 37 | -189k | -9k | -2k | -123k / -5k | +40k / +3k | -203k | +13k / -53k / +1k / -149k | WEAK |
| xi10all | 37 | -183k | -9k | -2k | -122k / -5k | +42k / +3k | -205k | +13k / -54k / +13k / -155k | WEAK |
| xi10ext | 37 | -181k | -9k | -2k | -119k / -5k | +44k / +3k | -209k | +18k / -70k / +16k / -145k | WEAK |
| lv13t | 42 | -257k | -10k | +1k | -127k / -3k | +17k / +4k | -211k | -56k / -94k / +62k / -168k | WEAK |
| xi15all | 37 | -184k | -10k | -2k | -109k / -5k | +44k / +3k | -209k | -5k / -62k / +28k / -144k | WEAK |
| g75a50 | 42 | -378k | -14k | -1k | -156k / -12k | +14k / +4k | -287k | -59k / -112k / +0k / -207k | WEAK |
| lv07t | 42 | -319k | -15k | +1k | -147k / -11k | +13k / +4k | -239k | -45k / -94k / +8k / -188k | WEAK |
| tr100 | 42 | -46k | -18k | +34k | -172k / +2k | -118k / -19k | +88k | +104k / +40k / -0k / -189k | WEAK |
| g50a50 | 42 | -287k | -25k | +12k | -221k / -3k | +17k / -7k | -528k | -54k / -62k / +74k / -244k | WEAK |
| so0 | 42 | -257k | -43k | -9k | -575k / -44k | -183k / -65k | +58k | +72k / +46k / +164k / -540k | WEAK |

## NY-OFI (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT PASS: best landscape exit = `x7` (TL3_DX_NY_MF5_ls_x7_M)**: income +6k (+0.2%), max DD gap +0k, worst-week gap +10k, L6M income -52k / DD gap +0k, L3M income -20k / DD gap -1k, NQ-down weeks +1332k vs +1223k, years better-DD 2 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| tr50 | 42 | +87k | +11k | +7k | +5k / +2k | -11k / -5k | +60k | +49k / -37k / +27k / +49k | WEAK |
| lv07p | 42 | +30k | +8k | +9k | -15k / +6k | -10k / -4k | +89k | +27k / -60k / +33k / +29k | WEAK |
| lv13t | 42 | +28k | +7k | +9k | -17k / +6k | -11k / -4k | +84k | +19k / -63k / +43k / +29k | WEAK |
| g67a50 | 42 | +10k | +6k | +9k | -23k / +6k | -13k / -4k | +78k | +21k / -68k / +36k / +20k | WEAK |
| g50a50 | 42 | -6k | +4k | +7k | +37k / +5k | +26k / -2k | -20k | +70k / -164k / +14k / +74k | WEAK |
| xi15all | 37 | +0k | +4k | +9k | -25k / +6k | -15k / -4k | +90k | +27k / -70k / +27k / +17k | WEAK |
| lv07t | 42 | +64k | +3k | +11k | -6k / +6k | -6k / -4k | +99k | +35k / -24k / +22k / +31k | WEAK |
| g75a50 | 42 | +39k | +2k | +10k | -1k / +6k | -8k / -3k | +81k | +34k / -59k / +26k / +39k | WEAK |
| g67a70 | 42 | +21k | +2k | +10k | -30k / +0k | -7k / -0k | +77k | +16k / -12k / +36k / -20k | WEAK |
| g67a30 | 42 | -117k | +1k | +12k | -34k / +6k | -17k / -6k | -10k | +92k / -109k / -82k / -18k | WEAK |
| x7 | 37 | +6k | +0k | +10k | -52k / +0k | -20k / -1k | +110k | +28k / -18k / +14k / -18k | PASS |
| g75a70 | 42 | +97k | -0k | +11k | -2k / +0k | -2k / -1k | +98k | +25k / +37k / +22k / +13k | WEAK |
| l7 | 42 | +34k | -2k | +10k | -21k / +0k | -6k / +2k | +87k | +22k / -2k / +8k / +6k | WEAK |
| tr100 | 42 | -67k | -3k | +7k | -32k / -6k | -26k / -27k | -77k | +65k / -106k / -22k / -5k | WEAK |
| xi10tight | 37 | -11k | -3k | +12k | -28k / +6k | -14k / -5k | +104k | +19k / -74k / +18k / +26k | WEAK |
| g50a30 | 42 | -127k | -4k | +8k | +32k / +9k | +23k / -7k | -53k | +97k / -202k / -63k / +41k | WEAK |
| xi10all | 37 | -17k | -6k | +12k | -28k / +6k | -14k / -5k | +103k | +16k / -72k / +15k / +24k | WEAK |
| xi10ext | 37 | -17k | -6k | +12k | -30k / +6k | -13k / -5k | +104k | +15k / -65k / +16k / +17k | WEAK |
| g75a30 | 42 | -238k | -6k | +13k | -52k / +6k | -36k / -6k | -116k | +79k / -204k / -79k / -33k | WEAK |
| rg100 | 42 | -292k | -8k | +1k | -93k / +6k | -47k / -15k | -44k | +21k / -68k / -124k / -122k | WEAK |
| rg80 | 42 | -333k | -10k | +1k | -104k / +4k | -51k / -17k | -55k | +21k / -68k / -144k / -143k | WEAK |
| cbA | 37 | +40k | -20k | +5k | -25k / +3k | -24k / -6k | +130k | +32k / -41k / +13k / +37k | WEAK |
| so0 | 42 | -160k | -29k | +1k | -96k / -5k | -22k / -11k | -154k | +33k / -38k / -97k / -57k | WEAK |

## NY-VALUE (live bracket, same months: income +3498k, max DD -164k, worst week -110k; L6M income +1463k, L6M DD -35k, L3M income +507k)

**VERDICT WEAK: best landscape exit = `tr50` (TL3_DX_NY_MF2_ls_tr50_M)**: income -226k (-6.5%), max DD gap -4k, worst-week gap +5k, L6M income -168k / DD gap -10k, L3M income -117k / DD gap -31k, NQ-down weeks +1197k vs +1353k, years better-DD 1 of 3.

| code | months | income gap | max DD gap | worst-wk gap | L6M inc / DD | L3M inc / DD | NQ-down wks gap | 2023 / 2024 / 2025 / 2026 income gap | PASS |
|---|---|---|---|---|---|---|---|---|---|
| g67a50 | 42 | -381k | +4k | +5k | -162k / -5k | -114k / -16k | -221k | +90k / -127k / -218k / -126k | WEAK |
| xi15all | 37 | -417k | +0k | +10k | -157k / -5k | -115k / -18k | -246k | +87k / -154k / -238k / -112k | WEAK |
| xi10ext | 37 | -457k | -2k | +10k | -174k / -5k | -118k / -18k | -307k | +100k / -176k / -230k / -152k | WEAK |
| tr50 | 42 | -226k | -4k | +5k | -168k / -10k | -117k / -31k | -156k | +98k / -17k / -149k / -158k | WEAK |
| g50a50 | 42 | -456k | -5k | -4k | -242k / -10k | -174k / -22k | -290k | +66k / -56k / -239k / -227k | WEAK |
| so0 | 42 | -24k | -5k | +12k | -208k / -61k | -246k / -82k | +360k | +91k / +26k / -169k / +28k | WEAK |
| xi10all | 37 | -410k | -6k | +10k | -168k / -5k | -118k / -18k | -279k | +98k / -166k / -205k / -136k | WEAK |
| xi10tight | 37 | -400k | -6k | +11k | -166k / -5k | -116k / -18k | -273k | +98k / -167k / -196k / -135k | WEAK |
| g75a70 | 42 | -285k | -7k | -10k | -93k / -8k | -65k / +2k | -195k | +41k / -76k / -105k / -145k | WEAK |
| l7 | 42 | -166k | -10k | +1k | -82k / +3k | -65k / +3k | -90k | +74k / -67k / -79k / -95k | WEAK |
| g50a30 | 42 | -270k | -17k | +6k | -175k / -26k | -141k / -31k | -259k | +155k / -97k / -122k / -206k | WEAK |
| tr100 | 42 | -284k | -19k | +2k | -281k / -15k | -224k / -12k | -103k | +153k / -106k / -102k / -229k | WEAK |
| g75a50 | 42 | -296k | -20k | +2k | -127k / -15k | -91k / -1k | -197k | +95k / -69k / -222k / -100k | WEAK |
| lv07p | 42 | -417k | -22k | +0k | -161k / -6k | -118k / -15k | -209k | +80k / -142k / -205k / -151k | WEAK |
| lv07t | 42 | -394k | -24k | -1k | -156k / -7k | -119k / -12k | -225k | +63k / -124k / -187k / -146k | WEAK |
| lv13t | 42 | -417k | -25k | -1k | -149k / -2k | -107k / -16k | -214k | +93k / -143k / -223k / -144k | WEAK |
| g67a70 | 42 | -114k | -26k | +6k | -83k / -2k | -63k / +2k | -56k | +98k / -85k / -65k / -61k | WEAK |
| cbA | 37 | -393k | -28k | -3k | -163k / -11k | -130k / -32k | -230k | +62k / -183k / -88k / -184k | WEAK |
| rg100 | 42 | -571k | -29k | -7k | -281k / -32k | -128k / -24k | -318k | +90k / -127k / -260k / -274k | WEAK |
| g67a30 | 42 | -323k | -31k | -33k | -164k / -29k | -115k / -16k | -236k | +172k / -106k / -156k / -233k | WEAK |
| rg80 | 42 | -575k | -31k | -4k | -292k / -34k | -148k / -37k | -314k | +90k / -127k / -254k / -283k | WEAK |
| x7 | 37 | -253k | -33k | +12k | -125k / -4k | -87k / -3k | -147k | +56k / -161k / -87k / -63k | WEAK |
| g75a30 | 42 | -384k | -34k | -29k | -188k / -28k | -114k / -20k | -241k | +128k / -103k / -166k / -244k | WEAK |

## Notes and gaps
- Sets with a month missing (failed exact-engine rows, retried by the dispatcher) are left out of this page: AS-NR7 xi10all / xi10ext / xi10tight / xi15all / x7 / cbA (202309), NY-FIB x7 (202504), NY-FIB g67a30 / g67a70 (one month). Check the tables for the codes present.
- Not wired in this pass: liquidity-ahead take from MBO resting size (PoolHook coverage starts about 2025-07), NYSE TICK. Level takes use causal day levels (prior day, session, open, IB, VWAP, pivots, fib, POC, round 100) fixed at the entry bar.
- xi rows start 2023-09 (the age feed has no ES / RTY mids before 2023-08); rg rows act only from 2025-03 (the forecast file); on earlier months rg = its g67a50 base. 1-lot trades cannot take a partial (lv07p).
- Whole-mix numbers include interactions with the other books; the NQ-down-weeks column is the summed weekly P&L of weeks where NQ fell (nq_weekly.json).
- Strict PASS rule (see top) was met by no set; the VERDICT line gives the best exit by the drawdown-first rule with its cost either way.
