# DIY Condenser Microphone Preamplifier

Open-source preamp for 25mm condenser capsules — JFET + balanced output powered by +48V phantom power.

<p align="center">
  <img src="img/mic-and-pcb-on-top.jpeg" width="600"/>
</p>

## Mounting

The PCB is designed to mount **directly on the capsule body** for compact assembly. This eliminates the need for external cables and reduces noise.

<p align="center">
  <img src="img/mic-and-pcb.jpeg" width="45%"/>
  &nbsp;&nbsp;
  <img src="img/mic-assembled.jpeg" width="45%"/>
</p>

### Cardioid Pattern

For a cardioid polar pattern, the backplate needs proper acoustic resistance. This is achieved by:
- **Vent holes** on the backplate (typically 2–4mm diameter)
- **Resistance felt** or porous material behind the capsule
- The number/diameter of holes determines the cardioid ratio

## Circuit

```
Mic Capsule → JFET (2SK660) → Complementary PNP Output (2SA1162×2) → Balanced XLR
```

### Key Components

| Designator | Part | Value |
|------------|------|-------|
| J1 | JFET | 2SK660 (or 2SK170, 2N3819) |
| Q1, Q3 | PNP transistor | 2SA1162-GR |
| D1 | Zener diode | ZMM9V1 |
| R4 | Gate bias | 5kΩ |
| R7, R9 | DC bias | 5kΩ, 5.6kΩ |
| R11, R12 | Output resistors | 33Ω |
| C8, C9 | HF filter | 1.5nF |
| C10 | Coupling | 2.2µF |

### Operation

1. **Phantom power** (+48V) comes in on XLR pins 2/3
2. **Zener D1** drops voltage for the JFET bias circuit
3. **JFET J1** amplifies capsule signal with low noise
4. **Q1/Q3** form complementary output stage
5. **Balanced output** — signal on pins 2/3, return on pin 1 (ground)

## Build Notes

- JFET: 2SK660, 2SK170, or 2N3819 (low-noise)
- 2SA1162-GR can be substituted with other PNP transistors
- R11/R12 (33Ω) protect output; can be omitted
- Use shielded cable from capsule to PCB (or direct solder)
- Add 10MΩ–47MΩ resistor from capsule backplate to 48V for bias

## Testing

Compared to Sennheiser e845:
- DIY: Cleaner mids/highs, more noise in sub-bass
- e845: Very clean bass, slight noise in highs

## License

MIT — build, use, modify, share.
