# Runtime Build Concepts (ONNX Runtime Minimal, ARM)

Conceptual guide to produce a small, robust runtime for Raspberry Pi.

---

## Targeting ARM correctly

- **ARM variant**: Pi 3 (ARMv7), Pi 4/5 (ARMv8/aarch64).
- **NEON**: enable for vectorised math.
- **No AVX**: x86-only; ensure builds don’t assume it.

---

## Keep it minimal

- Build **only** the operators your model needs.
- Disable training, CUDA, and unused execution providers.
- Prefer a **static binary** to avoid dynamic `.so` dependencies.

---

## Build configuration themes (conceptual)

- Toolchain matches target (cross-compile or native).
- Optimisation flags for size/speed as appropriate.
- Link statically where licences allow (avoid glibc pinning issues).
- Include basic threading (pthreads / OpenMP if needed).

---

## Validation before shipping

- Run unit inference on workstation with the same build config.
- Confirm supported ops list matches your model.
- Measure latency on comparable hardware.
- Smoke test with representative windows.

---

## Packaging pattern

Place in `/app`:
