

\# DHVANI – Adaptive Software-Defined Sonar Transmitter



An embedded sonar transmission system designed to generate adaptive acoustic signals based on environmental sensor inputs.



\## Project Overview



DHVANI is an embedded system that explores software-defined sonar signal generation for underwater applications. It uses a microcontroller, digital-to-analog conversion, sensor integration and signal processing to generate configurable sonar waveforms.



\## Objectives



\- Generate configurable sonar transmission signals.

\- Implement multiple digital modulation techniques.

\- Integrate environmental sensors.

\- Explore adaptive signal parameter control.

\- Validate generated signals through hardware testing.



\## Hardware Components



| Component | Purpose |

|---|---|

| STM32U575 | Main microcontroller |

| 12-bit DAC | Analog signal generation |

| TL074 | Analog signal conditioning |

| TDS Sensor | Water quality measurement |

| DS18B20 | Temperature measurement |

| INA219 | Voltage and current monitoring |



\## Software \& Technologies



\- Embedded C

\- STM32U575

\- DAC configuration

\- DMA-based data streaming

\- Timer configuration

\- Digital Signal Processing

\- FFT analysis



\## Signal Generation Techniques



\- Linear Frequency Modulated (LFM) Chirp

\- Geometric Sweep

\- Barker-13 BPSK Modulation

\- Windowing techniques



\## System Working



1\. Environmental sensors collect measurement data.

2\. The STM32U575 processes sensor readings.

3\. Signal parameters are configured according to the system's adaptive logic.

4\. Timer and DMA control signal data transfer to the DAC.

5\. The analog output passes through signal conditioning.

6\. Generated waveforms are evaluated using an oscilloscope and FFT analysis.



\## Key Features



\- Multiple waveform generation techniques.

\- DAC-based analog output.

\- DMA-driven signal streaming.

\- Environmental sensor integration.

\- Adaptive frequency and amplitude control.

\- Hardware signal validation.



\## My Contribution



I worked across the project development, including:



\- Embedded firmware development.

\- STM32 peripheral configuration.

\- DAC, DMA and timer integration.

\- Digital waveform generation and modulation.

\- Sensor interfacing.

\- Analog signal conditioning.

\- Oscilloscope testing and FFT validation.



\## Future Improvements



\- Advanced adaptive signal processing.

\- Improved underwater signal characterization.

\- Extended sensor integration.

\- Further hardware optimization.



\---



\*\*Developer:\*\* Dipesh Janghel



\*\*Domain:\*\* Embedded Systems | Signal Processing | Underwater Communication



