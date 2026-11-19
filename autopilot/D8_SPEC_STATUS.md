**NY AM STAGE 1 ONE DATE LINE (simulated mix with handoff of empty streams, fleet 8598 /h measured / 5076 /h lead / 4000 low): NY AM first looks end 2026-11-20 02:42Z; NY AM stream incl. other-book REPLACE rows ends **2026-11-20 02:42Z** (low case 2026-11-20 07:30Z); follow-ups of strict passers end 2026-11-20 03:00Z (exit rows also wait for the unbuilt exit families ~21:00Z); FLEET-WIDE stage 1 (Asia + NY AM) ends **2026-11-20 03:06Z** (5 h); combination stage: W-COMBO; LONG POLE: follow-ups.**

Updated 2026-11-19 22:30Z by W-NYENG. **RULE (order 1337Z): NO D8 build spec until the Asia AND NY AM ladders are COMPLETE**: every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run and the today / REPLACE / ADD pick. No wave dates. London and NY PM follow (stages 2 and 3). Funnel model redone at 14:00Z from landed data (order 1400Z).

## STAGE 1 COMPLETE (Asia + NY AM): THREE dates from a funnel with explicit stage pass rates, at the current rate **8594 set-months/h** (HEALTH.md fleet rate; tp_admit last hour says a different number at times; W-COMPILED factor not yet available, W-FASTLADDER share not included)

**Funnel stages and rates read from landed NY AM data:** (1) first look: 1391 of 4557 ladder cells have REPLACE last-6-month + last-3-month rows; (2) BEATER under the W-ASIA gate (a REPLACE row beats today stack on BOTH L6M and L3M: ulcer lower, mean not lower, worst week and max DD not worse): **0.7% of looked-at cells (10 of 1391); 0.4% with a REPLACE-K7 row; the looser rule (ulcer < 0 and mean >= 0 only) gives 1.7% (23)** (uncalibrated, label BETTER; calibration caveat: the whole-search null gives per-mode FDR both-side 8-25%, long-only 12-18%, i.e. a share of these yes rows is noise); (3) PASS prior years + persistence (rule B: no RED year in 2023/24/25; pooled persistence >= 0.58): **7 of 12 yes rows with all three prior years landed pass = 58%** (3 of 8 cells); the 4 REPLACE-K7 beaters: 3 pass (L01811caa, L6a25b155 pass, L0f097450 RED 2023); Asia: 8 passers among the beaters evaluated (W-ASIA); (4) only PASSERS get 30 controls (ADD and REPLACE variants: 2 x 180), layers (347, W-LAYERS cost) and exit rows (438) = 890 set-months per passer; every beater gets prior years (37 per beating REPLACE set). REPLACE ONLY (order 1407Z): ADD rows are reference, not candidates, and are no longer queued; exit rows = top 3 recipes x REPLACE x (6+37) + 30 controls x 6 = 309.

**Remaining set-months that do NOT depend on the funnel:** NY AM first looks, REPLACE rows only, 16673 (16673 queued + -1936 unbuilt cells x 6; 6493 of 4557 cells built) + NY AM REPLACE vs the other live books for alive cells 74394 + Asia useful work as W-ASIA counts it after its gate (first looks 27k + a2 35k = 62000; follow-ups 4k prior years + 20k controls + 1.6k passer controls + 8 passers x layers/exit = 31880; total ~88k+). GATE applied to NY AM in the advance step at 14:25Z (same as Asia): prior years and controls only for sets that beat today stack on BOTH L6M and L3M; other cells wait in stage A2 for their a2 rows and drop out if none beats; 6,290 prior-year/control lines of non-beating sets were PARKED (parked_gate_1415.txt, 112 cells; 76 cells returned to A2).

