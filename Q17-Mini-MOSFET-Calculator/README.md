# Q17-Mini MOSFET Calculators

Two Excel workbooks for evaluating MOSFET combinations used in the **Q17-Mini audio power amplifier**.

The calculators compare candidate devices, highlight electrical mismatches, and illustrate possible starting points for further engineering investigation. They are **not validated design tools**.

> **⚠️ BETA — INFORMATION ONLY · NOT FOR USE**
>
> These workbooks are under development and shared **for information only, not for practical use**. Their results have not yet been fully validated.
>
> The files will be updated as development progresses and **physical MOSFET testing on the Q17-Mini** provides new results.

## Workbooks

| Workbook | Devices | Related resistors | Purpose |
| --- | --- | --- | --- |
| `Q17_MOSFET_Compatibility_List_1.1b38.xlsx` | Q15 (N-channel) / Q16 (P-channel) | R14 / R15 | Compare output MOSFET pairs, estimate initial gate-resistor values, and record physical validation and audio measurements. |
| `Q5_Q6_MOSFET_Compatibility_1.0*.xlsx` | Q5 / Q6 complementary MOSFETs | R7 / R8 | Compare candidate Q5/Q6 pairs with the existing 100 Ω resistor values. |

Both workbooks are intended for **Microsoft Excel**. They use formulas and visual indicators; open them in Excel to preserve the intended calculation and formatting behavior. The Q5/Q6 workbook is distributed separately and is not included in this Q15/Q16 package.

## 1. Q17 MOSFET Compatibility List

**Current version:** 1.1b38  
**File:** `Q17_MOSFET_Compatibility_List_1.1b38.xlsx`

This workbook evaluates complementary **power MOSFET pairs** for the Q17-Mini output stage:

- **Q15:** N-channel MOSFET.
- **Q16:** P-channel MOSFET.
- **R14 / R15:** associated gate resistors.

### Package structure

```text
Q17_MOSFET_Compatibility_List_1.1b38/
├── README.md
├── Q17_MOSFET_Compatibility_List_1.1b38.xlsx
└── Measurements/
    ├── Q17-3.1_C7_1W.png
    ├── Q17-3.1_C7_100W.png
    ├── Q17-3.1_C7_104W_OUT_BEFORE_CLIP.png
    ├── Q17-3.1_C7_106W_CLIP.png
    └── Q17-3.1_C7_SHORTED.png
```

Keep the workbook and `Measurements` folder together. Add new test captures to `Measurements` as they become available. The captures currently included concern pair **C7 on Q17-3.1**.

### Main features

- MOSFET reference data, including gate capacitances, gate charges, transconductance-related values, and datasheet references.
- Pair selection with a comparison of N-channel and P-channel electrical characteristics.
- Effective gate-capacitance (**Ceff**) profile comparison.
- Calculated **initial** R14/R15 values and their balance.
- **Qgd (Miller charge)** similarity as an additional diagnostic, not a standalone acceptance criterion.
- Configurable selection thresholds and suitability checks, including the **Ciss ≤ 3.5 nF** preselection limit used for the current Q17-Mini evaluation.
- Theoretical classification of candidate pairs: **A — Very Good Candidate**, **B — Good Candidate**, **C — Needs Review**, and **X — Unsuitable**.
- Separate tracking of physical Q17 test status, tested resistor values, and French/English test notes in the **Q17 PHYSICAL VALIDATION LOG** on `Selection`.
- Per-pair measurement fields for **1 W**, **100 W**, **before clipping**, **clipping observed**, and **shorted-input noise**.
- A theoretical comparison in `Summary` and a separate measured-performance comparison in `Summary 2`.
- French/English display controlled by `Config!B3`, including the headings, explanations, and measurement-status labels in `Summary 2`.

### Physical validation and theoretical comparison

1. Review the candidate MOSFET data and the limits in `Config`.
2. Select a Q15/Q16 pair in `Selection`.
3. Examine the calculated Ceff, Rgate, Qgd, warnings, and initial R14/R15 values.
4. Compare theoretical indicators in `Summary`.
5. Record physical test status, tested resistor values, and notes in the validation log.

`Summary` obtains test feedback and notes through the calculation sheets. Tested R14/R15 values override the theoretical starting values only when the pair is marked **VALIDÉ / VALIDATED** and **both tested resistor values are positive**. A validated status without both resistor values is reported as **incomplete validation**. Changing a physical test status does not change the theoretical class.

An **A** or **B** rating is a *theoretical preselection*, not confirmation of stability or successful operation on the Q17-Mini. Qgd similarity alone cannot predict dynamic behavior.

### Audio measurements

Current measurement conditions are **8 Ω**, approximately **1 kHz**, and a **20 Hz–20 kHz** measurement bandwidth. Record the analyzer input range and dBr reference where fields are provided. Weighting is not specified in the supplied captures; do not assume an A-weighted result.

