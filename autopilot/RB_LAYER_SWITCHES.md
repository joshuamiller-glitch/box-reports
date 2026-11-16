# RB_LAYER_SWITCHES - engine layer switches for T-REBUILD (W-EV, 2026-11-16 ~19:20Z). Base TL3_EV_JN05W2JL2. Code: outputs/code/th_engfix/{ev_switch.py, ev_layers.py, ev_panel.py, mk_ly.py}; la_hooks (th_deepen_la) for flat lines.
## What JL2 contains
JL2 = JN05W2J + P7 post-stop/cut blackout (30 min, all history) + ATR-SKIP (P7 atr_rel >= 1.6 = SKIP; series jnr_atr_ev3 with DS7's roll-jump rule) ; REG (atr_rel >= 1.3 -> lots x0.5, i.e. 12 -> 6 live) is inside the JN04 jnrule layers, same ev3 series. NKD take NOT included (cannot be run from owned data). Contents:
- state cut lines (state.by_unit, per book and session; book-based, engine book is the CLEAN one): K7 45/10x/w2/p3 var2; P7 40/5x/w5/p3 (but replaced by the F3 ctx cells below); M7 30/10x/w2/p2; U7 30/60x/w15/p5 var2; A7 30/60x/w15/p3; H7 15/30x/w10/p2 newmae var1 (H7 nyam 35/20x/w2/p1 var2); O7 25/20x/w10/p10.
- hooklist: wb_hooks (panel: P7 day cap [42000, 8400] and P7 table 7,4,0,4,0,0; ctxcut F3: P7 fresh 45/5x/w5/p10, rechase 30/10x/w5/p2), ec_hooks (K7 flat d45 = -0.75 x 60), scr_hooks (DAY-DONE C22: closes >= 22 and day P&L <= -2 x $1,200 = -$2,400 engine = $4,200 live), c_gov (governor/new evidence: P7, 2 same-side losers without a new session extreme, sessions 0,1,3,4), ev_panel (atr_skip, bo).
- set keys: sizer {thr .3, lo .5, hi 1.0} (Q1-A ER ladder), cde (JN04 STACK cap: code 8, cap 6 engine lots = 10 live, London, same side), jnrule (LOT/SIGQ/REG), works = JN05W2J.json (igate BR3S: P7 skip when breadth_ext15 == 3; needs ES/RTY 1-min bars: extended copy via ev_store_launch.py for November, shared bars end 11-10 07:59Z).
- engine defaults not in the set JSON: stack cut 50% Asia-only (sim.stack_on_stop), NTZ half size within 20 pts (sim.ntz_check), OTE-62 hold (sim.ote_ahead), A06 slot halving (sim.SLOTLIST: H7/K7/P7/U7), B02 quiet-overnight halving (10:30-18:00 K7/P7/H7), per-book day caps sim.DAYCAP (K7/M7 12000/4800, U7/H7 24000/9600, A7 6000/2400, P7 via wb panel), give-back lock (2R keep 50%) and week floor (12R) sim.check_book_lock, L2-gated 70/30 split with add confirmations (sim.L2GATE_BOOKS K7 P7 U7 H7 M7), P7 45-s three-bar confirmation in NY AM / NY PM, session lot tables sim.SESS, roll blackout (data), time-block guards (09:00-09:59, 15:00-17:59, 18:00-18:04).
- NOT in JL2: profit-side state lines (K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten): absent (inert by construction; th_ptr ptr_hooks implements profit lines if wanted); NKD take; P7 flat -42 (add with la_hooks).
## Switch table: OFF edit / inert (= current) setting
| layer | OFF | inert | note |
|--|--|--|--|
| LOT, SIGQ, REG | hooklist ev_switch par {"lot_off":true,"sigq_off":true,"reg_off":true} | absent / {} | needs a set with jnrule |
| JN04 STACK cap | delete set key "cde" | present | JN05W2 has none |
| ATR-SKIP, blackout | delete ev_panel par keys "atr_skip" / "bo" | present as in JL2 | |
| BREADTH (BR3S) | set key "works" -> cfg with igate {"rules":[]} (file written by mk_ly.build: /mnt/l2/l2vast/_engvslive/work/works_nobreadth_JN05W2J.json) | JN05W2J.json | |
| governor | c_gov par gov [] | rule list as JL2 | |
| DAY-DONE C22 | remove the scr_hooks entry (or gates []) | present | |
| F3 context cut (P7) | wb_hooks par delete "ctxcut" (P7 then uses P7_x state cell 40/5x/w5/p3) | present | |
| K7 flat 45 | ec_hooks par rules [] ; or la_hooks flat rules | rules [{"book":"K7","kind":"flat","p":{"d":45}}] | |
| P7 flat -42 | absent (JL2 has none) | absent | add: la_hooks par flat [{"book":"P7","sess":[s],"d":42,"lo":1,"hi":200}] per session s |
| book-based cut lines | la_hooks par scut [{"book":B,"nocut":true}] (also overrides the P7 ctx cell) or state by_unit arm 1e9 | engine cells | mk_ly 'statecut' = arm 1e9 for all |
| stack cut 50% Asia-only | ev_layers par {"stack_cut":"off"} (also "all" = every session) | "asia" | pm_hooks nosc/sc equivalent |
| NTZ | ev_layers {"ntz_off":true} | false | |
| OTE-62 hold | ev_layers {"ote_off":true} | false | |
| A06 slot halving | ev_layers {"a06_off":true} | false | |
| B02 quiet halving | ev_layers {"b02_off":true} | false | |
| ER ladder (Q1-A) | ev_layers {"er_off":true} (or set sizer lo=hi=1.0) | false | |
| give-back lock + week floor | ev_layers {"lock_off":true} | false | |
| day caps | ev_panel cap_tl [[book,"2000-01-01 00:00",0,0]] (0,0 = no cap) and wb_hooks panel p7_daycap [0,0] | defaults above | engine base-lot dollars; live = x1.75 |
| L2-gated split + add confirmations | ev_layers {"l2gate_off":true} (full lots at market on the signal) | false | live book/volume gate was void (section 14 of DS3_ENGINE_VS_LIVE) |
| P7 45-s confirmation | ev_layers {"cf_off":true} | false | |
| session lot tables | ev_panel sess_tl [[book,"2000-01-01 00:00","a,b,c,d,e,f"]]; wb_hooks panel p7_sess | K7 2,2,0,1,2,0; U7 4,4,0,0,0,0; P7 7,4,0,4,0,0; H7 4,0,0,1,0,0; M7 0,2,0,1,0,0; A7 1,0,0,0,0,0; O7 1 | base lots; live x1.75 |
| one book alone | ev_layers {"only":["K7"]} (signals of other books dropped at try_entry; one position per book anyway) | absent | |
| NKD take | not available | - | needs NKD book data, not on the box |
| profit lines (K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten) | not in JL2 | absent | th_ptr ptr_hooks to add |
## 'All layers OFF, one book alone'
python3 -c "import sys; sys.path.insert(0,'outputs/code/th_engfix'); import mk_ly; mk_ly.build('TL3_RB_OFF_K7', base='TL3_EV_JN05W2JL2', off='ALL', only='K7')" writes the set JSON (done for TL3_EV_LY_OFF_<K7 M7 U7 P7 H7 A7 O7>). 'ALL' = lot sigq reg stackcap atrskip bo breadth ntz ote a06 b02 er governor dayDone ctxcut k7flat stackcut statecut locks daycaps l2gate cf. The book then runs at its table lots (native, no halvings), 60-pt stop / 60-pt target (O7 40/90), its own entry signal at market, no caps, no cut lines; what stays: session table lots 0 = no entry, time-block guards, the roll blackout, the one-position-per-book rule, fills/slippage. Entry rules of K7/P7/U7/H7/M7/A7: price-only signals.
## Identity proofs (202610; cells queued under tag EV, results land in runs_rf)
TL3_EV_LY_ID (JL2 + ev_switch {} + ev_layers {"stack_cut":"asia"}) must equal TL3_EV_JN05W2JL2; TL3_EV_LY_ID_W2 (JN05W2 + the same inert hooks) must equal 598 trades / 25,943.82. A functional smoke cell TL3_EV_LY_OFF_K7 (K7 alone, all layers off) runs too. Do not use any switch result until the identity cells are IDENTICAL.
