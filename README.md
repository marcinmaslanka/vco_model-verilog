# ⏱️ VCO Verilog-A Model for Cadence Virtuoso

This repository contains a Verilog-A model of a **Voltage-Controlled Oscillator (VCO)** and instructions on how to simulate it using **Cadence Virtuoso ADE**.

---


## 🔧 VCO Description

The VCO is modeled in Verilog-A and produces an output frequency based on the input control voltage.

### Main Parameters:
- `f0`: Center frequency [Hz]
- `Kvco`: Gain (Hz/V)
- `vctrl`: Control voltage input
- `out`: Oscillating output signal

---

## 🧰 How to Use in Cadence Virtuoso

### 1️⃣ Create the Verilog-A Cellview
1. Open **Library Manager**.
2. Create a **new cell**:
   - View Name: `veriloga`
   - Tool: `Verilog-A`
3. Paste the `vco.va` code and **Check & Save**.

### 2️⃣ Create the Symbol
- Right-click on the `veriloga` view.
- Select **Create Symbol**.
- Define pins and save.

### 3️⃣ Create a Testbench
- Open the **Schematic Editor**.
- Instantiate:
  - The VCO symbol
  - A **voltage source** for control voltage (`vctrl`)
  - Connect `out`, `vctrl`, and power supplies

![vco](https://github.com/user-attachments/assets/cb06cab5-192f-4e7c-8e71-07fac61f380f)


### 4️⃣ Setup Simulation (ADE)
- **Analysis**: Transient (`tran`)
- **Stop Time**:
  - Choose at least **10 cycles** at your lowest expected frequency.
  - Example: For 1 MHz output, simulate for **10 µs**
- **Inputs**:
  - Use a **DC**, **PWL**, or **sine** source on `vctrl`

![vco](https://github.com/user-attachments/assets/7c4b86a2-ee32-4e14-91a6-83bf4c05b376)


---

## 📈 Plotting
- Plot `V(out)` to observe frequency change.
- Sweep `vctrl` to test VCO gain and linearity.

---

## 📌 Example Use Case
```spice
f0    = 10e6     // 10 MHz
Kvco  = 20e6     // 20 MHz/V
vctrl = 0.5 V    // Output ≈ 20 MHz
