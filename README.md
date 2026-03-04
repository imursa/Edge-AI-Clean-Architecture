# Edge AI Clean Architecture (Sensor-Focused Blueprint)

This repository captures the core principles, patterns, and workflow to deploy machine learning models on edge devices (e.g., Raspberry Pi) **without dependency hell**.

> **Purpose:** a durable, conceptual reference.  
> **Scope:** no runtime code, just architecture, diagrams, and decision guides.  
> **Outcome:** confidence in constraints, trade-offs, and a clean deployment path.

---

## Why this exists

AI frameworks (PyTorch, TensorFlow) are large, fast‑moving, and tightly coupled to native libraries. Edge devices (ARM, older glibc, tiny RAM) make this worse. The cure is a **clean, inference‑only architecture**:

- Train off-device → export to a stable **IR** (e.g., ONNX).
- Use a small **inference runtime** (e.g., ONNX Runtime Minimal).
- Ship a **static binary** + **model file** only.
- Avoid Python, wheels, and dynamic linking on the device.

---

## What you’ll find

- **/architecture** — diagrams, overview, glossary.
- **/design** — clean architecture, lifecycle, runtime selection, deployment patterns.
- **/examples/sensor-case-study** — a worked example (vibration anomaly detection).

---

## High-level pipeline
