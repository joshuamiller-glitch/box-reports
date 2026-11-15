## Dropped / rebuilt-causal list (W-CF4, no repainting)
- Nadaraya-Watson envelope, LuxAlgo end-point (repainting) form: DROPPED. Rebuilt as a one-sided Gaussian kernel over past bars only (nwe, nweF, nweS); APPROXIMATION.
- Kernel Regression (jdehorty) end-point/Nadaraya-Watson repaint behaviour: rebuilt with a one-sided Rational Quadratic kernel on past bars only (kr*).
- ZigZag / ZigZag++ and any swing indicator drawn at the pivot bar: DROPPED as plotted; replaced by fractal pivots usable only k bars after the pivot (confirmed-pivot version everywhere: BOS/CHoCH, OB, SD, premium/discount, OTE, divergence).
- Williams fractals: only the confirmed form (usable 2 bars late). Alligator forward-shifted lines: causal reading (value at t is the line computed `shift` bars earlier). Ichimoku: cloud at t = spans computed 26 bars earlier; chikou compared with price 26 bars earlier; future cloud colour is known at t.
- Market Cipher B: proprietary, DROPPED as the original; APPROXIMATION composite (WaveTrend + money flow + RSI) built instead (mcwt, mcmf, mc_comp).
- Lorentzian Classification (jdehorty): APPROXIMATION; labels are used only for rows whose forward return window is already complete at the signal bar.
- Volume profile / anchored VWAP: use bars completed before the signal second only.
- Not built in this pass: Elliott/harmonic patterns, Tr3ndy/proprietary Simpler tools (Block 1 owner W-CF1).
