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


