# Q17 LTspice simulations

Extract each archive into its own folder, open the `.asc` schematic in LTspice, and click **Run**. Keep the model files alongside the schematic. Both projects were tested with LTspice 26.0.2 on macOS.

| Project | Default simulation | Simulated output into 8 Ω |
| --- | --- | --- |
| **Q17-Mini 3.1.6** | 1 kHz sine wave, 30 ms transient | 2.83 V RMS, 1.00 W, 0.052% THD |
| **Q17-Turbo 1.3b29** | 1 kHz sine wave, 30 ms transient | 32.56 V RMS, 132.55 W, 0.027% THD |

Both simulations save the final 10 ms for waveform and distortion analysis. Open **View → SPICE Error Log** to see the measurements and Fourier results.
