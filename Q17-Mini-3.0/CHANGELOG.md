# Changelog Q17-Mini

Version [3.0.4] (7-10-2024)

- Modified low signal ground plane.
- Replaced 2SK3564 by FQPF3N80C for Q6.
- Updated Q17-Mini-BOM.html.

Version [3.0.3] (14-09-2024)

- Reduced hole size for R26, R27, R28 and R31.
- Added a dual footprint with lead spacing of 2.5mm and 5.0mm for C3 and C6.
- Changed R15 to 270R.
- Modified ground plane connection for C2.

Version [3.0.2] (23-08-2024)

- Added 2 diodes SL1M-AQ (D8/D9) for a more secure MOSFET protection.
- Added SOT-23 footprint for Q1 and Q4 on back PCB (Q1' = SI2328DS and Q4' = SI2325DS). Need 15V 1N5245B zener on D2 and D3 to get 13V.
- Replaced IXTH48P20P by IXTQ36P15P for Q16.
- Replaced JFET choice OPA1641 by OPA828 (U1).
- Updated R10 and R13 to 8R2 for IXTQ36P15 compatibility. Bias for class A stage is now 78mA (+8mA).
- Moved Q7' SMD footprint closer to Q7.
- The board now consume at idle 200mA @ 50Vdc (warm board).
- Updated diagram with last components and values.
- Updated Q17-Mini-BOM.html and Q17-Mini-SMD-BOM.md files.
- Added Q17-Power-Transistors-Selection table on Github repository.

Version [3.0.1] (27-07-2024)

- Complete new PCB design and components placement.
- Same PCB size, mounting holes and power transistor locations as v2.
- Removed all thermal brakes and VIAs (except for U2).
- Removed R32. No longer needed due to new ground plane.
- Removed C18 and C19. They are not needed with low ESR capacitors.
- Added D7 and D8 protection zener (MMSZ5245C).
- Updated R17 to 196R for 1.2V sensibility (with LSK170B).
- Updated R15 to 150R (with IXTH48P20P in Q16).
- Merged GND / GNDPWR ground and built a new ground plane using GND zones and star topology.
- Better thermal management on the PCB.
- Updated diagram to 2.3.
- Updated iBOM Q17-Mini-BOM file.
- Added Q17 Power Transistors Selection table PDF file on github repository.

Version [2.2.1] (8-06-2024)

- Modified C7 footprint to support 2.2uF MKP capacitor (Lead spacing 22.5mm).
- Added double footprint for SMD U2 (NDC7003P) or TH Q11 / Q111 (2 matched BS250P).
- Added D7 and D8 protection zener (MMSZ5245C).
- Removed R33 and C20 (removed LFE at input no longer used).
- Various changes on GND and GNDPWR backplane.
- Changed C15 and C16 to 470uF.
- Added more parts on the diagram.
- Updated diagram to 2.2.
- Updated iBOM Q17-Mini-BOM file.

Version [2.0.1] (21-05-2024)

- Changed C7 to 2.2uF (better bandwidth linearity).
- Changed R16 to 47k.
- Removed R33 (replace with 0R or strap).
- Removed C20.
- No PCB change.

Version [2.0] (3-09-2023)

- New Q17.3 circuit.
- Added Erno Borbely cascode type using JFET & depletion NMOS (Q7, Q8). Can now use low noise JFET's like LSK170B (TH) or TI Burr-Brown JFE150 (SMD).
- Current mirror was updated to a Wilson CCS with BS250 and NDC7003P (Q9 & U2).
- The signal-to-noise ratio is better over the entire audio band.
- Use handsoldering SMD footprints (enlarged tracks).
- Removed C29 and C30 from schematic and SMD footprint on back PCB.
- Removed C4' and C5' SMD footprint on back PCB.
- Added Q7' optional SMD footprint on back PCB for JFE150.
- R10 and R13 changed to 9R1 (was 10R).
- Replaced OPA1641 with OPA828 (SiGe JFET) for JFET lovers.
- The 4 M3 mounting holes have been ovalized for easier installation.
- Updated schematic with available Mouser part number and datasheet links.
- Updated iBOM Q17-Mini-BOM file and <a href="https://audio.cyberkata.org/Q17-Mini-2.0.html">Online Q17-Mini-2.0-BOM</a> with Mouser part number (can be exported).
- New audio measures available.

