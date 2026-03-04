Clean Architecture for Edge AI
This document distills the architecture into five layers:

Model Representation (ONNX)
Inference Runtime (ORT Minimal, NEON-enabled)
Binary Packaging (static or micro-container)
API Layer (thin CLI or JSON endpoint)
Deployment & Monitoring

Each layer is independent and simple.
The Pi is used only for inference, never training.
