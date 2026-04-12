# umsakazo
NanoVNA RF Learning board - RF demo kit SMA training (All MIT License, design files will be released by the end of 2027)

![](stuff/images/front.jpg)

![](stuff/images/back.jpg)

![](stuff/images/demo_rlc.jpg)

![](stuff/images/demo_att.jpg)

-------

Here’s an introductory **VIDEO** DEMO on how to use the UMSAKAZO board:

[https://youtu.be/kYVsM9EE5ec ![](stuff/images/videocover.jpg)](https://youtu.be/kYVsM9EE5ec)

-------

# You can now buy it at [https://www.rootkit.es ![](stuff/images/comp.jpg)](https://www.rootkit.es/) 

## **Available in July 2026**

-------

# Story behind the project

![](stuff/images/story.jpg)

The famous green "RF Demo Kit for NANOVNA" board with UFL connectors was a pain to use with students in my hardware hacking bootcamps. On top of that, you can't make many connections and disconnections without breaking something. That's why I decided to design this demonstration board with SMA connectors. 

It's more robust, easier to use and solder, and allows experimenting with different components and configurations to learn about RF and NanoVNA usage.

I also incorporated the concept from the famous "NanoVNA Testboard Kit," but with a larger prototyping area to fit more components.

I built everything pretty much from scratch in my own way. I hope you like the idea.

Additionally, the board comes fully assembled with high-quality 0805 SMD components (C0G, thin film... without exceeding the target price).

Being larger with more components, including more expensive components and through-hole parts, and more soldering required, the board is naturally more expensive.

If you look for a cheap SMA alternative, check this project by IMSAI Guy, but you need transplant components from the original UFL board: https://www.youtube.com/watch?v=2W0pjMk56rA

Btw, the IMSAI Guy's board is better from the point of view of RF performance, but umsakazo is designed for learning and experimentation, not for precision measurements, so I prioritized ease of use and component accessibility over high-frequency performance.

## Why umsakazo name? 

umsakazo means radio in Zulu (South Africa)

# Getting Started with NanoVNA and umsakazo

Learn how to use NanoVNA and some electronics from scratch with umsakazo, the NanoVNA RF Learning board (RF demo kit SMA training). This tutorial will guide you through the basics of using a NanoVNA, understanding S-parameters, and performing simple measurements with the umsakazo board.

This documentation is written for the **AURSINC NanoVNA-F V2 50KHz-3GHz**

Assume you have the latest firmware installed and everything configured by default, as it comes from the factory.

Reset using Tera Term or any serial terminal:

```
ch> clearconfig 1234
Config and all cal data cleared.
ch> saveconfig
Config saved.
ch> reset
Performing reset
```

Now disconnect NanoVNA from the computer and power off, then power it on again to start with a clean slate. Repeat power-off and power-on two times to ensure all settings are reset.

# Your first demo: SMITH S11 - RC Series

![](stuff/images/rcseries.jpg)

First, press on the right side of the screen to enter the NanoVNA main menu.

![](stuff/images/entermenu.jpg)

Select "Stimulus" to configure the frequency range.

![](stuff/images/main_menu_select_stim.jpg)

Select "Start/Stop" to set the frequency range for your measurements (1 MHz - 250 MHz for the RC Series demo).

![](stuff/images/stim_menu_select_start_stop.jpg)

![](stuff/images/start_rang.jpg)

After clicking OK, press the right side of the screen to access the menu again, then select "Stop" to set the stop frequency range:

![](stuff/images/stop_rang.jpg)

Press on the right side of the screen to enter the NanoVNA menu.

![](stuff/images/entermenu.jpg)

Select "Back" to return to the main menu.

![](stuff/images/stim_menu_select_back.jpg)

Select "CAL" to enter the calibration menu.

![](stuff/images/main_menu_select_cal.jpg)

Select "Reset CAL" to clear any previous calibration data (it is important to start with a clean slate for accurate measurements).

![](stuff/images/cal_menu_select_reset.jpg)

Select "Calibrate" to start the calibration process.

![](stuff/images/cal_menu_select_calibrate.jpg)

Connect PORT1 to the "Open" calibration standard on the umsakazo board, then select "Open" on the NanoVNA screen to perform the open calibration step.

![](stuff/images/open.jpg)

Next, connect PORT1 to the "Short" calibration standard on the umsakazo board, then select "Short" on the NanoVNA screen to perform the short calibration step.

![](stuff/images/short.jpg)

Next, connect PORT1 to the "Load" calibration standard on the umsakazo board, then select "Load" on the NanoVNA screen to perform the load calibration step.

![](stuff/images/load.jpg)

Next, connect PORT1 (left) and PORT2 (right) to the "Thru" calibration standard on the umsakazo board, then select "Thru" on the NanoVNA screen to perform the thru calibration step.

![](stuff/images/thru.jpg)

Select "Done" to complete the calibration process.

![](stuff/images/donecal.jpg)

Select SAVE 0 to save your calibration.

![](stuff/images/save0.jpg)

Select "S11 SMITH" from the top-left corner of the screen to display the S11 parameter on the Smith chart. The S11 green rectangle should be selected.

![](stuff/images/selectsmith.jpg)

Connect the RC Series demo component on the umsakazo board to PORT1, and you should see the S11 response on the Smith chart.

![](stuff/images/demo_rc.jpg)

In an RC series circuit, the impedance changes with frequency. At low frequencies, the capacitor acts as an open circuit (right). As frequency increases, the capacitor's reactance decreases, allowing current to flow more easily, and the impedance moves toward the 50-ohm center point. Since the 50-ohm resistor remains constant (aprox) while the capacitor's reactance decreases with frequency, the impedance traces a semicircle from the open-circuit point toward the ~50-ohm point.

Note: not all time is exactly 50 ohms, as the components and PCB design introduce variations, but you should see the general behavior of the RC series circuit on the Smith chart.

Now, you can use the cursor 1 to analyze the response. Press on the 1 cursor to select it, then use stick to move it around the Smith chart and observe how the S11 parameter changes with frequency. 

![](stuff/images/demo_rc_move_curs.jpg)

REMEMBER: Every time you change the frequency range, you must recalibrate your NanoVNA to obtain accurate results. Calibration compensates for losses and characteristics of your measurement system, ensuring that your results are as precise as possible within the limitations of the PCB design and components used.

# Your second demo: SWR S11 - 33 ohm

![](stuff/images/33gen.jpg)

Recalibrate your NanoVNA for the new frequency range: 1 MHz - 100 MHz, and perform the same calibration steps as before: Reset CAL, (Open, Short, Load, Thru) to ensure accurate measurements for the 33 ohm demo.

Select DISPLAY from the main menu to enter the display settings.

![](stuff/images/main_menu_select_display.jpg)

Connect PORT1 to the 33 ohm demo component on the umsakazo board, and you should see the S11 response on the screen.

![](stuff/images/demo_33.jpg)

Select TRACE from the display menu to configure the trace settings.

![](stuff/images/display_menu.jpg)

Select TRACE3 to configure the settings for the third trace.

![](stuff/images/trace_menu_select_trace3.jpg)

Select FORMAT to change the display format for the trace.

![](stuff/images/display_menu_select_format.jpg)

Select SWR to display the Standing Wave Ratio (SWR) for the S11 parameter.

![](stuff/images/format_menu_select_swr.jpg)

Select S11 (REFL) to display the S11 parameter for the SWR trace.

![](stuff/images/select_s11.jpg)

Now you should see the SWR response for the 33 ohm demo on the screen. The 1.5:1 SWR line indicates the point where the impedance is 33 ohms, which is a mismatch from the 50-ohm reference impedance. Is 1.5:1 because 33 ohms is 1.5 times less than 50 ohms (50/33 ≈ 1.5). The SWR will be higher at frequencies where the impedance mismatch is greater, and it will approach 1:1 at frequencies where the impedance is closer to 50 ohms.

![](stuff/images/swr.jpg)

# Your third demo: S21 LOGMAG - Band Stop

![](stuff/images/band_stop_gen.jpg)

Recalibrate your NanoVNA for the new frequency range: 1 MHz - 9 MHz, and perform the same calibration steps as before: Reset CAL, (Open, Short, Load, Thru) to ensure accurate measurements for the Band Stop demo.

Connect PORT1 to the input (left) and PORT2 to the output (right) of the Band Stop demo component on the umsakazo board, and you should see the S21 response on the screen.

![](stuff/images/band_stop.jpg)

Now you can view the S21 LOGMAG response for the Band Stop demo. The S21 parameter represents the transmission coefficient, and in a band stop filter, you should see a drop in the S21 magnitude at the frequencies where the filter is designed to attenuate signals. The LOGMAG format displays the magnitude of S21 in decibels (dB), making it easier to visualize the attenuation effect of the band stop filter.

![](stuff/images/band_stop_prob.jpg)

Select S21 LOGMAG UP RIGHT SCREEN RECTANGLE.

![](stuff/images/select_s21.jpg)

Move cursor 1 to analyze the S21 response. You should see the frequency and magnitude values for the point where the cursor is located, allowing you to identify the center frequency of the band stop filter and the amount of attenuation it provides at that frequency.

![](stuff/images/band_stop_cursor.jpg)

Select DISPLAY from the main menu to enter the display settings again.

![](stuff/images/main_menu_select_display.jpg)

Select SCALE to adjust the scale settings for the S21 LOGMAG trace.

![](stuff/images/display_menu_select_scale.jpg)

Select 2. 

![](stuff/images/scale.jpg)

Now you should see the S21 LOGMAG response for the Band Stop demo with a scale of 2 dB per division, allowing you to better visualize the attenuation effect of the band stop filter across the frequency range.

![](stuff/images/result_scale.jpg)

# Frequency Range and S-Parameters

The NanoVNA is a versatile vector network analyzer that can measure S-parameters (Scattering parameters) across a wide frequency range. S-parameters describe how RF signals behave in a network, such as reflection and transmission. The umsakazo board provides various components for testing, including resistors, capacitors, inductors, and attenuators.

# Measurement Frequency Ranges

| Demo | Frequency Range | Measurement Type |
|-----------|-----------------|------------------|
| 33 ohm | 1 MHz - 100 MHz | SWR S11 |
| 75 ohm | 1 MHz - 100 MHz | SWR S11 |
| -5 dB | 1 MHz - 9 MHz | S21 LOGMAG |
| -10 dB | 1 MHz - 9 MHz | S21 LOGMAG |
| C | 1 MHz - 250 MHz | SMITH S11 |
| L | 1 MHz - 100 MHz | SMITH S11 |
| RC Series | 1 MHz - 250 MHz | SMITH S11 |
| LC Series | 1 MHz - 30 MHz | SMITH S11 |
| RLC Series Parallel | 1 MHz - 800 MHz | SMITH S11 |
| RLC Parallel-Series | 1 MHz - 800 MHz | SMITH S11 |
| High Pass | 1 MHz - 40 MHz | S21 LOGMAG |
| Low Pass | 1 MHz - 80 MHz | S21 LOGMAG |
| SAW | 300 MHz - 460 MHz | S21 LOGMAG |
| Band Stop | 1 MHz - 9 MHz | S21 LOGMAG |

![](stuff/images/front_freqs.jpg)

Note: you must calibrate your NanoVNA before performing measurements using the CAL zone.

Use outside of these ranges may not yield accurate results, just use it for fun and learning, not for precision measurements. 

Since each PCB and component set will be slightly different, I've left a white rectangle on each demo section where you can write or place a sticker with the exact frequency range that works best for your board. Variation between boards shouldn't be significant, but you may need to fine-tune the range slightly based on your specific components and PCB characteristics.

# S11 SMITH - CAPACITOR DEMO 

![](stuff/images/democap.jpg)

Just a capacitor connected to GND on one side and PORT1 on the other. You can use it to see how a capacitor behaves across different frequencies, and how it affects the S11 parameter on the Smith chart.

A capacitor to ground starts near the right side of the Smith chart because, at low frequency, its impedance is very high, so it behaves almost like an open circuit and reflects most of the signal. As the frequency increases, the capacitor impedance gets lower, so more signal is pulled to ground and the S11 trace moves clockwise along the lower outer edge, which is the capacitive region. The thick line ends closer to the left side because, in that part of the sweep, the capacitor is acting more and more like a short to ground. If the trace later bends or makes loops, that is usually caused by real-world parasitic inductance and resistance, not by an ideal capacitor.

# S11 SMITH - INDUCTOR DEMO

![](stuff/images/demoind.jpg)

Just an inductor connected to GND on one side and PORT1 on the other. You can use it to see how an inductor behaves across different frequencies, and how it affects the S11 parameter on the Smith chart.

An inductor to ground starts near the left side of the Smith chart because, at low frequency, its impedance is very small, so it behaves almost like a short to ground. As the frequency increases, the inductor impedance becomes higher, so it pulls less signal to ground and the S11 trace moves through the upper part of the chart, which is the inductive region. The thick line ends closer to the right side because, at higher frequency, the inductor looks more and more like an open circuit. If the trace later bends or makes loops, that usually comes from real parasitic capacitance and resistance, not from an ideal inductor.

# S11 SMITH - RC SERIES DEMO

![](stuff/images/rcseries.jpg)

A resistor and capacitor in series between PORT1 and GND. You can use it to see how a simple RC series circuit behaves across different frequencies, and how it affects the S11 parameter on the Smith chart.

A capacitor in series with a 50 ohm resistor starts near the right side of the Smith chart because, at low frequency, the capacitor blocks the signal and the circuit looks almost like an open circuit. As the frequency increases, the capacitor reactance gets smaller, so the 50 ohm resistor becomes more visible to the source and the S11 trace moves through the lower part of the chart, which is the capacitive region. The thick line ends closer to the center because, in that part of the sweep, the capacitor is no longer blocking much and the circuit looks closer to a good 50 ohm match, so the reflection becomes smaller.

# S11 SMITH - LC SERIES DEMO

![](stuff/images/capinducdemo.jpg)

A capacitor and inductor in series between PORT1 and GND. You can use it to see how a simple LC series circuit behaves across different frequencies, and how it affects the S11 parameter on the Smith chart.

A series capacitor and inductor start near the right side of the Smith chart because, at low frequency, the capacitor dominates and the whole network looks almost like an open circuit. As frequency increases, the capacitive reactance gets smaller, so the trace moves along the lower outer edge until it reaches the left side, where the capacitor and inductor cancel each other and the circuit looks like a short circuit at resonance. Above that frequency, the inductor becomes dominant, so the trace continues through the upper outer edge and moves back toward the right side.

# S11 SMITH - RLC SERIES PARALLEL DEMO

![](stuff/images/capserandrlpar.jpg)

Just a capactor in series with a parallel combination of a resistor and inductor, between PORT1 and GND. You can use it to see how a more complex RLC circuit behaves across different frequencies, and how it affects the S11 parameter on the Smith chart.

This network starts near the right side of the Smith chart because, at low frequency, the series capacitor blocks the signal and the input looks almost like an open circuit. As frequency increases, the capacitor reactance gets smaller, so the shunt branch becomes visible, and since the inductor to ground looks very low impedance at first, it pulls the trace toward the left side like a near short. Then the curve bends inward and makes a loop because the 50 ohm resistor in parallel is always there, preventing a perfect short and damping the movement. At higher frequency, the inductor looks less like a short and more like an open circuit, while the capacitor looks more like a wire, so the circuit moves closer to the behavior of a simple 50 ohm load and the trace comes back toward the center.

# S11 SMITH - RLC PARALLEL-SERIES DEMO

![](stuff/images/demoparrandcapl.jpg)

Just a parallel combination of resistor and a capacitor in series with an inductor, between PORT1 and GND. You can use it to see how a more complex RLC circuit behaves across different frequencies, and how it affects the S11 parameter on the Smith chart.

This network starts near the center of the Smith chart because, at low frequency, the series capacitor blocks the LC branch, so the input mainly sees the 50 ohm resistor to ground, which is a good match. As the frequency increases, the LC branch starts to conduct and pulls the trace away from the center; below resonance it behaves like a capacitive shunt, so the curve moves through the lower half. At resonance, the series capacitor and inductor cancel each other, so that branch becomes almost a short to ground and the trace reaches the left side. Above resonance, the branch becomes inductive and its impedance rises again, so its effect becomes weaker and the trace comes back toward the center.

# S11 SWR - 33 OHM & 75 OHM DEMO

![](stuff/images/swrdemos.jpg)

Just a 33 ohm and 75 ohm resistor connected between PORT1 and GND. You can use them to see how different resistive loads affect the S11 parameter and the SWR (Standing Wave Ratio) on the NanoVNA.

A 75 ohm resistor and a 33 ohm resistor can both give about the same SWR in a 50 ohm system because SWR depends on how much the load differs from 50 ohms, not on whether the resistance is higher or lower. A 75 ohm load is above 50 ohms, so its point appears to the right of center, while a 33 ohm load is below 50 ohms, so its point appears to the left, but both are nearly the same distance from the center of the Smith chart. That means they produce nearly the same reflection magnitude, so the SWR is about 1.5 in both cases. Strictly speaking, the exact value symmetric to 75 ohms is 33.3 ohms, so 33 ohms is just a rounded practical example.

The SWR value of 1.5 comes from the reflection coefficient in a 50 ohm system. For a purely resistive load, the reflection coefficient is ((Z_L - 50)/(Z_L + 50)). With 75 ohms, this gives (25/125 = 0.2), and the SWR becomes ((1 + 0.2)/(1 - 0.2) = 1.5). A resistor below 50 ohms gives the same SWR if it creates the same reflection magnitude in the opposite direction. That is why 75 ohms and about 33.3 ohms are symmetric cases on the Smith chart: one is to the right of center, the other is to the left, but both are the same distance from the center, so both give the same SWR.

# S21 LOGMAG - HIGH PASS DEMO

![](stuff/images/highpassdemo.jpg)

Just connect PORT1 (left) to the input and PORT2 (right) to the output of the high pass filter demo on the umsakazo board. You can use it to see how a simple high pass filter behaves across different frequencies, and how it affects the S21 parameter in LOGMAG format on the NanoVNA.

This circuit is a high-pass filter built as a pi network, with one capacitor in series and one inductor to ground on each side, and that is why the S21 log magnitude curve starts low, rises through the transition region, and then becomes nearly flat. The series capacitor is the main part that blocks low-frequency signals and lets higher-frequency signals pass, while the two shunt inductors help remove unwanted low-frequency energy by giving it a path to ground from both sides of the network. Using two inductors instead of just one makes the filtering stronger and cleaner, improves the shape of the response, and helps the filter behave better between the input and output ports. At low frequency, the capacitor is hard to pass through and the inductors load the signal, so very little reaches the output. As frequency increases, the capacitor becomes easier to pass through and the inductors stop pulling the signal down as much, so transmission increases. Once the signal is in the passband, the network no longer blocks it much, so S21 stays high and the trace looks almost flat.

# S21 LOGMAG - LOW PASS DEMO

![](stuff/images/lowpassdemo.jpg)

Just connect PORT1 (left) to the input and PORT2 (right) to the output of the low pass filter demo on the umsakazo board. You can use it to see how a simple low pass filter behaves across different frequencies, and how it affects the S21 parameter in LOGMAG format on the NanoVNA.

This circuit is a low-pass filter built as a pi network, with one inductor in series and one capacitor to ground on each side, and that is why the S21 log magnitude trace starts high, then rolls off, and finally becomes very low at higher frequency. The series inductor lets low-frequency signals pass more easily, but as frequency increases it starts to oppose the signal more and more, reducing transmission. At the same time, the two shunt capacitors give high-frequency energy a path to ground from both sides of the network, so less of that signal reaches the output. Using two capacitors instead of just one makes the filtering stronger, improves the shape of the response, and helps the filter behave better between the input and output ports. That is why low frequencies pass with little loss, while higher frequencies are increasingly attenuated.

# Band Stop Filter DEMO

![](stuff/images/bandstopdemo.jpg)

Just connect PORT1 (left) to the input and PORT2 (right) to the output of the band stop filter demo on the umsakazo board. You can use it to see how a simple band stop filter behaves across different frequencies, and how it affects the S21 parameter in LOGMAG format on the NanoVNA.

This circuit is a band-stop, or notch, filter, so the S21 log magnitude trace starts high, drops sharply in the reject band, and then rises again after that frequency range. The two capacitors form the main signal path between the input and output, and they also work together with the inductor to create the notch. The inductor to ground is the part that removes energy at the stop frequency, because at that point the LC network resonates and the signal is strongly diverted away from the output. Away from resonance, that shunt path is much less effective, so the signal can pass again and S21 goes back up. The resistor across the network helps control the shape and depth of the notch, makes the response smoother, and helps the filter behave more predictably between the two ports.

# S21 LOGMAG - Band Pass 433MHz SAW DEMO 

![](stuff/images/sawdemo.jpg)

Just connect PORT1 (left) to the input and PORT2 (right) to the output of the SAW filter demo on the umsakazo board. You can use it to see how a simple band pass filter behaves across different frequencies, and how it affects the S21 parameter in LOGMAG format on the NanoVNA.

This band-pass filter uses a SAW device, which means Surface Acoustic Wave. Inside it, the electrical signal is converted into a very small mechanical wave that travels across a piezoelectric material, and then it is converted back into an electrical signal at the output. It works because the internal metal patterns are designed so that only a narrow range of frequencies creates the right acoustic wave and passes through efficiently, while frequencies above and below that range are strongly attenuated. That is why the S21 trace is low outside the passband, rises sharply in the wanted band, and then falls again. The main advantage of a SAW filter is that it gives very selective filtering in a very small part, so it is excellent for separating one RF band from nearby unwanted signals. It is widely used because it is compact, stable, and gives much better selectivity than a simple LC network of similar size.

# Attenuator DEMO

![](stuff/images/attsdemo.jpg)

Just connect PORT1 (left) to the input and PORT2 (right) to the output of the attenuator demo on the umsakazo board. You can use it to see how a simple attenuator behaves across different frequencies, and how it affects the S21 parameter in LOGMAG format on the NanoVNA.

These two circuits are resistive attenuators, so their S21 trace is almost a flat horizontal line because resistors do not filter one frequency more than another in the ideal case. The resistor in series reduces the signal that can go straight from input to output, and the two resistors to ground remove part of the signal energy while also helping the circuit stay close to the system impedance, so the source and load still see a good match. In the -5dB version, the resistor values are chosen so only part of the signal is lost, which is why the line stays a little below the top. In the -10dB version, the values make the attenuation stronger by reducing the direct path more and sending more energy to ground, so the line appears lower. In simple terms, both circuits do the same job, but the second one throws away more signal than the first one.

# PCB Design Limitations

The umsakazo board is designed with simplicity and affordability as key priorities. The design philosophy focuses on:

- **Simple Bill of Materials (BOM)** - Common, readily available components that are easy to source
- **Cost-effective PCB** - Optimized for educational use without unnecessary complexity
- **Easy component replacement** - 0805 SMD components can be quickly swapped to experiment with different values and behavior
- **Accessible learning tool** - Designed for students and hobbyists to learn RF fundamentals without expensive equipment

This approach prioritizes hands-on learning and experimentation over precision, making the board an excellent platform for understanding RF concepts and component behavior.

The board uses 0805 SMD components, which are not ideal for high-frequency due to their parasitic effects.

The PCB design is not optimized for high-frequency measurements. As a standard FR4 board without strict impedance control, several factors affect measurement accuracy:

- **Parasitic effects** from the 0805 SMD components introduce unwanted inductance and capacitance
- **Board material** and trace routing introduce loss and phase shift
- **Lack of impedance matching** between components and traces
- **Component placement** affects signal integrity at higher frequencies

These limitations are inherent to the learning board design and should be considered when interpreting results, especially above the recommended frequency ranges. This is ideal for educational purposes and experimentation, not for precision RF measurements.

The coplanar waveguide design is used for the RF traces, which provides a simple and cost-effective way to route high-frequency signals on a PCB. However, it is not optimized for high-frequency performance, and the lack of proper impedance control can lead to signal degradation and inaccurate measurements at higher frequencies.

# DIY BNC CALIBRATION KIT 50 OHM

**WARNING**: THIS SECTION IS STILL UNDER CONSTRUCTION AND TESTING. THERE MAY BE ERRORS, INCORRECT MEASUREMENTS, ETC. FOR NOW, THIS IS JUST FOR MY OWN USE.

**NOTE 1**: values shown by the NanoVNA in formats such as R+L/C should be treated as **equivalent models**, not as proof of the exact physical parasitics of the standard.

**NOTE 2**: Using **electrical delay** can help move the reference plane and partially compensate adapters or extra connector length, but it does not magically remove all the non-ideal behavior of the standard. It is a practical aid, not a perfect correction.

In this section, I will document different attempts so you can build your own DIY MALE calibration kits with BNC connectors. The goal is for them to work up to 1 GHz.

Why not just buy a commercial calibration kit? Because they are expensive, and I want to learn how to make my own. Also, the DIY approach allows for customization and experimentation, which is valuable for learning.

Expensive DC–10 GHz (or more) calibration kits:

- Maury Microwave 8550CK10 ~6000€
- Fairview Microwave FMCK1024 ~8000€
- Pasternack PE5CK1024 ~9000€ 

![](stuff/images/expensivekits.jpg)

These calibration kits are expensive because you are not just buying metal connectors, but precisely characterized standards. They can include data such as delay, parasitic capacitance or inductance, offset length, loss, or even full S-parameter files for each standard, so the VNA knows how the open, short, and load really behave across frequency. That data lets the VNA correct its own systematic measurement errors and produce much more accurate results.

**NOTE**: There is a cheaper option for 600 MHz:  "SDR-Kits BNC 4-pc Universal Calibration Kit" ~27€ (but I dont know if it is good or not, I have not tested it yet)

For the first tests, I calibrated the NanoVNA on the SMA connectors, then connected an SMA-to-BNC adapter to test the BNC connectors.

![](stuff/images/diycalsetup.jpg)

The SMA-BNC adapter I will use is the ADP-SMAF-BNCF from RF Solutions:

![](stuff/images/adapters.jpg)

https://www.rfsolutions.co.uk/content/download-files/ADP-SMAF-BNCF-DATASHEET.pdf

| Feature | Specification |
|---------|---------------|
| Frequency Range | DC-3GHz |
| Voltage Standing Wave Ratio | ≤1.15 |
| Impedance | 50Ω |
| Temperature Range | -55~+155oC |
| Centre Conductor Retention Range | ≥0.28N |
| Coupling nut Retention Force | ≥180Nq |
| Insertion Loss | ≤0.1dB/3GHz |
| Durability (mating) | >500 Cycles |
| Insulation Resistance | ≥5000MΩ |
| Working Voltage | 355Vrms |
| Max Voltage (can withstand) | 1000Vrms |

An electronic delay of about 225 ps will be used on the NanoVNA to extend the reference plane.

I calibrated from 100 MHz to 1 GHz.

First, we will measure a higher-quality and more expensive 50-ohm RF load than what should result from our DIY kit: 65_BNC-50-0-6/113_NE from HUBER+SUHNER.

![](stuff/images/goodload.jpg)

https://www.hubersuhner.com/Asset/eyJpZGVudGlmaWVyIjo3ODgyNCwidHlwZSI6ImFzc2V0In0/Hee_P8STgA3T8IfP/H%2BS_65_BNC-50-0-6113_N_EN.PDF

| Feature | Specification |
|---------|---------------|
| Impedance | 50Ω |
| Operating frequency | 0 GHz ... 4 GHz |
| VSWR | 1.15 |
| Return loss | 23.1 dB |

Electrical Data (frequency related):

| Frequency range | VSWR max |
|---------|---------------|
| 0 GHz to 3 GHz | 1.1 |
| 3 GHz to 4 GHz | 1.15 |

![](stuff/images/goodloadinvna.jpg)

------

We are not using THRU calibration for this section, but I keep these THRU adapters on hand for when I need them:

BNC FEMALE-FEMALE R141704000 from Radiall:

http://radiall-files.s3.amazonaws.com/tds/coaxialconnectors/R141704000%20C.pdf

![](stuff/images/bncfemfem.jpg)

| Parámetro                      | Valor                          |
|--------------------------------|--------------------------------|
| Impedance                      | 50 Ω                           |
| Frequency                      | 0–4 GHz                        |
| VSWR                           | 1.25 + 0.0000 × F(GHz) Max     |
| Insertion loss                 | 0.115 × √F(GHz) dB Max         |
| RF leakage                     | -(57 - F(GHz)) dB Max          |
| Voltage rating                 | 500 Veff Max                   |
| Dielectric withstanding voltage| 1500 Veff min                  |
| Insulation resistance          | 5000 MΩ min                    |

------

BNC MALE-MALE R141703000 from Radiall:

https://www.radiall.com/download/ds/index/f/aHR0cHM6Ly9yYWRpYWxsLWZpbGVzLnMzLmFtYXpvbmF3cy5jb20vdGRzL2NvYXhpYWxjb25uZWN0b3JzL1IxNDE3MDMwMDAgVi5wZGY~/

![](stuff/images/bncmalemale.jpg)

| Parameter | Value | Notes |
|-----------|-------|-------|
| NOMINAL IMPEDANCE | 50 | Ω |
| FREQUENCY RANGE | 0-4 | GHz |
| TEMPERATURE RATING | -65/+165 | °C |
| V.S.W.R | 1.25 + | x F(GHz) Maxi |
| RF INSERTION LOSS | 0.115 √F(GHz) | dB Maxi |
| VOLTAGE RATING | 500 | Veff Maxi |
| DIELECTRIC WITHSTANDING VOLTAGE | 1500 | Veff Mini |
| INSULATION RESISTANCE | 5000 | MΩ Mini |
| MECHANICAL DURABILITY | 500 | Cycles |

------

BNC FEMALE-MALE PE9269 from Pasternack:

https://www.pasternack.com/images/ProductPDF/PE9269.pdf

![](stuff/images/bncfemmale.jpg)

| Description | Minimum  | Maximum | Units |
|-------------|--------- |---------|-------|
| Frequency Range | DC  | 4 | GHz |
| VSWR | |1.3:1 |    |
| Operating Voltage (AC)   | | 500 | Vrms |

------


## 65_BNC-50-0-6/113_NE with e-delay, at 1 GHz:

![](stuff/images/herbedelay1.jpg)

56,2 ohm 23.0pF -21,16 dB 

-----

## 65_BNC-50-0-6/113_NE with e-delay, at 604 MHz:

![](stuff/images/herbedelay604.jpg)

51,6 ohm 45.2pF -24,53 dB

-----

## 65_BNC-50-0-6/113_NE with e-delay, at 316 MHz:

![](stuff/images/herbedelay316.jpg)

49,4 ohm 143pF -28,89 dB

-----

## DIY MALE LOAD

Aliexpress RF 50 ohm BNC Panel Mount:

![](stuff/images/aliexpresbncdiy.jpg)

Cut off the protruding part with a Dremel:

![](stuff/images/dremecut.jpg)

Sand it down to remove the protruding part (I’m not sure this was a good idea for the short and the open...):

![](stuff/images/polish.jpg)

Then make a LOAD, a SHORT, and an OPEN:

![](stuff/images/diykit.jpg)

Soldering to the outer part is difficult: patience, flux, and heat are required...

The load uses 3 RESI PTFR0603A150RP9 0603 thin-film resistors of 150 ohms ±0.05% in parallel, giving 50 ohms:

https://www.lcsc.com/datasheet/C19683979.pdf

The reason for using three in parallel and thin film is to try to reduce parasitic inductance, although I’m not sure whether I achieved that...

The result is pretty ugly and questionable xD, but it’s the first attempt:

![](stuff/images/diybncload.jpg)

## Low-frequency 4-wire/Kelvin LCR sanity check with DE-5000:

Low-frequency 4-wire/Kelvin LCR sanity check
Measured with a DE-5000 at 1 kHz using the TL-22 4-wire SMD tweezers. The DIY load measured 49.99 Ω with 0.0° phase, confirming that it behaves as an essentially ideal 50 Ω resistive load at low frequency.

![](stuff/images/derimg.jpg)

-----

## DIY MALE LOAD with e-delay, at 1 GHz:

![](stuff/images/diy1.jpg)

52,8 ohm 52.9pF -27.98 dB

-----

## DIY MALE LOAD with e-delay, at 604 MHz:

![](stuff/images/diy604.jpg)

50,7 ohm 48.2pF -25.24 dB

-----

## DIY MALE LOAD with e-delay, at 316 MHz:

![](stuff/images/diy316.jpg)

49,5 ohm 140pF -28.78 dB

-----

## Shorts

## Short BNC Male R141862000 from Radiall

https://www.mouser.es/datasheet/3/512/1/R141862000%20V.pdf

![](stuff/images/shortrf.jpg)


## SHORT R141862000 from Radiall with e-delay, at 1 GHz:

![](stuff/images/shortdelayrd1.jpg)

-106 mohm 477pH 0.04 dB

-----

## SHORT R141862000 from Radiall with e-delay, at 604 MHz:

![](stuff/images/shortdelayrd604.jpg)

-41.3 mohm 166pH  0.01 dB

-----

## SHORT R141862000 from Radiall with e-delay, at 316 MHz:

![](stuff/images/shortdelayrd316.jpg)

-9.85 mohm 16.0pH 0 dB

-----

## Aliexpress BNC Male Short

![](stuff/images/aliexpshort.jpg)

![](stuff/images/aliexpmaleshort.jpg)

## AliExpress short with e-delay, at 1 GHz:

![](stuff/images/shortdelayaliex1.jpg)

-120 mohm 554pH -0.04 dB

-----

## AliExpress short with e-delay, at 604 MHz:

![](stuff/images/shortdelayaliex604.jpg)

-97.8 mohm 226pH -0.03 dB

-----

## AliExpress short with e-delay, at 316 MHz:

![](stuff/images/shortdelayaliex316.jpg)

-151 mohm 89.1pH -0.04 dB

-----

## Open SC2008 BNC Male Open Circuit de Fairview Microwave

![](stuff/images/goodopen.jpg)

https://www.fairviewmicrowave.com/content/dam/infinite-electronics/product-assets/fairview-microwave/product-datasheets/SC2008.pdf?srsltid=AfmBOook1h7uDH7ZRd-_MdugQZYOZbGFYhvBcQH1GOCpUhCFNz_ZfDrP

The results are basically the same as leaving it open in air with nothing attached, so there is no point in adding more photos or information. Obviously, this is not a calibration open; it is meant to keep dust out of a BNC connector xD.

## My DIY MALE Open and DIY MALE Short were terrible

I must have done something wrong, maybe while soldering, sanding... or something else.

## Terrible DIY MALE OPEN 

![](stuff/images/diyopenpo.jpg)

![](stuff/images/dyopenvna.jpg)

At 604 MHz with e-delay: 10.9 ohms and 1.53 pF -0.29 dB

-----

## Terrible DIY MALE SHORT

![](stuff/images/diyopenshort.jpg)

![](stuff/images/diyshortcr.jpg)

At 604 MHz with e-delay: 9.38 ohms and 3.70 nH -3.04 dB

------

So it is better to use the SC2008 as OPEN (or nothing), and the AliExpress BNC short.

## Better DIY MALE OPEN & SHORT - second attempt

We deserve a better DIY male open & short, second attempt.

I bought some typical PCB-mount BNC male connectors from AliExpress and eBay. Using pliers and scissors, I removed the protruding pins as best I could. I didn't sand them or do anything else, so they aren't perfectly flush.

![](stuff/images/alicdinm.jpg)

Here's how the open looks:

![](stuff/images/opennewtry.jpg)

And here are the shorts:

![](stuff/images/newshortstry.jpg)

Note: You'll need heat and patience to solder well to the outer shell.

The open... meh... I'm still not happy with it:

![](stuff/images/reulsnewopen.jpg)

The short is better than the previous disaster, but I still don't like it (especially compared to the AliExpress short):

![](stuff/images/newsdhorttry.jpg)

At 604 MHz with e-delay, the short measures 172 mΩ, 1.92 nH, and -0.06 dB.

## DIY MALE BNC Kit Conclusions

### The DIY MALE Load works remarkably well

The three 150 Ω thin-film 0603 resistors, soldered in a star pattern directly onto the BNC panel-mount connector, produce results very close to the HUBER+SUHNER 65_BNC-50-0-6/113_NE commercial load up to 600 MHz. At 316 MHz, the DIY load measures 49.5 Ω versus 49.4 Ω for the commercial reference; at 604 MHz, it measures 50.7 Ω versus 51.6 Ω. Even at 1 GHz, the DIY load remains surprisingly close, measuring 52.8 Ω versus 56.2 Ω for the commercial unit. The NanoVNA also shows more equivalent capacitive behavior in the DIY version at 1 GHz (52.9 pF versus 23.0 pF), but the return loss is still very good: -27.98 dB for the DIY load versus -21.16 dB for the commercial one. For me, this is the main win of the project: 

This DIY load, which costs only about 3 EUR, achieves 1 GHz performance that is remarkably close to a commercial 50-ohm load (4 GHz, 1 GHz:VSWR 1.1, 23.1 dB) costing over 30 EUR.

### The DIY MALE Short and Open were a failure

(Maybe?) Cutting the BNC panel-mount connector with a Dremel and sanding it down destroyed the RF geometry. The DIY open measured 10.9 Ω at 604 MHz (should be near-infinite impedance) and the DIY short measured 9.38 Ω (should be near-zero). 

### Cheap commercial shorts are good enough

The AliExpress BNC male short measured -97.8 mΩ / 226 pH at 604 MHz and -120 mΩ / 554 pH at 1 GHz.

### Open standard: just leave the connector open

The Fairview SC2008 BNC open-circuit cap showed no meaningful difference compared to leaving the connector open with nothing attached. For this DIY setup, leaving the connector open was the cheapest and most practical open.

### Recommended budget DIY MALE BNC calibration kit

| Standard | Solution | Approx. cost |
|----------|----------|-------------|
| LOAD | BNC panel-mount (DC–1GHz or more) + 3 × 150 Ω 0603 thin-film PTFR0603A150RP9 in star | ~3 EUR |
| SHORT | BNC male short from AliExpress | ~2–3 EUR |
| OPEN | Nothing (air) | 0 EUR |
| SMA-BNC adapter | ADP-SMAF-BNCF or equivalent (DC–3 GHz) | ~5 EUR |
| **Total** | | **~10–15 EUR** |

If your goal is learning, debugging, comparing parts, checking cables, and doing affordable RF experiments, this DIY BNC kit is useful.

If your goal is accurate calibration with known standard parameters, then a proper commercial calibration kit is still the choice.

# EXPERIMENT WITH DIY MALE BNC CALIBRATION KIT

Now let's do the opposite: we will calibrate the NanoVNA from scratch using our DIY BNC kit (first attaching the SMA-BNC adapter), and then measure the NanoVNA's SMA calibration kit to see how it performs. (After calibrating, we'll need to add an SMA-BNC adapter (+edelay) to connect the short, load, and open standards from the SMA calibration kit.)

So, for CALIBRATION, we will use:

NanoVNA SMA -> ADP-SMAF-BNCM -> DIY BNC CALIBRATION KIT

So, for MEASUREMENT, we will use (+edelay):

NanoVNA SMA -> ADP-SMAF-BNCM -> ADP-SMAF-BNCF -> SMA CALIBRATION KIT

![](stuff/images/expiremtn1.jpg)

**NOTE:** Cross-check: calibrating with the DIY BNC kit and then measuring an independent SMA kit gives a practical consistency check, but this is not a formal validation because adapters and standard re-measurement limit the interpretation.

We will calibrate from 100 MHz to 1 GHz using the DIY MALE BNC kit with the SMA-BNC adapter ADP-SMAF-BNCF.

- LOAD: DIY BNC MALE 50 OHM
- SHORT: BNC SHORT ALIEXPRESS 
- OPEN: AIR

After calibrating in the BNC world, we will add a new ADP-SMAF-BNCM adapter from RF Solutions 

![](stuff/images/admapnew.jpg)

https://docs.rs-online.com/5e2e/A700000008303676.pdf

| Electrical Data | Detail |
|---|---|
| Impedance | 50 Ω |
| Frequency Range | 0 to 4 GHz |
| VSWR | ≤ 1.3 : 1 |
| Insulation Resistance | 5 000 MΩ min. |
| Voltage Rating | 500 V RMS |

| | Connector A | Connector B |
|---|---|---|
| Contact Resistance, Center | 2.0 mΩ max. | 2.0 mΩ max. |
| Contact Resistance, Outer | 2.0 mΩ max. | 2.0 mΩ max. |
| Insertion Loss | 0.06 dB max. x √f GHz | 0.2 dB max. @ 3 GHz |
| RF Leakage | -60 dB min. @ 3 GHz | -55 dB min. @ 3 GHz |

Next, we will adjust the electrical delay (edelay) 200 ps so that the reference plane is set at the tip of the ADP-SMAF-BNCM adapter.

Why do we add the ADP-SMAF-BNCM? This allows us to connect the NanoVNA's SMA calibration kit and check whether the short, open, and load standards behave the same as if we had calibrated directly with the SMA connector.

------

CAL OPEN (AIR)

------

CAL SHORT (ALIEXPRESS):

![](stuff/images/calshortaliex.jpg)

------

CAL LOAD (DIY MALE LOAD):

![](stuff/images/calloaddiymale.jpg) 

------

Add the ADP-SMAF-BNCM adapter:

![](stuff/images/newadaptedelay.jpg)

------

Adjust the edelay to 200 ps.

------

NanoVNA SMA SHORT CALIBRATION KIT:

![](stuff/images/smashortcomp.jpg)

------

NANOVNA SMA LOAD CALIBRATION KIT:

![](stuff/images/smaloadcomp.jpg)


# Design Files and Documentation

This PCB is released under the MIT License. All design files will be made available in the repository by the end of 2027. The repository will include:

- **Gerber files** - For PCB manufacturing
- **PCB layout files** - Complete board design
- **Pick & Place files** - Component placement coordinates for assembly
- **Bill of Materials (BOM)** - Complete list of components with part numbers
- **Schematic files** - Detailed electrical schematics

You are welcome to use these files to manufacture your own board, modify the design to suit your specific requirements, or adapt the project for educational and commercial purposes, as permitted by the MIT License.

# Future Improvements and Community Release

During 2026 and 2027, I will continuously optimize the Bill of Materials (BOM) to reduce costs while maintaining quality. **The final production release will be published once we achieve optimized component sourcing and cost-effective pricing.** Currently, material costs are higher than target, and we are working with suppliers to bring these down before the community release.

We welcome feedback from early adopters and users to enhance both the design and documentation. If you have suggestions, please open an issue. The final version will reflect community input and market-driven improvements to deliver maximum value.

If you would like to explore different design directions, feel free to fork the project and create your own version.

# Greetings

Gonzalo Carracedo @BatchDrake & Carlos Cabezas @EB4FBZ, who are true RF experts, and from whom I always learn so much through their critiques, comments, and conversations in the HardwareHackingES Telegram channel.

# Learn More

## Video 

- Resonance in AC Circuits Visualised | Series RLC Circuit, Resonant Frequency & Q Factor by Decipher Physics: https://www.youtube.com/watch?v=og6KsSDd644
- Impedance & Reactance (Full Visual Explanation) by Decipher Physics: https://www.youtube.com/watch?v=akVP_TF7jDI
- How to properly use a NanoVNA V2 Vector Network Analyzer & Smith Chart (Tutorial) by  Andreas Spiess: https://www.youtube.com/watch?v=_pjcEKQY_Tk
- Inverted-F PCB Antenna: How to tune PCB circuits using a NanoVNA by HB9BLA Wireless: https://www.youtube.com/watch?v=rbXq0ZwjETo
- What Effects Do Transmission Lines Have? by W0QE: https://www.youtube.com/watch?v=6458gZavAug
- What Effects Do Different Components Have? by W0QE: https://www.youtube.com/watch?v=79jbor_T9PU
- Back to Basics: What is a VNA / Vector Network Analyzer by w2aew: https://www.youtube.com/watch?v=Sb3q8f0NBZc
- NanoVNA Port Extension using the Electrical Delay setting by w2aew: https://www.youtube.com/watch?v=bEPUePy_buM
- NANOVNA Made Simple by IMSAI Guy: https://www.youtube.com/watch?v=QJYeFpiqY8c
- NANOVNA making BNC VNA calibration set by  IMSAI Guy: https://www.youtube.com/watch?v=I0kIH492DcY
- Building VNA Calibration Loads by W0QE: https://www.youtube.com/watch?v=NSAQ2iQNX2I
- The Reference Plane by W0QE: https://www.youtube.com/watch?v=xLGSblc-Fec
- Building VNA Calibration Loads - Revisited by W0QE: https://www.youtube.com/watch?v=-PK9Bn7Ixnw
- Transmission Line Terminations for Digital and RF signals - Intro/Tutorial by w2aew: https://www.youtube.com/watch?v=g_jxh0Qe_FY
- Smith Chart: Z, VSWR, Reflection Coef and Transmission Line Effects by w2aew: https://www.youtube.com/watch?v=ImNRca5ecF0
- Basics of the Smith Chart - Intro, impedance, VSWR, transmission lines, matching by w2aew: https://www.youtube.com/watch?v=TsXd6GktlYQ
- Why a VNA needs to be calibrated | how to calibrate a nanoVNA by w2aew: https://www.youtube.com/watch?v=x-tbvAbh9jk
- Use NanoVNA to measure coax length - BONUS Transmission Lines and Smith Charts, SWR and more by w2aew: https://www.youtube.com/watch?v=9thbTC8-JtA
- Debunking SWR Myths Once and For All! by TheSmokinApe Ham Radio: https://www.youtube.com/watch?v=5z6VnWC6V2g
- Understanding VNAs - Antenna Measurements by Rohde & Schwarz: https://www.youtube.com/watch?v=15-hd_JjmYY
- Understanding VSWR and Return Loss by Rohde & Schwarz: https://www.youtube.com/watch?v=BijMGKbT0Wk
- Understanding the Smith Chart by Rohde & Schwarz: https://www.youtube.com/watch?v=rUDMo7hwihs
- Understanding S Parameters by Rohde & Schwarz: https://www.youtube.com/watch?v=-Pi0UbErHTY 
- Understanding VNA Calibration Basics by Rohde & Schwarz: https://www.youtube.com/watch?v=bLfbg2p7PaE
- Understanding VNAs - Segmented Sweeps by Rohde & Schwarz: https://www.youtube.com/watch?v=XP4QBpu9MO0 
- Understanding VNAs - Cable Loss Measurements by Rohde & Schwarz: https://www.youtube.com/watch?v=xqLQH0eWs3E  
- Understanding VNAs - Cable Impedance Measurements by Rohde & Schwarz: https://www.youtube.com/watch?v=SaCH3Z7veNc
- nanoVNA - Alligator Clip Leads vs. VNA Test Fixture Kit - Measuring Inductors & Capacitors by Gregg Messenger - VE6WO: https://www.youtube.com/watch?v=Y2_aytTVvFw
- Alligator Test Leads and the NanoVNA by TheSmokinApe Ham Radio: https://www.youtube.com/watch?v=gzmrueSXteE
- NanoVNA 75 Ohm Calibration by The Volpe Firm, Inc: https://www.youtube.com/watch?v=X2a31PExqM0

## Doc

- Measurement and Application of Scattering Parameters in RF-Design by PROF. DR. THOMAS BAIER: [stuff/doc/HamRadio DG8SAQ 2013 English](stuff/doc/HamRadio_DG8SAQ_2013_English.pdf)
- RF engineering basic concepts: the Smith chart by F. Caspers - CERN, Geneva, Switzerland: [stuff/doc/p95.pdf](stuff/doc/p95.pdf)
- How to design your own BNC Female calibration Kit with verified performance:  [stuff/doc/How_to_design_your_own_BNC_Female_calibration_Kit_with_verified_performance.pdf](stuff/doc/How_to_design_your_own_BNC_Female_calibration_Kit_with_verified_performance.pdf)
- Characterizing a SMA calibration kit by Mario Hellmich: https://www.mariohellmich.de/projects/sma-cal-kit/sma-cal-kit.html

# People to follow 

- @therealdreg https://x.com/therealdreg
- https://www.youtube.com/@hardwarehackinges
- Gonzalo Carracedo @BatchDrake https://x.com/BatchDrake
- Carlos Cabezas @EB4FBZ https://x.com/eb4fbz
- Mehdi @MehdiHacks https://x.com/MehdiHacks
- https://www.youtube.com/@DecipherPhysics
- https://www.youtube.com/@AndreasSpiess
- https://www.youtube.com/@HB9BLA
- https://www.youtube.com/@w2aew
- https://www.youtube.com/@IMSAIGuy
- https://www.youtube.com/@TheSmokinApe
- https://www.youtube.com/@w0qe
- https://www.youtube.com/@ve6wo


