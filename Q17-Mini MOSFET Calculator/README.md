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
| `Q17_Q15-Q16_MOSFET_Compatibility_R14-R15_1.1*.xlsx` | Q15 (N-channel) / Q16 (P-channel) | R14 / R15 | Compare output MOSFET pairs and estimate suitable initial gate-resistor values. |
| `Q5_Q6_MOSFET_Compatibility_1.0*.xlsx` | Q5 / Q6 complementary MOSFETs | R7 / R8 | Compare candidate Q5/Q6 pairs with the existing 100 Ω resistor values. |

Both workbooks are intended for **Microsoft Excel**. They use formulas and visual indicators; open them in Excel to preserve the intended calculation and formatting behavior.

## 1. Q15/Q16 MOSFET Compatibility and R14/R15 Calculator

**File:** `Q17_Q15-Q16_MOSFET_Compatibility_R14-R15_1.1*.xlsx`

This workbook evaluates complementary **power MOSFET pairs** for the Q17-Mini output stage:

- **Q15:** N-channel MOSFET
- **Q16:** P-channel MOSFET
- **R14 / R15:** associated gate resistors

### Main features

- MOSFET reference data, including gate capacitances, gate charges, transconductance-related values, and datasheet references.
- Pair selection with a comparison of N-channel and P-channel electrical characteristics.
- Effective gate-capacitance (**Ceff**) profile comparison.
- Recommended **initial** R14/R15 values and their balance.
- **Qgd (Miller charge)** similarity as an additional diagnostic, not a standalone acceptance criterion.
- Configurable selection thresholds and suitability checks, including the **Ciss ≤ 3.5 nF** preselection limit used for the current Q17-Mini evaluation.
- Theoretical classification of candidate pairs:
  - **A — Very Good Candidate**
  - **B — Good Candidate**
  - **C — Needs Review**
  - **X — Unsuitable**
- Separate tracking of **physical Q17 test status**, tested resistor values, and test notes.
- A `Summary` worksheet with comparative indicators and data bars.

### What the workbook illustrates (reference only)

1. Review the candidate MOSFET data and the limits in `Config`.
2. Select a Q15/Q16 pair in `Selection`.
3. Examine the calculated Ceff, Rgate, Qgd, warnings, and initial R14/R15 values.
4. Compare alternatives in `Summary`.
5. Consult the physical validation log to distinguish preliminary calculations from independently obtained test results.

**Important:** An **A** or **B** rating is a *theoretical preselection*, **not** confirmation of stability or successful operation on the Q17-Mini. Experimental validation is tracked separately. In particular, Qgd similarity alone cannot predict dynamic behavior.

## 2. Q5/Q6 MOSFET Compatibility Calculator

**File:** `Q5_Q6_MOSFET_Compatibility_1.0*.xlsx`

This workbook compares **complementary MOSFET candidates for Q5 and Q6** in the Q17-Mini.

Unlike the Q15/Q16 calculator, it evaluates candidates with the associated resistor values held constant:

- **R7 = 100 Ω**
- **R8 = 100 Ω**

### Main features

- Candidate Q5 and Q6 MOSFET reference data.
- Comparison of complementary device characteristics and electrical mismatch.
- Suitability scores to help shortlist potential pairs.
- Graphical comparisons of device scores and mismatch associated with the fixed 100 Ω configuration.
- A summary of candidate combinations to prioritize for further investigation and testing.

The scores are **comparative indicators** based on the calculator's assumptions and available device data. They do not establish stability, reliability, or measured performance in the complete amplifier.

## Notes on the results

- **Theoretical vs. measured:** Calculated suitability and real-world Q17-Mini validation are distinct.
- **Datasheet conditions:** MOSFET parameters may be specified at different voltages, currents, temperatures, and test frequencies. Direct comparisons therefore have limitations.
- **Estimated parameters:** Some values may be estimated from typical datasheet curves when no directly comparable specification is available.
- **Gate-resistor values:** Suggested R14/R15 values are starting points; actual values must be confirmed experimentally.
- **Safety and stability:** Check operating conditions, temperature, safe operating area (SOA), and amplifier behavior under appropriate loads. Oscilloscope testing is essential before adopting a new device pair.

## Project status

**Status: BETA.** Candidate data, formulas, and ratings are preliminary and subject to change following ongoing development and physical MOSFET tests on the Q17-Mini.

## License and attribution

Refer to the parent Q17-Mini repository for project information, attribution, and applicable licensing terms.