| scenario | NY AM beaters share / pass rate | NY AM beaters -> passers | Asia beaters share / pass | NY AM follow-ups | Asia follow-ups | TOTAL set-months | hours | **STAGE 1 COMPLETE** |
|---|---|---|---|---|---|---|---|---|
| LOW (strict gate, half the measured share) | 0.4% / 50% | 16 -> 8 | 2.2% / 50% | 8077 | 15940 | 177084 | 21 | **2026-11-20 19:06Z** |
| BASE (STRICT gate, measured share less mid FDR) | 0.6% / 58% | 27 -> 16 | 3.0% / 58% | 15518 | 21736 | 190321 | 22 | **2026-11-20 20:38Z** |
| HIGH (strict gate, 3x: the a2 other-book rows add chances) | 2.2% / 80% | 98 -> 79 | 4.4% / 80% | 74704 | 31880 | 259651 | 30 | **2026-11-21 04:43Z** |
| VARIANT: LOOSER gate (ulcer < 0 and mean >= 0 only), measured share less mid FDR | 1.4% / 58% | 63 -> 37 | 3.0% / 58% | 35691 | 21736 | 210494 | 24 | **2026-11-20 22:59Z** |
| UPPER BOUND: every REPLACE beater gets everything (10% NY AM / 6.5% Asia) | 10.0% / 100% | 456 -> 456 | 6.5% / 100% | 427492 | 47095 | 627655 | 73 | 2026-11-22 23:32Z |

Scenario assumptions (REPLACE ONLY, STRICT gate = ulcer lower, mean not lower, worst week and max DD not worse on L6M and L3M): measured strict share 0.7%; LOW = half of it, 50% pass; BASE = the measured share minus the mid FDR 16.5% (calibration), pass rate = observed on the loose REPLACE yes rows (58%); HIGH = 3x the strict share, 80% pass; the LOOSER-gate row is a variant only. SMALL SAMPLE: 1391 REPLACE looks. Asia beater share 2.4% (W-ASIA strict rule: 15 of 614) / 4.4% / 6.5% (looser rule 50 of 766), Asia pass rates as NY AM. First looks alone (NY AM 16673 + Asia 62000) end 2026-11-20 07:39Z. CAVEAT: the observed beater share comes from the cells looked at so far, which are the BEST screen-ranked ones (the ladder runs in rank order), so extrapolating it to all 9,081 cells over-states the BASE and HIGH rows; the true beater share of the tail is probably lower (LOW is the REPLACE-only bound). The biggest remaining uncertainty is the beater and pass share; the null calibration (R4) and the persistence/rule-B gates move it.

## ENGINE-SLOT SPLIT (re-proposed from remaining FIRST LOOKS, then gate-pass follow-ups; NOT applied)

Remaining first looks: Asia 62000 vs NY AM 16673 (+74394 NY AM other-book rows) => **Asia 79% / NY AM 21%** (41% / 59% with the other-book rows) = ~3481 / ~5113 set-months/h at 8594/h; with the base-case follow-ups added the work ratio is NY AM 56% / Asia 44% (NY AM follow-ups 15518 vs Asia 21736): the follow-ups only exist for cells that pass, so they come AFTER the first looks, are small until prior years land, and are taken first by the mix when they appear. Proposal: start at **Asia 79% / NY AM 21%** (remaining first looks only; the other-book REPLACE rows are ordered behind the first looks of both ladders) and re-propose when the funnel is re-measured (each refresh of this page recomputes it). W-ASIA's passer controls (_asi/first.txt) stay first, my gate-pass follow-ups stay first in pending_l.txt / the front of pending_r5.txt; the mix file puts both unmixed ahead of the interleaved block. NY AM at the order's ~120/h would leave 888 h of work. NOT applied: the QUEUES.txt edit (replace the _asi/pending.txt and _nye/pending_r5.txt lines by /mnt/l2/l2vast/_split/pending_mix.txt, built by code/th_nyeng/ny_mix.py <NYAM share>, e.g. 0.41) waits for the lead.

## Early-rung exits (4c): lines queued for cells that already left the ladder