Version [1.3.1] (25-06-2023)
- Moved C10 for better placement (thermal).
- Modified some parts of GND ground plane.
- The SMD capacitors footprints have been moved slightly away from the active components. Was difficult to solder by hand.
- Added JST-XH connector footprint for J1 (input).
- Changed U1 to OPA1611 (Sound warmer and a little less midrange).
- Updated C3/C6 to 47uF/25v (Nichicon Muse KZ UKZ1E470MPM1).
- Changed R29 and R30 to 100R (no more noise at power on)
- Replaced BD139G on Q12 with KSC1845 and updated footprint.
- Many parts equivalences added in schematic.

Version [1.3](https://github.com/stefaweb/Q17-a-QUAD405-audiophile-approach/commit/e14c5743dc9d61eb0646178def298882dcf551b0) (26-08-2022)

- Moved Q8, R1, R5, R23 and R25 to new location.
- Moved R7 close to Q5.
- Moved R8 close to Q6.
- Removed R22 at opamp input.
- Changed R40 and R41 to 100 Ohms.
- Changed C29 and C30 to 15nF (optional).
- The holes in the PCB for C7 have been enlarged. You can now solder a larger high end capacitor to the back of the PCB.
- More silkscreen text on front and back side.
- Added component Part Number column in Q17-Mini-BOM.html.
- DC offset at output is now < 2mV.
- Added Q17-Mini-drilling.pdf to help to drill holes for power transistors.
- Updated Q17-Mini-BOM.html.

Version [1.2.1](https://github.com/stefaweb/Q17-a-QUAD405-audiophile-approach/commit/6671ab5b4a45497aaad0a56b8615fdbb069a5a3f) (9-08-2022)

- Removed R22 at opamp input.
- Changed R40 and R41 to 100 Ohms.
- Changed C29 and C30 to 15nF (optional).
- Changed R29 and R30 to 10k.
- R32 replaced by a strap (R2=0R).
- More silkscreen text on front and back side.
- Added component Part Number column in Q17-Mini-BOM.html.

Version [1.2](https://github.com/stefaweb/Q17-a-QUAD405-audiophile-approach/tree/8caf9e90742d23102cca4e3eea3342eca072945a) (6-03-2022)

- New (optional) LPF (R33/C20) at input to protect op-amp.
- L1 coil is now positioned vertically and have more space around.
- Q7 and its resistors moved to a better location.
- New gate stopper resistor R40/R41 for Q1 and Q4.
- R32 moved to a better location.
- New C7 footprint can fit Wima MKP2, FKP2 and MKS4 (5mm and 7.5mm pitch).
- C17 now can fit Wilma FKP3 and MKP10.
- New C20 can fit Wima FKP2, Vishay MKT and CDE Mica (5mm and 5.9mm pitch).
- New design for 70% of tracks. Removed all signal VIAS (there were eight).
- Ground plane on both sides with ground VIAS.
- Added some optional SMD footprints on the back side.
- More silkscreen text on back side.

Version [1.1.4](https://github.com/stefaweb/Q17-a-QUAD405-audiophile-approach/tree/5d390576078fdaf95bd449d5fe2e2c45a9edb5e6) (13-01-2022)

- Changed L1 footprint (vertical).
- Added R42 and R43.
- Switched R18 and C7.
- Added some optional SMD footprints.
- Rounded tracks.
- Updated diagram.

Initial release : [1.1.1](https://github.com/stefaweb/Q17-a-QUAD405-audiophile-approach/tree/8860557ad7c0319b1982263380b270c39a1ce374) (10-12-2021)
