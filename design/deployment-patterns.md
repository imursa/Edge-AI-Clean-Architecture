# Deployment Patterns (Edge and Fleet)

Patterns that keep systems robust and scalable.

---

## Single-device (appliance pattern)

- `/app` contains:
  - `inference_engine` (static)
  - `model.onnx`
  - `config.json`
- Local preprocessing + inference + decision.
- Optional local logs and periodic summaries.

---

## Fleet with optional gateway
