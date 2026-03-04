# Glossary (Edge AI, Clean Architecture)

**Dependency hell** — fragile, tangled dependency graph where any version mismatch breaks the system.

**Wheel (.whl)** — a Python distribution package. Often contains native `.so` extensions that depend on exact OS/ABI/CPU versions.

**.so (Shared Object)** — a dynamically loaded binary library on Linux. Requires compatible glibc/libstdc++ and CPU instructions.

**Compile** — translate source code (C/C++/etc.) to machine code for a target CPU/OS.

**Link** — assemble object files and libraries into an executable or shared library; resolve symbols and ABIs.

**Static linking** — library code copied into the final binary. Larger file, but self-contained and robust.

**Dynamic linking** — libraries loaded at runtime from the OS. Smaller binaries, but fragile across devices.

**IR (Intermediate Representation)** — framework-agnostic model format (e.g., ONNX, TFLite, GGUF) for portable inference.

**Inference runtime** — a small engine that loads IR and executes operators (e.g., ONNX Runtime, TFLite, ExecuTorch, GGML).

**NEON** — ARM SIMD instruction set for vectorised math; critical for CPU inference speed on Raspberry Pi.

**ABI (Application Binary Interface)** — rules for binary compatibility (calling conventions, data layout, symbols). Mismatches cause runtime errors.

**ORT Minimal** — ONNX Runtime built with only required ops; small footprint, ideal for edge.

**Appliance pattern** — treat the device as a fixed-function inference box: model + runtime only.
