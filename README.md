# Q17-a-QUAD405-audiophile-approach


![Q17](https://user-images.githubusercontent.com/22703498/168981362-8983cd89-4096-4918-838b-a98bf1d8269b.jpeg)



Q17 is a class B amplifier based on the QUAD405 current dumping principle.<br>
Please refer to <a href="https://github.com/tvicol/Q17-a-QUAD405-audiophile-approach/blob/main/Project%20description.pdf">Project description.pdf</a> for project description.<br>
Use KiCad 6 or later to open and edit source files.  KiCad 6 can be downloaded from CERN, https://www.kicad.org<br>
<b>LTSpice</b> - contain simulation asc file<br>
<b>Q17.7z</b> - ngspice simulation files for Q17. This will run directly in KiCad. Thank you, Holger Vogt !<br>
<b>KiCad source PS</b> - active rectification power supply KiCad source files<br>
<b>KiCad source</b> - Q17 amplifier KiCad source files<br>
<b>Q17_2final</b> - Q17 amplifier KiCad source files for dual output stage<br>
<b>Q17.pdf</b> - detailed presentation - bill of materials included<br>
<b>gerber-ps.zip</b> - production gerber for PCB active rectification power supply<br>
<b>GerberQ17.zip</b> - production gerber for Q17 amplifier<br>
<b>GerberQ17_2f.zip</b> - production gerber files for Q17 with dual output pair stage<br>

![image](https://user-images.githubusercontent.com/22703498/159252259-ddfc39c3-7433-49f7-a285-d0a09331d218.png)
<br>
<br>
Construction, discussion and support @ https://www.diyaudio.com/forums/solid-state/374507-q17-quad405-audiophile-approach-perfect-sound.html<br>
<br>
Click & Order your Q17 with dual output pair PCB @ <a href="https://www.pcbway.com/project/shareproject/Q17__a_QUAD405_audiophile_approach.html"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a><br>
Purchase parts with one click from mouser ->> https://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=1f37a45393 <br>
<br>
<br>
<b>Q&A collected from diyaudio forum and mail</b><br>
<br>
Q: Why no dc blocking input capacitor?<br>
A: <i>Q17 first stage make use of an operational that have a C7=1uF capacitor in negative reaction . <br>
This already make a dc block and we have a non polar capacitor C2&C22 in dc servo as well.<br>
On other hand, If there is any dc at amplifier input, you should look on your source and solved it. Do not try to “solve” previous stage problems by playing safe at the amplifier input.</i><br>
<br>
<br>
Q: Why no voltage/ESD input protection ?<br>
A: <i>A voltage/ESD can be made by using zener or reverse polarised diodes. The issue with this approach is that any reverse polarised p/n junction (diode etc) will have high parasitic capacitance modulated by voltage. This highly degrade amplifier performance. How to work around this ? Use a good Volume Controller (as Maya by Vicol-Audio).</i><br>
<br>
<br>
Q: Any amplifier need input LPF, otherwise EMI will affect SNR.  Q17 do not have one, therefore it is poorly designed. Why Q17 do not have input LPF?<br>
A: <i>People like to generalise. The world is not black and white.<br>
An LPF must be designed such way that will not be affected by input impedance. This is not the case with a potentiometer. Does not matter how good this potentiometer is, his attenuation will affect LPF and therefore amplifier bandwidth at low level volume.<br>
The classic way on how a potentiometer is implemented is that he offer constant input impedance and variable output impedance toward amplifier input. The down side is that, even you go for a high input impedance, at low audio levels input LPF will reach audio band affecting amplifier bandwidth. This is translated in poor audio performance at low audio levels.<br>
This issue was address in Vicol-Audio Maya volume controller that make use of an R-2R resistive network allowing constant output impedance with high input variable impedance.<br>
Beside this, input cable parasitic capacitance together with high amplifier impedance is enough to form a HF-LPF. Output operational LPF at ~125KHz will clean any noise further.</i><br>
<br>
<br>
Q: Why there is no super diode ?<br>
A: <i>A super diode is usually made with a BJT, where his Vbe variation with temperatures is used to adjust output stage bias. Unfortunately this is highly nonlinear and will modulate, with Vcb voltage (again reverse polarised p/n junction), output stage bias. While is very efficient, will highly degrade audio performance. I prefer to have plain and simple resistors, with no capacitor decoupling, between output mosfet gates.</i><br>
<br>
<br>
Q: What about transitory power ON ? <br>
A: <i>For this there are Q13&Q14. These have double role.<br>
One is to ensure soft start using RC made with R29C13 and R30C14. <br>
This can be seen at amplifier turn on, D1 & D4 will light after ~1s.<br>
Second role for Q13&Q14 is to act as super-capacitors, ensuring smooth power supply for class A and input stage.</i><br>
<br>
<br>
Q: Why no protection zeners on all mosfets ?<br>
A: <i>Well some need and some do not need.<br>
Let’s start with ones that do not need and later the ones that may need.<br>
Q1 and Q4 are part of regulators and Vgs is already limited by 18V zeners.<br>
Q8 is part of cascade and his Vgs is already limited by positive zener regulator to 18V. You may say it is high, but Q8 source is already lifted above ground by Q7.<br>
Q9 and Q11 are part of current mirror. Q9’s Vgs is limited by Q10 + Vbe and Q10 by Q9 Vgs + VR3. This will not exceed 4V.<br>
Q5 Vgs is also limited by Q9 Vds + VR3. Where Q9 Vds = Q10 Vgs. Therefore mirror with Q9&Q10 act as Vgs limiter for Q5.<br>
Q6 may need a zener to limit his Vgs due during a transitory turn on his Vgs may be higher, but for a soft turn on there are Q13&Q14.<br>
Q13&Q14 obviously need Vgs limiters because at power on, while C13&C14 are charging, Vgs will be above 45V. For such reason there are zener D4&D5, limiting Vgs to a value that keep Q13&Q14 on safe side.<br>
Q15&Q16&Q17&Q18 there are output transistors that may need protection zener. These are high transconductance mosfets that indeed will deliver very high transitory currents. Here the man advantage is that we are running these in class B with very low bias current. Turn on/off transitory is also softened by Q13&Q14 trough class A stage made with Q5&Q6.<br>
On other hand, I prefer to run output stage without protection zener due any zener internal parasitic capacitance is modulated with voltage. Any reverse biased diode act like a varicap. This is translated in muddy highs.</i><br>
<br>
<br>
Q: Why no output inductor ?<br>
A: <i>This is a highly debatable question.<br>
Engineers , I’m an engineer too, like to “play safe”, but I’m a nerd audiophile. I like good sound and I thrust my ears even more than “playing safe”.<br>
However, your speaker cables have already an important inductance and parasitic capacitance that must considered. <br>
In some particular cases adding an output inductor may be needed, but these are in very very … few particular cases.<br>
To be short, Q17 with no coil sound better.</i><br>
<br>
<br>
Q: May I use Lateral MOSFET's in ouput stage ?<br>
A: <i>No, you do not. Lateral mosfet transistor's have different piout than Vertical mosfet.<br>
  Q17 PCB was designed for Vertical mosfet, therefore PCB need to be redesigned to accomodate Lateral's, for both Class A and output Class B stage.
  Laterals have lover Vgsth than Verticals, therefore for laterals, R11 and R12 must be between 9.1 and 10 ohm.</i><br>
<br>
<br>
Q: Why you improved 405 and not 909 ?<br>
A: <i>QUAD405 was a revolutionary amplifier. This not happen very often. It had his flaws, but these where merely due the parts available at the time.  LM301 was one of the biggest issues.<br>
Using my topology 909 can be also improved as well. Maybe, some day …</i><br>
<br>
<br>
Q: Why no embedded protection in your schematic ?<br>
A: <i>This again due sound quality. There is always a trade between playing safe and having best sound.<br>
I like to have best sound even I do not play safe and currently market offer a wide range of speaker protection modules.<br>
Simplest protection would be to use a fast fuse (3A-5A) at amplifier output.</i><br>
<br>
<br>
Q: How much capacitance I may put in power supply ?<br>
A: <i>This is related to your power transformer. A huge capacitance must be charged to be efficient.  For a transformer with 3A in secondary, I would say 20mF per rail is enough.</i><br>
<br>
<br>
Q: Is there any sound difference between a normal bridge and your Saligny synchronous rectifiers ?<br>
A: Yes, it is and improvment is very important. You may compare yourself.
<br>
<br>
Q: It is Q17 quiet ?<br>
A: <i>Yes it is. No fass no buzz.</i><br>
<br>
<br>
Q: May you recommend a transformer ?<br>
A: <i>Any well made 300VA transformer, with 2 secondaries at 36Vac .</i><br>
<br>
<br>
Q: Can Q17 drive ESL speakers ?<br>
A: <i>Yes, will drive ESL speakers very well. Thanks to high transconductance mosfet’s will offer excellent performance.</i><br>
<br>
<br>
Q: What make Q17 special ?<br>
A: <i>His topology, class B operation, PCB with embedded coil and innovative active power supply. </i><br>
<br>
<br>
Q: Is Q17 power eficient ?<br>
A: <i>Yes, it is. Thanks to class B operation and Saligny synchronous rectification, Q17 is a modern amplifier with low power consumption.</i><br>
<br>
<br>
Q: Where you you place this amplifier in term of value ?<br>
A: <i>A well executed Q17 will be better or at least on pair with some $5 digit amplifiers.</i><br>
<br>
<br>
If you enjoy this project, you may offer to me a cup of coffee. :-) <br>
<br>
https://www.paypal.com/donate/?hosted_button_id=7K8RP22HP5UBA
<br>
or scan with your phone
<br>
![QR Code](https://user-images.githubusercontent.com/22703498/168473006-614d0b84-c3e2-4b54-8bb3-428a1676abe5.png)
