# sound-design

Interactive teaching tools for courses in music synthesis, sound design, and digital audio at California State University East Bay.

Maintained by [Inés Thiebaut](https://github.com/csuebmusic), Associate Professor of Music.

---

## About this repository

These tools are designed to make abstract audio-DSP concepts audible, visible, and interactive. Every tool is a single self-contained HTML file — open in any modern browser and the audio and visualizations run locally via the Web Audio API and Canvas, with no external dependencies.

The collection is organized around three large areas of the course:

1. **Digital Audio**
2. **Sound Synthesis**
3. **Mixing and Signal Processing**

The repository is **under active development** and will grow as the course progresses. Current contents span foundational concepts (phasors, sinusoidal motion) and the module on digital filters within the *Mixing and Signal Processing* area.

---

## How to use these tools

**For students:**
- Click any tool below to launch it in the browser.
- Drag the sliders, toggle playback, and watch how every visualization updates in real time.
- Each tool is meant to accompany a specific topic from the reading — use it while working through the chapter, not as a replacement for it.

**For instructors / remixers:**
- All files are MIT-licensed and self-contained; fork, adapt, or rehost freely.
- The visual language (warm light palette, DM Mono + DM Sans typography, consistent metric cards and calc blocks) is shared across every tool so students can move between them without re-orienting.

---

## Current contents

### Sinusoidal motion

#### [`phasor.html`](./phasor.html)

A rotating point on a circle tracing sine and cosine waves through its vertical and horizontal projections. Four independent animated panels, each with its own play/pause/reset, sharing a common set of sliders (frequency, amplitude, phase): the sine projection unrolling to the right; the cosine projection showing why it starts at its peak; the complex exponential `A·e^(jθ) = A·(cos(θ) + j·sin(θ))` with both projections simultaneously on one circle; and a time-domain view showing `sin(θ)` (teal), `cos(θ)` (crimson), and their sum (terra-cotta) — a sinusoid at the same frequency with amplitude A√2 and a 45° phase shift. Each panel includes a note connecting the geometry to signal processing: why sine and cosine always travel in pairs, what the imaginary unit means spatially, and how the sum of same-frequency sinusoids is always another sinusoid. This tool establishes the geometric foundation for the z-plane, complex poles, and Fourier analysis that the filter tools build on.

### Digital filters

Interactive tools covering the foundations of recursive (IIR) and non-recursive (FIR) digital filtering, designed to accompany Puckette (Ch. 8) and Roads (Ch. 28), among other standard texts.

#### IIR

##### [`one_pole_iir.html`](./one_pole_iir.html)

The simplest recursive digital filter: `y[n] = g·x[n] + r·y[n−1]`. A single pole sliding along the real axis of the z-plane, which you can move from lowpass (r > 0) through neutral (r ≈ 0) into highpass (r < 0), all the way to r = ±1 where the pole lands on the unit circle and the gain at DC (or Nyquist) becomes infinite. Students can hear the filter on white noise, read a live magnitude response with `g/(1−|r|)` peaks of up to +80 dB, and watch the single pole slide in real time while the impulse response, frequency response, group delay curve, and live equation all update together.

##### [`two_pole_iir.html`](./two_pole_iir.html)

The building block of resonant filtering: `y[n] = g·x[n] + b₁·y[n−1] − b₂·y[n−2]`, with coefficients `b₁ = 2r·cos(ω₀)` and `b₂ = r²`. The tool shows a complex conjugate pole pair on the z-plane — the geometric object responsible for resonance — and pairs it with an impulse response that rings exponentially, a frequency response curve with an adaptive dense-sampling region that captures peaks up to Q > 1000, a group delay chart that makes the frequency-dependent timing of resonance visible, and a live equation that rewrites itself as the sliders move. At r = 1 the poles land on the unit circle and the resonance peak becomes infinite, visible as the curve pinned to the +80 dB ceiling. This is the foundation for formant filters, plucked-string models, and analog synth emulations.

#### FIR

##### [`fir_avg_diff.html`](./fir_avg_diff.html)

The simplest finite impulse response filters: N-tap moving average and N-tap differentiator, two sides of the same structure. The tool toggles between `h[k] = +1/N` (all coefficients positive → lowpass) and `h[k] = (−1)ᵏ/N` (alternating signs → highpass comb), showing that the same N-tap tapped delay line becomes a completely different filter under just a sign flip. Students can watch the zeros march around the unit circle as N grows, see the impulse response equal the coefficient list exactly (the defining property of FIR), hear how "linear phase" sounds on noise, and read the group delay as a single number `(N−1)/2` that applies uniformly to every frequency — the critical contrast with the IIR tools, whose group delay curves bulge at resonance. The frequency response follows the Dirichlet kernel `(1/N)·|sin(Nω/2)/sin(ω/2)|`, whose first null at `SR/N` is the width of the main lobe.

##### [`fir_2_zero.html`](./fir_2_zero.html)

A 3-tap FIR with a complex conjugate zero pair: `y[n] = g·(x[n] + a₁·x[n−1] + a₂·x[n−2])`, where `a₁ = −2r·cos(ω₀)` and `a₂ = r²` (g factors outside the sum, matching the BiQuad numerator exactly). The tool is the FIR counterpart to `two_pole_iir.html` — same geometric vocabulary (angle, radius, unit circle), same z-plane display, but with zeros instead of poles. The key pedagogical distinction is that this filter behaves as a true notch only when `r = 1` (zeros on the unit circle); at `r < 1` the zeros pull inside and the filter combines a partial dip at the zero frequency with a broader spectral tilt whose shape depends on where `r` and `f_zero` sit. Students can sweep radius from 0 to 1 and watch this transition on the frequency response (−200 dB floor, dense sampling around the zero angle), observe the group delay go to −∞ at the notch as `r → 1` (the FIR sign-mirror of the IIR's positive resonance spike), and read a live coefficient substitution showing how `ω₀`, `a₁`, and `a₂` are computed from the human-friendly sliders. Impulse response, z-plane, and white-noise playback via Web Audio complete the picture.

#### IIR + FIR

##### [`biquad.html`](./biquad.html)

The second-order pole/zero filter: `y(n) = g·(x(n) + a₁·x(n−1) + a₂·x(n−2)) + b₁·y(n−1) − b₂·y(n−2)`. Two poles and two zeros, independently tunable, in a single structure — the direct combination of the two-pole IIR and the 2-zero FIR that precede it in the suite. Coefficients: `a₁ = −2rz·cos(ω_z)`, `a₂ = rz²` (zero pair), `b₁ = 2rp·cos(ω_p)`, `b₂ = rp²` (pole pair). The block diagram shows the direct-form II topology: a single shared delay chain with each tap firing left (feedback via b₁, b₂ to summer ⊕₁) and right (feedforward via a₁, a₂ to summer ⊕₂). The z-plane shows poles (crimson ×) and zeros (teal ○) simultaneously — the first tool in the suite where both appear at once — and the frequency response, group delay, and impulse response all update together as the five sliders move. The key special case: when `freq_z = freq_p`, the zero and pole sit at the same angle; if `rz = rp` they cancel exactly (flat response), if `rz < rp` the pole wins (peak), if `rz > rp` the zero wins (notch). This is the core of parametric EQ, visible directly on the z-plane.

---

## Source texts

The tools are developed in dialogue with the following core texts:

- Cook, *Real Sound Synthesis for Interactive Applications* (CRC Press, 2015)
- Puckette, *The Theory and Technique of Electronic Music* (2006)
- Roads, *The Computer Music Tutorial* (2nd ed., MIT Press, 2023)
- Kapur et al., *Programming for Musicians and Digital Artists: Creating Music with ChucK* (Manning, 2015)
- Wang & Cook, *ChucK Manual*

---