Cells with stage "out" in the NY advance state: 595. Later-rung lines (other-book, prior-year, control) still queued for them: **1766** (the advance step queues a later rung only after the earlier one passes). Park rule: any such line goes to /mnt/l2/l2vast/_nye/parked_out_cells.txt (not deleted). Exclusion list for W-DEDUP: cell ids with stage out = L0005282f, L0018ff2b, L0044a103, L00e9ef7d, L00ef412d, L01ae185e, L01b83d93, L02307192, L027c6cc7, L02831614, L029c1536, L031c8045, L047eebef, L0612a129, L063c1550, L064f893e, L065c2291, L066b4da5, L0705a05d, L076bc130, L08c1815f, L08c38a8a, L094ee8e5, L09c9a917, L0ae4276c, L0affdff7, L0bac981a, L0bd23639, L0cb34690, L0d7bea1f, L0ddd0c84, L0ebb3bcd, L0eeaa018, L0f097450, L0f11d2f7, L1020a386, L11089f98, L121542b3, L1229e64c, L13e165bc, L143274ab, L153a9ab3, L15658e51, L1589e0b8, L15e18f8b, L16344500, L16653aa0, L175f93d1, L1801f948, L189d197c, L18ab065e, L18f42af2, L1920a20b, L19c3031f, L1a10b4db, L1a9381e0, L1aa656d8, L1b0fee34, L1b77a301, L1bd2be11, L1beb50d9, L1c0f69fd, L1ce5c41b, L1ce61a64, L1d01954c, L1d0a98af, L1e0094b0, L201241f4, L2013a2c5, L2140f591, L21bffd7e, L21f079b6, L2230e4ef, L228a2c4a, L22b5c5d1, L22cf3215, L23b82a1a, L2438b7d7, L24e2abe5, L24ec3736, L2645ba76, L2658360c, L27a925f8, L27a93ead, L280828cf, L28393d3d, L28c3922b, L28e26f99, L28e7ee31, L29e37d0c, L2bc649b6, L2becd23c, L2cc89f59, L2cd163fd, L2d1b439e, L2d406d8d, L2d60df7d, L2db980e5, L2dbb7680, L2e45679e, L2eb9ac1b, L2ed2f633, L2ed70e23, L2fa1b60e, L30ae34bf, L30e2c8aa, L31000131, L3122d86b, L317eb843, L32591d74, L334ee144, L3426e2ca, L34d66961, L3516aa98, L359f1868, L36dfa540, L36fefaed, L3701b464, L37897907, L384f5251, L385ef576, L38ff2b59, L39ed8ccd, L39f71c1e, L3c82df8a, L3cf3cc92, L3d5908cd, L3dabd7b1, L3e4745d2, L3e6ebc24, L3eb6b968, L3eba69b2, L3f67e925, L3fbe0f8d, L4023189a, L40f3022e, L41042978, L413810a9, L416cf628, L41d3a8da, L41eda10c, L42935176, L42a44cee, L439967d6, L43f0cbfb, L440aa51b, L44290ea7, L4466aa9d, L453ecfdf, L45bbaa6b, L45e72f8b, L4661e113, L46c24b4c, L474262d9, L4744d92c, L47a52047, L47e7770d, L4932c506, L4a47ecfe, L4add28dc, L4aeda76f, L4b441c50, L4c001809, L4d1c3ef6, L4d6fa935, L4dcb4c69, L4e89079d, L4ebf6aef, L4ee926f6, L4fad2a44, L4fe091df, L50480de3, L50ac6ff3, L51770ecd, L523f4d50, L52599445, L52d28a9a, L537ea1d3, L53aaee00, L542e900e, L545ccc02, L54adb58c, L54d8b908, L54f86171, L55b31b0a, L55bd963b, L55d44545, L55ee1500, L56accca6, L56dd415f, L56e69508, L56ea5eb4, L5733d1ad, L5761ce13, L5814d305, L587b902b, L5916c8ec, L597837ab, L59855e53, L598b62a5, L59b2e323, L5a49e86d, L5a4f924e, L5bb9ae2f, L5c4c8c9a, L5c621a0e, L5ca77208, L5ce83827, L5d9313d2, L5d98fe32, L5ea34e54, L5f405e4b, L60367862, L60936dc9, L60aed383, L6118cace, L617f2c33, L62a6a6b7, L631a8535, L632bb3c8, L638c37cf, L63b1d509, L64299ed3, L649a387a, L64a0b978, L652327d9, L65e06e99, L66b909fe, L6755b324, L6772d676, L67e9df70, L68413e62, L68f4e8d6, L69514a8f, L6af3e195, L6b5f4955, L6c027ebe, L6cb86f62, L6cdb09b8, L6cef7ca5, L6cfe503f, L6d0ae138, L6dc6bb7f, L70fbd6a7, L70fd7253, L731f3a21, L734ab4c9, L73b20f78, L75194540, L75313db5, L755b7b45, L75ad06c2, L75c2b2e8, L769fdf33, L76c6e684, L77082875, L775c6ba4, L7950d9dc, L7af47322, L7b2166a5, L7ce10fc0, L7d2c80d3, L7ead5d0a, L7ebc49f8, L7f23f0d5, L7fa34284, L7fc2dbc1, L7fc96650, L803fc54c, L80f5d118, L815801d4, L81a1349f, L821971d5, L82db62cd, L8320d626, L840f5f7e, L848867d4, L8553d968, L8580e226, L862d9ab1, L87220a58, L8820726f, L889c761a, L8989cde7, L8a4907eb, L8a68ae23, L8a7d04c3, L8a8dd5b7, L8b3681a5, L8b83a467, L8be740c3, L8c4b5096, L8d47873d, L8d78e68e, L8db3d632, L8dcfb4d2, L8dfb9b8c, L8e8dc6f4, L8eca41a9, L8f00668e, L8f47a7f4, L8fe0dc6f, L9014a4d5, L90842741, L90aedba2, L9106a04a, L9118c160, L9120c667, L928ee468, L9365ece7, L9397d8c8, L93e7f7e5, L94012503, L948f2a7e, L9513708b, L955779bc, L957a0544, L95b1cc17, L962501c9, L96424791, L964cfc29, L966b7824, L966b7e14, L973aa7a1, L984a3d00, L98834592, L98a567fd, L99000f8d, L9978660d, L99c985bf, L9a60042a, L9aa810ff, L9ade175b, L9c2f04fe, L9e449cb7, L9e706c57, L9f43c17a, L9f888218, L9fc0238e, La059a8e8, La087e948, La092861b, La0e358d7, La173c238, La1ed8df7, La201dd83, La234f575, La2cff349, La372e6e4, La3e5bc8e, La3e7712e, La53db301, La5a1a5ec, La6102ffc, La62b0509, La6a45b1a, La6c0ac4d, La6c7c86a, La6e1543c, La767493f, La8600386, La86531b2, La872937f, La894b287, La8a5e841, La8f7d729, La96512f6, La96d4160, La9ab8331, Laac6b61d, Lab0ec3ca, Lab7654ec, Lab808296, Lab985018, Labf3c62a, Lad357def, Lad9f94cb, Laddc32be, Ladec93ae, Lae1b59ec, Lb13de797, Lb1626f1e, Lb23d399b, Lb248e87c, Lb28f30c8, Lb309c9b6, Lb35e02b8, Lb37b2695, Lb3d8483f, Lb3dbcf28, Lb46d2b5d, Lb4b1526a, Lb4ee29cb, Lb4efe93c, Lb5101a28, Lb52cf323, Lb549d698, Lb5d2fb00, Lb68a4cab, Lb6ffbdd5, Lb7db97e8, Lb809e889, Lb8da6068, Lb8fe4f02, Lb9026469, Lb9818bde, Lb9c7c06a, Lba356762, Lbb00ef18, Lbb258b12, Lbb44a057, Lbb5b84f5, Lbb5e0a25, Lbb6282e1, Lbb8dc803, Lbbb39855, Lbbb92057, Lbbdd2890, Lbc4ad3b5, Lbcc110fa, Lbd1a1d57, Lbe0cbeff, Lbe660734, Lbe9e3d0d, Lbf234099, Lbf545353, Lbfdb7dfe, Lc02f38c2, Lc06cbfac, Lc08f2494, Lc0aecc18, Lc0d81f93, Lc0dd72a1, Lc22d07b2, Lc2b684bb, Lc3736705, Lc38f3a49, Lc3ec3a0b, Lc43862b6, Lc4e81ec2, Lc594c76e, Lc5ff363e, Lc66b8fed, Lc723e512, Lc7333ae2, Lc7e078a6, Lc7edb246, Lc80e2b3b, Lc889083d, Lc8d51dc7, Lca2ed2a5, Lca409c7e, Lca57ebf7, Lccba36a3, Lcccca0ec, Lcd1b77c9, Lcd4b0473, Lcd80dfef, Lcd9d9059, Lcdd6a540, Lce070e31, Lce1c241f, Lce34df6d, Lce4b6104, Lcef44bf0, Lcfbaf18c, Lcfdf6a30, Lcfe53f35, Ld05d76e4, Ld0eb2c83, Ld1499727, Ld1a8a78d, Ld2339be1, Ld2537ef3, Ld3898b7a, Ld40c5e85, Ld4cb48d4, Ld4ffc994, Ld52800f7, Ld62c5532, Ld6468e0c, Ld6f467f5, Ld7278aa9, Ld7a70858, Ld87ff441, Ld95ec786, Ld9b4da69, Lda27b4d8, Lda741b04, Ldaf19410, Ldc1b06a0, Ldd5dd7c3, Ldd6284ee, Ldda3fdd8, Lde046d66, Lde72d37e, Ldead827c, Ldecfe020, Le0089501, Le0bf852b, Le0d695f3, Le0da99e2, Le1a69b6c, Le1b9bdf2, Le1cf849f, Le1f36da0, Le27dc486, Le30d987f, Le3193838, Le36ba157, Le494ddab, Le4bbdc2f, Le5019545, Le5148785, Le534251c, Le5457a79, Le54a1a93, Le65f7dfd, Le6693872, Le6986a73, Le6edc0a0, Le727d1fa, Le74aaf47, Le788e239, Le8370942, Le8403d39, Le944b0b0, Le96a00db, Lea3ea462, Lea620d76, Leac51c1d, Lec4e334f, Lec6afe3f, Lec804905, Led8d70a3, Leddd6d68, Lee8c3266, Lee8cb424, Lef1792aa, Lefa05e76, Lefe43a1e, Lf024d52e, Lf04cbe7d, Lf0aacb4f, Lf11c3d85, Lf11e08be, Lf24a84da, Lf25a4095, Lf29cffba, Lf328379c, Lf3466e88, Lf3741df0, Lf3c276f9, Lf4224a5d, Lf46de2b6, Lf4900ad5, Lf506479f, Lf63aeb97, Lf67c3049, Lf6be7f5f, Lf74144f7, Lf76e3db4, Lf837960b, Lf8cf358d, Lf8e1a552, Lf9224ca2, Lf94730bc, Lf967df3b, Lfa5912ed, Lfaf84902, Lfb16b890, Lfb69580e, Lfb7da229, Lfbcde421, Lfc41c8c2, Lfc8753c0, Lfc8a41f2, Lfcba7672, Lfcf3e0b2, Lfd3fc422, Lfd4c2d53, Lfd763b0d, Lfdd046b4, Lfe00f53f, Lfe2dbc4b, Lfe4cf0cb, Lfe63b474, Lfe900eef, Lfee6ee88, Lff5bd358, Lff8cabe0, Lff9aa73b, Lffb0f715, Lffb1b796, Lffd711a2 (file /mnt/l2/l2vast/_nye/ladder_adv_state.json, key stage starting with "out"); W-DEDUP does the sweep, I own the advance logic.

