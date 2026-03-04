Clean Architecture for Edge AI
This document distills the architecture into five layers:

  1.Model Representation (ONNX)
  2.Inference Runtime (ORT Minimal, NEON-enabled)
  3.Binary Packaging (static or micro-container)
  4.API Layer (thin CLI or JSON endpoint)
  5.Deployment & Monitoring

Each layer is independent and simple.
The Pi is used only for inference, never training.
