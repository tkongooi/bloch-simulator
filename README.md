# Bloch Simulator — the ω₁T₂ > 1 condition

An interactive web simulator showing the qualitative transition from **CW** to **pulsed** magnetic resonance, governed by the inequality

$$\omega_1 T_2 > 1$$

where ω₁ is the RF/microwave Rabi frequency and T₂ is the transverse relaxation time. The same condition demarcates **CW DNP** from **pulsed DNP** on the electron spin (ω₁ₑ T₂ₑ > 1).

## What it shows

- **CW regime** (ω₁T₂ ≪ 1): transverse magnetization never builds up; M_z relaxes monotonically toward a saturated steady state. Relaxation dominates.
- **Pulsed regime** (ω₁T₂ ≫ 1): magnetization undergoes many Rabi cycles before T₂ damps them out. This is where pulsed sequences (NOVEL, ISE, …) operate.

Three preset buttons jump between the regimes; the live ω₁T₂ readout color-codes the current regime.

## Run locally

It's a single static HTML file — open `index.html` in a browser, or:

```bash
npx serve .
```

## Deploy

Static deployment on Vercel — no build step, no framework. Just `vercel --prod`.

## Stack

- Plotly.js for plotting
- Tailwind (CDN) for layout
- MathJax 2.7 for inline LaTeX (required by Plotly's tick labels)
- RK4 integration of the Bloch equations with adaptive `dt`

## Reference

Based on the framing in *Quo Vadis Pulsed DNP* (K. O. Tan et al., Springer book chapter, 2026). The ω₁T₂ > 1 criterion is introduced in the Introduction as the conceptual analogue of the Ernst–Anderson transition from CW NMR to pulsed FT NMR.
