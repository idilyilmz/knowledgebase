# Power Modes

## Available Modes
- 5W: low power, throttled performance
- 10W: balanced
- 15W: max performance

## Commands
- `nvpmodel -m <mode>`
- `jetson_clocks`

## Thermal Behavior
- Sustained GPU load can throttle without cooling
- Active cooling recommended for 15W mode

## Design Considerations
- Power mode affects:
  - Inference latency
  - FPS stability
  - Thermal headroom
