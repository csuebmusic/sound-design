# sound-design

A growing library of interactive teaching tools, code examples, and supporting materials for courses in **music synthesis, sound design, and digital signal processing** at California State University East Bay.

Maintained by [Inés Thiebaut](https://github.com/csuebmusic), Associate Professor of Music.

---

## About this repository

These materials are developed alongside the textbooks and topics covered in the course — each tool is designed to make an abstract DSP or synthesis concept audible, visible, and interactive. The goal is to let students hear the math, see the signal flow, and manipulate parameters in real time so the theory becomes intuitive.

The library is **under active development** and will expand as the course progresses. Expect new modules on synthesis techniques, sound design topics, physical modeling, and further DSP concepts to appear over time.

Every tool is a self-contained HTML file. Open in any modern browser (Chrome, Firefox, Safari) and the audio and visualizations run locally via the Web Audio API and Canvas.

---

## How to use these tools

**For students:**
- Click any tool below to launch it directly in the browser.
- Adjust the controls, listen to the audio output, and watch how the visualizations respond.
- Each tool is meant to accompany a specific topic from the reading — use it while working through the chapter, not as a replacement for it.

**For instructors / remixers:**
- All tools are plain HTML + JavaScript with no external dependencies. Fork, clone, or adapt freely.
- Source is readable and commented for anyone wanting to see how the DSP is implemented in the browser.

---

## Current contents

### Filters (FIR and IIR)

A set of six interactive tools covering the fundamentals of digital filtering, designed to accompany Cook, *Real Sound Synthesis for Interactive Applications* (Ch. 3) and related material in Puckette and Roads.

| Tool | Focus |
| --- | --- |
| [`fir_impulse_visualizer.html`](./fir_impulse_visualizer.html) | Animated block diagram of an FIR filter processing an impulse — shows the delay chain, tap-by-tap summation, and the resulting impulse response. |
| [`fir_interactive_explorer.html`](./fir_interactive_explorer.html) | Live FIR filter with adjustable taps, frequency response chart, and spectrum analyzer. Hear and see the effect of moving-average and weighted-tap designs. |
| [`iir_filter_explorer.html`](./iir_filter_explorer.html) | One-, two-, and four-pole IIR filters with a polar z-plane plot, live audio, and parameter controls. Built on `IIRFilterNode` for accurate coefficient implementation. |
| [`biquad_explorer.html`](./biquad_explorer.html) | The BiQuad as the general second-order filter — feedforward and feedback structure, poles and zeros, and classic filter types (LPF, HPF, BPF, notch). |
| [`biquad_explorerv2.html`](./biquad_explorerv2.html) | Extended BiQuad explorer with additional visualization and parameter mapping. |
| [`fir_vs_iir_comparison.html`](./fir_vs_iir_comparison.html) | Side-by-side comparison of FIR and IIR responses to the same input — stability, phase behavior, and computational cost. |

**Concepts covered across the suite:**
- FIR: moving averages, convolution, LTI systems, impulse response, sinc frequency response, linear phase
- IIR: one-pole / two-pole / cascaded structures, complex conjugate pole pairs, stability condition (|r| < 1)
- BiQuad: general second-order form combining feedforward and feedback
- z-plane: poles, zeros, geometric interpretation of frequency response

---

## Roadmap

Planned additions as the course progresses. Topics listed here are intentions rather than promises — the exact shape of each section will depend on what's most useful pedagogically.

- **Synthesis techniques** — subtractive, additive, FM, AM/ring modulation, wavetable, granular
- **Sound design** — envelopes, modulation, signal flow patterns, effects chains
- **Physical modeling** — Karplus-Strong, waveguides, modal synthesis
- **Further DSP** — delay lines, reverb structures, time-frequency analysis, spectral processing
- **ChucK code library** — commented `.ck` patches paralleling the interactive tools, for students working in the ChucK environment

---

## Source texts

The tools and examples in this library are developed in dialogue with the following core texts:

- Cook, *Real Sound Synthesis for Interactive Applications* (CRC Press, 2015)
- Puckette, *The Theory and Technique of Electronic Music* (2006)
- Roads, *The Computer Music Tutorial* (MIT Press, 2023)
- Kapur et al., *Programming for Musicians and Digital Artists: Creating Music with ChucK* (Manning, 2015)
- Wang & Cook, *ChucK Manual*
- Pluta, *Sound Synthesis for Music Reproduction and Performance*
- Pejrolo, *Creative Sequencing Techniques for Music Production*

---

## License and reuse

These materials are provided for educational use. Students and colleagues are welcome to fork, adapt, and share. If you use or modify these tools for your own teaching, attribution is appreciated.

---

## Contact

For questions, corrections, or suggestions, please open an issue on this repository or reach out directly.
