# Contributing to DHVANI

Thank you for your interest in contributing to **DHVANI (Adaptive Software-Defined Sonar Transmitter)**!

This project is an open-source, embedded DSP and sonar engineering initiative. We welcome contributions in firmware optimization, signal processing algorithms, hardware development, machine learning pipeline enhancement, and documentation.

---

## Code of Conduct

We are committed to providing a welcoming, constructive, and respectful environment for all contributors. Please maintain professional courtesy, constructive critiques, and technical rigor in all discussions, issues, and pull requests.

---

## Areas for Contribution

1. **Firmware & DSP Optimization (`firmware/`)**
   - Direct Memory Access (DMA) and circular streaming pipeline optimizations.
   - Fixed-point or CMSIS-DSP accelerated waveform generation to reduce lookup math during dynamic reconfiguration.
   - Additional modulation schemes (e.g., hyperbolic frequency modulation, Frank codes, Costas arrays).
   - Low-power mode tuning (Stop mode transitions between pings).

2. **Ground-Station Dashboard & Telemetry (`dashboard/`)**
   - Serial transmission robustness and error correction (CRC-16 framing).
   - Real-world training data collection pipeline to replace the initial synthetic dataset.
   - Integration with external oceanographic visualization tools (e.g., ROS2, WebGL water column rendering).

3. **Analog Front-End & Hardware Design (`hardware/`)**
   - KiCad schematic and layout review for the Nucleo-144 shield.
   - Active filter topology refinement and impedance matching for specific underwater acoustic transducers.
   - Hydrophone receiver preamplifier and ADC sampling stages for closed-loop echo capture.

4. **AUV Payload Enclosure (`hardware/pod/`)**
   - Hydrodynamic drag optimization using CFD simulations.
   - Waterproofing (O-ring groove integration, IP68 cable glands, resin potting guides).

---

## Development & Submission Workflow

### 1. Fork & Branch

```bash
git checkout -b feature/your-feature-name
```

Use descriptive branch names:
- `feature/add-costas-modulation`
- `fix/dma-underrun-check`
- `docs/update-pin-map`

### 2. Embedded Firmware Guidelines

- Follow standard STM32 HAL / CMSIS conventions.
- Do not introduce blocking delays (`HAL_Delay`) inside time-critical ping loops or interrupt service routines (ISRs).
- Maintain timing determinism: pin toggles (e.g., `PE0` CPU-busy probe) must remain accurate for oscilloscope verification.
- Always verify register configurations against the **STM32U575 Reference Manual (RM0456)**.
- Document any modified peripheral prescalers, ARR values, or DMA channel allocations in both code comments and `firmware/README.md`.

### 3. Dashboard & ML Guidelines

- Ensure Python code complies with PEP 8 standards.
- Keep dependencies minimal to retain lightweight ground-station deployment.
- Any ML retrain must provide reproducible random seeds and documented evaluation metrics (`dhvani_model_report.txt`).
- **Transparency Rule**: Always clearly disclose whether datasets are synthetic or measured from bench/field tests.

### 4. Commit Conventions

We follow Conventional Commits:

- `feat: add Frank code polyphase modulation`
- `fix: correct INA219 shunt calculation calibration factor`
- `docs: update bench measurement table with oscilloscope captures`
- `refactor: clean up GPDMA channel configuration structs`

### 5. Pull Request Process

1. Ensure the project builds cleanly in STM32CubeIDE without warnings.
2. If modifying the dashboard, test both live serial connection and demo replay (`sample/log_demo.txt`).
3. Update relevant documentation in `docs/` and directory-level `README.md` files.
4. Submit your pull request with a detailed description of the changes, hardware setup used for testing, and bench measurement artifacts (e.g., scope captures, FFT plots).

---

## Contact & Maintainer

- **Developer:** Dipesh Janghel
- **GitHub:** [@dipeshjanghel](https://github.com/dipeshjanghel)
- **Repository:** [DHVANI-Software-Defined-Sonar](https://github.com/dipeshjanghel/DHVANI-Software-Defined-Sonar)
