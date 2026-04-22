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

The repository is **under active development** and will grow as the course progresses. Current contents are in the *Mixing and Signal Processing* area, specifically the module on digital filters.

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

### Digital filters

Interactive tools covering the foundations of recursive (IIR) and non-recursive (FIR) digital filtering, designed to accompany Cook, *Real Sound Synthesis for Interactive Applications* (Ch. 3), Puckette (Ch. 8), and Roads (Ch. 28).

#### IIR

##### [`one_pole_iir.html`](./one_pole_iir.html)

The simplest recursive digital filter: `y[n] = g·x[n] + r·y[n−1]`. A single pole sliding along the real axis of the z-plane, which you can move from lowpass (r > 0) through neutral (r ≈ 0) into highpass (r < 0), and all the way into instability (|r| > 1) to see what "outside the unit circle" actually means. Students can hear the filter on white noise, read a live magnitude response with `g/(1−|r|)` peaks of up to +80 dB at extreme settings, and watch the single pole slide in real time while the impulse response, frequency response, group delay curve, and live equation all update together.

##### [`two_pole_iir.html`](./two_pole_iir.html)

The building block of resonant filtering: `y[n] = g·x[n] + b₁·y[n−1] + b₂·y[n−2]`, with coefficients derived from the user-friendly parameters of *resonant frequency* and *radius* via `b₁ = 2r·cos(ω₀)` and `b₂ = −r²`. The tool shows a complex conjugate pole pair on the z-plane — the geometric object responsible for resonance — and pairs it with an impulse response that rings exponentially, a frequency response curve with an adaptive dense-sampling region that captures peaks up to Q > 1000, a group delay chart that makes the frequency-dependent timing of resonance visible, and a live equation that rewrites itself as the sliders move. This is the foundation for formant filters, plucked-string models, and analog synth emulations.

#### FIR

##### [`fir_avg_diff.html`](./fir_avg_diff.html)

The simplest finite impulse response filters: N-tap moving average and N-tap differentiator, two sides of the same structure. The tool toggles between `h[k] = +1/N` (all coefficients positive → lowpass) and `h[k] = (−1)ᵏ/N` (alternating signs → highpass comb), showing that the same N-tap tapped delay line becomes a completely different filter under just a sign flip. Students can watch the zeros march around the unit circle as N grows, see the impulse response equal the coefficient list exactly (the defining property of FIR), hear how "linear phase" sounds on noise, and read the group delay as a single number `(N−1)/2` that applies uniformly to every frequency — the critical contrast with the IIR tools, whose group delay curves bulge at resonance. The frequency response follows the Dirichlet kernel `(1/N)·|sin(Nω/2)/sin(ω/2)|`, whose first null at `SR/N` is the width of the main lobe.

---

## Source texts

The tools are developed in dialogue with the following core texts:

- Cook, *Real Sound Synthesis for Interactive Applications* (CRC Press, 2015)
- Puckette, *The Theory and Technique of Electronic Music* (2006)
- Roads, *The Computer Music Tutorial* (2nd ed., MIT Press, 2023)
- Kapur et al., *Programming for Musicians and Digital Artists: Creating Music with ChucK* (Manning, 2015)
- Wang & Cook, *ChucK Manual*

---
