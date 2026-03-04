# ONNX Export Notes (Conceptual)

Guidance to keep exports predictable and portable.

---

## Inputs and shapes

- Fix input shape (no dynamic dims for edge).
- Include batch=1 unless you truly need batching.
- Record dtype (float32 / int8) and normalisation.

---

## Opset and operators

- Use a stable opset supported by your target ORT build.
- Avoid exotic/custom ops; stick to standard layers (Conv, GEMM, ReLU, GRU, etc.).

---

## Validation flow

1. Save a small set of representative input windows.
2. Run inference in the training framework.
3. Run ONNX inference with the **same pre/post-processing**.
4. Compare outputs (tolerance thresholds).

---

## Optional optimisation

- **ONNX Simplifier** to fold constants and remove no-ops.
- Quantisation (INT8/FP16) only if you validate accuracy and latency gains.

---

## Reproducibility

- Record:
  - framework version
  - opset version
  - export script parameters
  - pre/post-processing details
  - test vectors (input/output pairs)
