# Components for Q17-Turbo 2.0 SMD version

Some components of the Q17-Turbo amplifier board can also be used with SMD variants.

- The Q11 and Q111 pair of BS250P can be replaced below the PCB with a NDC7003P on the U2 footprint.

- Q1 and Q4 can be replaced by Q1' and Q4' below the PCB.

	Q1': SI2328DS
	Q4': SI2325DS

	In this case with 60V rails, zeners D2 and D3 MUST BE REPLACED by 15V 1N5245B zener to get 13V.

	Other Mosfet pairs are compatible and have been tested. For more information see the Q17-Power-Transistors-Selection PDF table available in the Github repository.

- Q7 can be replaced by Q7' below the PCB with a JFE150 (don't forget to change R6 value to 182R).

- It is also possible to solder the opamp directly below the PCB on the U1 footprint without using a DIP socket.
