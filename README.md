# digital-filters

Interactive teaching tools for **digital filter design and analysis**, developed for courses in music synthesis, sound design, and DSP at California State University East Bay.

Maintained by [Inés Thiebaut](https://github.com/csuebmusic), Associate Professor of Music.

---

## About this repository

These tools are designed to make abstract filter concepts audible, visible, and interactive. Every tool is a single self-contained HTML file — open in any modern browser and the audio and visualizations run locally via the Web Audio API and Canvas, with no external dependencies.

The focus is on the **mathematical and sonic behavior of recursive (IIR) and non-recursive (FIR) digital filters**: how coefficients map to poles and zeros, how pole placement shapes the frequency response, and how the same filter sounds when you can hear it in real time.

The library is **under active development** and will grow as the course progresses. Current contents are focused on IIR filter fundamentals; FIR tools and more advanced filter structures are on the roadmap.

---

## How to use these tools

**For students:**
- Click any tool below to launch it in the browser.
- Drag the sliders, toggle playback, and watch how every visualization updates in real time.
- Each tool is meant to accompany a specific topic from the reading — use it while working through the chapter, not as a replacement for it.

**For instructors / remixers:**
- All tools are plain HTML + JavaScript with no external dependencies. Fork, clone, or adapt freely.
- Source is readable and commented for anyone wanting to see how the DSP is implemented in the browser.

---

## Current contents

### IIR filters

Two interactive tools covering the foundations of recursive filtering, designed to accompany Cook, *Real Sound Synthesis for Interactive Applications* (Ch. 3), Puckette (Ch. 8), and Roads (Ch. 28).

#### [`one_pole_iir.html`](./one_pole_iir.html)

The simplest recursive digital filter: `y[n] = g·x[n] + r·y[n−1]`. A single pole sliding along the real axis of the z-plane, which you can move from lowpass (r > 0) through neutral (r ≈ 0) into highpass (r < 0), and all the way into instability (|r| > 1) to see what "outside the unit circle" actually means. Students can hear the filter on white noise, read a live magnitude response with `g/(1−|r|)` peaks of up to +80 dB at extreme settings, and watch the single pole slide in real time while the impulse response, frequency response, and live equation all update together.

#### [`two_pole_iir.html`](./two_pole_iir.html)

The building block of resonant filtering: `y[n] = g·x[n] + b₁·y[n−1] + b₂·y[n−2]`, with coefficients derived from the user-friendly parameters of *resonant frequency* and *radius* via `b₁ = 2r·cos(ω₀)` and `b₂ = −r²`. The tool shows a complex conjugate pole pair on the z-plane — the geometric object responsible for resonance — and pairs it with an impulse response that rings exponentially, a frequency response curve with an adaptive dense-sampling region that captures peaks up to Q > 1000, and a live equation that rewrites itself as the sliders move. This is the foundation for formant filters, plucked-string models, and analog synth emulations.

**Concepts covered across both tools:**
- Recursive feedback and the infinite impulse response
- Poles on the z-plane: real-axis poles (one-pole) and complex conjugate pairs (two-pole)
- Stability condition `|r| < 1` and what happens when you cross it
- Peak gain, bandwidth, Q, time constant, and impulse decay
- The relationship between pole radius and resonance sharpness
- Translating mathematical coefficients into audible filter behavior

---

## Roadmap

Planned additions as the course progresses. Topics listed here are intentions rather than promises — the exact shape of each tool will depend on what's most useful pedagogically.

- **BiQuad** — the general second-order filter combining feedforward and feedback, unifying LPF, HPF, BPF, notch, peaking, and shelving designs
- **FIR filters** — moving averages, windowed-sinc designs, linear phase, the sinc frequency response, convolution as filtering
- **FIR vs IIR comparison** — stability, phase behavior, computational cost, and when each is the right choice
- **Filter banks and cascades** — parallel two-poles for formant synthesis, cascaded one-poles for steeper rolloff, Moog-ladder structures
- **ChucK patches** — commented `.ck` files paralleling each interactive tool, for students working in the ChucK environment
- **Beyond filters** — synthesis techniques (subtractive, FM, additive, wavetable, granular), physical modeling (Karplus-Strong, waveguides, modal), and further DSP (delays, reverb, spectral processing) will eventually migrate here or into sibling repositories

---

## Source texts

The tools are developed in dialogue with the following core texts:

- Cook, *Real Sound Synthesis for Interactive Applications* (CRC Press, 2015)
- Puckette, *The Theory and Technique of Electronic Music* (2006)
- Roads, *The Computer Music Tutorial* (2nd ed., MIT Press, 2023)
- Kapur et al., *Programming for Musicians and Digital Artists: Creating Music with ChucK* (Manning, 2015)
- Wang & Cook, *ChucK Manual*

---

## License and reuse

These materials are provided for educational use. Students and colleagues are welcome to fork, adapt, and share. If you use or modify these tools for your own teaching, attribution is appreciated.

---

## Contact

For questions, corrections, or suggestions, please open an issue on this repository or reach out directly.
