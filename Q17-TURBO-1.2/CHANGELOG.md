# Changelog Q17-Turbo


Version [1.2.3] (26-10-2023)

- Modified R32 footprint to support potentiometer type T93YA100KT20 (for testing).
- Added zener D7 and D5 (1N5245B) to protect output.
- Added Faston connector footprint on J3 input power connector.
- Removed useless fuse sockets to fit new Faston footprint.
- Optimized some tracks on GNDPWD parts.
- Added T5 and T6 to a better location.
- Various adds on schematic.
- New measures with a better measurement device.

Version [1.2.2] (4-09-2023)

- Added J4 jumper to be able to strap R32 more easily.
- R25 changed to 8k2 (was 7k5). Value optimized for 60Vdc.

Version [1.2.1] (08-08-2023)

- New version of PCB files. Corrected an error on the SMD footprint for U1 on the back.
- Added PJS6839 as replacement of NDC7003P.

Version [1.2.0] (30-07-2023)

- New circuits for handling low level signals and better specs at frequencies above 10KHz.
- Added Erno Borbely cascode type using JFET & depletion NMOS (Q7, Q8). Can now use low noise JFET's like LSK170B (TH) or TI Burr-Brown JFE150 (SMD).
- Current mirror was updated to a Wilson CCS with BS250 and NDC7003P (Q9 & U2).
- DC offset is now below 1mV (with R32=0R).
- The signal-to-noise ratio is better over the entire audio band.
- Now work at 60vDC (recommended voltage).
- Use handsoldering SMD footprints (enlarged tracks).
- Removed C29 and C30 from schematic and SMD footprint on back PCB.
- Removed C4' and C5' SMD footprint on back PCB.
- Added Q7' optional SMD footprint on back PCB for JFE150.
- Moved C31 and C32 close to the power input.
- R10 and R13 changed to 9R1 (was 10R).
- New footprint and parts for C18 and C19 (0.1uF MKP). Can accept 15mm and 7.5mm lead spacing.
- Added voltage test point footprints.
- Enlarged fuse footprint holes (fit 1mm2 wire now).
- Reverted J3 in schematic and PCB. Silkscreen was not on the right side.
- Replaced OPA1641 with OPA828 (SiGe JFET) for JFET lovers.
- Updated schematic with available Mouser part number and datasheet links.
- Updated iBOM Q17-TURBO-BOM file and <a href="https://audio.cyberkata.org/Q17-TURBO-BOM.html">Online Q17-TURBO-BOM</a> with Mouser part number (can be exported).
- New audio measures available.

Version [1.0.2] (26-06-2023)

- Replaced BD139G on Q12 with KSC1845 and updated footprint.
- Added parts equivalences in schematic.

Version [1.0.1](https://github.com/stefaweb/Q17-a-QUAD405-audiophile-approach/tree/5d390576078fdaf95bd449d5fe2e2c45a9edb5e6) (9-05-2023)

- Added U2 footprint on back PCB (replace Q9 and Q11).
- Updated some silkscreen on back PCB.
- Updated schematic with new parts.

Initial release : [1.0.0](https://github.com/stefaweb/Q17-a-QUAD405-audiophile-approach/tree/8860557ad7c0319b1982263380b270c39a1ce374) (10-12-2021)
