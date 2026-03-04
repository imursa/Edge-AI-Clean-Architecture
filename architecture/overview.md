Architecture Overview
This document summarizes the full clean architecture for edge AI inference.
High-Level Pipeline

Train (PyTorch/TF)
   ↓
Export to ONNX
   ↓
Optimize ONNX
   ↓
Compile ONNX Runtime Minimal (static, ARM)
   ↓
Package model + runtime
──────────────────────────────────────────
Deploy to Raspberry Pi
──────────────────────────────────────────
Sensor → Preprocess → Inference → Logic

Philosophy

Everything complex happens on the workstation
The Raspberry Pi is treated as an appliance
Use static binaries to avoid dependency hell
Python is excluded from deployment
Model + runtime = entire system

Artifacts on the Pi
/app
   inference_engine  (static C++ binary)
   model.onnx
   config.json




