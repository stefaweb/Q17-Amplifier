# Q17-a-QUAD405-audiophile-approach
Q17 is a class B amplifier based on the QUAD405 current dumping principle.<br>
Please refer to <a href="https://github.com/tvicol/Q17-a-QUAD405-audiophile-approach/blob/main/Project%20description.pdf">Project description.pdf</a> for project description.<br>
Use KiCad 6 or later to open and edit source files.  KiCad 6 can be downloaded from CERN, https://www.kicad.org<br>
<b>LTSpice</b> - contain simulation asc file<br>
<b>KiCad source PS</b> - active rectification power supply KiCad source files<br>
<b>KiCad source</b> - Q17 amplifier KiCad source files<br>
<b>Q17_2final</b> - Q17 amplifier KiCad source files for dual output stage<br>
<b>Q17.pdf</b> - detailed presentation - bill of materials included<br>
<b>Q17.7z</b> - ngspice simulation files for Q17. This will run directly in KiCad. Thank you, Holger Vogt !<br>
<b>gerber-ps.zip</b> - production gerber for PCB active rectification power supply<br>
<b>GerberQ17.zip</b> - production gerber for Q17 amplifier<br>
<b>GerberQ17_2f.zip</b> - production gerber files for Q17 with dual output pair stage<br>

![image](https://user-images.githubusercontent.com/22703498/159252259-ddfc39c3-7433-49f7-a285-d0a09331d218.png)

Construction, discussion and support @ https://www.diyaudio.com/forums/solid-state/374507-q17-quad405-audiophile-approach-perfect-sound.html

Click & Order your Q17 with dual output pair PCB @ https://www.pcbway.com/project/shareproject/Q17__a_QUAD405_audiophile_approach.html


Q&A colled from diyaudio forum and mail
Q: Why no dc blocking input capacitor?
A: Q17 first stage make use of an operational that have a C7=1uF capacitor in negative reaction . 
This already make a dc block and we have a non polar capacitor C2&C22 in dc servo as well.
On other hand, If there is any dc at amplifier input you should look on your source and solved it. Do not try to “solve” previous stage problem by playing safe at the amplifier input.

Q: Why no voltage/ESD input protection ?
A voltage/ESD can be made by using zener or reverse polarised diodes. The issue with this approach is that any reverse polarised p/n junction (diode etc) will have high parasitic capacitance modulated by voltage. This highly degrade amplifier performance. How to work around this ? Use a good Volume Controller as Maya by Vicol-Audio.

Q: Any amplifier need input LPF, otherwise EMI will affect SNR.  Q17 do not have one, therefore it is poorly designed. Why Q17 do not have input LPF?
A: People like to generalise. The world is not black and white.
An LPF must be designed such way that will not be affected by input impedance. This is not the case with a potentiometer. Does not matter how good this potentiometer is, his attenuation will affect LPF.
The classic way on how a potentiometer is implemented is that he offer constant input impedance and variable output impedance toward amplifier input. The down side is that, even you go for a high input impedance, at low audio levels input LPF is highly degraded.  with very low frequency transfer affecting amplifier bandwidth. This is translated in poor audio performance at low audio levels.
This issue was address in Vicol-Audio Maya volume controller that make use of an R-2R resistive network allowing constant output impedance with high input variable impedance.
Beside this, input cable parasitic capacitance together with high amplifier impedance is enough to form a HF-LPF. Output operational LPF at ~125KHz will clean any noise further.


Q: Why there is no super diode ?
A: A super diode is usually made with a self polarised BJT. Unfortunately this is highly nonlinear and will modulate with voltage output stage bias. While is very efficient will highly degrade audio performance. I prefer to have plain and simple resistors, with no capacitor decoupling, between output mosfet gates.


Q: What about transitory power ON ? 
A: For this there are Q13&Q14. These have double role.
One is to ensure soft start using RC made with R29C13 and R30C14. 
This can be seen at amplifier turn on, D1 & D4 will light after ~1s.
Second role for Q13&Q14 is to act as super-capacitors, ensuring smooth power supply for class A and input stage.


Q: Why no protection zeners on all mosfets ?
A: Well some need and some do not need.
Let’s start with ones that do not need and later the ones that may need.
Q1 and Q4 are part of regulators and Vgs is already limited by 18V zeners.
Q8 is part of cascade and his Vgs is already limited by positive zener regulator to 18V. You may say it is high, but Q8 source is already lifted above ground by Q7.
Q9 and Q11 are part of current mirror. Q9’s Vgs is limited by Q10 + Vbe and Q10 by Q9 Vgs + VR3. This will not exceed 4V.
Q5 Vgs is also limited by Q9 Vds + VR3. Where Q9 Vds = Q10 Vgs. Therefore mirror with Q9&Q10 act as Vgs limiter for Q5.
Q6 may need a zener to limit his Vgs due during a transitory turn on his Vgs may be higher, but for a soft turn on there are Q13&Q14.
Q13&Q14 obviously need Vgs limiters because at power on, while C13&C14 are charging, Vgs will be above 45V. For such reason there are zener D4&D5, limiting Vgs to a value that keep Q13&Q14 on safe side.
Q15&Q16&Q17&Q18 there are output transistors that may need protection zener. These are high transconductance mosfets that indeed will deliver very high transitory currents. Here the man advantage is that we are running these in class B with very low bias current. Turn on/off transitory is also softened by Q13&Q14 trough class A stage made with Q5&Q6.
On other hand, I prefer to run output stage without protection zener due any zener internal parasitic capacitance is modulated with voltage. Any reverse biased diode act like a varicap. This is translated in muddy highs.


Q: Why no output inductor ?
A: This is a highly debatable question.
Engineers , I’m an engineer too, like to “play safe”, but I’m a nerd audiophile. I like good sound and I thrust my ears even more than “playing safe”.
However, your speaker cables have already an important inductance and parasitic capacitance that must considered. 
In some particular cases adding an output inductor may be needed, but these are in very very … few particular cases.
To be short, Q17 with no coil sound better.

Q: Why you improved 405 and not 909 ?
A: QUAD405 was a revolutionary amplifier. This not happen very often. It had his flaws, but these where merely due the parts available at the time. LM301 was one of the biggest issues.
Using my topology 909 can be also improved as well. Maybe, some day …

Q: Why no embedded protection in your schematic ?
A: This again due sound quality. There is always a trade between playing safe and having best sound.
I like to have best sound even I do not play safe and currently market offer a wide range of speaker protection modules.
Simplest protection would be to use a fast fuse (3A-5A) at amplifier output.


Q: How much capacitance I may put in power supply ?
A: This is related to your power transformer. A huge capacitance must be charged to be efficient.  For a transformer with 3A in secondary, I would say 20mF per rail is enough.


Q: It is Q17 quiet ?
A: Yes it is. No fass no buzz.
	
Q: Can Q17 drive ESL speakers ?
A: Yes, will drive ESL speakers very well. Thanks to high transconductance mosfet’s will offer excellent performance.

Q: What make Q17 special ?
A: His topology, class B operation, PCB with embedded coil and innovative active power supply. 

Q: Is Q17 power eficient ?
A: Yes, it is. Thanks to class B operation and Saligny synchronous rectification, Q17 is a modern amplifier with low power consumption.


Q: Where you you place this amplifier in term of value ?
A: A well executed Q17 will be better or at least on pair with some 25.000$ amplifiers.

Q: May I have an amplifier based on Q17 made by you ?
A:  Yes, you can. Mail me and I’ll make a custom one just for you.
