# Sensor Case Study: Vibration Anomaly Detection

A concrete example to make the architecture tangible.

---

## Problem summary

Detect abnormal vibration patterns from an accelerometer on a Raspberry Pi.  
Binary output: **normal / abnormal** (or a continuous anomaly score).

---

## Data window

- Sample rate: e.g., 200–1,000 Hz.
- Window size: e.g., 0.5–2.0 seconds.
- Channels: X/Y/Z.

**Input tensor example:** `[batch, time, channels] = [1, 512, 3]`.

---

## Model options

- **Autoencoder** (reconstructs normal; high error → anomaly).
- **1D CNN classifier** (normal vs abnormal).
- **Tiny transformer** (for periodicity/structure, if needed).

---

## Preprocessing

- DC offset removal / standardisation.
- Optional FFT / spectrogram features.
- Fixed input shape (pad/trim).

Document precisely in `config.json` (scales, window length).

---

## IR and runtime

- Export to **ONNX**.
- Run with **ONNX Runtime Minimal** (ARM + NEON, static).

---

## On-device layout

/app
├─ inference_engine
├─ model.onnx
└─ config.json

---

## Decision logic

- Threshold on anomaly score (e.g., > 0.7 → alarm).
- Hysteresis to avoid chatter.
- Log events and last N windows for diagnostics.

---

## Validation checklist

- Compare ONNX output vs training framework on test windows.
- Confirm latency (e.g., < 10 ms per window).
- Confirm memory footprint stable under long runs.
- Smoke test with known normal/abnormal patterns.

---

## Versioning

- `model_vX.Y.onnx`
- `config_vA.B.json`
- `runtime vR.S` (rare updates; treat as firmware)

- 




