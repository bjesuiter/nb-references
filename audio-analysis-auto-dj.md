---
title: Audio Analysis for Auto-DJ Experience
anchor: Libraries and techniques for beat detection, BPM analysis, and building automated DJ experiences
tags: [audio, dj, bpm, beat-detection, music, analysis]
description: Resources for analyzing audio to build auto-DJ systems with beat matching and tempo detection
---

## My Reference

### Overview
Building an auto-DJ requires several audio analysis capabilities:
- **BPM/tempo detection** — Identify track speed
- **Beat tracking** — Locate individual beats within a track
- **Key detection** — Musical key for harmonic mixing
- **Energy/crowd detection** — Dynamic track selection

### Key Libraries & Tools

**audioFlux (Python/C)**
- **GitHub:** https://github.com/libAudioFlux/audioFlux
- **Website:** https://audioflux.top/
- **Description:** Deep learning tool library for audio and music analysis with 60+ TF transforms
- **Key Features:**
  - **Transforms:** BFT, CWT, NSGT, CQT, VQT, STFT, DWT, WPT, SWT + reassignment/synchrosqueezing
  - **Scales:** Linear, Mel, Bark, Erb, Log, Octave, Linspace
  - **Features:** Spectral, Cepstrum, Chroma, Deconvolution
  - **MIR:** Pitch detection (YIN, STFT, etc.), Onset detection, HPSS (source separation)
  - **ML:** PitchShift, TimeStretch algorithms
- **Installation:** `pip install audioflux` or `conda install -c tanky20 -c conda-forge audioflux`
- **Cross-platform:** Linux, macOS, Windows, iOS, Android
- **Use cases:** Classification, separation, MIR, ASR, DJ analysis

**Essentia (C++/Python)**
- **Website:** https://essentia.upf.edu/
- **Algorithms:**
  - `RhythmExtractor2013` — BPM + beat positions + confidence
  - `PercivalBpmEstimator` — High-accuracy BPM detection
  - `LoopBpmEstimator` — Optimized for short audio loops
  - `TempoCNN` — Deep learning tempo estimation
  - `BpmHistogramDescriptors` — BPM distribution analysis
- **Features:** Open-source, comprehensive MIR (Music Information Retrieval)

**realtime-bpm-analyzer (TypeScript/WebAudio)**
- **NPM:** https://www.npmjs.com/package/realtime-bpm-analyzer
- **Website:** https://www.realtime-bpm-analyzer.com
- **Features:**
  - Zero dependencies (native Web Audio API)
  - Real-time analysis from files, streams, or microphone
  - Full TypeScript support
  - 100% client-side (privacy-focused)
- **Use cases:** DJ apps, audio players, live streams

**SoundTouch (C++)**
- BPM detection (~80% accurate)
- Pitch/tempo manipulation
- Good for real-time processing

**Vamp SDK**
- Plugin architecture for audio analysis
- Fixed BPM Detector with high accuracy
- Used by Mixxx (open-source DJ software)

### Auto-DJ Pipeline

```
Audio Input → BPM Detection → Beat Grid → Key Detection → Crossfade/Mix → Output
              ↓                    ↓              ↓
          120 BPM            Beat markers    C minor
              ↓                    ↓              ↓
         Match with        Sync tracks      Harmonic mix
         compatible                      ( Camelot Wheel)
         tracks
```

### DJ Software Reference
- **Mixxx** — Open-source DJ software, excellent BPM analysis
- **VirtualDJ** — Analyze tracks feature for beat grids
- **Serato** — Beat grid/BPM detection

### Key Concepts

| Term | Description |
|------|-------------|
| **BPM** | Beats per minute (tempo) |
| **Beat Grid** | Temporal markers for each beat |
| **Camelot Wheel** | System for harmonic mixing (1A-12A, 1B-12B) |
| **Crossfade** | Smooth transition between tracks |
| **Phase alignment** | Syncing beat positions, not just tempo |
| **Energy curve** | Track intensity over time |

### Resources
- **Essentia Tutorial:** https://essentia.upf.edu/tutorial_rhythm_beatdetection.html
- **Realtime BPM Analyzer:** https://www.realtime-bpm-analyzer.com/
- **Research Paper:** "From raw audio to a seamless mix: creating an automated DJ system for Drum and Bass" (Springer)
