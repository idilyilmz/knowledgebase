# Memory and Storage

## RAM
- Unified LPDDR5 memory shared by CPU and GPU
- No dedicated VRAM
- GPU memory allocations reduce system RAM

## Implications
- Large models can starve the OS
- Memory leaks crash the whole system
- Batch sizes matter more than on desktops

## Storage
- Boot from microSD / NVMe (depending on config)
- NVMe strongly preferred for:
  - Dataset loading
  - Model caching
  - Logging

## Best Practices
- Monitor with `tegrastats`
- Use smaller batch sizes
- Prefer TensorRT INT8/FP16
