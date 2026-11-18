# DHVANI Engineering Documentation & Build Guides

This directory contains the complete technical reference guides, circuit roadmaps, hardware assembly instructions, and testing protocols for the **DHVANI Adaptive Software-Defined Sonar Transmitter**.

---

## Document Index & Categorization

```
docs/
│
├── hardware/                                  # Hardware wiring, breadboard layouts & pinout guides
│   ├── DHVANI_Builtin_DAC_Build_v3.pdf        # PRIMARY REFERENCE: Wiring guide for internal 12-bit DAC
│   ├── DHVANI_Pins_and_Values_Roadmap.pdf     # Complete Nucleo-144 pin mapping and passive component values
│   └── DHVANI_Breadboard_Build_v2.pdf         # Historical reference: Earlier DAC0800 external DAC build
│
├── firmware/                                  # Embedded architecture & software stack
│   └── DHVANI_Tech_Stack.pdf                  # Technical stack breakdown & STM32 HAL peripheral overview
│
└── testing/                                   # Hardware verification & laboratory test procedures
    └── DHVANI_Complete_Test_Guide.pdf         # Oscilloscope probing, FFT analysis, & calibration guide
```

---

## Summary of Reference Guides

### 1. Primary Hardware Reference: Built-in DAC (`docs/hardware/DHVANI_Builtin_DAC_Build_v3.pdf`)
- Documents the active, low-power hardware implementation.
- Details the connection between the internal DAC output (`PA4`), the TL074 second-order Sallen-Key low-pass filter, the unity-gain buffer stage, and the output test loads (47 $\Omega$ scope line, 1 k$\Omega$ acoustic buzzer).
- Illustrates power rail routing (+5 V digital/analog, -9 V negative rail).

### 2. Pins & Values Roadmap (`docs/hardware/DHVANI_Pins_and_Values_Roadmap.pdf`)
- Serves as the master electrical lookup table.
- Details resistor and capacitor component values for the 340 kHz Butterworth filter ($R_1, R_2, C_1, C_2$).
- Enumerates pull-up resistors (4.7 k$\Omega$ on DS18B20 1-Wire pin `PF12`), I2C bus pull-ups (`PB8`/`PB9`), and ADC voltage divider scaling factors.

### 3. Complete Test & Validation Guide (`docs/testing/DHVANI_Complete_Test_Guide.pdf`)
- Step-by-step laboratory verification manual for oscilloscope and spectrum analyzer measurement.
- Guides oscilloscope probe attachment for the `PE0` CPU-busy signal to verify zero-CPU sleep during DMA streaming.
- Details FFT spectrum analyzer setup for verifying Barker-13 BPSK carrier center frequency (8.7 kHz measured vs 8.45 kHz expected) and chirp bandwidths.
- Includes step-by-step sensor calibration routines for the TDS salinity probe and clarity dial.

### 4. Technical Stack Guide (`docs/firmware/DHVANI_Tech_Stack.pdf`)
- Explains the dual-tier architecture: Real-time STM32 embedded C signal generation coupled with Python/Streamlit ground-station monitoring.
- Provides peripheral register mapping for GPDMA1, TIM6, DAC1, ADC1, and USART1.

---

## Versioning & Architecture Note

> [!NOTE]
> **Evolution from External DAC to Internal DAC**:
> - `DHVANI_Breadboard_Build_v2.pdf` and sections of `DHVANI_Tech_Stack.pdf` document an earlier hardware prototype that utilized an external 8-bit parallel DAC (DAC0800) driven by GPIO Port E.
> - The final, production-ready DHVANI architecture migrated to the STM32U575's **internal 12-bit DAC** with **TIM6 hardware triggering and GPDMA streaming** to significantly minimize PCB footprint and drastically reduce operating power.
> - **`DHVANI_Builtin_DAC_Build_v3.pdf` is the definitive current hardware reference.**
