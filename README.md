# Bloch Simulator — the ω₁T₂ > 1 condition

An interactive web simulator showing the qualitative transition from **CW** to **pulsed** magnetic resonance, governed by the inequality

$$\omega_1 T_2 > 1$$

where ω₁ is the RF/microwave Rabi frequency and T₂ is the transverse relaxation time. The same condition demarcates **CW DNP** from **pulsed DNP** on the electron spin (ω₁ₑ T₂ₑ > 1).

## What it shows

- **CW regime** (ω₁T₂ ≪ 1): transverse magnetization never builds up; M_z relaxes monotonically toward a saturated steady state. Relaxation dominates.
- **Pulsed regime** (ω₁T₂ ≫ 1): magnetization undergoes many Rabi cycles before T₂ damps them out. This is where pulsed sequences (NOVEL, ISE, …) operate.

Three preset buttons jump between the regimes; the live ω₁T₂ readout color-codes the current regime.

## Slider scales (DNP-relevant)

| Parameter | Range | Default |
|---|---|---|
| Rabi ω₁/2π | 10 kHz – 1 GHz (log) | 1 MHz |
| T₁ | 100 µs – 1 s (log) | 1 ms |
| T₂ | 10 ns – 10 µs (log) | 1 µs |
| Off-resonance Δν | ±10 MHz | 0 |

The plot window covers max(5·T₂, 8 nutation periods, 5× the CW saturation time), so both coherent decay and M_z saturation are visible. When that would contain more than 500 nutation cycles (ω₁T₂ ≳ 10³), the window is capped at 500 cycles and labelled, rather than aliasing the oscillation. The time axis auto-picks its display unit (s / ms / µs / ns).

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
- Exact solution of the Bloch equations: M(t+h) = M∞ + e^{Ah}(M(t) − M∞), with a 3×3 matrix exponential (scaling-and-squaring), sampled at 8000 points

## Reference

Based on the framing in *Quo Vadis Pulsed DNP* (K. O. Tan et al., Springer book chapter, 2026). The ω₁T₂ > 1 criterion is introduced in the Introduction as the conceptual analogue of the Ernst–Anderson transition from CW NMR to pulsed FT NMR.
