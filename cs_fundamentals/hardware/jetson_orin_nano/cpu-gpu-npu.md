# CPU vs GPU vs NPU on Jetson Orin Nano

## CPU (ARM Cortex-A78AE)
- Best for:
  - Control logic
  - ROS nodes
  - Pre/post-processing
- Not ideal for heavy parallel math

## GPU (Ampere)
- Best for:
  - Deep learning inference
  - CUDA-accelerated OpenCV
  - Parallel workloads
- Uses shared system memory

## NPU / AI Accelerators
- Best for:
  - Optimized inference via TensorRT
  - Low-latency pipelines
- Requires model conversion and tuning

## Design Rule of Thumb
- CPU: orchestration
- GPU: compute
- NPU: optimized inference
