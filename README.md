# 8-Bit Digital Logic Calculator (Gates, Decoders, Multiplexers)

This is an **8-bit calculator** project we built for a Digital Logic Design course.
Operands are two 4-bit values (A, B). Results are up to 8 bits to accommodate multiplication. Subtraction currently supports
positive results only. 

Everything is done in the [Digital](https://github.com/hneemann/Digital) logic simulator using circuits only — no code.

The calculator supports:

- **Addition**
- **Subtraction** (positive results)
- **Multiplication**

Each operand is a **4-bit value**, and the result shows up live on **seven-segment displays**, 
similar to a simple pocket calculator — except the numbers are entered in binary inside the simulator.

---

## 🔧 Implementations

We implemented the same calculator in **three different ways**, each using a different design style:

- `Project Calculator C.dig` – **Combinational / basic gates** 
  Uses AND / OR and other basic gates to build the datapath and control.

- `Project Calculator D.dig` – **Decoder-based implementation** 
  Uses decoders to generate control signals and pick which outputs are active.

- `Project Calculator M.dig` – **Multiplexer-based implementation** 
  Uses multiplexers to route data and select the operation.

All three do the same job: 
> 8-bit calculator, three different digital logic techniques.

---

## 🧱 Building Blocks (Key Subcircuits)

The top-level calculators reuse several smaller circuits:

- `FA_4B+4B.dig` – 4-bit adder block 
- `FA_4B-4B.dig` – 4-bit subtractor block 
- `Multiplier (015)C.dig`, `Multiplier (015)D.dig`, `Multiplier (015)M.dig` – multiplier variants 
- `DDA 4B.dig`, `DDA 8B.dig` – binary-to-BCD conversion (Double Dabble Algorithm) 
- `7-segment driver.dig` – binary/BCD to 7-segment driver 
- `SEQ 0-7.dig` and a few others – sequence / testing / support circuits

File names are kept as they were in the original project so they still match the report and slides.

---

## 📂 Repository Structure

```text
.
├── circuits/                     # All Digital (.dig) circuit files
│   ├── Project Calculator C.dig
│   ├── Project Calculator D.dig
│   ├── Project Calculator M.dig
│   └── (...supporting subcircuits)
├── docs/
│   ├── 8 Bit Calculator.pdf      # Exported version of the slides (easy to view)
│   ├── 8 Bit Calculator.pptx     # Original PowerPoint (editable)
│   └── png/                      # Screenshots used in the docs
└── README.md

```

---

## ▶️ How to Run

1. Install **Digital** from its GitHub repo or releases page.
2. Open one of the main calculator files from the `circuits/` folder:
   - `Project Calculator C.dig`
   - `Project Calculator D.dig`
   - `Project Calculator M.dig`
3. Set the binary inputs for the two 4-bit operands.
4. Select the operation (ADD / SUB / MUL) using the control inputs.
5. Watch the **seven-segment displays** update with the result.

More details about the inputs/outputs are in the PDF and slides in `docs/`.

---

## 💡 What We Got Out of This Project

This wasn’t just “do the project and submit it”.

While building this calculator we actually got to:

- See how the **same idea** (ADD/SUB/MUL) can be built in three totally different ways: 
  basic gates, decoders, and multiplexers.
- Think more in terms of **blocks** instead of random wires everywhere:
  adders, multipliers, DDA, 7-seg driver, etc. that plug together like LEGO.
- Get more comfortable reading messy circuits and still understanding which part is doing the math and which part is just displaying logic.
- Translate the theory from class (K-maps, BCD, etc.) into something that actually **runs**.
- Research a way out of hurdles we faced during the building process, which is how we discovered the Double Dabble Algorithm.

It also forced us to be more organized with subcircuits and naming, which is why this repo exists in the first place.

---

## 👥 Project Context

This calculator started as a group project for a Digital Logic Design course.

We shared the work across the team, including:

-Designing and wiring the main calculator circuits
-Breaking the design into subcircuits (adders, multipliers, DDA, 7-segment driver)
-Preparing the documentation and slides

I took the lead on keeping the design structured and making sure the different implementations (gates / decoder / mux) stayed consistent.
This repo is my cleaned-up version of the project so it can be reused as a reference and shared publicly.

---

## 🚀 Things We’d Like to Add Later

If we (or I) come back to this project, here are some ideas to extend it:

- **Full signed support** – handle negative numbers properly, not just “positive results only”.
- **More operations** – bitwise AND/OR/XOR, comparisons (>, <, =), maybe even division.
- **Real hardware** – use switches, an FPGA or microcontroller, and real 7-seg displays to make a physical version.

For now, this stays as a logic-simulator project, but it’s a solid base for any future “real” calculator build.
