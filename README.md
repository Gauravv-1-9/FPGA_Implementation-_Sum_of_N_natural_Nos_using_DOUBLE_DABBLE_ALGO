# FPGA Project : Verilog_Based_Implementation_of_Sum_of_N_natural_Nos_using_DOUBLE_DABBLE_ALGO

Sum of First N Natural Numbers

This FPGA project computes the **sum of the first N natural numbers** and displays the output on a **three-digit multiplexed seven-segment display**. The design is written in **Verilog HDL**, synthesized and implemented using **Xilinx Vivado**, and targeted for an **Nexys A7-100T FPGA**.

---

## 📌 Objective

Given a 4-bit input `N`, 

the FPGA calculates:

S = 1 + 2 + 3 + ..... + N = {N(N+1)}/{2}

The result is then converted to **BCD format** and displayed on a **3-digit seven-segment display**.

---

## 🧠 Features
- Binary-to-BCD conversion using the **Double-Dabble algorithm**
- Supports values of N from **0 to 15**
- Displays result up to **three digits**
- 7-segment multiplexed display driver with clock division
- Modular Verilog design for readability and reuse

---

## 🛠 Tools & Hardware

| Category | Details |
|---------|---------|
| HDL | Verilog |
| Design Tool | Xilinx Vivado |
| Target Device | Nexys A7-100T |
| Clock Source | On-board 100 MHz system clock |
| Inputs | `rst`, `init`, `N[3:0]` |
| Output | Three-digit 7-segment display |

---

## 📂 File Structure
src/                         # All synthesizable RTL sources

---> sum_of_natural_nos.v     # Logic for summing numbers iteratively using n(n+1)/2

---> sum_n.v                  # Wrapper: integrates summation + BCD conversion

---> dd_algo.v                # Single-stage "Add-3" logic (Double-Dabble core)

---> dd_integration.v         # Multi-stage Double-Dabble BCD converter

---> bcd7seg.v                # BCD to 7-segment display decoder

---> digit_mux_3.v            # Multiplexing logic for 3-digit 7-segment display

---> sevenSegrefresh.v        # Top-level: clock division + display refresh

sim/                         # Testbenches and waveform files

---> tb_sevenSegrefresh.v     # Top-level simulation testbench


## Block FLow

<img width="247" height="583" alt="image" src="https://github.com/user-attachments/assets/bb2c93a4-8bc3-4247-a39b-c1b76ebeae53" />



## 🚀 Running on FPGA

1. Open the project in Vivado.
2. Assign pins in the constraints file:
   - System clock pin
   - Switches (`N[3:0]`)
     <img width="1097" height="270" alt="Constraints_1" src="https://github.com/user-attachments/assets/76590e54-523d-4a33-a166-8631e362bb7a" />

   - Pushbuttons (`rst`, `init`)
   - 7-segment display pins
    <img width="1075" height="557" alt="Constraints_2" src="https://github.com/user-attachments/assets/f88043f1-81ea-4437-83af-f6510ca7ff4b" />

3. Synthesize → Implement → Generate Bitstream.
4. Program FPGA via Hardware Manager.
   ![IMG_20251124_002102](https://github.com/user-attachments/assets/c4a081b0-b2c7-4db3-88c8-949f9b4daa7a)
5. Set input `N` using switches and pulse `init`.

---

## 📷 Results 



| Actual FPGA Output Screenshots |
 Here , N =4-Bit Binary Input
 
 
 N=0001 
 
 <img width="642" height="600" alt="N = 0001" src="https://github.com/user-attachments/assets/21353a75-85f0-481e-8f61-7b5722e5f1fa" />

 N=0010 
 
 <img width="587" height="642" alt="N=0010" src="https://github.com/user-attachments/assets/13d75799-1abe-4145-a4cc-3a5eb92305e5" />
 
 N=0011
 
 <img width="537" height="496" alt="N=0011" src="https://github.com/user-attachments/assets/6807b7d2-a74e-412a-b114-315ef24ac295" />

 N=0100 
 
 <img width="582" height="482" alt="N=0100" src="https://github.com/user-attachments/assets/c55aa354-dbe4-4e90-bbe5-f95cf92280cb" />
 
 
 N=0101
 
 <img width="463" height="482" alt="N=0101" src="https://github.com/user-attachments/assets/45cfc981-180d-4380-8cad-83047144d69e" />
 
 
 N=0110
 
 <img width="500" height="487" alt="N=0110" src="https://github.com/user-attachments/assets/20b60f77-558d-4ed7-959a-2273f769ba7d" />

 
 N=0111
 
 <img width="437" height="472" alt="N=0111" src="https://github.com/user-attachments/assets/a7ef7577-fb7d-4370-bf6f-32e11a206060" />

 
 N=1000
 
 <img width="486" height="453" alt="N=1000" src="https://github.com/user-attachments/assets/88b4349d-0079-4454-bfce-08bb3b030576" />


 N=1001
 
 <img width="486" height="453" alt="N=1000" src="https://github.com/user-attachments/assets/17bfe281-ba7b-4130-9551-b516f2f25d96" />

 
 N=1010
 
 <img width="462" height="451" alt="N=1010" src="https://github.com/user-attachments/assets/a59efa34-2856-4aeb-a808-9d07652a3f68" />


 N=1011
 
 <img width="432" height="428" alt="N=1011" src="https://github.com/user-attachments/assets/d1612383-ab0d-4a43-927e-de1fccb23fce" />

 
 N=1100
 
 <img width="435" height="387" alt="N=1100" src="https://github.com/user-attachments/assets/138d8a71-4f8a-4291-8ace-eb32905c16ac" />

 N=1101
 
 <img width="452" height="447" alt="N=1101" src="https://github.com/user-attachments/assets/b92f05b0-bc7e-4295-98c4-66c1821ed0f1" />

 N=1110
 
 <img width="462" height="447" alt="N=1110" src="https://github.com/user-attachments/assets/e73ac0aa-a276-4529-b246-b2abeecf2c37" />

 N=1111
 
 <img width="468" height="392" alt="N=1111" src="https://github.com/user-attachments/assets/76ce8cbf-b040-422d-a34c-61b269bbc89a" />

---

## 📈 Future Improvements

- Increase N input beyond 4-bit range
- Implement debounce logic for buttons
- Add automatic count mode

---

## 🧑‍🎓 Author

**Name:** Gaurav Dinkar_  
**Field:** FPGA / VLSI  
**Board:** Artix-7 Based Platform  

---




