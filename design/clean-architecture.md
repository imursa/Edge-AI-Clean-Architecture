# Clean Architecture (Edge Inference)

A minimal, stable architecture for running ML models on edge devices.

---

## Layers

1. **Model Representation (IR)**
   - Use ONNX for general models; TFLite for very small ones; GGUF for LLMs.
   - Keep models framework-agnostic on-device.

2. **Inference Runtime**
   - ONNX Runtime Minimal preferred for sensors (NEON-enabled).
   - Alternatives: TFLite, ExecuTorch, GGML/llama.cpp, MLC.

3. **Binary Packaging**
   - Prefer a **statically linked** executable.
   - Alternative: minimal OCI/Docker container pinned to exact base image.

4. **API Layer**
   - CLI or thin HTTP endpoint.
   - Keep it simple: JSON in/out or file pipe.

5. **Deployment & Monitoring**
   - Drop files under `/app`.
   - Log inference time and basic metrics.
   - Optional: MQTT/HTTP for event output.

---

## Constraints → Design Choices

- **ARM variance** (Pi Zero/3/4/5): build specifically for the target CPU.
- **OS lag** (glibc/libstdc++): static link to avoid runtime mismatches.
- **RAM limits**: small models, NEON kernels, no Python.
- **Reproducibility**: freeze builds off-device; never “pip install” on-device.

---

## Anti-patterns (avoid)

- Installing PyTorch/TensorFlow on the Pi via pip.
- Relying on system `.so` versions (dynamic linking).
- Training on-device.
- Mixing multiple runtimes on the same device.

---

## Upgrades

- **Model**: safe to update frequently (versioned).
- **Runtime**: update rarely; treat as firmware.
- **Config**: per-device thresholds and rates.