(pick table unavailable: FileNotFoundError(2, 'No such file or directory'))

## ENGINE RULE B (prior-year gate) for the 4 NY AM K7 beaters (order 1122Z; full table also on NEW_BOOK_BEATS_LIVE_NYAM.md)

**SIGN CONVENTION (explicit).** Rule B columns below are "% WORSE than today s stack" (positive = WORSE, negative = better): ulcer % = (new-ref)/ref; max DD % and worst week % = (ref-new)/|ref|; mean $/wk % = (ref-new)/|ref| (lower mean = positive = worse). The dollar columns elsewhere on this page: "d ulcer negative = better" (lower ulcer), "d worst week +1,631 = the worst week is $1,631 LESS bad than today s stack", "d max DD positive = less deep", "d mean positive = more $/wk". RED > 30% worse, AMBER 15-30%, GREEN otherwise; cell colour = worst of the four metrics; the verdict needs no RED year; a year with no engine rows yet = pending (not fail).

**Rule B = engine (REPLACE / ADD row vs TODAY s stack, same year).** Rule A (screen: bare stream, prior-year weekly R > 30% worse than the cell s own L6M) only orders the queue and is shown in its own column from the shortlist.

| cell | variant | year | ulcer % worse | max DD % worse | worst wk % worse | mean $/wk % worse | colour | persistence (2-wk windows new stack not worse) | rule A (screen, queue order only) |
|---|---|---|---|---|---|---|---|---|---|
| L01811caa | both sides REPLACE K7 | 2023 | -21% | +11% | +24% | -25% | AMBER | 0.47 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2024 | -14% | -4% | +6% | -14% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2025 | -12% | -9% | -11% | -8% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2023 | -15% | -2% | +7% | -64% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2024 | -12% | -1% | +3% | -12% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides ADD | 2025 | -17% | -14% | -2% | -17% | GREEN | 0.77 | see shortlist |
| L01811caa | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2023 | -12% | +12% | +13% | -30% | GREEN | 0.53 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2024 | -3% | -8% | -6% | -16% | GREEN | 0.54 | see shortlist |
| L0f097450 (twin of L21f079b6) | both sides ADD | 2025 | -22% | -17% | -11% | -11% | GREEN | 0.69 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L0f097450 (twin of L21f079b6) | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L0f097450 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L3701b464 (twin of L21f079b6) | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L3701b464 | both sides ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L3701b464 (twin of L21f079b6) | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L3701b464 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | both sides REPLACE K7 | 2023 | -4% | +15% | +5% | -34% | AMBER | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2024 | +10% | -3% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2025 | +3% | +3% | +0% | -7% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides ADD | 2023 | -18% | +3% | -8% | -72% | GREEN | 0.79 | see shortlist |
| L6a25b155 | both sides ADD | 2024 | +12% | -0% | -6% | -20% | GREEN | 0.54 | see shortlist |
| L6a25b155 | both sides ADD | 2025 | -6% | +0% | +12% | -20% | GREEN | 0.65 | see shortlist |
| L6a25b155 | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |

