# Jetson Orin Nano Architecture

## Overview
- Embedded AI SoC designed for edge inference
- ARM-based CPU + NVIDIA GPU + dedicated AI accelerators
- Optimized for low power, always-on workloads

## SoC Components
- CPU: ARM Cortex-A78AE cluster
- GPU: NVIDIA Ampere architecture
- AI: Tensor Cores, NVDLA (if applicable)
- Memory controller shared across CPU/GPU

## Design Philosophy
- Unified memory (no discrete VRAM)
- Power efficiency over peak performance
- Tight coupling between hardware + NVIDIA software stack
