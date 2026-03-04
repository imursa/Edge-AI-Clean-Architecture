# Model Lifecycle (Edge Deployment)

A practical flow to control change and preserve stability.

---

## Stages

1. **Development**
   - Experiment in PyTorch/TF on a workstation.
   - Track input scaling, windowing, and feature extraction.

2. **Export**
   - Export to ONNX with explicit input shapes and dtypes.
   - Include a representative test vector.

3. **Validation**
   - Run ONNX inference on workstation with the **same runtime** build settings.
   - Compare outputs to framework outputs (tolerance checks).

4. **Optimisation (optional)**
   - Apply ONNX graph simplification.
   - Consider quantisation if needed (INT8/FP16) and validate accuracy.

5. **Packaging**
   - Compile a minimal runtime (static, NEON).
   - Pair with `model.onnx` and `config.json`.

6. **Deployment**
   - Ship to device under `/app`.
   - Smoke test with known input window(s).

7. **Monitoring**
   - Log inference latency, anomaly scores, and thresholds hit.
   - Keep a rolling buffer for diagnostics.

8. **Versioning**
   - `model_vX.Y.onnx`, `config_vA.B.json`.
   - Runtime gets semantic versioning and a changelog.

---

## Rollback Plan

- Keep previous model and config on-device.
- If new model fails validation or drifts, switch symlink/file name back.
- Runtime updates are rare; treat them like firmware with staged rollout.

---

## Reproducibility

- Save export script, opset version, and pre/post-processing notes in repo.
- Use the same ONNX Runtime build config for validation and device builds.