**Rule B verdict per row:**
- L01811caa both sides REPLACE K7: no RED year
- L01811caa both sides ADD: no RED year
- L01811caa long-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa long-only ADD: pending (no prior-year rows yet)
- L01811caa short-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa short-only ADD: pending (no prior-year rows yet)
- L0f097450 both sides REPLACE K7: RED year
- L0f097450 both sides ADD: no RED year
- L0f097450 long-only REPLACE K7: no RED year
- L0f097450 long-only ADD: no RED year
- L0f097450 short-only REPLACE K7: pending (no prior-year rows yet)
- L0f097450 short-only ADD: pending (no prior-year rows yet)
- L3701b464 both sides REPLACE K7: RED year
- L3701b464 both sides ADD: pending (no prior-year rows yet)
- L3701b464 long-only REPLACE K7: no RED year
- L3701b464 long-only ADD: no RED year
- L3701b464 short-only REPLACE K7: pending (no prior-year rows yet)
- L3701b464 short-only ADD: pending (no prior-year rows yet)
- L6a25b155 both sides REPLACE K7: no RED year
- L6a25b155 both sides ADD: no RED year
- L6a25b155 long-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 long-only ADD: pending (no prior-year rows yet)
- L6a25b155 short-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 short-only ADD: pending (no prior-year rows yet)

