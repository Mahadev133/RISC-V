RISC V Architecture<img width="1644" height="1062" alt="Screenshot 2026-01-17 141739" src="https://github.com/user-attachments/assets/842a9260-61c2-465e-b190-ec8496f25cb6" />

# ⚙️ Pipelined RISC-V Processor

A **pipelined RISC-V processor implemented in Verilog HDL**, designed to explore processor microarchitecture, instruction execution, pipelining, hazard handling, and forwarding.

The processor is divided into the classic five pipeline stages:

**Fetch → Decode → Execute → Memory → Write Back**

---

## 🧠 Processor Architecture

![RISC-V Architecture](YOUR_EXISTING_IMAGE_LINK_HERE)

> Keep the image already present in this README here.

---

## 🔄 Five-Stage Pipeline

```text
          ┌─────────┐
          │  FETCH  │
          │   IF    │
          └────┬────┘
               │
             IF/ID
               │
               ▼
          ┌─────────┐
          │ DECODE  │
          │   ID    │
          └────┬────┘
               │
             ID/EX
               │
               ▼
          ┌─────────┐
          │ EXECUTE │
          │   EX    │
          └────┬────┘
               │
             EX/MEM
               │
               ▼
          ┌─────────┐
          │ MEMORY  │
          │   MEM   │
          └────┬────┘
               │
             MEM/WB
               │
               ▼
          ┌──────────┐
          │WRITE BACK│
          │    WB    │
          └──────────┘
```

Pipelining allows multiple instructions to be processed simultaneously at different stages of execution.

---

## 🧩 RTL Modules

| Module | Function |
|---|---|
| `Pipeline_Top.v` | Top-level pipelined processor |
| `Fetch_Cycle.v` | Instruction fetch stage |
| `Decode_Cyle.v` | Instruction decode stage |
| `Execute_Cycle.v` | Execute stage |
| `Memory_Cyle.v` | Memory access stage |
| `Writeback_Cyle.v` | Write-back stage |
| `ALU.v` | Arithmetic Logic Unit |
| `Register_File.v` | General-purpose register file |
| `Control_Unit_Top.v` | Processor control unit |
| `Main_Decoder.v` | Main instruction decoder |
| `ALU_Decoder.v` | Generates ALU control signals |
| `Hazard_unit.v` | Pipeline hazard and forwarding logic |
| `Instruction_Memory.v` | Instruction memory |
| `Data_Memory.v` | Data memory |
| `PC.v` | Program counter |
| `PC_Adder.v` | Program-counter address calculation |
| `Sign_Extend.v` | Immediate/sign extension |
| `Mux.v` | Datapath multiplexers |

---

## ⚠️ Hazard Handling

Pipelined processors can encounter data and control hazards when multiple instructions overlap during execution.

The processor includes a dedicated:

`Hazard_unit.v`

for pipeline hazard management and forwarding.

```text
             ┌──────────────────────┐
             │     Hazard Unit      │
             └──────────┬───────────┘
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
         Forward A   Forward B   Pipeline
                                 Control
```

Forwarding allows results from later pipeline stages to be reused by instructions that require them without always waiting for register write-back.

---

## 🧮 Datapath

The processor datapath contains the major components required for instruction execution:

- Program Counter
- Instruction Memory
- Register File
- Immediate Extension
- ALU
- Data Memory
- Pipeline Registers
- Multiplexers
- Control Logic
- Forwarding Logic

---

## 🛠️ Technologies

- Verilog HDL
- RISC-V Architecture
- RTL Design
- Digital Logic Design
- Computer Architecture
- Pipelined Processor Design

---

## 📚 Concepts Demonstrated

This project demonstrates:

- Five-stage processor pipelining
- Instruction fetch and decoding
- Register-file operation
- ALU design
- Processor control logic
- Pipeline registers
- Data forwarding
- Hazard handling
- Instruction and data memory
- RTL-based CPU implementation

---

## 🚀 Future Improvements

- Extend instruction support
- Improve branch handling
- Add more comprehensive verification
- FPGA implementation
- Performance and timing analysis
