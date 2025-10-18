# Verilog_Full_Adder
Project Overview  This project implements a 1-bit Full Adder circuit using Verilog HDL, which performs binary addition of three input bits — two significant bits (A, B) and a carry-in (Cin) — to produce a sum (S) and a carry-out (Cout). The Full Adder is a core building block of digital arithmetic circuits such as adders, ALUs, and CPUs.
# ⚙️ Verilog_Full_Adder

### 🧩 Project Overview  
This project implements a **1-bit Full Adder** using **Verilog HDL**.  
A Full Adder is a fundamental **combinational logic circuit** that performs the addition of three binary inputs: two significant bits (**A**, **B**) and a **carry-in (Cin)**. It produces a **Sum (S)** and a **Carry-out (Cout)**.  

Full Adders are essential in **ALUs, processors, and digital systems**, serving as the basic unit for multi-bit addition and arithmetic operations.

---

## 🎯 Objectives
- Design and simulate a **1-bit Full Adder** in Verilog  
- Demonstrate **gate-level**, **dataflow**, and **behavioral modeling** styles  
- Develop a **testbench** to verify the correctness of the design  
- Observe the **waveform outputs** and verify truth table behavior  

---

## 🧠 Theoretical Background

A Full Adder adds three input bits: **A**, **B**, and **Cin**.

\[
\text{Sum} = A \oplus B \oplus C_{in}
\]
\[
\text{Carry} = (A \cdot B) + (B \cdot C_{in}) + (A \cdot C_{in})
\]

| Inputs | Output | |
|:------:|:-------:|:----:|
| A | B | Cin | Sum | Cout |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

---

## 💻 Design Methodology

### 🧩 1. Gate-Level Modeling

```verilog
module full_adder_gate (
  input A, B, Cin,
  output Sum, Cout
);
  wire w1, w2, w3;

  xor (w1, A, B);
  xor (Sum, w1, Cin);
  and (w2, w1, Cin);
  and (w3, A, B);
  or  (Cout, w2, w3);
endmodule

----

🧩 2. Dataflow Modeling

module full_adder_dataflow (
  input A, B, Cin,
  output Sum, Cout
);
  assign Sum  = A ^ B ^ Cin;
  assign Cout = (A & B) | (B & Cin) | (A & Cin);
endmodule


🧩 3. Behavioral Modeling
module full_adder_behavioral (
  input A, B, Cin,
  output reg Sum, Cout
);
  always @(*) begin
    {Cout, Sum} = A + B + Cin;
  end
endmodule


## 🧪 Testbench Code