## NY AM ONE DATE LINE (order 1750Z, restated 1900Z: 4,557-cell ladder, other-book rows parked, id-duplicate first-look lines parked: first looks + ranked follow-ups)

**NY AM STAGE 1 ONE DATE LINE (simulated mix with handoff of empty streams, fleet 8598 /h measured / 5076 /h lead / 4000 low): NY AM first looks end 2026-11-20 02:42Z; NY AM stream incl. other-book REPLACE rows ends **2026-11-20 02:42Z** (low case 2026-11-20 07:30Z); follow-ups of strict passers end 2026-11-20 03:00Z (exit rows also wait for the unbuilt exit families ~21:00Z); FLEET-WIDE stage 1 (Asia + NY AM) ends **2026-11-20 03:06Z** (5 h); combination stage: W-COMBO; LONG POLE: follow-ups.**

| part (NY AM) | set-months left | measured last 60 min |
|---|---|---|
| first looks: stage A REPLACE-K7 lines (ladder = 4557 DISTINCT cells, all built; 1961 first-looked; the 2588 old-seed-only ids are duplicate ids of built cells; duplicate-side lines of identical-stream pairs parked) | 16659 | 1748 /h |
| other-book REPLACE rows P7/M7/H7 (0 queued + ~0 to be appended as first looks finish: 2776 cells x 55% non-negative x 18) | 0 | 42 /h |
| stage B/C of the strict passers (prior years 37 + controls 526 left for the 8 strict sets in 5 cells) | 563 | 2006 /h |
| layers (0 queued, W-LAYERS + 1388 to be created for the 4 new passer cells) | 1388 | 2173 /h |
| exit pairs (95 queued) + exit rows for the 5 passer cells (309 each, families unbuilt until builders W-XB1/XB2 ~21:00Z) | 1640 | 55 /h |
| follow-ups of FUTURE strict passers (about 7 more cells x 873 set-months each, at the measured passer rate 5 of 1961) | 6180 | 0 /h |

