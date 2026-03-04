# Inference Runtime Selection

Pick the simplest runtime that meets performance and portability needs.

---

## Quick guide

- **Sensors / time-series, small models** → **ONNX Runtime Minimal** (preferred)
- **Ultra-tiny models** → TFLite (micro or interpreter)
- **LLMs on CPU** → GGML / llama.cpp (GGUF models)
- **PyTorch export & mobile-first** → ExecuTorch
- **Compiler-based optimisation** → MLC / TVM

---

## Selection criteria

1. **Supported IR**
   - ONNX: broad operator coverage, good for most tasks.
   - TFLite: compact ops, small footprint.
   - GGUF: LLMs only.

2. **Build footprint**
   - Minimal ORT builds are ~15–25 MB (depending on ops).
   - TFLite can be even smaller for micro models.

3. **CPU optimisations**
   - Ensure NEON and ARM target match.

4. **Link strategy**
   - Prefer static linking for robustness.

5. **Tooling and community**
   - ONNX/ORT has strong tooling for debugging and validation.

---

## Decision

For the **sensor case study**, choose **ONNX Runtime Minimal** statically linked for ARM with NEON enabled.