- **1 W and 100 W:** record QA403 SNR, THD, H2, H3, H4, INPUT, and OUTPUT. INPUT and OUTPUT are in **Vrms**; the generator is connected directly to the amplifier input without intermediate attenuation.
- **Harmonics:** identify H2/H3/H4 by frequency, not by marker number. The QA403 marker list can change order between captures.
- **50 Hz:** record the displayed dBr value and the reference shown in `Sys: Dbr`. The workbook converts the level using **dBV = dBr + reference dBV**.
- **Clipping:** use the oscilloscope to identify the onset of visible flattening, then record the QA403 output voltage immediately before clipping. Keep this limit separate from the fixed **100 W** comparison point.
- **SHORTED:** disconnect the generator and short the amplifier input. Record the QA403 **RMS Volts** reading as output noise in **µVrms**. This includes the measurement system's contribution; the analyzer range must therefore be documented.

Do not use the QA403 SNR, THD, or THD+N tiles from a signal-free SHORTED capture as the amplifier's signal-to-noise result. The workbook calculates reference SNR from the measured total output noise:

```text
SNR = 20 × log10(reference output voltage / measured output noise)

1 W into 8 Ω:    reference voltage = √8   ≈ 2.828 Vrms
100 W into 8 Ω:  reference voltage = √800 ≈ 28.284 Vrms
```

Use volts for both quantities in the calculation. `Pk Vrms` is the RMS level of the largest spectral peak, not the total integrated noise; use **RMS Volts** for the SHORTED noise value.

### Summary 2: measured-performance ranking

`Summary 2` links to measurements entered in `Selection` and automatically sorts the pairs by:

1. **Lowest THD at 1 W.**
2. **Lowest THD at 100 W**, when THD at 1 W is equal.
3. **Highest SNR referenced to 1 W**, when both THD values are equal.

The SNR columns in this summary are calculated from **SHORTED noise**, referenced to **1 W** and **100 W**. They are distinct from the QA403 SNR readings obtained during tests with a signal, which remain in `Selection`.

The summary also displays **50 Hz with the input shorted, in dBV**, and the voltage and power immediately before clipping. These are supplementary indicators and are not part of the ranking criteria. Exact ties share the same rank. Pairs without the required THD measurements and a valid SHORTED noise measurement remain unranked.

Only C7 currently has the measurements required for ranking. Its rank of 1 does not establish superiority over the unmeasured pairs.

### Current C7 reference measurements

| Quantity | Recorded value |
| --- | ---: |
| THD at 1 W | 0.00091 % |
| THD at 100 W | 0.06971 % |
| Output noise, input shorted, range +18 dBV | 33.89 µVrms |
| Calculated SNR, reference 1 W into 8 Ω | 98.43 dB |
| Calculated SNR, reference 100 W into 8 Ω | 118.43 dB |
| 50 Hz, input shorted | −107.82 dBV |
| Last recorded point before clipping | 28.91 Vrms; QA403 power reading 104 W |
| Recorded point with clipping observed | 29.23 Vrms; QA403 power reading 106 W |

The latest 1 W and SHORTED captures use **+18 dBV** full-scale input and a **9.04 dBV** dBr reference. The supplied 100 W capture uses **+36 dBV** full-scale input. These settings and results describe the recorded tests, not universal performance guarantees.

### Printing and editing

`Summary` and `Summary 2` have defined print areas and use **A4 landscape** layout. `Summary 2` includes its full comparison table and is fitted to one page. Preserve these settings and existing user inputs when updating the workbook. Continue editing the latest workbook rather than rebuilding it from an older version.

## 2. Q5/Q6 MOSFET Compatibility Calculator

**File:** `Q5_Q6_MOSFET_Compatibility_1.0*.xlsx` — distributed separately.

This workbook compares complementary MOSFET candidates for Q5 and Q6 in the Q17-Mini, with the associated resistor values held constant:

- **R7 = 100 Ω**.
- **R8 = 100 Ω**.

Its features include candidate reference data, comparisons of complementary device characteristics and electrical mismatch, suitability scores, graphical comparisons, and a summary of combinations to prioritize for further investigation.

The scores are comparative indicators based on the calculator's assumptions and available device data. They do not establish stability, reliability, or measured performance in the complete amplifier.

## Notes on the results

- **Theoretical vs. measured:** calculated suitability and physical Q17-Mini validation are distinct.
- **Datasheet conditions:** MOSFET parameters may be specified at different voltages, currents, temperatures, and test frequencies. Direct comparisons therefore have limitations.
- **Estimated parameters:** some values may be estimated from typical datasheet curves when no directly comparable specification is available.
- **Gate-resistor values:** suggested R14/R15 values are starting points; actual values must be confirmed experimentally.
- **Measurement consistency:** compare results obtained with documented bandwidth, weighting, load, input range, and reference conditions. A SNR with signal and a SNR calculated from shorted-input noise are different results.
- **Safety and stability:** check operating conditions, temperature, safe operating area (SOA), and amplifier behavior under appropriate loads. Oscilloscope testing is essential before adopting a new device pair.

## Project status

**Status: BETA.** Candidate data, formulas, and ratings are preliminary and subject to change following ongoing development and physical MOSFET tests on the Q17-Mini.

## License and attribution

Refer to the parent Q17-Mini repository for project information, attribution, and applicable licensing terms.