Other streams in the mix: Asia first looks 2214, follow-ups total 20159 (NY AM 9771 + Asia 10388).

| fleet rate | Asia first looks end | NY AM first looks end | NY AM stream (first looks + other-book rows) ends | follow-ups end | **ALL (stage 1)** |
|---|---|---|---|---|---|
| 5076 /h | 2026-11-19 23:30Z | 2026-11-20 05:36Z | 2026-11-20 05:36Z | 2026-11-20 06:12Z | **2026-11-20 06:18Z** (8 h) |
| 8598 /h | 2026-11-19 23:06Z | 2026-11-20 02:42Z | 2026-11-20 02:42Z | 2026-11-20 03:00Z | **2026-11-20 03:06Z** (5 h) |
| 4000 /h | 2026-11-19 23:48Z | 2026-11-20 07:30Z | 2026-11-20 07:30Z | 2026-11-20 08:12Z | **2026-11-20 08:18Z** (10 h) |

OWN-MERIT FOLLOW-UPS (order 1806Z: ranked, no cap): follow-ups for the top-N ranked cells per session = N x 873 set-months (prior years 37 + 30 controls 180 + layers 347 + exit rows 309); fleet 8598 /h; the stage-1 date depends on N:

| N cells per session (NY AM and Asia each) | extra follow-up set-months | ALL stage 1 ends | hours |
|---|---|---|---|
| 50 | 87300 | 2026-11-20 13:18Z | 15 |
| 100 | 174600 | 2026-11-20 23:30Z | 25 |
| 200 | 349200 | 2026-11-21 19:48Z | 45 |
| 500 | 873000 | 2026-11-24 08:42Z | 106 |

Assumptions: weights Asia first looks 41.3%% / NY AM stream 28.7%% / follow-ups 30%% with the share of an EMPTY stream handed to the others (ny_mix3.py); the other-book rows are modelled as available from the start (they are appended as first looks complete, so this is the optimistic end); strict-passer follow-ups as in the part table (8 sets in 5 cells + extrapolated future passers). The mix is applied on the dispatchers (the lead measures it).
