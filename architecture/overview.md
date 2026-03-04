# Architecture Overview

This document summarises the clean, first‑principles architecture for **edge AI inference**.

---

## Principles

1. **Model-first**: Use a portable IR (e.g., ONNX).  
2. **Tiny runtime**: Inference-only engine, compiled for ARM + NEON.  
3. **Static linking**: Avoid dynamic `.so` dependencies on device.  
4. **Python-free device**: No wheels, no pip, no virtualenv.  
5. **Immutable artifact**: One binary + one model file.  
6. **Reproducible builds**: Rebuild off-device; deploy identical outputs.

---

## End-to-end pipeline




