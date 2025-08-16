# M1_AC3E-Chile/README.md

Place the GDS file with the following nomenclature in this folder: M1_AC3E-Chile.gds --> Area estimation: 400um X 250um for main intrinsic blocks (no routing)

Pin list and pin description: https://docs.google.com/spreadsheets/d/1F9zDj1jvnRmzFUO-1ObZYb9zHFiqyZSlHh3pm4B81cA/edit?gid=1059496676#gid=1059496676 --> 19 pins (7 analog + 8 digital + 4 supply)

---

# M10_RAZAVUS/README.md

pin list : https://docs.google.com/spreadsheets/d/1ihq9DLaxf77A22eylFtpDfQRq1X3if69aSoamc0Y-gU/edit?usp=sharing

---

# M11_RF_MOSbius/README.md

Place the GDS file with the following nomenclature in this folder: M11_RF_MOSbius.gds

Also, update the README.md file to include the pin list and pin description.

Pin List:  
1: VDD (3.3V)  
2: VSS (Ground)  
3: DATA (Scan Chain Input)  
4: CLK (Scan Chain Clock)  
5: EN (Scan Chain Enable)  
6: REF (PLL Reference Frequency)  
7: EXT_PFD_REF (External Phase-Frequency Detector Reference Input)  
8: EXT_PFD_DIV (External Phase-Frequency Detector Divider Input)  
9: EXT_PFD_UP (External Phase-Frequency Detector Up Output)  
10: EXT_PFD_DOWN (External Phase-Frequency Detector Down Outpu)  
11: LOCK (Lock Detection)  
12: UP (Charge Pump Up Input)  
13: DOWN (Charge Pump Down Input)  
14: I_CP_100U (Charge Pump Reference Current, 100uA)  
15: FILTER_IN (Filter Input)  
16: FILTER_OUT (Filter Output)  
17: EXT_VCO_IN (External VCO Input)  
18: EXT_VCO_OUT (External VCO Output)  
19: DIV_IN (Divider Input)  
20: DIV_OUT (Divider Output)  
21: DIV_DEF (External Reset to Divider to Define Divider State)  
22: OUT (PLL Output)  

---

# M13_SpikCore/README.md

Place the GDS file with the following nomenclature in this folder: M13_SpikCore.gds

### The proposed pin list and pin description can be found [here](https://docs.google.com/spreadsheets/d/1vhMIvf8tOUEVN5lxGAr1D5x2heG8VZecuYUK63GFHpc/edit?usp=sharing)

---

# M15_XDAC/README.md

Here's a link to our chipathon pin list, which includes comments about revisions since the proposal:
https://docs.google.com/spreadsheets/d/10HO0HoQ3GUK976rmQ6aZCDh89Qx8e9ZePqYx5dRUv4g
We use a large number of pins to provide access to fundamental building blocks of larger transistor circuits, many of which we can remove while retaining the intended functionality of our chip

---

# M17_Onchip/README.md

GDS estimation area: M17_Onchip.gds

[Pin List](https://docs.google.com/spreadsheets/d/1hse_XdPZdaKd3ZbdsHfHNfzGuXlAMb_W/edit?usp=sharing&ouid=112236817285919892043&rtpof=true&sd=true)

[Pad frame](https://docs.google.com/presentation/d/1W0zZGZtBgGh6meqKxxQhfWxT1dJBS5Fr/edit?usp=sharing&ouid=112236817285919892043&rtpof=true&sd=true)

---

# M2_ChipOdyssey/README.md

Place the GDS file with the following nomenclature in this folder: M2_ChipOdyssey.gds

Also, update the README.md file to include the pin list and pin description.

[Pin List and Description]
Number of Pins:
Power
4 (Analog VDD, VSS, Digital VDD, VSS)
TIA
3 (V+, V-, Out)
Comparator
12 (V+, V-, Clk, Out, 8 offset correction) (will try to reduce offset correction pins with calibration circuit)
SAR Logic
9 (In, 6 digital out, 1 ready pin for clock cycles, 1 ready pin for full conversion cycle)
CDAC
3 (Vref, ADC reset, DAC out)
Switch Matrix
3 (1 between TIA and CDAC, 1 between CDAC and Comparator, 1 between Comparator and SAR Logic)
Total: 34 pins
Area Estimate: 600um x 400um
Used this paper as minimum estimate and added our approximate TIA and other component area: https://drive.google.com/file/d/191QjsD6ZHyCCeeVFDZAnm8slRRV7lbvb/view?usp=sharing 
Also added ADC gds file to submission

Link to Pin Padframe: https://docs.google.com/presentation/d/1M6atEBdrpoQDF44i9qx-kfYodAoFVWYvb3GMPAhebwY/edit?usp=sharing 

---

# M3_CreActive/README.md

# M3 CreActive GDS Submission

## Links
- [Pin Map](https://docs.google.com/spreadsheets/d/1_3lQBcbkPWE0qjfvSXVyYYxNycXKxWRLHg75SAif4VQ/edit?gid=530173844#gid=530173844)
- [Area Estimation](https://github.com/assaify/creactive-chipathon-2025/blob/main/docs/layout/README.md)

## External Pin

| Pin Type | IO Name | Main Function | Notes |
| :--- | :---: | :---: | :---: |
| **VDD** | VDD | 3.3 V Supply | |
| **VSS** | VSS | Ground | |
| **Digital** | DATA | Digital Input| |
| **Digital** | CLK | Digital Input| |
| **Digital** | RSTN | Digital Input| |
| **Analog** | A[0] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[1] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[2] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[3] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[4] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[5] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[6] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[7] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[8] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | A[9] | Analog GPIO| Connected to 39 x 10 switch matrix |
| **Analog** | I_BIAS_1 | Current Bias| Current bias for all 3 single ended OTA |
| **Analog** | I_BIAS_2 | Current Bias| Current bias for all 3 differential output OTA |

---

# M5_FPTA/README.md

Place the GDS file with the following nomenclature in this folder: M5_FPTA.gds

Also, update the README.md file to include the pin list and pin description.

---

# M6_LowNoiseAnomaly/README.md

Place the GDS file with the following nomenclature in this folder: M6_LowNoiseAnomaly.gds

Here the Top Level Module Pin List : [PIN LIST](https://docs.google.com/spreadsheets/d/1HLCBr9n6uBO21hwIzQUWf1YsKppcE_WuBvNP1LRq54w/edit?gid=530173844#gid=530173844)

<img width="763" height="631" alt="image" src="https://github.com/user-attachments/assets/347fd49f-7fbf-4a83-854c-e07eacbaa223" />

---

# M8_Nirvana/README.md

Place the GDS file with the following nomenclature in this folder: M8_Nirvana.gds

Also, update the README.md file to include the pin list and pin description.

---

# M9_ProfMorbius/README.md

Place the GDS file with the following nomenclature in this folder: M9_ProfMorbius.gds

Also, update the README.md file to include the pin list and pin description.

---
